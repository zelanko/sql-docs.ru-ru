---
title: "WITH обобщенное_табличное_выражение (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WITH common_table_expression
- WITH_TSQL
- WITH
- common table expression
dev_langs:
- TSQL
helpviewer_keywords:
- WITH common_table_expression clause
- CTEs
- hierarchical queries [SQL Server], WITH common_table_expression
- recursive CTEs [SQL Server]
- recursive queries [SQL Server]
- common table expressions
- MAXRECURSION hint
- clauses [SQL Server], WITH common_table_expression
ms.assetid: 27cfb819-3e8d-4274-8bbe-cbbe4d9c2e23
caps.latest.revision: 60
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a065ef1f5c21d0fb5a458d55108acd8a9fd0678e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="with-commontableexpression-transact-sql"></a>WITH обобщенное_табличное_выражение (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задается временно именованный результирующий набор, называемый обобщенным табличным выражением (ОТВ). Он извлекается при выполнении простого запроса и определяется в области выполнения одиночной инструкции SELECT, INSERT, UPDATE или DELETE. Это предложение может использоваться также в инструкции CREATE VIEW как часть определяющей ее инструкции SELECT. Обобщенное табличное выражение может включать ссылки на само себя. Такое выражение называется рекурсивным обобщенным табличным выражением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[ WITH <common_table_expression> [ ,...n ] ]  
  
<common_table_expression>::=  
    expression_name [ ( column_name [ ,...n ] ) ]  
    AS  
    ( CTE_query_definition )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression_name*  
Является допустимым идентификатором для обобщенного табличного выражения. *expression_name* должно отличаться от имени любого другого обобщенного табличного выражения определены в одном WITH \<общее_табличное_выражение > предложение, но *expression_name* может быть таким же, как имя Базовая таблица или представление. Любая ссылка на *expression_name* в запросе использует обобщенное табличное выражение, а не с базовым объектом.
  
 *column_name*  
 Задается имя столбца в обобщенном табличном выражении. Повторяющиеся имена в определении одного обобщенного табличного выражения не допускаются. Количество заданных имен столбцов должно соответствовать числу столбцов в результирующем наборе *определений запроса*. Список имен столбцов необязателен только в том случае, если всем результирующим столбцам в определении запроса присвоены уникальные имена.  
  
 *Определений запроса*  
 Задается инструкция SELECT, результирующий набор которой заполняет обобщенное табличное выражение. Инструкция SELECT для *определений запроса* должен соответствовать тем же требованиям, что и при создании представления, за исключением обобщенного табличного Выражения не может определять другое ОТВ. Дополнительные сведения см. в разделе «Примечания» и [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 Если несколько объектов *определений запроса* будет определено, определения запроса должны быть присоединены одним из следующих операторов работы с наборами: UNION ALL, UNION, EXCEPT или INTERSECT.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="guidelines-for-creating-and-using-common-table-expressions"></a>Рекомендации по созданию и использованию обобщенных табличных выражений  
 Следующие рекомендации относятся к нерекурсивным обобщенным табличным выражениям. Рекомендации, применимые к рекурсивным обобщенным табличным выражениям, см. в расположенном ниже разделе «Рекомендации по определению и использованию рекурсивных обобщенных табличных выражений».  
  
-   За обобщенным табличным выражением (ОТВ) должны следовать одиночные инструкции SELECT, INSERT, UPDATE или DELETE, ссылающиеся на некоторые или на все столбцы ОТВ. Обобщенное табличное выражение может задаваться также в инструкции CREATE VIEW как часть определяющей инструкции SELECT представления.  
  
-   Несколько определений запросов обобщенных табличных выражений (ОТВ) могут быть определены в нерекурсивных ОТВ. Определения могут объединяться одним из следующих операторов работы с наборами: UNION ALL, UNION, INTERSECT или EXCEPT.  
  
-   Обобщенные табличные выражения (ОТВ) могут иметь ссылки на самих себя, а также на ОТВ, определенные до этого в том же предложении WITH. Ссылки на определяемые далее обобщенные табличные выражения недопустимы.  
  
-   Задание в одном обобщенном табличном выражении нескольких предложений WITH недопустимо. Например если *определений запроса* содержит вложенный запрос, этот вложенный запрос не может содержать вложенное предложение WITH, определяющее другое обобщенное табличное Выражение.  
  
-   Следующие предложения не может использоваться в *определений запроса*:  
  
    -   ORDER BY (за исключением случаев задания предложения TOP)  
  
    -   INTO  
  
    -   Предложение OPTION с указаниями запроса  
  
    -   FOR BROWSE  
  
-   Если обобщенное табличное выражение используется в инструкции, являющейся частью пакета, то за инструкцией, стоящей перед ней, должен следовать символ точки с запятой.  
  
-   Запрос, ссылающийся на обобщенное табличное выражение, может использоваться для определения курсора.  
  
-   В обобщенном табличном выражении могут быть ссылки на таблицы, находящиеся на удаленных серверах.  
  
-   При выполнении обобщенного табличного выражения (ОТВ) между указаниями, ссылающимися на ОТВ, может быть конфликт с другими указаниями, обнаруживаемыми, когда ОТВ обращаются к их базовым таблицам, так же, как если бы указания ссылались на представления в запросах. Когда это происходит, запрос возвращает ошибку.  
  
## <a name="guidelines-for-defining-and-using-recursive-common-table-expressions"></a>Рекомендации по созданию и использованию рекурсивных обобщенных табличных выражений  
 Следующие рекомендации применимы к определению рекурсивных обобщенных табличных выражений.  
  
-   Определение рекурсивного обобщенного табличного выражения должно содержать по крайней мере два определения обобщенного табличного выражения запросов — закрепленный элемент и рекурсивный элемент. Может быть определено несколько закрепленных элементов и рекурсивных элементов, однако все определения запросов закрепленного элемента должны быть поставлены перед первым определением рекурсивного элемента. Все определения обобщенных табличных выражений запросов (ОТВ) являются закрепленными элементами, если только они не ссылаются на само ОТВ.  
  
-   Элементы привязки должны объединяться одним из следующих операторов работы с наборами: UNION ALL, UNION, INTERSECT или EXCEPT. UNION ALL является единственным оператором над множествами, который может находиться между последним закрепленным элементом и первым рекурсивным элементом, а также может применяться при объединении нескольких рекурсивных элементов.  
  
-   Количество столбцов членов указателя и рекурсивных элементов должно совпадать.  
  
-   Тип данных столбца в рекурсивном элементе должен совпадать с типом данных соответствующего столбца в закрепленном элементе.  
  
-   Предложение FROM рекурсивного элемента должно ссылаться только один раз на обобщенное табличное выражение *expression_name*.  
  
-   Следующие элементы не разрешены в *определений запроса* рекурсивного элемента:  
  
    -   SELECT DISTINCT  
  
    -   GROUP BY  
  
    -   PIVOT (Если уровень совместимости базы данных имеет значение 110 или больше. В разделе [критические изменения в функциях ядра СУБД в SQL Server 2016](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).)  
  
    -   HAVING  
  
    -   Скалярное агрегирование  
  
    -   В начало  
  
    -   LEFT, RIGHT, OUTER JOIN (INNER JOIN допускается)  
  
    -   Вложенные запросы  
  
    -   Указание, применимое к рекурсивной ссылке на обобщенное *определений запроса*.  
  
 Следующие рекомендации применимы к использованию рекурсивных обобщенных табличных выражений.  
  
-   Все столбцы, возвращаемые рекурсивным обобщенным табличным выражением, могут содержать значения NULL, независимо от того, могут ли иметь значения NULL столбцы, возвращаемые участвующими инструкциями SELECT.  
  
-   Неправильно составленное рекурсивное ОТВ может привести к бесконечному циклу. Например, если определение запроса рекурсивного элемента возвращает одинаковые значения как для родительского, так и для дочернего столбца, то образуется бесконечный цикл. Для предотвращения бесконечного цикла можно ограничить количество уровней рекурсии, допустимых для определенной инструкции, при помощи указания MAXRECURSION и значения в диапазоне от 0 до 32767 в предложении OPTION инструкции INSERT, UPDATE, DELETE или SELECT. Это дает возможность контролировать выполнение инструкции до тех пор, пока не будет разрешена проблема с кодом, из-за которой происходит зацикливание программы. Серверное значение по умолчанию равно 100. Если указано значение 0, ограничения не применяются. В одной инструкции может быть указано только одно значение MAXRECURSION. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
-   Представление, содержащее рекурсивное обобщенное табличное выражение, не может использоваться для обновления данных.  
  
-   Курсоры могут определяться на запросах при помощи обобщенных табличных выражений. ОНО является *select_statement* аргумент, который определяет результирующий набор курсора. Для рекурсивных обобщенных табличных выражений допустимы только однонаправленные и статические курсоры (курсоры моментального снимка). Если в рекурсивном обобщенном табличном выражении указан курсор другого типа, тип курсора преобразуется в статический.  
  
-   В обобщенном табличном выражении могут быть ссылки на таблицы, находящиеся на удаленных серверах. Если на удаленный сервер имеются ссылки в рекурсивном элементе обобщенного табличного выражения, создается буфер для каждой удаленной таблицы, так что к таблицам может многократно осуществляться локальный доступ. Если это запрос обобщенного табличного выражения, Index Spool/Lazy Spools отображается в плане запроса и будет иметь дополнительный предикат WITH STACK. Это один из способов подтверждения надлежащей рекурсии.  
  
-   Аналитические и агрегатные функции в рекурсивной части обобщенных табличных выражений применяются для задания текущего уровня рекурсии, а не для задания обобщенных табличных выражений. Такие функции, как ROW_NUMBER, работают только с подмножествами данных, которые передаются им текущим уровнем рекурсии, но не со всем множеством данных, которые передаются в рекурсивную часть обобщенного табличного выражения. Дополнительные сведения см. пример л. Использование аналитических функций в рекурсивном ОТВ, которое соответствует.  
  
## <a name="features-and-limitations-of-common-table-expressions-in-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Возможности и ограничения общие табличные выражения в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Текущая реализация обобщенных табличных выражений в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] имеют следующие возможности и ограничения:  
  
-   Обобщенное табличное Выражение может быть указано в **ВЫБЕРИТЕ** инструкции.  
  
-   Обобщенное табличное Выражение может быть указано в **CREATE VIEW** инструкции.  
  
-   Обобщенное табличное Выражение может быть указано в **CREATE TABLE AS SELECT** инструкции (CTAS).  
  
-   Обобщенное табличное Выражение может быть указано в **СОЗДАНИЯ УДАЛЕННОГО TABLE AS SELECT** инструкции (CRTAS).  
  
-   Обобщенное табличное Выражение может быть указано в **CREATE EXTERNAL TABLE AS SELECT** инструкции (CETAS).  
  
-   Удаленную таблицу можно ссылаться из обобщенного табличного Выражения.  
  
-   Внешнюю таблицу можно ссылаться из обобщенного табличного Выражения.  
  
-   Несколько определений запроса обобщенного табличного Выражения могут быть определены в обобщенного табличного Выражения.  
  
-   Обобщенное табличное Выражение должно следовать один **ВЫБЕРИТЕ** инструкции. **Вставить**, **обновление**, **удаление**, и **СЛИЯНИЯ** операторы не поддерживаются.  
  
-   Обобщенное табличное выражение, которое включает в себя ссылки на себя (Рекурсивное обобщенное табличное выражение) не поддерживается.  
  
-   Указание более одного **WITH** предложение в обобщенное табличное Выражение недопустимо. Например, если определений запроса содержит вложенный запрос, этот вложенный запрос не может содержать вложенный **WITH** предложение, определяющее другое обобщенное табличное Выражение.  
  
-   **ORDER BY** предложения не может использоваться в определений запроса, за исключением случаев **ВЕРХНЕЙ** указано предложение.  
  
-   Если обобщенное табличное выражение используется в инструкции, являющейся частью пакета, то за инструкцией, стоящей перед ней, должен следовать символ точки с запятой.  
  
-   При использовании в инструкции, созданные **sp_prepare**, обобщенных табличных выражений будет функционировать так же, как другие **ВЫБЕРИТЕ** инструкций в PDW. Однако если обобщенных табличных выражений используются как часть подготовил CETAS **sp_prepare**, поведения можно отложить от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и других инструкций PDW из-за привязки, каким образом реализуется для **sp_prepare**. Если **ВЫБЕРИТЕ** , ссылки на обобщенное табличное Выражение использует неверный столбец, который не существует в обобщенного табличного Выражения, **sp_prepare** пройдет без обнаружения ошибки, однако данная ошибка возникает во время **sp_execute**  вместо него.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-simple-common-table-expression"></a>A. Создание простого обобщенного табличного выражения  
 В следующем примере выводится общее количество заказов на продажу в год для каждого коммерческого представителя в [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
  
-- Define the CTE expression name and column list.  
WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
AS  
-- Define the CTE query.  
(  
    SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
)  
-- Define the outer query referencing the CTE name.  
SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
FROM Sales_CTE  
GROUP BY SalesYear, SalesPersonID  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
### <a name="b-using-a-common-table-expression-to-limit-counts-and-report-averages"></a>Б. Использование обобщенного табличного выражения для ограничения общего и среднего количества отчетов  
 В следующем примере выводится среднее количество заказов на продажу за все годы для коммерческих представителей.  
  
```  
WITH Sales_CTE (SalesPersonID, NumberOfOrders)  
AS  
(  
    SELECT SalesPersonID, COUNT(*)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
    GROUP BY SalesPersonID  
)  
SELECT AVG(NumberOfOrders) AS "Average Sales Per Person"  
FROM Sales_CTE;  
GO  
```  
  
### <a name="c-using-multiple-cte-definitions-in-a-single-query"></a>В. Использование нескольких определений ОТВ (обобщенных табличных выражений) в одном запросе  
 В следующем примере показано, как определить несколько ОТВ в одном запросе. Обратите внимание, что для разделения определений запросов обобщенных табличных выражений используется запятая. Функция FORMAT, используемая для отображения денежных сумм в формате валюты, доступна в SQL Server 2012 и более поздних версиях.  
  
```  
  
WITH Sales_CTE (SalesPersonID, TotalSales, SalesYear)  
AS  
-- Define the first CTE query.  
(  
    SELECT SalesPersonID, SUM(TotalDue) AS TotalSales, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
       GROUP BY SalesPersonID, YEAR(OrderDate)  
  
)  
,   -- Use a comma to separate multiple CTE definitions.  
  
-- Define the second CTE query, which returns sales quota data by year for each sales person.  
Sales_Quota_CTE (BusinessEntityID, SalesQuota, SalesQuotaYear)  
AS  
(  
       SELECT BusinessEntityID, SUM(SalesQuota)AS SalesQuota, YEAR(QuotaDate) AS SalesQuotaYear  
       FROM Sales.SalesPersonQuotaHistory  
       GROUP BY BusinessEntityID, YEAR(QuotaDate)  
)  
  
-- Define the outer query by referencing columns from both CTEs.  
SELECT SalesPersonID  
  , SalesYear  
  , FORMAT(TotalSales,'C','en-us') AS TotalSales  
  , SalesQuotaYear  
  , FORMAT (SalesQuota,'C','en-us') AS SalesQuota  
  , FORMAT (TotalSales -SalesQuota, 'C','en-us') AS Amt_Above_or_Below_Quota  
FROM Sales_CTE  
JOIN Sales_Quota_CTE ON Sales_Quota_CTE.BusinessEntityID = Sales_CTE.SalesPersonID  
                    AND Sales_CTE.SalesYear = Sales_Quota_CTE.SalesQuotaYear  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
 Здесь приводится частичный результирующий набор.  
  
```  
  
SalesPersonID SalesYear   TotalSales    SalesQuotaYear SalesQuota  Amt_Above_or_Below_Quota  
------------- ---------   -----------   -------------- ---------- ----------------------------------   
  
274           2005        $32,567.92    2005           $35,000.00  ($2,432.08)  
274           2006        $406,620.07   2006           $455,000.00 ($48,379.93)  
274           2007        $515,622.91   2007           $544,000.00 ($28,377.09)  
274           2008        $281,123.55   2008           $271,000.00  $10,123.55  
  
```  
  
### <a name="d-using-a-recursive-common-table-expression-to-display-multiple-levels-of-recursion"></a>Г. Использование рекурсивного обобщенного табличного выражения для отображения нескольких уровней рекурсии  
 В следующем примере представлен иерархический список руководителей и служащих, отчитывающихся перед ними. Пример начинается с создания и заполнения таблицы `dbo.MyEmployees`.  
  
```  
-- Create an Employee table.  
CREATE TABLE dbo.MyEmployees  
(  
EmployeeID smallint NOT NULL,  
FirstName nvarchar(30)  NOT NULL,  
LastName  nvarchar(40) NOT NULL,  
Title nvarchar(50) NOT NULL,  
DeptID smallint NOT NULL,  
ManagerID int NULL,  
 CONSTRAINT PK_EmployeeID PRIMARY KEY CLUSTERED (EmployeeID ASC)   
);  
-- Populate the table with values.  
INSERT INTO dbo.MyEmployees VALUES   
 (1, N'Ken', N'Sánchez', N'Chief Executive Officer',16,NULL)  
,(273, N'Brian', N'Welcker', N'Vice President of Sales',3,1)  
,(274, N'Stephen', N'Jiang', N'North American Sales Manager',3,273)  
,(275, N'Michael', N'Blythe', N'Sales Representative',3,274)  
,(276, N'Linda', N'Mitchell', N'Sales Representative',3,274)  
,(285, N'Syed', N'Abbas', N'Pacific Sales Manager',3,273)  
,(286, N'Lynn', N'Tsoflias', N'Sales Representative',3,285)  
,(16,  N'David',N'Bradley', N'Marketing Manager', 4, 273)  
,(23,  N'Mary', N'Gibson', N'Marketing Specialist', 4, 16);  
```  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(ManagerID, EmployeeID, Title, EmployeeLevel) AS   
(  
    SELECT ManagerID, EmployeeID, Title, 0 AS EmployeeLevel  
    FROM dbo.MyEmployees   
    WHERE ManagerID IS NULL  
    UNION ALL  
    SELECT e.ManagerID, e.EmployeeID, e.Title, EmployeeLevel + 1  
    FROM dbo.MyEmployees AS e  
        INNER JOIN DirectReports AS d  
        ON e.ManagerID = d.EmployeeID   
)  
SELECT ManagerID, EmployeeID, Title, EmployeeLevel   
FROM DirectReports  
ORDER BY ManagerID;  
GO  
```  
  
### <a name="e-using-a-recursive-common-table-expression-to-display-two-levels-of-recursion"></a>Д. Использование рекурсивного обобщенного табличного выражения для отображения двух уровней рекурсии  
 В следующем примере представлены руководители и отчитывающиеся перед ними служащие. Количество возвращаемых уровней ограничено двумя.  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(ManagerID, EmployeeID, Title, EmployeeLevel) AS   
(  
    SELECT ManagerID, EmployeeID, Title, 0 AS EmployeeLevel  
    FROM dbo.MyEmployees   
    WHERE ManagerID IS NULL  
    UNION ALL  
    SELECT e.ManagerID, e.EmployeeID, e.Title, EmployeeLevel + 1  
    FROM dbo.MyEmployees AS e  
        INNER JOIN DirectReports AS d  
        ON e.ManagerID = d.EmployeeID   
)  
SELECT ManagerID, EmployeeID, Title, EmployeeLevel   
FROM DirectReports  
WHERE EmployeeLevel <= 2 ;  
GO  
  
```  
  
### <a name="f-using-a-recursive-common-table-expression-to-display-a-hierarchical-list"></a>Е. Использование рекурсивного обобщенного табличного выражения для отображения иерархического списка  
 Следующий пример строится на примере D с добавлением имен руководителей и служащих и соответствующих им должностей. Иерархия руководителей и служащих дополнительно выделяется с помощью соответствующих отступов на каждом уровне.  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(Name, Title, EmployeeID, EmployeeLevel, Sort)  
AS (SELECT CONVERT(varchar(255), e.FirstName + ' ' + e.LastName),  
        e.Title,  
        e.EmployeeID,  
        1,  
        CONVERT(varchar(255), e.FirstName + ' ' + e.LastName)  
    FROM dbo.MyEmployees AS e  
    WHERE e.ManagerID IS NULL  
    UNION ALL  
    SELECT CONVERT(varchar(255), REPLICATE ('|    ' , EmployeeLevel) +  
        e.FirstName + ' ' + e.LastName),  
        e.Title,  
        e.EmployeeID,  
        EmployeeLevel + 1,  
        CONVERT (varchar(255), RTRIM(Sort) + '|    ' + FirstName + ' ' +   
                 LastName)  
    FROM dbo.MyEmployees AS e  
    JOIN DirectReports AS d ON e.ManagerID = d.EmployeeID  
    )  
SELECT EmployeeID, Name, Title, EmployeeLevel  
FROM DirectReports   
ORDER BY Sort;  
GO  
```  
  
### <a name="g-using-maxrecursion-to-cancel-a-statement"></a>Ж. Использование подсказки MAXRECURSION для отмены инструкции  
 Подсказка `MAXRECURSION` может использоваться для предотвращения входа в бесконечный цикл из-за неверно сформированного рекурсивного CTE-выражения. В следующем примере преднамеренно формируется бесконечный цикл и используется указание `MAXRECURSION` для ограничения числа уровней рекурсии двумя.  
  
```  
USE AdventureWorks2012;  
GO  
--Creates an infinite loop  
WITH cte (EmployeeID, ManagerID, Title) as  
(  
    SELECT EmployeeID, ManagerID, Title  
    FROM dbo.MyEmployees  
    WHERE ManagerID IS NOT NULL  
  UNION ALL  
    SELECT cte.EmployeeID, cte.ManagerID, cte.Title  
    FROM cte   
    JOIN  dbo.MyEmployees AS e   
        ON cte.ManagerID = e.EmployeeID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT EmployeeID, ManagerID, Title  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 После исправления ошибки в коде подсказка MAXRECURSION больше не нужна. В следующем примере приводится правильный код.  
  
```  
USE AdventureWorks2012;  
GO  
WITH cte (EmployeeID, ManagerID, Title)  
AS  
(  
    SELECT EmployeeID, ManagerID, Title  
    FROM dbo.MyEmployees  
    WHERE ManagerID IS NOT NULL  
  UNION ALL  
    SELECT  e.EmployeeID, e.ManagerID, e.Title  
    FROM dbo.MyEmployees AS e  
    JOIN cte ON e.ManagerID = cte.EmployeeID  
)  
SELECT EmployeeID, ManagerID, Title  
FROM cte;  
GO  
```  
  
### <a name="h-using-a-common-table-expression-to-selectively-step-through-a-recursive-relationship-in-a-select-statement"></a>З. Использование обобщенного табличного выражения для выборочного прохождения рекурсивной связи в инструкции SELECT  
 В следующем примере показана иерархия узлов и компонентов продукции, необходимых для создания велосипеда для `ProductAssemblyID = 800`.  
  
```  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
SELECT AssemblyID, ComponentID, Name, PerAssemblyQty, EndDate,  
        ComponentLevel   
FROM Parts AS p  
    INNER JOIN Production.Product AS pr  
    ON p.ComponentID = pr.ProductID  
ORDER BY ComponentLevel, AssemblyID, ComponentID;  
GO  
```  
  
### <a name="i-using-a-recursive-cte-in-an-update-statement"></a>И. Использование рекурсивного обобщенного табличного выражения в инструкции UPDATE  
 В следующем примере обновляется `PerAssemblyQty` значение для всех элементов, которые используются для построения продукта «Road-550-W Yellow, 44» `(ProductAssemblyID``800`). Обобщенное табличное выражение возвращает иерархический список деталей, которые непосредственно используются для сборки `ProductAssemblyID 800`, и компонентов, которые используются для сборки этих деталей и т. д. Изменяются только строки, возвращенные обобщенным табличным выражением.  
  
```  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
UPDATE Production.BillOfMaterials  
SET PerAssemblyQty = c.PerAssemblyQty * 2  
FROM Production.BillOfMaterials AS c  
JOIN Parts AS d ON c.ProductAssemblyID = d.AssemblyID  
WHERE d.ComponentLevel = 0;  
```  
  
### <a name="j-using-multiple-anchor-and-recursive-members"></a>К. Использование нескольких привязок и рекурсивных элементов  
 В следующем примере несколько членов указателя и рекурсивных элементов используются для возврата всех предков указанного лица. Создается и заполняется значениями таблица для формирования генеалогии семьи, возвращаемой рекурсивным обобщенным табличным выражением.  
  
```  
-- Genealogy table  
IF OBJECT_ID('dbo.Person','U') IS NOT NULL DROP TABLE dbo.Person;  
GO  
CREATE TABLE dbo.Person(ID int, Name varchar(30), Mother int, Father int);  
GO  
INSERT dbo.Person   
VALUES(1, 'Sue', NULL, NULL)  
      ,(2, 'Ed', NULL, NULL)  
      ,(3, 'Emma', 1, 2)  
      ,(4, 'Jack', 1, 2)  
      ,(5, 'Jane', NULL, NULL)  
      ,(6, 'Bonnie', 5, 4)  
      ,(7, 'Bill', 5, 4);  
GO  
-- Create the recursive CTE to find all of Bonnie's ancestors.  
WITH Generation (ID) AS  
(  
-- First anchor member returns Bonnie's mother.  
    SELECT Mother   
    FROM dbo.Person  
    WHERE Name = 'Bonnie'  
UNION  
-- Second anchor member returns Bonnie's father.  
    SELECT Father   
    FROM dbo.Person  
    WHERE Name = 'Bonnie'  
UNION ALL  
-- First recursive member returns male ancestors of the previous generation.  
    SELECT Person.Father  
    FROM Generation, Person  
    WHERE Generation.ID=Person.ID  
UNION ALL  
-- Second recursive member returns female ancestors of the previous generation.  
    SELECT Person.Mother  
    FROM Generation, dbo.Person  
    WHERE Generation.ID=Person.ID  
)  
SELECT Person.ID, Person.Name, Person.Mother, Person.Father  
FROM Generation, dbo.Person  
WHERE Generation.ID = Person.ID;  
GO  
```  
  
###  <a name="bkmkUsingAnalyticalFunctionsInARecursiveCTE"></a>Л. Использование аналитических функций в рекурсивном обобщенном табличном выражении  
 Следующий пример демонстрирует проблему, которая может возникнуть при использовании аналитической или агрегатной функции в рекурсивной части обобщенного табличного выражения.  
  
```  
DECLARE @t1 TABLE (itmID int, itmIDComp int);  
INSERT @t1 VALUES (1,10), (2,10);   
  
DECLARE @t2 TABLE (itmID int, itmIDComp int);   
INSERT @t2 VALUES (3,10), (4,10);   
  
WITH vw AS  
 (  
    SELECT itmIDComp, itmID  
    FROM @t1  
  
    UNION ALL  
  
    SELECT itmIDComp, itmID  
    FROM @t2  
)   
,r AS  
 (  
    SELECT t.itmID AS itmIDComp  
           , NULL AS itmID  
           ,CAST(0 AS bigint) AS N  
           ,1 AS Lvl  
    FROM (SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4) AS t (itmID)   
  
UNION ALL  
  
SELECT t.itmIDComp  
    , t.itmID  
    , ROW_NUMBER() OVER(PARTITION BY t.itmIDComp ORDER BY t.itmIDComp, t.itmID) AS N  
    , Lvl + 1  
FROM r   
    JOIN vw AS t ON t.itmID = r.itmIDComp  
)   
  
SELECT Lvl, N FROM r;  
```  
  
 Следующие результаты являются ожидаемыми результатами выполнения запроса.  
  
```  
Lvl  N  
1    0  
1    0  
1    0  
1    0  
2    4  
2    3  
2    2  
2    1  
```  
  
 Следующие результаты являются фактическими результатами выполнения запроса.  
  
```  
Lvl  N  
1    0  
1    0  
1    0  
1    0  
2    1  
2    1  
2    1  
2    1  
```  
  
 `N` возвращает 1 для каждого прохода рекурсивной части ОТВ, так как в `ROWNUMBER` передается только подмножество данных для данного уровня рекурсии. Для каждой итерации рекурсивной части запроса в `ROWNUMBER` передается только одна строка.  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="l-creating-a-simple-common-table-expression"></a>М. Создание простого обобщенного табличного выражения  
 В следующем примере выводится общее количество заказов на продажу в год для каждого коммерческого представителя в [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
-- Uses AdventureWorks  
  
-- Define the CTE expression name and column list.  
WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
AS  
-- Define the CTE query.  
(  
    SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
)  
-- Define the outer query referencing the CTE name.  
SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
FROM Sales_CTE  
GROUP BY SalesYear, SalesPersonID  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
### <a name="m-using-a-common-table-expression-to-limit-counts-and-report-averages"></a>Н. Использование обобщенного табличного выражения для ограничения общего и среднего количества отчетов  
 В следующем примере выводится среднее количество заказов на продажу за все годы для коммерческих представителей.  
  
```  
WITH Sales_CTE (SalesPersonID, NumberOfOrders)  
AS  
(  
    SELECT SalesPersonID, COUNT(*)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
    GROUP BY SalesPersonID  
)  
SELECT AVG(NumberOfOrders) AS "Average Sales Per Person"  
FROM Sales_CTE;  
GO  
```  
  
### <a name="n-using-a-common-table-expression-within-a-ctas-statement"></a>О. Использование обобщенного табличного выражения в операторе CTAS  
 Следующий пример создает новую таблицу, содержащую общее количество заказов на продажу в год для каждого торгового представителя в [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
-- Uses AdventureWorks  
  
CREATE TABLE SalesOrdersPerYear  
WITH  
(  
    DISTRIBUTION = HASH(SalesPersonID)  
)  
AS  
    -- Define the CTE expression name and column list.  
    WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
    AS  
    -- Define the CTE query.  
    (  
        SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
        FROM Sales.SalesOrderHeader  
        WHERE SalesPersonID IS NOT NULL  
    )  
    -- Define the outer query referencing the CTE name.  
    SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
    FROM Sales_CTE  
    GROUP BY SalesYear, SalesPersonID  
    ORDER BY SalesPersonID, SalesYear;  
GO  
```  
  
### <a name="o-using-a-common-table-expression-within-a-cetas-statement"></a>П. Использование обобщенного табличного выражения в операторе CETAS  
 В следующем примере создается новый внешней таблицы, содержащего общее количество заказов на продажу в год для каждого торгового представителя в [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
-- Uses AdventureWorks  
  
CREATE EXTERNAL TABLE SalesOrdersPerYear  
WITH  
(  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:5000/files/Customer',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|' )   
)  
AS  
    -- Define the CTE expression name and column list.  
    WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
    AS  
    -- Define the CTE query.  
    (  
        SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
        FROM Sales.SalesOrderHeader  
        WHERE SalesPersonID IS NOT NULL  
    )  
    -- Define the outer query referencing the CTE name.  
    SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
    FROM Sales_CTE  
    GROUP BY SalesYear, SalesPersonID  
    ORDER BY SalesPersonID, SalesYear;  
GO  
```  
  
### <a name="p-using-multiple-comma-separated-ctes-in-a-statement"></a>Т. С помощью нескольких разделенный запятыми обобщенных табличных выражений в операторе  
 В следующем примере показано, включая два обобщенных табличных выражений в одной инструкции. Обобщенных табличных выражений не могут быть вложенными (без рекурсии).  
  
```  
WITH   
 CountDate (TotalCount, TableName) AS  
    (  
     SELECT COUNT(datekey), 'DimDate' FROM DimDate  
    ) ,  
 CountCustomer (TotalAvg, TableName) AS  
    (  
     SELECT COUNT(CustomerKey), 'DimCustomer' FROM DimCustomer  
    )  
SELECT TableName, TotalCount FROM CountDate  
UNION ALL  
SELECT TableName, TotalAvg FROM CountCustomer;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [EXCEPT и INTERSECT &#40; Transact-SQL &#41;](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)  
  
  

