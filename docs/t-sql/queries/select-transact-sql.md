---
title: "SELECT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT_TSQL
- SELECT
dev_langs:
- TSQL
helpviewer_keywords:
- retrieving rows
- SELECT statement [SQL Server]
- SELECT statement [SQL Server], about SELECT statement
- row retrieval [SQL Server], SELECT statement
- DML [SQL Server], SELECT statement
- data manipulation language [SQL Server], SELECT statement
- row retrieval [SQL Server]
- queries [SQL Server], results
ms.assetid: dc85caea-54d1-49af-b166-f3aa2f3a93d0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: b8cca7419cce15dcbb83b4aa72dc551e5eb89eb1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="select-transact-sql"></a>SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Извлекает строки из базы данных и позволяет делать выборку одной или нескольких строк или столбцов из одной или нескольких таблиц в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Полный синтаксис инструкции SELECT сложен, однако основные предложения можно вкратце описать следующим образом:  
  
[С {[WITH XMLNAMESPACES,] [ \<общее_табличное_выражение >]}]
  
 ВЫБЕРИТЕ *select_list* [INTO *new_table* ]  
  
 [Из *table_source* ] [ГДЕ *search_condition* ]  
  
 [ GROUP BY *group_by_expression* ]  
  
 [НАЛИЧИЕ *search_condition* ]  
  
 [ORDER BY *order_expression* [ASC | DESC]]  
  
 UNION, EXCEPT и INTERSECT операторы можно использовать между запросами, чтобы сравнить их результаты в один результирующий набор или объединения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<SELECT statement> ::=    
    [ WITH { [ XMLNAMESPACES ,] [ <common_table_expression> [,...n] ] } ]  
    <query_expression>   
    [ ORDER BY { order_by_expression | column_position [ ASC | DESC ] }   
  [ ,...n ] ]   
    [ <FOR Clause>]   
    [ OPTION ( <query_hint> [ ,...n ] ) ]   
<query_expression> ::=   
    { <query_specification> | ( <query_expression> ) }   
    [  { UNION [ ALL ] | EXCEPT | INTERSECT }  
        <query_specification> | ( <query_expression> ) [...n ] ]   
<query_specification> ::=   
SELECT [ ALL | DISTINCT ]   
    [TOP ( expression ) [PERCENT] [ WITH TIES ] ]   
    < select_list >   
    [ INTO new_table ]   
    [ FROM { <table_source> } [ ,...n ] ]   
    [ WHERE <search_condition> ]   
    [ <GROUP BY> ]   
    [ HAVING < search_condition > ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[ WITH <common_table_expression> [ ,...n ] ]  
SELECT <select_criteria>  
[;]  
  
<select_criteria> ::=  
    [ TOP ( top_expression ) ]   
    [ ALL | DISTINCT ]   
    { * | column_name | expression } [ ,...n ]   
    [ FROM { table_source } [ ,...n ] ]  
    [ WHERE <search_condition> ]   
    [ GROUP BY <group_by_clause> ]   
    [ HAVING <search_condition> ]   
    [ ORDER BY <order_by_expression> ]  
    [ OPTION ( <query_option> [ ,...n ] ) ]  
  
```  
  
## <a name="remarks"></a>Remarks  
 Учитывая сложность инструкции SELECT, элементы ее синтаксиса и аргументы подробно представлены в предложении:  
  
|||  
|-|-|  
|[WITH XMLNAMESPACES](../../t-sql/xml/with-xmlnamespaces.md)<br /><br /> [WITH <обобщенное_табличное_выражение>](../../t-sql/queries/with-common-table-expression-transact-sql.md)|[НАЛИЧИЕ](../../t-sql/queries/select-having-transact-sql.md)|  
|[Предложение SELECT](../../t-sql/queries/select-clause-transact-sql.md)|[UNION](../../t-sql/language-elements/set-operators-union-transact-sql.md)|  
|[Предложение INTO](../../t-sql/queries/select-into-clause-transact-sql.md)|[EXCEPT и INTERSECT](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)|  
|[FROM](../../t-sql/queries/from-transact-sql.md)|[ORDER BY](../../t-sql/queries/select-order-by-clause-transact-sql.md)|  
|[WHERE](../../t-sql/queries/where-transact-sql.md)|[Предложение FOR](../../t-sql/queries/select-for-clause-transact-sql.md)|  
|[ГРУППИРОВАТЬ ПО](../../t-sql/queries/select-group-by-transact-sql.md)|[Предложение OPTION](../../t-sql/queries/option-clause-transact-sql.md)|  
  
 Порядок предложений в инструкции SELECT имеет значение. Любое из необязательных предложений может быть опущено; но если необязательные предложения используются, они должны следовать в определенном порядке.  
  
 Инструкции SELECT разрешено использовать в определяемых пользователем функциях только в том случае, если списки выбора этих инструкций содержат выражения, которые присваивают значения переменным, локальным для функций.  
  
 Четырехкомпонентное имя, использующее функцию OPENDATASOURCE в качестве части имени сервера, может служить в качестве исходной таблицы в любом месте инструкции SELECT, где может появляться имя таблицы. Четырехчастное имя не может быть указано для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Для инструкций SELECT, которые задействуют удаленные таблицы, существуют некоторые ограничения на синтаксис.  
  
## <a name="logical-processing-order-of-the-select-statement"></a>Логический порядок обработки инструкции SELECT  
 Следующие действия демонстрируют логический порядок обработки или порядок привязки инструкции SELECT. Этот порядок определяет, когда объекты, определенные в одном шаге, становятся доступными для предложений в последующих шагах. Например, если обработчик запросов можно привязать (для доступа) к таблицам или представлениям, определенным в предложении FROM, эти объекты и их столбцы становятся доступными для всех последующих шагов. И наоборот, поскольку предложение SELECT является шагом 8, любые псевдонимы столбцов или производных столбцов, определенные в этом предложении, не могут быть объектом для ссылки предыдущих предложений. Вместе с тем к ним могут обращаться последующие предложения, например предложение ORDER BY. Фактическое физическое выполнение оператора определяется обработчиком запросов и порядок может отличаться от этого списка.  
  
1.  FROM  
2.  ON  
3.  JOIN  
4.  WHERE  
5.  GROUP BY  
6.  WITH CUBE или WITH ROLLUP  
7.  HAVING  
8.  SELECT  
9. DISTINCT  
10. ORDER BY  
11. В начало  

> [!WARNING]
> Предыдущей последовательности обычно верно. Однако существуют редких случаях, где последовательности может отличаться.
>
> Предположим, у вас есть кластеризованный индекс в представлении и представлении исключает некоторые строки таблицы и список ВЫБИРАЕМЫХ столбцов в представлении использует ПРЕОБРАЗОВАНИЯ, который изменяет тип данных из *varchar* для *целое*. В этом случае ПРЕОБРАЗОВАНИЯ, может выполняться перед выполняет предложение WHERE. Нередко на самом деле. Часто имеется возможность изменить представление во избежание различные последовательности, если он имеет значение в случае. 

## <a name="permissions"></a>Разрешения  
 Для выборки данных требуется разрешение **SELECT** на таблицу или представление, которое может быть унаследовано из области более высокого уровня, например разрешение **SELECT** на схему или разрешение **CONTROL** на таблицу. Или членство в **db_datareader** или **db_owner** предопределенных ролей базы данных или **sysadmin** предопределенной роли сервера. Создание новой таблицы с помощью **SELECTINTO** также необходимы **CREATETABLE** разрешение и **ALTERSCHEMA** на схему, которой принадлежит новая таблица.  
  
## <a name="examples"></a>Примеры:   
В следующих примерах используется база данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
### <a name="a-using-select-to-retrieve-rows-and-columns"></a>A. Использование SELECT для получения строк и столбцов  
 В этом разделе приведены три примера кода. В первом примере кода возвращает все строки (предложение WHERE не указано), а также все столбцы (с помощью `*`) из `DimEmployee` таблицы.  
  
```sql  
SELECT *  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
 В следующем примере с помощью присвоения псевдонимов таблицы для достижения такого же результата.  
  
```sql  
SELECT e.*  
FROM DimEmployee AS e  
ORDER BY LastName;  
```  
  
 Этот пример возвращает все строки (предложение WHERE не указано) и подмножества столбцов (`FirstName`, `LastName`, `StartDate`) из `DimEmployee` в таблицу `AdventureWorksPDW2012` базы данных. Заголовок третьего столбца переименовывается в `FirstDay`.  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
ORDER BY LastName;  
```  
  
 Этот пример возвращает только строки для `DimEmployee` , имеющих `EndDate` , не равно NULL и `MaritalStatus` из am "(состоит в браке).  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
WHERE EndDate IS NOT NULL   
AND MaritalStatus = 'M'  
ORDER BY LastName;  
```  
  
### <a name="b-using-select-with-column-headings-and-calculations"></a>Б. Использование SELECT с заголовками столбцов и вычислениями  
 Следующий пример возвращает все строки из `DimEmployee` таблицы, а затем вычисляет валовой заработной платы для каждого сотрудника на основе их `BaseRate` и 40-часовую рабочую неделю.  
  
```sql  
SELECT FirstName, LastName, BaseRate, BaseRate * 40 AS GrossPay  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
### <a name="c-using-distinct-with-select"></a>В. Совместное использование DISTINCT и SELECT  
 В следующем примере используется `DISTINCT` создать список всех уникальных заголовков в `DimEmployee` таблицы.  
  
```sql  
SELECT DISTINCT Title  
FROM DimEmployee  
ORDER BY Title;  
```  
  
### <a name="d-using-group-by"></a>Г. Использование GROUP BY  
 В следующем примере вычисляется общая сумма всех продаж за каждый день.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
 Из-за `GROUP BY` предложение, возвращается только одна строка, содержащая суммы всех продаж за каждый день.  
  
### <a name="e-using-group-by-with-multiple-groups"></a>Д. Использование GROUP BY с несколькими группами  
 В следующем примере вычисляется средние цены и суммы продаж через Интернет за каждый день, сгруппированные по дате заказа и ключ повышения роли.  
  
```sql  

SELECT OrderDateKey, PromotionKey, AVG(SalesAmount) AS AvgSales, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey, PromotionKey  
ORDER BY OrderDateKey;   
```  
  
### <a name="f-using-group-by-and-where"></a>Е. Использование GROUP BY и WHERE  
 Следующий пример помещает результаты в группы после извлечения строк со значениями даты заказа позже 1 августа 2002 г.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
WHERE OrderDateKey > '20020801'  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="g-using-group-by-with-an-expression"></a>Ж. Использование GROUP BY с выражением  
 В следующем примере производится группировка с помощью выражения. Группировку можно производить только с помощью выражения, не содержащего агрегатных функций.  
  
```sql  
SELECT SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY (OrderDateKey * 10);  
```  
  
### <a name="h-using-group-by-with-order-by"></a>З. Использование GROUP BY с ORDER BY  
 В следующем примере вычисляется суммы продаж в день, а также заказы по дням.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-the-having-clause"></a>И. Использование предложения HAVING  
 В этом запросе используется `HAVING` предложений, чтобы ограничить результаты поиска.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
HAVING OrderDateKey > 20010000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>См. также  
 [ВЫБЕРИТЕ примеры &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)  
 [Указания &#40; Transact-SQL &#41;](../../t-sql/queries/hints-transact-sql.md)
  

