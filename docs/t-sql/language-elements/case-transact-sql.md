---
title: CASE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CASE_TSQL
- CASE
dev_langs:
- TSQL
helpviewer_keywords:
- CASE expression [Transact-SQL]
- simple CASE expression
- comparing expressions
- searched CASE expression
ms.assetid: 658039ec-8dc2-4251-bc82-30ea23708cee
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1a81dcda3e14ad2637580ab74eb8cef3d2c99c1d
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36251966"
---
# <a name="case-transact-sql"></a>Выражение CASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Оценка списка условий и возвращение одного из нескольких возможных выражений результатов.  
  
 Выражение CASE имеет два формата:  
  
-   простое выражение CASE для определения результата сравнивает выражение с набором простых выражений;  
  
-   поисковое выражение CASE для определения результата вычисляет набор логических выражений.  
  
 Оба формата поддерживают дополнительный аргумент ELSE.  
  
 Выражение CASE может использоваться в любой инструкции или предложении, которые допускают допустимые выражения. Например, выражение CASE можно использовать в таких инструкциях, как SELECT, UPDATE, DELETE и SET, а также в таких предложениях, как select_list, IN, WHERE, ORDER BY и HAVING.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
Simple CASE expression:   
CASE input_expression   
     WHEN when_expression THEN result_expression [ ...n ]   
     [ ELSE else_result_expression ]   
END   
Searched CASE expression:  
CASE  
     WHEN Boolean_expression THEN result_expression [ ...n ]   
     [ ELSE else_result_expression ]   
END  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CASE  
     WHEN when_expression THEN result_expression [ ...n ]   
     [ ELSE else_result_expression ]   
END  
```  
  
## <a name="arguments"></a>Аргументы  
 *input_expression*  
 Выражение, полученное при использовании простого формата функции CASE. *input_expression* — это любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 WHEN *when_expression*  
 Простое выражение, с которым сравнивается *input_expression* при использовании простого формата CASE. *when_expression* — это любое допустимое выражение. Типы данных аргумента *input_expression* и каждого из выражений *when_expression* должны быть одинаковыми или неявно приводимыми друг к другу.  
  
 THEN *result_expression*  
 Выражение, возвращаемое, когда равенство *input_expression* и *when_expression* имеет значение TRUE или *Boolean_expression* имеет значение TRUE. *result expression* — это любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 ELSE *else_result_expression*  
 Это выражение, возвращаемое, если ни одна из операций сравнения не дает в результате TRUE. Если этот аргумент опущен и ни одна из операций сравнения не дает в результате TRUE, функция CASE возвращает NULL. *else_result_expression* — это любое допустимое выражение. Типы данных аргумента *else_result_expression* и каждого из выражений *result_expression* должны быть одинаковыми или неявно приводимыми друг к другу.  
  
 WHEN *Boolean_expression*  
 Логическое выражение, полученное при использовании поискового формата функции CASE. *Boolean_expression* — это любое допустимое логическое выражение.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает тип с наивысшим приоритетом из набора типов в выражении *result_expressions* и необязательном выражении *else_result_expression*. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
### <a name="return-values"></a>Возвращаемые значения  
 **Простое выражение CASE**  
  
 Простое выражение CASE сравнивает первое выражение с выражением в каждом предложении WHEN. Если эти выражения эквивалентны, то возвращается выражение в предложении THEN.  
  
-   Допускается только проверка равенства.  
  
-   В указанном порядке сравнивает значения выражений input_expression и when_expression для каждого предложения WHEN.  
  
-   Возвращает выражение *result_expression*, соответствующее первой операции *input_expression* = *when_expression*, равной TRUE.  
  
-   Если ни одна из операций *input_expression* = *when_expression* не дает значения TRUE, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] возвращает выражение *else_result_expression*, если указано предложение ELSE, или значение NULL, если предложение ELSE не указано.  
  
 **Поисковое выражение CASE**  
  
-   Вычисляет в указанном порядке выражения *Boolean_expression* для каждого предложения WHEN.  
  
-   Возвращает выражение *result_expression*, соответствующее первому выражению *Boolean_expression*, которое имеет значение TRUE.  
  
-   Если ни одно выражение *Boolean_expression* не равно TRUE, [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает выражение *else_result_expression*, если указано предложение ELSE, или значение NULL, если предложение ELSE не указано.  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] допускает применение в выражениях CASE не более 10 уровней вложенности.  
  
 Выражение CASE нельзя использовать для управления потоком выполнения инструкций Transact-SQL, блоков инструкций, определяемых пользователем функций и хранимых процедур. Список методов управления потоком см. в статье [Язык управления потоком (Transact-SQL)](~/t-sql/language-elements/control-of-flow.md).  
  
 Инструкция CASE последовательно оценивает свои условия и останавливается, когда находит первое условие, удовлетворяющее ей. В некоторых ситуациях выражение оценивается то того, как инструкция CASE получает результаты выражения в качестве входных данных. При оценке этих выражений возможны ошибки. Агрегатные выражения в аргументах WHEN инструкции CASE вначале оцениваются, после чего передаются инструкции CASE. Например в следующем запросе создается ошибка деления на ноль при вычислении значения агрегата MAX. Это происходит до оценки выражения CASE.  
  
```sql  
WITH Data (value) AS   
(   
SELECT 0   
UNION ALL   
SELECT 1   
)   
SELECT   
   CASE   
      WHEN MIN(value) <= 0 THEN 0   
      WHEN MAX(1/value) >= 100 THEN 1   
   END   
FROM Data ;  
```  
  
 Следует создавать зависимости только от порядка оценки условий WHEN для скалярных выражений (в том числе нескоррелированных вложенных запросов, возвращающих скалярные значения), а не для агрегатных выражений.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-select-statement-with-a-simple-case-expression"></a>A. Использование инструкции SELECT с простым выражением CASE  
 При использовании в инструкции `SELECT` простое выражение `CASE` позволяет выполнить только проверку на равенство. Другие проверки не выполняются. В следующем примере выражение `CASE` используется для изменения способа отображения категорий линейки продуктов с целью сделать их более понятными.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductNumber, Category =  
      CASE ProductLine  
         WHEN 'R' THEN 'Road'  
         WHEN 'M' THEN 'Mountain'  
         WHEN 'T' THEN 'Touring'  
         WHEN 'S' THEN 'Other sale items'  
         ELSE 'Not for sale'  
      END,  
   Name  
FROM Production.Product  
ORDER BY ProductNumber;  
GO  
  
```  
  
### <a name="b-using-a-select-statement-with-a-searched-case-expression"></a>Б. Использование инструкции SELECT с поисковым выражением CASE  
 При использовании в инструкции `SELECT` поисковое выражение `CASE` позволяет заменять значения в результирующем наборе в зависимости от результатов сравнения. В следующем примере отображается список цен в виде текстового комментария, основанного на диапазоне цен для продукта.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductNumber, Name, "Price Range" =   
      CASE   
         WHEN ListPrice =  0 THEN 'Mfg item - not for resale'  
         WHEN ListPrice < 50 THEN 'Under $50'  
         WHEN ListPrice >= 50 and ListPrice < 250 THEN 'Under $250'  
         WHEN ListPrice >= 250 and ListPrice < 1000 THEN 'Under $1000'  
         ELSE 'Over $1000'  
      END  
FROM Production.Product  
ORDER BY ProductNumber ;  
GO  
  
```  
  
### <a name="c-using-case-in-an-order-by-clause"></a>В. Использование выражения CASE в предложении ORDER BY  
 В следующем примере выражение CASE используется в предложении ORDER BY, чтобы определить порядок сортировки строк на основе значения заданного столбца таблицы. В первом примере вычисляется значение столбца `SalariedFlag` таблицы `HumanResources.Employee`. Сотрудники, для которых столбец `SalariedFlag` имеет значение 1, возвращаются в порядке `BusinessEntityID` (по убыванию). Сотрудники, для которых столбец `SalariedFlag` имеет значение 0, возвращаются в порядке `BusinessEntityID` (по возрастанию). Во втором примере результирующий набор упорядочивается по столбцу `TerritoryName`, если столбец `CountryRegionName` содержит значение «United States», и по столбцу `CountryRegionName` в остальных строках.  
  
```  
SELECT BusinessEntityID, SalariedFlag  
FROM HumanResources.Employee  
ORDER BY CASE SalariedFlag WHEN 1 THEN BusinessEntityID END DESC  
        ,CASE WHEN SalariedFlag = 0 THEN BusinessEntityID END;  
GO  
  
```  
  
```  
SELECT BusinessEntityID, LastName, TerritoryName, CountryRegionName  
FROM Sales.vSalesPerson  
WHERE TerritoryName IS NOT NULL  
ORDER BY CASE CountryRegionName WHEN 'United States' THEN TerritoryName  
         ELSE CountryRegionName END;  
  
```  
  
### <a name="d-using-case-in-an-update-statement"></a>Г. Использование выражения CASE в инструкции UPDATE  
 В следующем примере выражение CASE используется в инструкции UPDATE, чтобы определить значение, установленное в столбце `VacationHours` для сотрудников, у которых столбец `SalariedFlag` имеет значение 0. Если при вычитании 10 часов из `VacationHours` получается отрицательное значение, `VacationHours` увеличивается на 40 часов. В противном случае значение `VacationHours` увеличивается на 20 часов. С помощью предложения OUTPUT отображаются исходная и обновленная продолжительности отпуска.  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee  
SET VacationHours =   
    ( CASE  
         WHEN ((VacationHours - 10.00) < 0) THEN VacationHours + 40  
         ELSE (VacationHours + 20.00)  
       END  
    )  
OUTPUT Deleted.BusinessEntityID, Deleted.VacationHours AS BeforeValue,   
       Inserted.VacationHours AS AfterValue  
WHERE SalariedFlag = 0;  
  
```  
  
### <a name="e-using-case-in-a-set-statement"></a>Д. Использование выражения CASE в инструкции SET  
 В следующем примере выражение CASE используется в инструкции SET для функции `dbo.GetContactInfo` с табличным значением. В базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] все данные, связанные с людьми, хранятся в таблице `Person.Person`. Например, человек может быть сотрудником, представителем поставщика или заказчиком. Функция возвращает имя и фамилию человека с заданным `BusinessEntityID` и соответствующий тип контакта для этого пользователя. Выражение CASE в инструкции SET определяет отображаемое значение для столбца `ContactType` в зависимости от наличия столбца `BusinessEntityID` в таблицах `Employee`, `Vendor` или `Customer`.  
  
```  
  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.GetContactInformation(@BusinessEntityID int)  
    RETURNS @retContactInformation TABLE   
(  
BusinessEntityID int NOT NULL,  
FirstName nvarchar(50) NULL,  
LastName nvarchar(50) NULL,  
ContactType nvarchar(50) NULL,  
    PRIMARY KEY CLUSTERED (BusinessEntityID ASC)  
)   
AS   
-- Returns the first name, last name and contact type for the specified contact.  
BEGIN  
    DECLARE   
        @FirstName nvarchar(50),   
        @LastName nvarchar(50),   
        @ContactType nvarchar(50);  
  
    -- Get common contact information  
    SELECT   
        @BusinessEntityID = BusinessEntityID,   
@FirstName = FirstName,   
        @LastName = LastName  
    FROM Person.Person   
    WHERE BusinessEntityID = @BusinessEntityID;  
  
    SET @ContactType =   
        CASE   
            -- Check for employee  
            WHEN EXISTS(SELECT * FROM HumanResources.Employee AS e   
                WHERE e.BusinessEntityID = @BusinessEntityID)   
                THEN 'Employee'  
  
            -- Check for vendor  
            WHEN EXISTS(SELECT * FROM Person.BusinessEntityContact AS bec  
                WHERE bec.BusinessEntityID = @BusinessEntityID)   
                THEN 'Vendor'  
  
            -- Check for store  
            WHEN EXISTS(SELECT * FROM Purchasing.Vendor AS v            
                WHERE v.BusinessEntityID = @BusinessEntityID)   
                THEN 'Store Contact'  
  
            -- Check for individual consumer  
            WHEN EXISTS(SELECT * FROM Sales.Customer AS c   
                WHERE c.PersonID = @BusinessEntityID)   
                THEN 'Consumer'  
        END;  
  
    -- Return the information to the caller  
    IF @BusinessEntityID IS NOT NULL   
    BEGIN  
        INSERT @retContactInformation  
        SELECT @BusinessEntityID, @FirstName, @LastName, @ContactType;  
    END;  
  
    RETURN;  
END;  
GO  
  
SELECT BusinessEntityID, FirstName, LastName, ContactType  
FROM dbo.GetContactInformation(2200);  
GO  
SELECT BusinessEntityID, FirstName, LastName, ContactType  
FROM dbo.GetContactInformation(5);  
  
```  
  
### <a name="f-using-case-in-a-having-clause"></a>Е. Использование выражения CASE в предложении HAVING  
 В следующем примере выражение CASE используется в предложении HAVING, чтобы ограничить строки, возвращаемые инструкцией SELECT. Инструкция возвращает максимальную почасовую ставку для каждой должности в таблице `HumanResources.Employee`. Предложение HAVING ограничивает должности, оставляя только те, которые заняты мужчинами с максимальной почасовой ставкой более 40 долларов или женщинами с максимальной почасовой ставкой более 42 долларов.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT JobTitle, MAX(ph1.Rate)AS MaximumRate  
FROM HumanResources.Employee AS e  
JOIN HumanResources.EmployeePayHistory AS ph1 ON e.BusinessEntityID = ph1.BusinessEntityID  
GROUP BY JobTitle  
HAVING (MAX(CASE WHEN Gender = 'M'   
        THEN ph1.Rate   
        ELSE NULL END) > 40.00  
     OR MAX(CASE WHEN Gender  = 'F'   
        THEN ph1.Rate    
        ELSE NULL END) > 42.00)  
ORDER BY MaximumRate DESC;  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="g-using-a-select-statement-with-a-case-expression"></a>Ж. Использование инструкции SELECT с выражением CASE  
 При использовании в инструкции SELECT выражение CASE позволяет заменять значения в результирующем наборе в зависимости от результатов сравнения. В приведенном ниже примере выражение CASE используется для изменения способа отображения категорий линейки продуктов с целью сделать их более понятными. Если значение отсутствует, выводится текст "Not for sale".  
  
```  
-- Uses AdventureWorks  
  
SELECT   ProductAlternateKey, Category =  
      CASE ProductLine  
         WHEN 'R' THEN 'Road'  
         WHEN 'M' THEN 'Mountain'  
         WHEN 'T' THEN 'Touring'  
         WHEN 'S' THEN 'Other sale items'  
         ELSE 'Not for sale'  
      END,  
   EnglishProductName  
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="h-using-case-in-an-update-statement"></a>З. Использование выражения CASE в инструкции UPDATE  
 В следующем примере выражение CASE используется в инструкции UPDATE, чтобы определить значение, установленное в столбце `VacationHours` для сотрудников, у которых столбец `SalariedFlag` имеет значение 0. Если при вычитании 10 часов из `VacationHours` получается отрицательное значение, `VacationHours` увеличивается на 40 часов. В противном случае значение `VacationHours` увеличивается на 20 часов.  
  
```  
-- Uses AdventureWorks   
  
UPDATE dbo.DimEmployee  
SET VacationHours =   
    ( CASE  
         WHEN ((VacationHours - 10.00) < 0) THEN VacationHours + 40  
         ELSE (VacationHours + 20.00)   
       END  
    )   
WHERE SalariedFlag = 0;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [COALESCE (Transact-SQL)](../../t-sql/language-elements/coalesce-transact-sql.md)   
 [IIF (Transact-SQL)](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [CHOOSE (Transact-SQL)](../../t-sql/functions/logical-functions-choose-transact-sql.md)  
  
  



