---
title: Указание параметров | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- stored procedures [SQL Server], parameters
- output parameters [SQL Server]
- input parameters [SQL Server]
ms.assetid: 902314fe-5f9c-4d0d-a0b7-27e67c9c70ec
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fc633915c27d2e604db110b3c118c0b1c287029f
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084056"
---
# <a name="specify-parameters"></a>Указание параметров
  Путем указания параметров процедуры вызывающие программы могут передавать значения в тело процедуры. Эти значения могут использоваться для разных целей во время исполнения процедуры. Параметры процедуры могут также возвращать значения вызывающей программе, если параметр помечен признаком OUTPUT.  
  
 Хранимая процедура может иметь не более 2100 параметров, каждый из которых имеет имя, тип данных и направление. При необходимости параметрам можно задавать значения по умолчанию.  
  
 В следующем разделе содержатся сведения о передаче значений параметрам и о том, как каждый из атрибутов параметров используется во время вызова процедуры.  
  
## <a name="passing-values-into-parameters"></a>Передача значений в параметры  
 Значения параметра, переданные при вызове процедуры, должны быть константами или переменными. Имя функции не может быть значением параметра. Переменные могут быть пользовательские или системные переменные, такие как \@ \@spid.  
  
 В следующих примерах демонстрируется передача значений параметров процедуре `uspGetWhereUsedProductID`. В них показано, как передать в качестве параметров константы и переменные, а также как использовать переменную для передачи значения функции.  
  
```  
USE AdventureWorks2012;  
GO  
-- Passing values as constants.  
EXEC dbo.uspGetWhereUsedProductID 819, '20050225';  
GO  
-- Passing values as variables.  
DECLARE @ProductID int, @CheckDate datetime;  
SET @ProductID = 819;  
SET @CheckDate = '20050225';  
EXEC dbo.uspGetWhereUsedProductID @ProductID, @CheckDate;  
GO  
-- Try to use a function as a parameter value.  
-- This produces an error message.  
EXEC dbo.uspGetWhereUsedProductID 819, GETDATE();  
GO  
-- Passing the function value as a variable.  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
## <a name="specifying-parameter-names"></a>Указание имен параметров  
 При создании процедуры и объявлении имени параметра, имя параметра должно начинаться с одним \@ символов и должно быть уникальным в рамках процедуры.  
  
 Явные имена параметров и задание значений каждому параметру в процедуре позволяет передавать параметры в любом порядке. Например если процедура **my_proc** ожидает три параметра с именем  **\@первый**,  **\@второй**, и  **\@третий**, значения, передаваемые в процедуру могут быть присвоены именам параметров, таких как: `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`  
  
> [!NOTE]  
>  Если какое-либо из значений параметров указано в виде **/@parameter =***значение*, все последующие параметры необходимо задать в том же формате. Если значение параметра передаются не в виде **\@параметра = *** значение*, значения должны предоставляться в строгом порядке (слева направо), они перечислены в инструкции CREATE PROCEDURE.  
  
> [!WARNING]  
>  Параметры, переданные в виде **\@параметра = *** значение* с ошибками, приведет к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает ошибку и отменяет выполнение процедуры.  
  
## <a name="specifying-parameter-data-types"></a>Указание типов данных параметров  
 Параметры должны быть определены с типом данных в момент объявления в инструкции CREATE PROCEDURE. Тип данных параметра определяет тип и диапазон допустимых значений параметра при вызове процедуры. Например, параметр типа `tinyint` может принимать только численные значения в диапазоне от 0 до 255 в момент передачи этому параметру. При попытке выполнить процедуру со значением, не совместимым с типом данных, происходит ошибка.  
  
## <a name="specifying-parameter-default-values"></a>Указание значений параметра по умолчанию  
 Параметр считается необязательным, если он имеет значение по умолчанию при объявлении. Нет необходимости указывать значение необязательного параметра при вызове процедуры.  
  
 Значение параметра по умолчанию используется, когда:  
  
-   не указано значение для параметра при вызове процедуры.  
  
-   в качестве значения при вызове процедуры указывается ключевое слово DEFAULT.  
  
> [!NOTE]  
>  Если значением по умолчанию является символьная строка, включающая в себя знаки пробела или пунктуации, либо содержащая первым элементом число, например 6ххх, то ее следует заключить в одинарные прямые кавычки.  
  
 Если значение по умолчанию указать нельзя, укажите NULL. Желательно, чтобы процедура возвращала сообщение, если она выполняется без значения для параметра.  
  
 В следующем примере создается процедура `usp_GetSalesYTD` с единственным входным параметром `@SalesPerson`. В качестве значения по умолчанию параметру присваивается значение NULL, которое используется в инструкциях обработки ошибок для выдачи сообщения, если процедура выполняется с неопределенным параметром `@SalesPerson` .  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetSalesYTD  
@SalesPerson nvarchar(50) = NULL  -- NULL default value  
AS   
    SET NOCOUNT ON;   
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
BEGIN  
   PRINT 'ERROR: You must specify the last name of the sales person.'  
   RETURN  
END  
-- Get the sales for the specified sales person and   
-- assign it to the output parameter.  
SELECT SalesYTD  
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 Следующий пример выполняет процедуру. Первая инструкция выполняет процедуру без указания входного значения. В результате чего инструкции обработки ошибок процедуры возвращают пользовательское сообщение об ошибке. Вторая инструкция задает входное значение и возвращает ожидаемый результирующий набор.  
  
```  
-- Run the procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the procedure with an input value.  
EXEC Sales.usp_GetSalesYTD N'Blythe';  
GO  
```  
  
 Хотя разрешается опустить параметры, для которых предоставлены значения по умолчанию, можно лишь подвергнуть усечению список параметров. Например, если у процедуры пять параметров, можно опустить как четвертый, так и пятый параметр. Тем не менее пропустить четвертый параметр не может быть до тех пор, пока пятый включен, если параметры передаются в виде **\@параметра = *** значение*.  
  
## <a name="specifying-parameter-direction"></a>Указание направления параметров  
 Параметр может быть как входным, когда значение передается в тело процедуры, так и выходным, возвращаемым процедурой вызывающей программе. По умолчанию параметр определен как входной.  
  
 Для указания выходного параметра в определении процедуры необходимо указать ключевое слово OUTPUT в инструкции CREATE PROCEDURE. Процедура, завершая свою работу, возвращает текущее значение выходного параметра в вызывающую программу. При выполнении процедуры вызывающая программа также должна использовать ключевое слово OUTPUT для сохранения значения параметра в переменной, которое затем может быть использовано в вызывающей программе.  
  
 В следующем примере создается процедура `Production.usp`_`GetList` , которая возвращает список продуктов, стоимость которых не превышает заданного значения. На данном примере демонстрируется использование нескольких инструкций SELECT и нескольких параметров OUTPUT. Параметры OUTPUT позволяют внешней процедуре, пакету или нескольким инструкциям [!INCLUDE[tsql](../../includes/tsql-md.md)] осуществлять доступ к набору значений во время выполнения процедуры.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Production.uspGetList', 'P' ) IS NOT NULL   
    DROP PROCEDURE Production.uspGetList;  
GO  
CREATE PROCEDURE Production.uspGetList @Product varchar(40)   
    , @MaxPrice money   
    , @ComparePrice money OUTPUT  
    , @ListPrice money OUT  
AS  
    SET NOCOUNT ON;  
    SELECT p.[Name] AS Product, p.ListPrice AS 'List Price'  
    FROM Production.Product AS p  
    JOIN Production.ProductSubcategory AS s   
      ON p.ProductSubcategoryID = s.ProductSubcategoryID  
    WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice;  
-- Populate the output variable @ListPprice.  
SET @ListPrice = (SELECT MAX(p.ListPrice)  
        FROM Production.Product AS p  
        JOIN  Production.ProductSubcategory AS s   
          ON p.ProductSubcategoryID = s.ProductSubcategoryID  
        WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice);  
-- Populate the output variable @compareprice.  
SET @ComparePrice = @MaxPrice;  
GO  
  
```  
  
 Процедура `usp_GetList` возвращает из базы данных [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] список товаров (велосипедов) стоимостью менее $ 700. ВЫХОДНЫЕ параметры  **\@стоимость** и  **\@compareprices** используются с языком управления выполнением для вывода информации в **сообщений** окно.  
  
> [!NOTE]  
>  Переменная OUTPUT должна быть определена во время создания процедуры, а также в ходе использования переменной. Имена параметра и переменной не должны совпадать. Тем не менее, тип данных и порядок расположения параметров должны совпадать (если только не  **\@listprice =** *переменной* используется).  
  
```  
DECLARE @ComparePrice money, @Cost money ;  
EXECUTE Production.uspGetList '%Bikes%', 700,   
    @ComparePrice OUT,   
    @Cost OUTPUT  
IF @Cost <= @ComparePrice   
BEGIN  
    PRINT 'These products can be purchased for less than   
    $'+RTRIM(CAST(@ComparePrice AS varchar(20)))+'.'  
END  
ELSE  
    PRINT 'The prices for all products in this category exceed   
    $'+ RTRIM(CAST(@ComparePrice AS varchar(20)))+'.';  
  
```  
  
 Частичный результирующий набор:  
  
```  
Product                                            List Price  
-------------------------------------------------- ------------------  
Road-750 Black, 58                                 539.99  
Mountain-500 Silver, 40                            564.99  
Mountain-500 Silver, 42                            564.99  
...  
Road-750 Black, 48                                 539.99  
Road-750 Black, 52                                 539.99  
  
(14 row(s) affected)  
  
These items can be purchased for less than $700.00.  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
