---
title: sys.Objects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.objects_TSQL
- objects
- sys.objects
- objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.objects catalog view
- table-valued parameters, sys.objects catalog view
- user-defined table types [SQL Server]
- table types [SQL Server]
ms.assetid: f8d6163a-2474-410c-a794-997639f31b3b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0707db4e44a647ee87ca592339ad4f408a551608
ms.sourcegitcommit: 07d4ebb8438f7c348880c39046e2b452b2152fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2018
ms.locfileid: "47158055"
---
# <a name="sysobjects-transact-sql"></a>sys.objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по строке для каждого объекта области схемы, определяемые пользователем, который создается в базе данных, включая скомпилированную в собственном коде скалярной определяемой пользователем функции.  
  
 Дополнительные сведения см. в разделе [Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
> [!NOTE]  
>  Представление sys.objects не показывает триггеры DDL, так как они не принадлежат области схемы. Все триггеры DML и DDL, можно найти в [sys.triggers](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md). sys.triggers поддерживает смешанные правила имен для различного рода триггеров.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Имя объекта.|  
|object_id|**int**|Идентификационный номер объекта. Уникален в базе данных.|  
|principal_id|**int**|Идентификатор отдельного владельца, если он отличается от владельца схемы. По умолчанию содержащиеся в схеме объекты принадлежат владельцу схемы. Однако с помощью инструкции ALTER AUTHORIZATION можно изменить право собственности и указать другого владельца.<br /><br /> Принимает значение NULL, если нет альтернативного отдельного владельца.<br /><br /> Имеет значение NULL, если типом объекта является один из следующих:<br /><br /> C = ограничение CHECK<br /><br /> D = значение по умолчанию (DEFAULT), в ограничении или независимо заданное<br /><br /> F = ограничение FOREIGN KEY<br /><br /> PK = ограничение PRIMARY KEY<br /><br /> R = правило (старый стиль, изолированный)<br /><br /> TA = триггер сборки (интеграция со средой CLR)<br /><br /> TR = триггер SQL<br /><br /> UQ = ограничение UNIQUE<br /><br /> EC = ограничение границ |  
|schema_id|**int**|Идентификатор схемы, в которой содержится объект.<br /><br /> Системные объекты области схемы всегда содержатся в схемах sys или INFORMATION_SCHEMA.|  
|parent_object_id|**int**|Идентификатор объекта, которому принадлежит данный объект.<br /><br /> 0 = не дочерний объект|  
|Тип|**char(2)**|Тип объекта:<br /><br /> AF = агрегатная функция (среда CLR)<br /><br /> C = ограничение CHECK<br /><br /> D = значение по умолчанию (DEFAULT), в ограничении или независимо заданное<br /><br /> F = ограничение FOREIGN KEY<br /><br /> FN = скалярная функция SQL<br /><br /> FS = скалярная функция сборки (среда CLR)<br /><br /> FT = функция сборки (среда CLR) с табличным значением<br /><br /> IF = встроенная функция SQL с табличным значением<br /><br /> IT = внутренняя таблица<br /><br /> P = хранимая процедура SQL<br /><br /> PC = хранимая процедура сборки (среда CLR)<br /><br /> PG = структура плана<br /><br /> PK = ограничение PRIMARY KEY<br /><br /> R = правило (старый стиль, изолированный)<br /><br /> RF = процедура фильтра репликации<br /><br /> S = системная базовая таблица<br /><br /> SN = синоним<br /><br /> SO = объект последовательности<br /><br /> U = таблица (пользовательская)<br /><br /> V = представление<br /><br /> EC = ограничение границ <br /><br /> <br /><br /> **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> SQ = очередь обслуживания<br /><br /> TA = триггер DML сборки (среда CLR)<br /><br /> TF = возвращающая табличное значение функция SQL<br /><br /> TR = триггер DML SQL<br /><br /> TT = табличный тип<br /><br /> UQ = ограничение UNIQUE<br /><br /> X = расширенная хранимая процедура<br /><br /> <br /><br /> **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].<br /><br /> <br /><br /> ET = внешней таблицы|  
|type_desc|**nvarchar(60)**|Описание типа объекта:<br /><br /> AGGREGATE_FUNCTION<br /><br /> CHECK_CONSTRAINT<br /><br /> CLR_SCALAR_FUNCTION<br /><br /> CLR_STORED_PROCEDURE<br /><br /> CLR_TABLE_VALUED_FUNCTION<br /><br /> CLR_TRIGGER<br /><br /> DEFAULT_CONSTRAINT<br /><br /> EXTENDED_STORED_PROCEDURE<br /><br /> FOREIGN_KEY_CONSTRAINT<br /><br /> INTERNAL_TABLE<br /><br /> PLAN_GUIDE<br /><br /> PRIMARY_KEY_CONSTRAINT<br /><br /> REPLICATION_FILTER_PROCEDURE<br /><br /> RULE<br /><br /> SEQUENCE_OBJECT<br /><br /> <br /><br /> **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> SERVICE_QUEUE<br /><br /> SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> SQL_SCALAR_FUNCTION<br /><br /> SQL_STORED_PROCEDURE<br /><br /> SQL_TABLE_VALUED_FUNCTION<br /><br /> SQL_TRIGGER<br /><br /> SYNONYM<br /><br /> SYSTEM_TABLE<br /><br /> TABLE_TYPE<br /><br /> UNIQUE_CONSTRAINT<br /><br /> USER_TABLE<br /><br /> VIEW|  
|create_date|**datetime**|Дата создания объекта.|  
|modify_date|**datetime**|Дата последнего изменения объекта с помощью инструкции ALTER. Если объект является таблицей или представлением, то столбец modify_date также изменяется при создании или изменении кластеризованного индекса таблицы или представления.|  
|is_ms_shipped|**bit**|Объект создан внутренним компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_published|**bit**|Объект опубликован.|  
|is_schema_published|**bit**|Опубликована только схема объекта.|  
  
## <a name="remarks"></a>Примечания  
 Можно применить [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md), [OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md), и [OBJECTPROPERTY](../../t-sql/functions/objectproperty-transact-sql.md)встроенные функции () к объектам, содержащимся в представлении sys.objects.  
  
 Версия этого представления с той же схемой, вызывается [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md), которое показывает системные объекты. Есть другое представление с именем [sys.all_objects](../../relational-databases/system-catalog-views/sys-all-objects-transact-sql.md) которое показывает системные и пользовательские объекты. Все три представления каталогов имеют одну и ту же структуру.  
  
 В этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширенный индекс, такой как XML-индекс или пространственный индекс, считается внутренней таблицей в sys.objects (type = IT, а type_desc = INTERNAL_TABLE). Для расширенного индекса:  
  
-   name — это внутреннее имя таблицы индексов;  
  
-   parent_object_id — это object_id базовой таблицы;  
  
-   столбцы is_ms_shipped, is_published и is_schema_published установлены в 0.  

**Связанные полезные системные представления**  
Подмножества объектов можно просмотреть с помощью системных представлений для определенного типа объекта, например:  
- [sys.tables](sys-tables-transact-sql.md)  
- [sys.views](sys-views-transact-sql.md)  
- [sys.procedures](sys-procedures-transact-sql.md)  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-the-objects-that-have-been-modified-in-the-last-n-days"></a>A. Возвращаются все объекты, измененные в течение последних N дней  
 Перед запуском следующего запроса замените `<database_name>` и `<n_days>` действительными значениями.  
  
```sql  
USE <database_name>;  
GO  
SELECT name AS object_name   
  ,SCHEMA_NAME(schema_id) AS schema_name  
  ,type_desc  
  ,create_date  
  ,modify_date  
FROM sys.objects  
WHERE modify_date > GETDATE() - <n_days>  
ORDER BY modify_date;  
GO  
```  
  
### <a name="b-returning-the-parameters-for-a-specified-stored-procedure-or-function"></a>Б. Возвращаются параметры для указанной хранимой процедуры или функции  
 Перед запуском следующего запроса замените `<database_name>` и `<schema_name.object_name>` действительными именами.  
  
```sql  
USE <database_name>;  
GO  
SELECT SCHEMA_NAME(schema_id) AS schema_name  
    ,o.name AS object_name  
    ,o.type_desc  
    ,p.parameter_id  
    ,p.name AS parameter_name  
    ,TYPE_NAME(p.user_type_id) AS parameter_type  
    ,p.max_length  
    ,p.precision  
    ,p.scale  
    ,p.is_output  
FROM sys.objects AS o  
INNER JOIN sys.parameters AS p ON o.object_id = p.object_id  
WHERE o.object_id = OBJECT_ID('<schema_name.object_name>')  
ORDER BY schema_name, object_name, p.parameter_id;  
GO  
```  
  
### <a name="c-returning-all-the-user-defined-functions-in-a-database"></a>В. Возвращаются все определяемые пользователем функции в базе данных  
 Перед запуском следующего запроса замените `<database_name>` действительным именем базы данных.  
  
```sql  
USE <database_name>;  
GO  
SELECT name AS function_name   
  ,SCHEMA_NAME(schema_id) AS schema_name  
  ,type_desc  
  ,create_date  
  ,modify_date  
FROM sys.objects  
WHERE type_desc LIKE '%FUNCTION%';  
GO  
```  
  
### <a name="d-returning-the-owner-of-each-object-in-a-schema"></a>Г. Возвращается владелец каждого объекта в схеме  
 Перед запуском следующего запроса замените все экземпляры `<database_name>` и `<schema_name>` действительными именами.  
  
```sql  
USE <database_name>;  
GO  
SELECT 'OBJECT' AS entity_type  
    ,USER_NAME(OBJECTPROPERTY(object_id, 'OwnerId')) AS owner_name  
    ,name   
FROM sys.objects WHERE SCHEMA_NAME(schema_id) = '<schema_name>'  
UNION   
SELECT 'TYPE' AS entity_type  
    ,USER_NAME(TYPEPROPERTY(SCHEMA_NAME(schema_id) + '.' + name, 'OwnerId')) AS owner_name  
    ,name   
FROM sys.types WHERE SCHEMA_NAME(schema_id) = '<schema_name>'   
UNION  
SELECT 'XML SCHEMA COLLECTION' AS entity_type   
    ,COALESCE(USER_NAME(xsc.principal_id),USER_NAME(s.principal_id)) AS owner_name  
    ,xsc.name   
FROM sys.xml_schema_collections AS xsc JOIN sys.schemas AS s  
    ON s.schema_id = xsc.schema_id  
WHERE s.name = '<schema_name>';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-objects-transact-sql.md)   
 [sys.system_objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.internal_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-tables-transact-sql.md)  
  
  
