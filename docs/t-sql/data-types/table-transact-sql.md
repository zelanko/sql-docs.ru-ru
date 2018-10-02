---
title: table (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 67919bf72fa411aedb7709ef81c6af9ac4cb5121
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839762"
---
# <a name="table-transact-sql"></a>table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Специальный тип данных, который может быть использован для хранения результирующего набора для обработки в будущем. Тип **table** используется в первую очередь для временного хранения набора строк, возвращаемых как результирующий набор функции с табличным значением. Функции и переменные могут быть объявлены как имеющие тип **table**. Переменные **table** могут использоваться в функциях, хранимых процедурах и пакетах. Для объявления переменных типа **table** используйте инструкцию [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  

**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
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
Дополнительные сведения о синтаксисе см. в статьях [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md), [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md) и [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  
*collation_definition*  
Параметры сортировки столбцов, состоящие из поддерживаемых [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows языкового стандарта и стиля сопоставления, языкового стандарта Windows и двоичной записи или параметров сортировки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если значение аргумента *collation_definition* не установлено, столбец наследует параметры сортировки текущей базы данных. Либо, если столбец определен как имеющий определяемый пользователем тип данных среды CLR, он унаследует параметры сортировки этого определяемого пользователем типа.
  
## <a name="remarks"></a>Remarks  
На переменные **table** можно ссылаться по имени в пакетном предложении FROM, как показано в следующем примере:
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
Вне предложения FROM на переменные **table** нужно ссылаться по псевдонимам, как показано в следующем примере:
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
Переменные **table** предоставляют указанные ниже преимущества для запросов малого масштаба, которые содержат планы запросов и не меняются. Их также рекомендуется использовать, когда соображения повторной компиляции являются доминирующими.
-   Переменная **table** ведет себя как локальная переменная. Она имеет точно определенную область применения. Это функция, хранимая процедура или пакет, в котором она объявлена.  
     Внутри этой области переменная **table** может использоваться как обычная таблица. Она может быть применена в любом месте, где используется таблица или табличное выражение в инструкциях SELECT, INSERT, UPDATE и DELETE. Однако переменная **table** не может использоваться в следующей инструкции:  
  
```sql
SELECT select_list INTO table_variable;
```
  
Переменные **table** автоматически очищаются в конце функции, хранимой процедуры или пакета, где они были определены.
  
-   При использовании переменных **table** в хранимых процедурах приходится прибегать к повторным компиляциям реже, чем при использовании временных таблиц в случае отсутствия необходимости осуществлять выбор, основанный на стоимости, который влияет на производительность.  
-   Транзакции с использованием переменных **table** продолжаются только во время процесса обновления соответствующей переменной **table**. Поэтому переменные **table** реже подвергаются блокировке и требуют меньше ресурсов для ведения журналов.  
  
## <a name="limitations-and-restrictions"></a>ограничения
Переменные **table** не имеют статистики распределения. Они не запускают повторных компиляций. Поэтому во многих случаях оптимизатор построит план запроса в предположении, что у табличной переменной нет строк. По этой причине следует проявлять осторожность относительно использования табличной переменной, если ожидается большое число строк (больше 100). В этом случае временные таблицы могут быть предпочтительным решением. В качестве альтернативы для запросов, которые объединяют табличную переменную с другими таблицами, можно использовать указание RECOMPILE, в результате чего оптимизатор будет использовать правильную кратность для табличной переменной.
  
Переменные **table** не поддерживаются в модели выбора с учетом затрат оптимизатора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вследствие этого, они не должны использоваться при необходимости осуществления выбора с учетом затрат для получения эффективного плана запроса. Временные таблицы являются предпочтительными при необходимости осуществления выбора с учетом затрат. Обычно их следует использовать в запросах с соединениями, решениях в отношении параллелизма и при выборе индекса.
  
Запросы, изменяющие переменные **table**, не создают параллельных планов выполнения запроса. При изменении очень больших переменных **table** или переменных **table** в сложных запросах может снизиться производительность. В подобных случаях целесообразно рассмотреть возможность использования временных таблиц. Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md). Запросы, которые считывают переменные **table**, не изменяя их, могут выполняться параллельно.
  
Для переменных **table** нельзя создавать индексы и статистику. Начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], реализован новый синтаксис, который позволяет создавать определенные встроенные типы индекса с использованием определения таблицы.  С помощью этого нового синтаксиса можно создавать индексы в переменной **table** как часть определения таблицы. В некоторых случаях можно добиться повышения производительности за счет использования временных таблиц, которые позволяют работать с индексами и статистикой. Дополнительные сведения о временных таблицах и создании встроенных индексов см. в руководстве по [использованию CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).

Ограничения CHECK, значения DEFAULT и вычисляемые столбцы в объявлении типа **table** не могут вызывать пользовательские функции.
  
Операция присвоения между переменными **table** не допускается.
  
Так как переменные **table** имеют ограниченную область действия и не являются частью постоянной базы данных, они не изменяются в случае откатов транзакций.
  
Табличные переменные нельзя изменить после их создания.

## <a name="table-variable-deferred-compilation"></a>Отложенная компиляция табличных переменных
**Отложенная компиляция табличных переменных** позволяет оптимизировать план и повысить общую производительность для запросов, ссылающихся на табличные переменные. Во время оптимизации и первичной компиляции плана эта функция будет распространять оценки кратности, основанные на фактическом числе строк табличных переменных. Эти точные сведения о числе строк затем будут использоваться для оптимизации последующих операций планирования.

> [!NOTE]
> Отложенная компиляция табличных переменных предоставляется в Базе данных SQL Azure в режиме общедоступной предварительной версии.  

При отложенной компиляции табличных переменных компиляция инструкции со ссылкой на табличную переменную откладывается до момента первого фактического выполнения инструкции. Такое поведение при отложенной компиляции идентично поведению временных таблиц. В результате вместо исходного однострочного предположения используется фактическое значение кратности. 

Чтобы включить общедоступную предварительную версию отложенной компиляции табличных переменных, активируйте режим совместимости базы данных 150 для базы данных, к которой вы подключаетесь при выполнении запроса.

Отложенная компиляция табличных переменных **не** изменяет другие характеристики табличных переменных. Например, эта функция не добавляет в табличные переменные статистику по столбцам.

Также эта функция **не увеличивает частоту перекомпиляции**.  Эта функция эффективна при начальной компиляции. Итоговый кэшированный план создается на основе числа строк табличных переменных начальной отложенной компиляции. Кэшированный план повторно используется при выполнении последовательных запросов до тех пор, пока план не будет удален или перекомпилирован. 

Если число строк табличных переменных, используемое для начальной компиляции плана, представляет стандартное значение, которое значительно отличается от предположительного фиксированного числа строк, последующие операции будут производительными.  Если число строк табличных переменных существенно меняется при каждом выполнении, производительность не будет повышена с помощью этой функции.

  
## <a name="examples"></a>Примеры  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. Объявление переменной типа table  
В следующем примере создается переменная типа `table`, в которой хранятся значения, задаваемые в предложении OUTPUT инструкции UPDATE. Две следующие инструкции `SELECT` возвращают значения в табличную переменную `@MyTableVar`, а результаты операции обновления — в таблицу `Employee`. Обратите внимание, что результаты в столбце `INSERTED.ModifiedDate` отличны от значений в столбце `ModifiedDate` таблицы `Employee`. Это связано с тем, что для таблицы `AFTER UPDATE` определен триггер `ModifiedDate`, обновляющий значение `Employee` до текущей даты. Однако столбцы, возвращенные из `OUTPUT`, отражают состояние данных перед срабатыванием триггеров. Дополнительные сведения см. в статье [Предложение OUTPUT (Transact-SQL)](../../t-sql/queries/output-clause-transact-sql.md).
  
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
Результатом следующего примера является встроенная функция, возвращающая табличное значение. Для каждого из товаров, проданных в магазине, она возвращает три столбца: `ProductID`, `Name` и статистику с начала года по магазину — `YTD Total`.
  
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
  
## <a name="see-also"></a>См. также раздел
[COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)  
[Определяемые пользователем функции](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[Использование параметров, возвращающих табличные значения (ядро СУБД)](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md)
