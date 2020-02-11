---
title: Создание пользовательских функций (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 37a6846d8c185549bd6c54f32cb5ab02eb564d1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211712"
---
# <a name="create-user-defined-functions-database-engine"></a>Создание определяемых пользователем функций (компонент Database Engine)
  В этом разделе описывается создание определяемой пользователем функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание определяемой пользователем функции:**  
  
     [Создание скалярной функции](#Scalar)  
  
     [Создание функции, возвращающей табличное значение](#TVF)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Определяемые пользователем функции не могут выполнять действия, изменяющие состояние базы данных.  
  
-   Определяемые пользователем функции не могут содержать предложение OUTPUT INTO, целью которого является таблица.  
  
-   Определяемые пользователем функции не могут возвращать несколько результирующих наборов. Используйте хранимую процедуру, если нужно возвращать несколько результирующих наборов.  
  
-   Обработка ошибок в функциях, определяемых пользователем, ограниченна. Определяемая пользователем функция не поддерживает TRY... CATCH @ERROR или RAISERROR.  
  
-   Определяемые пользователем функции не могут вызывать хранимую процедуру, но могут вызывать расширенную хранимую процедуру.  
  
-   Определяемые пользователем функции не могут использовать динамический SQL и временные таблицы. Табличные переменные разрешены к использованию.  
  
-   Инструкцию SET нельзя использовать в определяемых пользователем функциях.  
  
-   Предложение FOR XML не допускается к использованию.  
  
-   Определяемые пользователем функции могут быть вложенными, то есть из одной функции может быть вызвана другая. Уровень вложенности увеличивается на единицу каждый раз, когда начинается выполнение вызванной функции и уменьшается на единицу, когда ее выполнение завершается. Вложенность определяемых пользователем функций не может превышать 32 уровней. Превышение максимального уровня вложенности приводит к ошибке выполнения для всей цепочки вызываемых функций. Каждый вызов управляемого кода из определяемой пользователем функции Transact-SQL считается одним уровнем вложенности из 32 возможных. Методы, вызываемые из управляемого кода, под это ограничение не подпадают.  
  
-   Следующие инструкции компонента Service Broker не могут быть включены в определение определяемой пользователем функции Transact-SQL:  
  
    -   BEGIN DIALOG CONVERSATION  
  
    -   END CONVERSATION  
  
    -   GET CONVERSATION GROUP  
  
    -   MOVE CONVERSATION  
  
    -   RECEIVE  
  
    -   SEND  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение CREATE FUNCTION на базу данных и разрешение ALTER на схему, в которой создается функция. Если в функции указан определяемый пользователем тип, требуется разрешение EXECUTE на этот тип.  
  
##  <a name="Scalar"></a>Скалярные функции  
 В следующем примере создается скалярная функция из нескольких инструкций в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Функция имеет один входной параметр `ProductID`и возвращает одно значение — количество указанного товара на складе.  
  
```  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END;  
GO  
  
```  
  
 В следующем примере функция `ufnGetInventoryStock` используется для получения сведений о количестве товаров с идентификаторами `ProductModelID` от 75 до 80.  
  
```  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
  
```  
  
##  <a name="TVF"></a>Функции с табличным значением  
 Результатом следующего примера является встроенная функция, создающая табличное значение в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Функция имеет один входной параметр — идентификатор клиента (магазина) — и возвращает столбцы `ProductID`, `Name`и столбец `YTD Total` со сведениями о продажах продукта за текущий год.  
  
```  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
  
```  
  
 В следующем примере функция вызывается с идентификатором 602.  
  
```  
SELECT * FROM Sales.ufn_SalesByStore (602);  
  
```  
  
 В следующем примере создается функция с табличным значением в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Функция имеет один входной параметр `EmployeeID` и возвращает список всех сотрудников, которые напрямую или косвенно отчитываются перед заданным сотрудником. Затем функция вызывается с указанием идентификатора сотрудника 109.  
  
```  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем функции](user-defined-functions.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)  
  
  
