---
title: Реализация OR оператора в скомпилированных хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce9b8660fa52d2a09302b51b0f95e368071caa4d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228184"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a>Реализация оператора OR в скомпилированных в собственном коде хранимых процедурах
  Операторы OR не поддерживаются в предикатах запросов в скомпилированных в собственном коде хранимых процедурах. Так как операторы NOT также не поддерживаются в предикатах запросов в скомпилированных в собственном коде хранимых процедурах, использование операторов OR нельзя имитировать только с помощью эквивалентных логических операторов. Однако результаты выполнения оператора OR можно имитировать с помощью переменных оптимизированных для памяти таблиц.  
  
## <a name="or-operator-in-where-clause"></a>Оператор OR в предложении WHERE  
 Если в предложении WHERE имеется оператор OR, то для имитации его поведения можно использовать следующий подход.  
  
1.  Создайте переменную оптимизированной для памяти таблицы с соответствующей схемой. Для этого требуется стандартный тип оптимизированной для памяти таблицы.  
  
2.  Начиная с оператора OR верхнего уровня, разделите предложение WHERE на две части в соответствии с предикатами, соединенными оператором OR. При наличии в предложении WHERE нескольких операторов OR это необходимо будет сделать несколько раз. Повторяйте этот шаг до тех пор, пока операторов OR больше не останется. Например, предположим, что имеется следующий предикат:  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     После выполнения этого шага у вас должны получиться следующие предикаты:  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  Выполните запрос с каждой из двух частей, образованных в шаге 2 в качестве предиката. Введите результат выполнения каждого запроса в переменную оптимизированной для памяти таблицы, созданной на шаге 1.  
  
4.  При необходимости удалите повторения из переменной оптимизированной для памяти таблицы.  
  
5.  Используйте содержимое переменной оптимизированной для памяти таблицы в качестве результата запроса.  
  
 В следующем образце используются таблицы из базы данных AdventureWorks2012, которые были обновлены для [!INCLUDE[hek_2](../includes/hek-2-md.md)]. Для загрузки файлов для этого примера можно на странице [баз данных AdventureWorks — 2012, 2008R2 и 2008](http://msftdbprodsamples.codeplex.com/releases/view/93587). Чтобы применить [!INCLUDE[hek_2](../includes/hek-2-md.md)] кода примера к базе данных AdventureWorks2012, перейдите к [образца SQL Server 2014 In-Memory OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Добавьте в базу данных следующую хранимую процедуру. Мы преобразуем эту хранимую процедуру так, чтобы она компилировалась в собственном коде.  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 После преобразования схема таблицы и хранимой процедуры будет выглядеть следующим образом.  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a>Оператор OR в условии JOIN  
 Если в условии JOIN инструкции SELECT есть оператор OR, то для имитации его работы можно использовать следующий подход. Если в условии JOIN есть несколько операторов OR или имеется несколько условий JOIN с операторами OR, выполнить это действие нужно будет несколько раз.  
  
 При наличии условий OUTER JOIN этот способ можно использовать в сочетании со способом для условий OUTER JOIN.  
  
1.  Создайте переменную оптимизированной для памяти таблицы с соответствующей схемой. Для этого требуется стандартный тип оптимизированной для памяти таблицы.  
  
2.  Разделите предикат из условия JOIN на две части в соответствии с предикатами, объединяемыми оператором OR. При наличии нескольких условий JOIN сделать это необходимо будет для каждого условия JOIN, а затем создать набор сочетаний получившихся фрагментов. Например, если есть три условия JOIN с одним оператором OR в каждом из них, количество предикатов может составить 2x2x2=8.  
  
3.  Для каждого предиката, полученного на шаге 2, создайте запрос, который будет вставлять результат его выполнения в переменную оптимизированной для памяти таблицы, созданной на шаге 1.  
  
4.  При необходимости удалите повторения из переменной оптимизированной для памяти таблицы.  
  
5.  Используйте содержимое переменной оптимизированной для памяти таблицы в качестве результата запроса.  
  
 В следующем образце используются таблицы из базы данных AdventureWorks2012, которые были обновлены для [!INCLUDE[hek_2](../includes/hek-2-md.md)]. Для загрузки файлов для этого примера можно на странице [баз данных AdventureWorks — 2012, 2008R2 и 2008](http://msftdbprodsamples.codeplex.com/releases/view/93587). Чтобы применить [!INCLUDE[hek_2](../includes/hek-2-md.md)] кода примера к базе данных AdventureWorks2012, перейдите к [образца SQL Server 2014 In-Memory OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Добавьте в базу данных следующую хранимую процедуру. Мы преобразуем эту хранимую процедуру так, чтобы она компилировалась в собственном коде. В этом образце используются условия INNER JOIN.  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 После преобразования схема таблицы и хранимой процедуры будет выглядеть следующим образом.  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a>Побочные эффекты  
 При наличии в предложении WHERE или условии JOIN нескольких операторов OR количество запросов, которые необходимо выполнить для имитации поведения, может увеличиваться экспоненциально. Из-за этого выполнение запросов может замедлиться или же может увеличиться объем используемой памяти из-за необходимости использовать переменные оптимизированных для памяти таблиц.  
  
## <a name="see-also"></a>См. также  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
