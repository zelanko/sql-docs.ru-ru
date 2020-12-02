---
description: Конструктор табличных значений (Transact-SQL)
title: Конструктор табличных значений (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- inserting multiple rows
- row value expression
- row constructor [SQL Server]
- table value constructor [SQL Server]
ms.assetid: e57cd31d-140e-422f-8178-2761c27b9deb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c82909bb5a128ee0a1dff9fa48b0a213a3c931e4
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91115409"
---
# <a name="table-value-constructor-transact-sql"></a>Конструктор табличных значений (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Задает набор выражений значений строк, которые будут использоваться для создания таблицы. Конструктор табличных значений [!INCLUDE[tsql](../../includes/tsql-md.md)] позволяет указать в одной инструкции DML несколько строк данных. Конструктор табличных значений можно указать в виде предложения VALUES инструкции INSERT... VALUES либо производной таблицы в предложении USING инструкции MERGE или предложении FROM.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
VALUES ( <row value expression list> ) [ ,...n ]   
  
<row value expression list> ::=  
    {<row value expression> } [ ,...n ]  
  
<row value expression> ::=  
    { DEFAULT | NULL | expression }  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 VALUES  
 Представляет списки выражений значений строк. Все списки должны быть заключены в круглые скобки и разделены запятыми.  
  
 Количество значений в каждом списке должно быть одинаковым, а значения должны следовать в том же порядке, что и столбцы таблицы. Должно быть указано значение для всех столбцов в таблице, либо список столбцов должен явно указывать столбцы для всех входных значений.  
  
 DEFAULT  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет вставлять значение по умолчанию, определенное для столбца. Если для столбца не задано значение по умолчанию и он может содержать значение NULL, вставляется значение NULL. Значение DEFAULT недопустимо для столбца идентификаторов. При указании в конструкторе табличных значений DEFAULT может использоваться только в инструкции INSERT.  
  
 *expression*  
 Константа, переменная или выражение. Выражение не может содержать инструкцию EXECUTE.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 При использовании в виде производной таблицы ограничение на количество строк отсутствует.  
 
 При использовании в виде предложения VALUES инструкции INSERT... VALUES применяется ограничение в размере 1000 строк. Если число строк превышает 1000, возвращается ошибка 10738. Чтобы вставить более 1000 строк, используйте один из следующих методов:  
  
- Создайте несколько инструкций INSERT  
  
- Используйте производную таблицу  
  
- Выполните массовый импорт данных, используя [служебную программу **bcp**](../../tools/bcp-utility.md), [класс SqlBulkCopy](/dotnet/api/system.data.sqlclient.sqlbulkcopy) .NET, [OPENROWSET (BULK ...)](../../t-sql/functions/openrowset-transact-sql.md) или инструкцию [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
 Для выражения значения строк можно использовать только отдельные скалярные значения. Вложенный запрос, содержащий несколько столбцов, не может быть использован в выражении значений строк. Например, следующий код вызовет ошибку синтаксиса, поскольку в третьем списке выражений значений строк содержится вложенный запрос с несколькими столбцами.  
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE dbo.MyProducts (Name VARCHAR(50), ListPrice MONEY);  
GO  
-- This statement fails because the third values list contains multiple columns in the subquery.  
INSERT INTO dbo.MyProducts (Name, ListPrice)  
VALUES ('Helmet', 25.50),  
       ('Wheel', 30.00),  
       (SELECT Name, ListPrice FROM Production.Product WHERE ProductID = 720);  
GO  
```  
  
 Однако можно переписать инструкцию таким образом, чтобы каждый столбец отдельно задавался во вложенном запросе. В следующем примере в таблицу `MyProducts` успешно вставляются три строки.  
  
```sql
INSERT INTO dbo.MyProducts (Name, ListPrice)  
VALUES ('Helmet', 25.50),  
       ('Wheel', 30.00),  
       ((SELECT Name FROM Production.Product WHERE ProductID = 720),  
        (SELECT ListPrice FROM Production.Product WHERE ProductID = 720));  
GO  
```  
  
## <a name="data-types"></a>Типы данных  
 Значения, указанные в инструкции INSERT для нескольких строк, соблюдают правила преобразования типов данных для синтаксиса UNION ALL. В результате выполняется неявное преобразование несовпадающих типов к типу с более высоким [приоритетом](../../t-sql/data-types/data-type-precedence-transact-sql.md). Если неявное преобразование не поддерживается, возвращается ошибка. Например, следующая инструкция вставляет целочисленное значение и символьное значение в столбец типа **char**.  
  
```sql
CREATE TABLE dbo.t (a INT, b CHAR);  
GO  
INSERT INTO dbo.t VALUES (1,'a'), (2, 1);  
GO  
```  
  
 При выполнении инструкции INSERT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается преобразовать символ «a» в целое число, так как установленные правила определения приоритетов типов данных указывают, что целое число имеет тип данных с более высоким приоритетом, чем символ. Попытка преобразования оканчивается неудачей и возвращается ошибка. Этой ошибки можно избежать путем явного преобразования значений при необходимости. Например, приведенную выше инструкцию можно записать следующим образом:  
  
```sql
INSERT INTO dbo.t VALUES (1,'a'), (2, CONVERT(CHAR,1));  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-inserting-multiple-rows-of-data"></a>A. Вставка нескольких строк данных  
 В следующем примере создается таблица `dbo.Departments`, а затем при помощи конструктора табличных значений в таблицу вставляется пять строк. Так как значения для всех столбцов предоставлены и перечислены в том же порядке, что и столбцы в таблице, то не нужно в параметре указывать имена столбцов.  
  
```sql
USE AdventureWorks2012;  
GO  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT2', N'Square Feet ', '20080923'), (N'Y', N'Yards', '20080923'),
       (N'Y3', N'Cubic Yards', '20080923');  
GO  
```  
  
### <a name="b-inserting-multiple-rows-with-default-and-null-values"></a>Б. Вставка нескольких строк со значениями DEFAULT и NULL  
 Следующий пример демонстрирует указание DEFAULT и NULL при использовании конструктора табличных значений для вставки строк в таблицу.  
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE Sales.MySalesReason(  
SalesReasonID int IDENTITY(1,1) NOT NULL,  
Name dbo.Name NULL ,  
ReasonType dbo.Name NOT NULL DEFAULT 'Not Applicable' );  
GO  
INSERT INTO Sales.MySalesReason   
VALUES ('Recommendation','Other'), ('Advertisement', DEFAULT), (NULL, 'Promotion');  
  
SELECT * FROM Sales.MySalesReason;  
```  
  
### <a name="c-specifying-multiple-values-as-a-derived-table-in-a-from-clause"></a>В. Указание нескольких значений как производной таблицы в предложении FROM  
 В следующих примерах используется конструктор табличных значений для указания нескольких значений в предложении FROM инструкции SELECT.  
  
```sql
SELECT a, b FROM (VALUES (1, 2), (3, 4), (5, 6), (7, 8), (9, 10) ) AS MyTable(a, b);  
GO  
-- Used in an inner join to specify values to return.  
SELECT ProductID, a.Name, Color  
FROM Production.Product AS a  
INNER JOIN (VALUES ('Blade'), ('Crown Race'), ('AWC Logo Cap')) AS b(Name)   
ON a.Name = b.Name;  
```  
  
### <a name="d-specifying-multiple-values-as-a-derived-source-table-in-a-merge-statement"></a>Г. Указание нескольких значений как производной исходной таблицы в инструкции MERGE  
 В следующем примере инструкция MERGE используется для изменения таблицы `SalesReason` путем обновления или вставки строк. Если значение `NewName` в исходной таблице соответствует значению в столбце `Name` целевой таблицы (`SalesReason`), то в целевой таблице обновляется столбец `ReasonType`. Если значение `NewName` не совпадает со значением в целевой таблице, исходная строка вставляется в целевую таблицу. Исходной таблицей является производная таблица, в которой используется конструктор табличных значений [!INCLUDE[tsql](../../includes/tsql-md.md)] для указания нескольких строк исходной таблицы.  
  
```sql
USE AdventureWorks2012;  
GO  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
```  
  
### <a name="e-inserting-more-than-1000-rows"></a>Д. Вставка более 1000 строк
  Следующий пример демонстрирует использование конструктора табличных значений в виде производной таблицы. Это позволяет вставить более 1000 строк из одного конструктора табличных значений.
  
```sql
CREATE TABLE dbo.Test ([Value] INT);  
  
INSERT INTO dbo.Test ([Value])  
  SELECT drvd.[NewVal]
  FROM   (VALUES (0), (1), (2), (3), ..., (5000)) drvd([NewVal]);
```  


## <a name="see-also"></a>См. также:  
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)  
  
  
