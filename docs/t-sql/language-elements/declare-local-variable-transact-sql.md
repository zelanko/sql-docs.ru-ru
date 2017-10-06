---
title: "ОБЪЯВИТЕ @local_variable (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECLARE
- DECLARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table-valued parameters
- variables [SQL Server], declaring
- DECLARE statement
- declaring variables
ms.assetid: d1635ebb-f751-4de1-8bbc-cae161f90821
caps.latest.revision: 76
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70decceb0fb5bc34f5ac7a32c64ca80cb0977de2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="declare-localvariable-transact-sql"></a>ОБЪЯВИТЕ @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Переменные объявляются в теле пакета или процедуры при помощи инструкции DECLARE, а значения им присваиваются при помощи инструкций SET или SELECT. При помощи этой инструкции можно объявлять переменные курсоров для использования в других инструкциях. После декларации все переменные инициализируются значением NULL, если иное значение не предоставляется как часть декларации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DECLARE   
{   
    { @local_variable [AS] data_type  | [ = value ] }  
  | { @cursor_variable_name CURSOR }  
} [,...n]   
| { @table_variable_name [AS] <table_type_definition> }   
  
<table_type_definition> ::=   
     TABLE ( { <column_definition> | <table_constraint> } [ ,... ] )   
  
<column_definition> ::=   
     column_name { scalar_data_type | AS computed_column_expression }  
     [ COLLATE collation_name ]   
     [ [ DEFAULT constant_expression ] | IDENTITY [ (seed ,increment ) ] ]   
     [ ROWGUIDCOL ]   
     [ <column_constraint> ]   
  
<column_constraint> ::=   
     { [ NULL | NOT NULL ]   
     | [ PRIMARY KEY | UNIQUE ]   
     | CHECK ( logical_expression )   
     | WITH ( <index_option > )  
     }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,... ] )   
     | CHECK ( search_condition )   
     }   
  
<index_option> ::=  
See CREATE TABLE for index option syntax.  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DECLARE   
{{ @local_variable [AS] data_type } [ =value [ COLLATE <collation_name> ] ] } [,...n]  
  
```  
  
## <a name="arguments"></a>Аргументы  
@*local_variable*  
 Имя переменной. Имена переменных должны начинаться с символа @. Имена локальных переменных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
*Тип данных*  
 Любой системный тип данных, определяемый пользователем табличный тип среды CLR или псевдоним типа данных. Переменная не может быть **текст**, **ntext**, или **изображения** тип данных.  
  
 Дополнительные сведения о системных типах данных см. в разделе [типы данных &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md). Дополнительные сведения об определяемых пользователем типов CLR и псевдонимов типов данных см. в разделе [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md).  
  
 =*значение*  
 Подставляет значение переменной. Значение может быть константой или выражением, но должно совпадать с объявленным типом переменной или явно преобразовываться в этот тип. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
@*cursor_variable_name*  
 Имя переменной курсора. Имена переменных курсора должны начинаться с символа @ и должны соответствовать правилам именования идентификаторов.  
  
CURSOR  
 Указывает, что переменная является локальной переменной курсора.  
  
@*table_variable_name*  
 Имя переменной типа **таблицы**. Имена переменных должны начинаться с символа @ и соответствовать правилам именования идентификаторов.  
  
<table_type_definition>  
Определяет **таблицы** тип данных. Декларация таблицы включает определения столбцов, имен, типов данных и ограничений. Допустимы только ограничения PRIMARY KEY, UNIQUE, NULL и CHECK. Псевдоним типа данных не может использоваться как скалярный тип данных столбца, если к этому столбцу привязано правило или значение по умолчанию.
  
\<table_type_definiton > является подмножеством сведения, используемые для определения таблицы в инструкции CREATE TABLE. Сюда включены элементы и наиболее существенные определения. Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).  
  
 *n*  
 Заполнитель, указывающий на то, что могут быть заданы несколько переменных и им могут быть присвоены значения. При объявлении **таблицы** переменных, **таблицы** переменная должна иметь только переменной в операторе DECLARE.  
  
 *column_name*  
 Имя столбца таблицы.  
  
 *scalar_data_type*  
 Указывает, что столбец имеет скалярный тип данных.  
  
 *computed_column_expression*  
 Выражение, определяющее значение вычисляемого столбца. Значение вычисляется из выражения при помощи других столбцов той же таблицы. Например, вычисляемый столбец может иметь определение **стоимость** AS **цены \* qty**. Выражение может быть именем невычисляемого столбца, константой, встроенной функцией, переменной или любым их сочетанием, созданным с помощью одного или нескольких операторов. Выражение не может быть вложенным запросом или определяемой пользователем функцией. Выражение не может ссылаться на определяемый пользователем тип данных CLR.  
  
 [COLLATE *имя_параметров_сортировки*]  
 Задает параметры сортировки для столбца. *collation_name* может быть либо именем параметров сортировки Windows, либо именем параметров сортировки SQL и применяется только к столбцам **char**, **varchar**, **текста** , **nchar**, **nvarchar**, и **ntext** типов данных. Если этот аргумент не указан, столбцу назначаются либо параметры сортировки определяемого пользователем типа данных (если столбец принадлежит к определяемому пользователем типу данных), либо параметры сортировки текущей базы данных.  
  
 Дополнительные сведения об именах параметров сортировки Windows и SQL см. в разделе [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 DEFAULT  
 Указывает значение, присваиваемое столбцу в случае отсутствия явно заданного значения при вставке. Определения DEFAULT могут применяться к любым столбцам, за исключением определенных как **timestamp** или обладающих свойством IDENTITY. Определения DEFAULT удаляются, когда таблица удаляется из памяти. По умолчанию могут использоваться только константные значения, например символьные строки, системные функции, например SYSTEM_USER(), или NULL. Для сохранения совместимости с более ранними версиями сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значению DEFAULT может быть присвоено имя ограничения.  
  
 *constant_expression*  
 Константа, NULL или системная функция, используемые в качестве значения по умолчанию для столбца.  
  
 IDENTITY  
 Указывает, что новый столбец является столбцом идентификаторов. При добавлении в таблицу новой строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует для столбца уникальное, последовательное значение. Столбцы идентификаторов наиболее часто используются в сочетании с ограничениями PRIMARY KEY для выполнения функции уникального идентификатора строки таблицы. Свойство IDENTITY может назначаться **tinyint**, **smallint**, **int**, **decimal(p,0)**, или **numeric(p,0)** столбцов. Для каждой таблицы можно создать только один столбец идентификаторов. Ограниченные значения по умолчанию и ограничения DEFAULT не могут использоваться в столбце идентификаторов. Необходимо указывать либо оба значения seed и increment, либо ни тот, ни другой. Если ничего не указано, применяется значение по умолчанию (1,1).  
  
 *Начальное значение*  
 Значение, используемое для самой первой строки, загружаемой в таблицу.  
  
 *приращение*  
 Значение, добавляемое к значению идентификатора предыдущей загруженной строки.  
  
 ROWGUIDCOL  
 Указывает, что новый столбец является столбцом глобального уникального идентификатора строки. Только один **uniqueidentifier** столбца в каждой таблице можно определить как столбец ROWGUIDCOL. Свойство ROWGUIDCOL может присваиваться только **uniqueidentifier** столбца.  
  
 NULL | NOT NULL  
 Указывает, является ли значение null допустимым в переменной. Значение по умолчанию — NULL.  
  
 PRIMARY KEY  
 Ограничение, которое с помощью уникального индекса требует целостности сущностей для данного столбца или столбцов. Можно создать только одно ограничение PRIMARY KEY для таблицы.  
  
 UNIQUE  
 Ограничение, которое с помощью уникального индекса обеспечивает целостность сущностей для данного столбца или столбцов. В таблице может быть несколько ограничений UNIQUE.  
  
 CHECK  
 Ограничение, обеспечивающее целостность домена путем ограничения возможных значений, которые могут быть введены в столбец или столбцы.  
  
 *Logical_Expression*  
 Логическое выражение, возвращающее значения TRUE или FALSE.  
  
## <a name="remarks"></a>Замечания  
 Переменные часто используются в пакете или процедуре в качестве счетчиков для циклов WHILE, LOOP или в блоке IF…ELSE.  
  
 Переменные могут использоваться только в выражениях, но не вместо имен объектов или ключевых слов. Для построения динамических инструкций SQL используйте EXECUTE.  
  
 Областью локальной переменной является пакет, в котором она объявлена.  
 
 Табличная переменная не обязательно оперативной памяти. Нехватка памяти страниц, относящихся к табличной переменной могут быть перемещены в базу данных tempdb.
  
 На переменную курсора, которая в настоящее время содержит назначенный ей курсор, можно ссылаться в качестве источника из:  
  
-   инструкции CLOSE;  
  
-   инструкции DEALLOCATE;  
  
-   инструкции FETCH;  
  
-   инструкции OPEN;  
  
-   позиционированных инструкций DELETE или UPDATE;  
  
-   инструкции SET CURSOR с использованием переменных (в правой части).  
  
 Во всех этих инструкциях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует ошибку, если переменная курсора, на которую они ссылаются, существует, но не содержит курсор, назначенный ей в настоящее время. Если переменная курсора, на которую производится ссылка, не существует, сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует ту же ошибку, что и для необъявленной переменной другого типа.  
  
 Переменная курсора:  
  
-   Может быть целью типа курсора или другой переменной курсора. Дополнительные сведения см. в разделе [ЗАДАТЬ @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
-   Может быть объектом ссылки в качестве цели выходного параметра курсора в инструкции EXECUTE, если эта переменная не содержит курсора, назначенного ей в настоящее время.  
  
-   Должна рассматриваться в качестве указателя на курсор.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-declare"></a>A. Использование инструкции DECLARE  
 В следующем примере локальная переменная с именем `@find` используется для получения контактных данных для лиц с фамилией, начинающейся на `Man`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @find varchar(30);   
/* Also allowed:   
DECLARE @find varchar(30) = 'Man%';   
*/  
SET @find = 'Man%';   
SELECT p.LastName, p.FirstName, ph.PhoneNumber  
FROM Person.Person AS p   
JOIN Person.PersonPhone AS ph ON p.BusinessEntityID = ph.BusinessEntityID  
WHERE LastName LIKE @find;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName            FirstName               Phone
------------------- ----------------------- -------------------------
Manchepalli         Ajay                    1 (11) 500 555-0174
Manek               Parul                   1 (11) 500 555-0146
Manzanares          Tomas                   1 (11) 500 555-0178
  
(3 row(s) affected)
```  
  
### <a name="b-using-declare-with-two-variables"></a>Б. Использование инструкции DECLARE с двумя переменными  
 В следующем примере возвращаются имена коммерческих представителей компании [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], находящихся в Северной Америке и имеющих объемы продаж на сумму не менее 2 000 000 долларов в год.  
  
```  
USE AdventureWorks2012;  
GO  
SET NOCOUNT ON;  
GO  
DECLARE @Group nvarchar(50), @Sales money;  
SET @Group = N'North America';  
SET @Sales = 2000000;  
SET NOCOUNT OFF;  
SELECT FirstName, LastName, SalesYTD  
FROM Sales.vSalesPerson  
WHERE TerritoryGroup = @Group and SalesYTD >= @Sales;  
```  
  
### <a name="c-declaring-a-variable-of-type-table"></a>В. Объявление переменной типа table  
 В следующем примере создается переменная типа `table`, в которой хранятся значения, задаваемые в предложении OUTPUT инструкции UPDATE. Две следующие инструкции `SELECT` возвращают значения в табличную переменную `@MyTableVar`, а результаты операции обновления — в таблицу `Employee`. Обратите внимание, что результаты в `INSERTED.ModifiedDate` столбца отличаются от значений в `ModifiedDate` столбца в `Employee` таблицы. Это связано с тем, что для таблицы `AFTER UPDATE` определен триггер `ModifiedDate`, обновляющий значение `Employee` до текущей даты. Однако столбцы, возвращенные из `OUTPUT`, отражают состояние данных перед срабатыванием триггеров. Дополнительные сведения см. в разделе [предложение OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
```  
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
  
### <a name="d-declaring-a-variable-of-user-defined-table-type"></a>Г. Объявление переменной определяемого пользователем табличного типа  
 Следующий пример демонстрирует создание параметра, возвращающего табличное значение, или табличной переменной с именем `@LocationTVP`. Здесь требуется соответствующий определяемый пользователем табличный тип с именем `LocationTableType`. Дополнительные сведения о способах создания определяемого пользователем табличного типа см. в разделе [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md). Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [использование возвращающих табличные значения параметры &#40; компонент Database Engine &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
```  
DECLARE @LocationTVP   
AS LocationTableType;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-declare"></a>Д. Использование инструкции DECLARE  
 В следующем примере локальная переменная с именем `@find` используется для получения контактных данных для лиц с фамилией, начинающейся на `Walt`.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @find varchar(30);  
/* Also allowed:   
DECLARE @find varchar(30) = 'Man%';  
*/  
SET @find = 'Walt%';  
  
SELECT LastName, FirstName, Phone  
FROM DimEmployee   
WHERE LastName LIKE @find;  
```  
  
### <a name="f-using-declare-with-two-variables"></a>Е. Использование инструкции DECLARE с двумя переменными  
 В следующем примере извлекается использует переменные, чтобы указать имена и фамилии сотрудников из `DimEmployee` таблицы.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @lastName varchar(30), @firstName varchar(30);  
  
SET @lastName = 'Walt%';  
SET @firstName = 'Bryan';  
  
SELECT LastName, FirstName, Phone  
FROM DimEmployee   
WHERE LastName LIKE @lastName AND FirstName LIKE @firstName;  
```  
  
## <a name="see-also"></a>См. также:  
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [Таблица &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)  
  
  





