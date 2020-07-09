---
title: Указание параметров | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- stored procedures [SQL Server], parameters
- output parameters [SQL Server]
- input parameters [SQL Server]
ms.assetid: 902314fe-5f9c-4d0d-a0b7-27e67c9c70ec
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 56a9e844499d8cee843b596380edb726f3efdabe
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "85998139"
---
# <a name="specify-parameters"></a>Указание параметров
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Путем указания параметров процедуры вызывающие программы могут передавать значения в тело процедуры. Эти значения могут использоваться для разных целей во время исполнения процедуры. Параметры процедуры могут также возвращать значения вызывающей программе, если параметр помечен признаком OUTPUT.  
  
 Хранимая процедура может иметь не более 2100 параметров, каждый из которых имеет имя, тип данных и направление. При необходимости параметрам можно задавать значения по умолчанию.  
  
 В следующем разделе содержатся сведения о передаче значений параметрам и о том, как каждый из атрибутов параметров используется во время вызова процедуры.  
  
## <a name="passing-values-into-parameters"></a>Передача значений в параметры  
 Значения параметра, переданные при вызове процедуры, должны быть константами или переменными. Имя функции не может быть значением параметра. Переменные могут быть пользовательскими или системными, например \@\@spid.  
  
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
 При создании процедуры и объявлении имени параметра, последнее должно начинаться с единичного символа \@ и быть уникальным для всей процедуры.  
  
 Явные имена параметров и задание значений каждому параметру в процедуре позволяет передавать параметры в любом порядке. Например, если в процедуре **my_proc** ожидается три параметра с именами **\@first**, **\@second** и **\@third**, передаваемые в процедуру значения могут быть присвоены параметрам следующим образом: `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`.  
  
> [!NOTE]  
>  При указании одного значения параметра в формате **\@parameter =** _value_ необходимо точно так же предоставить все последующие параметры. Если значения параметра передаются не в формате **\@parameter =** _value_, значения должны передаваться в том порядке (слева направо), в котором они перечислены в инструкции CREATE PROCEDURE.  
  
> [!WARNING]  
>  Передача параметров в формате **\@parameter =** _value_ с ошибками приведет к возникновению ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и невозможности выполнения процедуры.  
  
## <a name="specifying-parameter-data-types"></a>Указание типов данных параметров  
 Параметры должны быть определены с типом данных в момент объявления в инструкции CREATE PROCEDURE. Тип данных параметра определяет тип и диапазон допустимых значений параметра при вызове процедуры. Например, параметр типа **tinyint** может принимать только численные значения в диапазоне от 0 до 255 в момент передачи этому параметру. При попытке выполнить процедуру со значением, не совместимым с типом данных, происходит ошибка.  
  
## <a name="specifying-parameter-default-values"></a>Указание значений параметра по умолчанию  
 Параметр считается необязательным, если он имеет значение по умолчанию при объявлении. Нет необходимости указывать значение необязательного параметра при вызове процедуры.  
  
 Значение параметра по умолчанию используется, когда:  
  
-   не указано значение для параметра при вызове процедуры.  
  
-   в качестве значения при вызове процедуры указывается ключевое слово DEFAULT.  
  
> [!NOTE]  
>  Если значением по умолчанию является символьная строка, включающая в себя знаки пробела или пунктуации, либо содержащая первым элементом число, например 6ххх, то ее следует заключить в одинарные прямые кавычки.  

> [!NOTE] 
> Параметры по умолчанию не поддерживаются для хранилища данных SQL Azure или Parallel Data Warehouse. 
  
 Если значение по умолчанию указать нельзя, укажите NULL. Желательно, чтобы процедура возвращала сообщение, если она выполняется без значения для параметра.  
  
 В следующем примере создается процедура `uspGetSalesYTD` с единственным входным параметром `@SalesPerson`. В качестве значения по умолчанию параметру присваивается значение NULL, которое используется в инструкциях обработки ошибок для выдачи сообщения, если процедура выполняется с неопределенным параметром `@SalesPerson` .  
  
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
EXEC Sales.uspGetSalesYTD;  
GO  
-- Run the procedure with an input value.  
EXEC Sales.uspGetSalesYTD N'Blythe';  
GO  
```  
  
 Хотя разрешается опустить параметры, для которых предоставлены значения по умолчанию, можно лишь подвергнуть усечению список параметров. Например, если у процедуры пять параметров, можно опустить как четвертый, так и пятый параметр. При этом нельзя пропустить четвертый параметр, если включен пятый, если только параметры не передаются в формате **\@parameter =** _value_.  
  
## <a name="specifying-parameter-direction"></a>Указание направления параметров  
 Параметр может быть как входным, когда значение передается в тело процедуры, так и выходным, возвращаемым процедурой вызывающей программе. По умолчанию параметр определен как входной.  
  
 Для указания выходного параметра в определении процедуры необходимо указать ключевое слово OUTPUT в инструкции CREATE PROCEDURE. Процедура, завершая свою работу, возвращает текущее значение выходного параметра в вызывающую программу. При выполнении процедуры вызывающая программа также должна использовать ключевое слово OUTPUT для сохранения значения параметра в переменной, которое затем может быть использовано в вызывающей программе.  
  
 В следующем примере создается процедура `Production.usp_GetList`, которая возвращает список продуктов, цены которых не превышают заданного значения. На данном примере демонстрируется использование нескольких инструкций SELECT и нескольких параметров OUTPUT. Параметры OUTPUT позволяют внешней процедуре, пакету или нескольким инструкциям [!INCLUDE[tsql](../../includes/tsql-md.md)] осуществлять доступ к набору значений во время выполнения процедуры.  
  
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
  
 Процедура `usp_GetList` возвращает из базы данных [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] список товаров (велосипедов) стоимостью менее $ 700. Параметры **\@cost** и **\@compareprices** инструкции OUTPUT используются в языке управления потоком для вывода информации в окне **Сообщения**.  
  
> [!NOTE]  
>  Переменная OUTPUT должна быть определена во время создания процедуры, а также в ходе использования переменной. Имена параметра и переменной не должны совпадать. При этом тип данных и положение параметра должны быть одинаковыми (если только не используется **\@listprice=** _переменная_).  
  
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
  
## <a name="see-also"></a>См. также:  
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)  
  
  
