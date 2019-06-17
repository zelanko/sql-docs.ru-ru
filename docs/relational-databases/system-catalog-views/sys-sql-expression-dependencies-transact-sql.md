---
title: sys.sql_expression_dependencies (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_expression_dependencies
- sql_expression_dependencies_TSQL
- sql_expression_dependencies
- sys.sql_expression_dependencies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_expression_dependencies catalog view
ms.assetid: 78a218e4-bf99-4a6a-acbf-ff82425a5946
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e4ef878879fb5c2896c45aedbf2a86f83557804c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62856108"
---
# <a name="syssqlexpressiondependencies-transact-sql"></a>Представление каталога sys.sql_expression_dependencies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждой именованной зависимости определяемой пользователем сущности в текущей базе данных. Сюда входят зависимости между скомпилированных в собственном коде скалярных определяемых пользователем функций и другой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] модулей. Зависимость между двумя сущностями создается в том случае, когда некоторой сущности, называемой *упоминаемая сущность*, отображается именем в материализованном выражении SQL другой сущности, называемой *ссылающейся сущностью*. Например, если на таблицу ссылается определение представления, это представление, как ссылающаяся сущность, зависит от таблицы или упоминаемой сущности. При удалении таблицы представление становится непригодным для использования.  
  
 Дополнительные сведения см. в разделе [Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 Это представление каталога можно использовать для получения сведений о зависимостях по следующим сущностям:  
  
-   привязанные к схеме сущности;  
  
-   сущности без привязки к схеме;  
  
-   межбазовые и межсерверные сущности. Выводятся имена сущностей без идентификаторов;  
  
-   зависимости на уровне столбцов в сущностях, привязанных к схеме. Зависимости уровня столбца для не привязанных к схеме объектов, которые могут быть возвращены с помощью [sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md).  
  
-   триггеры DDL на уровне сервера в контексте базы данных master.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|referencing_id|**int**|Идентификатор ссылающейся сущности. Не допускает значение NULL.|  
|referencing_minor_id|**int**|Идентификатор столбца, если ссылающаяся сущность является столбцом; в противном случае — 0. Не допускает значение NULL.|  
|referencing_class|**tinyint**|Класс ссылающейся сущности.<br /><br /> 1 = Объект или столбец<br /><br /> 12 = триггер DDL базы данных<br /><br /> 13 = серверный триггер DDL<br /><br /> Не допускает значение NULL.|  
|referencing_class_desc|**nvarchar(60)**|Описание класса ссылающейся сущности.<br /><br /> OBJECT_OR_COLUMN<br /><br /> DATABASE_DDL_TRIGGER<br /><br /> SERVER_DDL_TRIGGER<br /><br /> Не допускает значение NULL.|  
|is_schema_bound_reference|**bit**|1 = упоминаемая сущность привязана к схеме.<br /><br /> 0 = упоминаемая сущность не привязана к схеме.<br /><br /> Не допускает значение NULL.|  
|referenced_class|**tinyint**|Класс упоминаемой сущности.<br /><br /> 1 = Объект или столбец<br /><br /> 6 = Тип<br /><br /> 10 = коллекция схем XML<br /><br /> 21 = функция секционирования<br /><br /> Не допускает значение NULL.|  
|referenced_class_desc|**nvarchar(60)**|Описание класса упоминаемой сущности.<br /><br /> OBJECT_OR_COLUMN<br /><br /> TYPE<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> PARTITION_FUNCTION<br /><br /> Не допускает значение NULL.|  
|referenced_server_name|**sysname**|Имя сервера упоминаемой сущности.<br /><br /> Этот столбец заполняется для межсерверных зависимостей, которые создаются путем задания допустимого четырехкомпонентного имени. Сведения о многокомпонентных именах см. в разделе [синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).<br /><br /> Значение NULL для не привязанных к схеме сущностей, ссылка на которые осуществляется без указания четырехкомпонентного имени.<br /><br /> Имеет значение NULL для привязанных к схеме сущностей, поскольку они должны находиться в той же базе данных и поэтому может быть определен только с помощью двухкомпонентного (*схема.объект*) имя.|  
|referenced_database_name|**sysname**|Имя базы данных упоминаемой сущности.<br /><br /> Этот столбец заполняется для межбазовых и межсерверных ссылок, которые задаются путем указания допустимого трехкомпонентного или четырехкомпонентного имени.<br /><br /> Имеет значение NULL для не привязанных к схеме ссылок, задаваемых с помощью однокомпонентного или двухкомпонентного имени.<br /><br /> Имеет значение NULL для привязанных к схеме сущностей, поскольку они должны находиться в той же базе данных и поэтому может быть определен только с помощью двухкомпонентного (*схема.объект*) имя.|  
|referenced_schema_name|**sysname**|Схема, которой принадлежит упоминаемая сущность.<br /><br /> Имеет значение NULL для не привязанных к схеме ссылок, в которых сущность упоминается без указания имени схемы.<br /><br /> Никогда не имеет значение NULL для привязанных к схеме ссылок, поскольку привязанные к схеме сущности должны определяться двухкомпонентным именем и ссылаться с помощью двухкомпонентных ссылок.|  
|referenced_entity_name|**sysname**|Имя упоминаемой сущности. Не допускает значение NULL.|  
|referenced_id|**int**|Идентификатор упоминаемой сущности. Значение этого столбца никогда не равно NULL для привязанных к схеме ссылок. Значение этого столбца всегда равно NULL для межсерверных и межбазовых ссылок.<br /><br /> Имеет значение NULL для ссылок в пределах базы данных, когда не удается определить идентификатор. Для ссылок, не привязанных к схеме, идентификатор не удается разрешить в следующих случаях.<br /><br /> Упоминаемая сущность не существует в базе данных.<br /><br /> Схема упоминаемой сущности зависит от схемы участника и разрешается во время выполнения. В этом случае параметр is_caller_dependent устанавливается в значение 1.|  
|referenced_minor_id|**int**|Идентификатор ссылочного столбца в случае, если ссылающейся сущностью является столбец; в противном случае — 0. Не допускает значение NULL.<br /><br /> Упоминаемая сущность представляет собой столбец, если в ссылающейся сущности столбец определяется по имени или если в инструкции SELECT * используется родительская сущность.|  
|is_caller_dependent|**bit**|Указывает, что привязка к схеме для упоминаемой сущности происходит во время выполнения, и поэтому разрешение идентификатора сущности зависит от схемы ссылающейся сущности. Это происходит, если упоминаемая сущность является хранимой процедурой, расширенной хранимой процедурой или определяемой пользователем функцией, не привязанной к схеме, вызываемой в инструкции EXECUTE.<br /><br /> 1 = упоминаемая сущность зависит от ссылающейся и разрешается во время выполнения. В этом случае параметр referenced_id принимает значение NULL.<br /><br /> 0 = идентификатор упоминаемой сущности не зависит от вызывающего объекта.<br /><br /> Всегда имеет значение 0 для привязанных к схеме ссылок, а также для межбазовых и межсерверных ссылок, которые явно указывают имя схемы. Например, ссылка на сущность в формате `EXEC MyDatabase.MySchema.MyProc` не зависит от вызывающего объекта. При этом ссылка в формате `EXEC MyDatabase..MyProc` зависит от вызывающего объекта.|  
|is_ambiguous|**bit**|Указывает, является неоднозначным его разрешается во время выполнения определяемой пользователем функции, определяемого пользователем типа (UDT) или ссылке xquery на столбец типа **xml**.<br /><br /> Например, предположим, что инструкция `SELECT Sales.GetOrder() FROM Sales.MySales` определена в хранимой процедуре. До выполнения хранимой процедуры неизвестно, является ли `Sales.GetOrder()` определяемой пользователем функцией в схеме `Sales` или столбцом `Sales` определяемого пользователем типа с методом `GetOrder()`.<br /><br /> 1 = ссылка неоднозначна.<br /><br /> 0 = ссылка однозначна, или сущность можно успешно привязать при вызове представления.<br /><br /> Всегда принимает значение 0 для привязанных к схеме ссылок.|  
  
## <a name="remarks"></a>Примечания  
 В следующей таблице перечислены типы сущностей, для которых созданы и обновляются данные о зависимостях. Данные о зависимостях не создаются и не обновляются для правил, значений по умолчанию, временных таблиц, временных хранимых процедур и системных объектов.  
  
|Тип сущности|Ссылающаяся сущность|Упоминаемая сущность|  
|-----------------|------------------------|-----------------------|  
|Таблица|Да*|Да|  
|Представление|Да|Да|  
|Фильтруемый индекс|Да**|Нет|  
|Статистика фильтрации|Да**|Нет|  
|Хранимая процедура [!INCLUDE[tsql](../../includes/tsql-md.md)]***|Да|Да|  
|Хранимая процедура CLR|Нет|Да|  
|Определяемая пользователем функция [!INCLUDE[tsql](../../includes/tsql-md.md)]|Да|Да|  
|Определяемая пользователем функция CLR|Нет|Да|  
|Триггер CLR (DML и DDL)|Нет|Нет|  
|Триггер DML [!INCLUDE[tsql](../../includes/tsql-md.md)]|Да|Нет|  
|Триггер DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] уровня базы данных|Да|Нет|  
|Триггер DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] уровня сервера|Да|Нет|  
|Расширенные хранимые процедуры|Нет|Да|  
|Очередь|Нет|Да|  
|Синоним|Нет|Да|  
|Тип (псевдоним и определяемый пользователем тип данных CLR)|Нет|Да|  
|Коллекция схем XML|Нет|Да|  
|Функция секционирования|Нет|Да|  
  
 \* Таблица отслеживается как ссылающаяся сущность, только в том случае, если оно ссылается на [!INCLUDE[tsql](../../includes/tsql-md.md)] модуля, определяемый пользователем тип или коллекцию схем XML в определении вычисляемого столбца, ограничения CHECK или ограничении DEFAULT.  
  
 **Каждый столбец, используемый в предикате фильтра, отслеживается как ссылающаяся сущность.  
  
 *** Пронумерованные хранимые процедуры с целочисленным значением больше 1 не отслеживаются в качестве ссылающихся или упоминаемых сущностей.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DEFINITION в базе данных и разрешение SELECT на представление sys.sql_expression_dependencies в базе данных. По умолчанию разрешение SELECT предоставляется только членам предопределенной роли базы данных db_owner. Если разрешения SELECT и VIEW DEFINITION предоставлены другому пользователю, он может просматривать все зависимости в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-entities-that-are-referenced-by-another-entity"></a>A. Возвращение сущностей, на которые ссылаются другие сущности  
 В следующем примере возвращаются таблицы и столбцы, на которые ссылается представление `Production.vProductAndDescription`. Это представление зависит от сущностей (таблиц и столбцов), возвращаемых в столбцах `referenced_entity_name` и `referenced_column_name`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc,  
    referenced_server_name, referenced_database_name, referenced_schema_name,  
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');  
GO  
  
```  
  
### <a name="b-returning-entities-that-reference-another-entity"></a>Б. Возвращение сущностей, ссылающихся на другую сущность  
 В следующем примере возвращаются сущности, ссылающиеся на таблицу `Production.Product`. Сущности, возвращенные в столбце `referencing_entity_name`, зависят от таблицы `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
    OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,  
    referenced_server_name, referenced_database_name, referenced_schema_name,  
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referenced_id = OBJECT_ID(N'Production.Product');  
GO  
  
```  
  
### <a name="c-returning-cross-database-dependencies"></a>В. Возвращение межбазовых зависимостей  
 В следующем примере возвращаются все межбазовые зависимости. Вначале в примере создается база данных `db1` и две хранимые процедуры, которые ссылаются на таблицы в базах данных `db2` и `db3`. Затем запрашивается таблица `sys.sql_expression_dependencies`, чтобы сообщить о наличии межбазовых зависимостей между процедурами и таблицами. Обратите внимание, что в столбце `referenced_schema_name` для упоминаемой сущности `t3` возвращается значение NULL, потому что для этой сущности в определении процедуры не указано имя схемы.  
  
```  
CREATE DATABASE db1;  
GO  
USE db1;  
GO  
CREATE PROCEDURE p1 AS SELECT * FROM db2.s1.t1;  
GO  
CREATE PROCEDURE p2 AS  
    UPDATE db3..t3  
    SET c1 = c1 + 1;  
GO  
SELECT OBJECT_NAME (referencing_id),referenced_database_name,   
    referenced_schema_name, referenced_entity_name  
FROM sys.sql_expression_dependencies  
WHERE referenced_database_name IS NOT NULL;  
GO  
USE master;  
GO  
DROP DATABASE db1;  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
  
