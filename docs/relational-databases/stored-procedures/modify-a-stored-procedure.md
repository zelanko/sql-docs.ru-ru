---
title: "Изменение хранимой процедуры | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stored-Procs
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6eb24cf562396f61af07735fa741e50d447a4b50
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="modify-a-stored-procedure"></a>Изменение хранимой процедуры
    
##  <a name="Top"></a> В этом разделе описывается, как изменить хранимую процедуру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)  
  
-   **To alter a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] нельзя преобразовать в хранимые процедуры CLR и наоборот.  
  
 Если предыдущее определение процедуры было создано с параметрами WITH ENCRYPTION или WITH RECOMPILE, эти параметры будут включены только в случае, если они указаны в инструкции ALTER PROCEDURE.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER PROCEDURE на процедуру.  
  
##  <a name="Procedures"></a> Изменение хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение процедуры в среде Management Studio**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните **Хранимые процедуры**, щелкните правой кнопкой мыши изменяемую процедуру, затем выберите **Изменить**.  
  
4.  Изменение текста хранимой процедуры.  
  
5.  Для проверки синтаксиса выберите пункт **Выполнить анализ** в меню **Запрос**.  
  
6.  Чтобы сохранить изменения определения процедуры, в меню **Запрос** выберите пункт **Выполнить**.  
  
7.  Чтобы сохранить обновленное определение процедуры в качестве скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] , в меню **Файл** выберите команду **Сохранить как...** Можно принять предложенное имя файла или заменить его новым, после чего следует нажать кнопку **Сохранить**.  
  
> [!IMPORTANT]  
>  Проверяйте все данные, вводимые пользователем. Не включайте их в сценарий, не выполнив проверку. Никогда не выполняйте команду, построенную на основании непроверенных пользовательских входных данных.  
  
###  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение процедуры в редакторе запросов**  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура. Также можно выбрать необходимую базу данных из списка доступных баз данных на панели инструментов. В данном примере выберите базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  В меню **Файл** выберите команду **Создать запрос**.  
  
4.  Скопируйте и вставьте следующий пример в редактор запросов. В этом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  В меню **Файл** выберите команду **Создать запрос**.  
  
6.  Скопируйте и вставьте следующий пример в редактор запросов. В следующем примере изменяется процедура `uspVendorAllInfo` . Предложение EXECUTE AS CALLER удаляется, и изменяется текст процедуры, чтобы возвращать только поставщиков, предлагающих конкретный товар. Содержимое результирующего набора определяется при помощи функций `LEFT` и `CASE` .  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  Чтобы сохранить изменения определения процедуры, в меню **Запрос** выберите пункт **Выполнить**.  
  
8.  Чтобы сохранить обновленное определение процедуры в качестве скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] , в меню **Файл** выберите команду **Сохранить как...** Можно принять предложенное имя файла или заменить его новым, после чего следует нажать кнопку **Сохранить**.  
  
9. Чтобы выполнить измененную хранимую процедуру, выполните следующий пример.  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a>См. также:  
 [ALTER PROCEDURE (Transact-SQL)](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
  

