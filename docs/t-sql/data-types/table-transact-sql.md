---
title: "Table (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b22ecfa04f949af77df974abc3359b7bc5144a82
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="table-transact-sql"></a>table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Специальный тип данных, который может быть использован для хранения результирующего набора для обработки в будущем. **Таблица** в основном используется для временного хранения набора строк, возвращаемых как результирующий набор функции, возвращающие табличные значения. Функции и переменные могут быть объявлены с типом **таблицы**. **Таблица** переменные могут использоваться в функциях, хранимых процедур и пакетов. При объявлении переменных типа **таблицы**, используйте [DECLARE @local_variable ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  

**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
## <a name="arguments"></a>Аргументы  
*table_type_definition*  
То же подмножество данных, которое используется для определения таблицы с помощью инструкции CREATE TABLE. Декларация таблицы включает определения столбцов, имен, типов данных и ограничений. К допустимым типам ограничений относятся только PRIMARY KEY, UNIQUE KEY и NULL.  
Дополнительные сведения о синтаксисе см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md), [Создать ФУНКЦИЮ &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md), и [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  
*collation_definition*  
Параметры сортировки столбца, который состоит из [!INCLUDE[msCoName](../../includes/msconame-md.md)] языковой стандарт Windows и стиль сравнения, языковой стандарт Windows и двоичном представлении или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметров сортировки. Если *collation_definition* не указан, столбец унаследует параметры сортировки текущей базы данных. Либо, если столбец определен как имеющий определяемый пользователем тип данных среды CLR, он унаследует параметры сортировки этого определяемого пользователем типа.
  
## <a name="remarks"></a>Замечания  
**Таблица** переменные можно ссылаться по имени в предложении FROM пакета, как показано в следующем примере:
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
Вне предложения FROM **таблицы** переменные должны ссылаться по псевдонимам, как показано в следующем примере:
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
**Таблица** переменные обеспечивают следующие преимущества для небольших запросов, которые содержат планы запросов, не изменяйте и когда соображения повторной компиляции являются доминирующими:
-   Объект **таблицы** переменной ведет себя как локальная переменная. Она имеет точно определенную область применения. Это функция, хранимая процедура или пакет, в котором она объявлена.  
     В пределах ее области действия **таблицы** переменная может использоваться как к обычной таблице. Она может быть применена в любом месте, где используется таблица или табличное выражение в инструкциях SELECT, INSERT, UPDATE и DELETE. Тем не менее **таблицы** не может использоваться в следующей инструкции:  
  
```sql
SELECT select_list INTO table_variable;
```
  
**Таблица** переменные автоматически очищаются в конце функции, хранимой процедуры или пакета, в котором они определены.
  
-   **Таблица** переменные, используемые в хранимых процедурах к повторным компиляциям хранимых процедур, чем при использовании временных таблиц при нет вариантов выбора основанный на стоимости, которые влияют на производительность.  
-   Транзакции с использованием **таблицы** переменных последнего только в течение обновления на **таблицы** переменной. Таким образом **таблицы** переменных требуют меньших блокировки и ведение журнала ресурсов.  
  
## <a name="limitations-and-restrictions"></a>ограничения
**Таблица** переменные не имеют статистики распределения, не будет вызывать повторных компиляций. Поэтому во многих случаях оптимизатор построит план запроса в предположении, что у табличной переменной нет строк. По этой причине следует проявлять осторожность относительно использования табличной переменной, если ожидается большое число строк (больше 100). В этом случае временные таблицы могут быть предпочтительным решением. Кроме того для запросов, которые объединяют табличную переменную с другими таблицами, можно используйте указание RECOMPILE, что вызовет оптимизатор использовать правильное количество элементов для табличной переменной.
  
**Таблица** переменные не поддерживаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] модели выбора с учетом затрат оптимизатора. Вследствие этого, они не должны использоваться при необходимости осуществления выбора с учетом затрат для получения эффективного плана запроса. Временные таблицы являются предпочтительными при необходимости осуществления выбора с учетом затрат. Обычно их следует использовать в запросах с соединениями, решениях в отношении параллелизма и при выборе индекса.
  
Запросы, изменяющие **таблицы** переменные не создают параллельных планов выполнения запроса. Производительность может снизиться при очень больших **таблицы** переменных, или **таблицы** переменных в сложных запросах, будут изменены. В подобных случаях целесообразно рассмотреть возможность использования временных таблиц. Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md). Запросы, которые считывают **таблицы** переменные, не изменяя их, могут выполняться параллельно.
  
Индексы не могут быть созданы явно на **таблицы** переменных и статистики не сохраняются на **таблицы** переменных. В некоторых случаях можно добиться повышения производительности за счет использования вместо табличных переменных временных таблиц, которые позволяют создавать индексы и вести статистический учет. Дополнительные сведения о временных таблицах см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).
  
ПРОВЕРОЧНЫЕ ограничения, значения по умолчанию и вычисляемых столбцов в **таблицы** объявление типа не может вызывать определяемые пользователем функции.
  
Выполнение операций назначения между **таблицы** переменных не поддерживается.
  
Поскольку **таблицы** переменные имеют ограниченную область применения и не являются частью постоянных баз данных, они не изменяются в случае откатов транзакций.
  
Табличные переменные нельзя изменить после их создания.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. Объявление переменной типа table  
В следующем примере создается переменная типа `table`, в которой хранятся значения, задаваемые в предложении OUTPUT инструкции UPDATE. Две следующие инструкции `SELECT` возвращают значения в табличную переменную `@MyTableVar`, а результаты операции обновления — в таблицу `Employee`. Обратите внимание, что результаты в `INSERTED.ModifiedDate` столбца отличаются от значений в `ModifiedDate` столбца в `Employee` таблицы. Это связано с тем, что для таблицы `AFTER UPDATE` определен триггер `ModifiedDate`, обновляющий значение `Employee` до текущей даты. Однако столбцы, возвращенные из `OUTPUT`, отражают состояние данных перед срабатыванием триггеров. Дополнительные сведения см. в разделе [предложение OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).
  
```sql
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>Б. Создание встроенной функции с табличным значением  
Результатом следующего примера является встроенная функция, возвращающая табличное значение. Он возвращает три столбца `ProductID`, `Name` и статистическое вычисление итоговых значений с начала года по магазину — `YTD Total` для каждого продукта, проданных в магазине.
  
```sql
USE AdventureWorks2012;  
GO  
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
GO  
```  
  
При вызове этой функции выполняется следующий запрос.
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>См. также:
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)  
[Определяемые пользователем функции](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[Использование возвращающих табличные значения параметры &#40; компонент Database Engine &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md)
  
  

