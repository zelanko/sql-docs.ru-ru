---
title: "sys.Tables (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- tables_TSQL
- sys.tables_TSQL
- sys.tables
- tables
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tables catalog view
ms.assetid: 8c42eba1-c19f-4045-ac82-b97a5e994090
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b6b5b2c25c3391c23102e837437cf77c69c445e3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="systables-transact-sql"></a>sys.tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждой пользовательской таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|\<унаследованные столбцы >||Список столбцов, наследуемых этим представлением см. в разделе [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|lob_data_space_id|**int**|Ненулевое значение — это идентификатор пространства данных (файловой группы или схемы секционирования), хранящего данные больших двоичных объектов (LOB) для этой таблицы. Примеры типов данных LOB **varbinary(max)**, **varchar(max)**, **geography**, или **xml**.<br /><br /> 0 = таблица не содержит данных LOB.|  
|filestream_data_space_id|**int**|Идентификатор пространства данных для файловой группы FILESTREAM или схемы секционирования, состоящей из файловых групп FILESTREAM.<br /><br /> Для сообщения имени файловой группы FILESTREAM, выполните запрос `SELECT FILEGROUP_NAME (filestream_data_space_id) FROM sys.tables`.<br /><br /> sys.tables можно объединить со следующими представлениями по условию filestream_data_space_id = data_space_id.<br /><br /> -sys.filegroups<br /><br /> -sys.partition_schemes<br /><br /> -sys.indexes<br /><br /> -sys.allocation_units<br /><br /> -sys.fulltext_catalogs<br /><br /> -sys.data_spaces<br /><br /> -sys.destination_data_spaces<br /><br /> -sys.master_files<br /><br /> -sys.database_files<br /><br /> -backupfilegroup (соединенная по столбцу filegroup_id)|  
|max_column_id_used|**int**|Максимальный идентификатор столбца, когда-либо использованный в таблице.|  
|lock_on_bulk_load|**bit**|Таблица заблокирована при массовой загрузке. Дополнительные сведения см. в разделе [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|  
|uses_ansi_nulls|**bit**|Таблица была создана при установленном параметре SET ANSI_NULLS = ON.|  
|is_replicated|**bit**|1 = таблица опубликована путем репликации моментальных снимков или транзакций.|  
|has_replication_filter|**bit**|1 = для таблицы имеется фильтр репликации.|  
|is_merge_published|**bit**|1 = таблица опубликована путем репликации слиянием.|  
|is_sync_tran_subscribed|**bit**|1 = таблица используется в немедленно обновляемой подписке.|  
|has_unchecked_assembly_data|**bit**|1 = таблица содержит материализованные данные, зависящие от сборки, определение которых изменилось во время последней операции ALTER ASSEMBLY. Будет сброшено в значение 0 после следующей успешной операции DBCC CHECKDB или DBCC CHECKTABLE.|  
|text_in_row_limit|**int**|Максимальное число байтов, разрешенное для текста в строке.<br /><br /> 0 = параметр текста в строке не установлен. Дополнительные сведения см. в разделе [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|  
|large_value_types_out_of_row|**bit**|1 = типы больших значений хранятся вне строк. Дополнительные сведения см. в разделе [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|  
|is_tracked_by_cdc|**bit**|1 = в таблице включена система отслеживания измененных данных. Дополнительные сведения см. в разделе [sys.sp_cdc_enable_table &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).|  
|lock_escalation|**tinyint**|Значение параметра LOCK_ESCALATION для таблицы.<br /><br /> 0 = TABLE<br /><br /> 1 = DISABLE<br /><br /> 2 = AUTO|  
|lock_escalation_desc|**nvarchar(60)**|Текстовое описание параметра lock_escalation для таблицы. Возможные значения: TABLE, AUTO и DISABLE.|  
|is_filetable|**bit**|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> 1 = таблица имеет тип FileTable.<br /><br /> Дополнительные сведения о таблицах Filetable см. в разделе [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).|  
|устойчивость|**tinyint**|**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Возможные следующие значения.<br /><br /> 0 = SCHEMA_AND_DATA<br /><br /> 1 = SCHEMA_ONLY<br /><br /> Значением по умолчанию является значение 0.|  
|durability_desc|**nvarchar(60)**|**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Допустимы следующие значения:<br /><br /> SCHEMA_ONLY<br /><br /> SCHEMA_AND_DATA<br /><br /> Значение SCHEMA_AND_DATA указывает, что таблица является надежной и оптимизированной для памяти. SCHEMA_AND_DATA — это значение по умолчанию для таблиц, оптимизированных для памяти. Значение SCHEMA_ONLY указывает, что табличные данные не будут сохранены после перезапуска базы данных с объектами, оптимизированными для памяти.|  
|is_memory_optimized|**bit**|**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Допустимы следующие значения:<br /><br /> 0 = не оптимизировано для памяти.<br /><br /> 1 = оптимизировано для памяти<br /><br /> Значение по умолчанию — 0.<br /><br /> Оптимизированные для памяти таблицы — это хранящиеся в памяти пользовательские таблицы, схемы которых сохраняются на диске аналогично другим пользовательским таблицам. Доступ к оптимизированным для памяти таблицам можно осуществлять из скомпилированных в собственном коде хранимых процедур.|  
|temporal_type|**tinyint**|**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Числовое значение, представляющее тип таблицы:<br /><br /> 0 = NON_TEMPORAL_TABLE<br /><br /> 1 = HISTORY_TABLE<br /><br /> 2 = SYSTEM_VERSIONED_TEMPORAL_TABLE|  
|temporal_type_desc|**nvarchar(60)**|**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Текстовое описание тип таблицы:<br /><br /> NON_TEMPORAL_TABLE<br /><br /> HISTORY_TABLE<br /><br /> SYSTEM_VERSIONED_TEMPORAL_TABLE|  
|history_table_id|**int**|**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Если в temporal_type (2, 4) возвращает object_id таблицы, которая хранит данные журналов, в противном случае возвращает значение NULL.|  
|is_remote_data_archive_enabled|**bit**|**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и[!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]<br /><br /> Указывает, является ли таблица с включенным Stretch.<br /><br /> 0 = таблица не включена.<br /><br /> 1 = таблица является совместимую со Stretch.<br /><br /> Дополнительные сведения см. в разделе [Stretch Database](../../sql-server/stretch-database/stretch-database.md).|  
|is_external|**bit**|**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)], и [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)].<br /><br /> Указывает, что таблица является внешней таблицы.<br /><br /> 0 = таблица не внешней таблицы.<br /><br /> 1 = таблица является внешней таблицы.| 
|history_retention_period|**int**|**Область применения**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>Числовое значение, представляющее продолжительность срока хранения журнала в единицах, задаваемых с history_retention_period_unit. |  
|history_retention_period_unit|**int**|**Область применения**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>Числовое значение, представляющее тип единицы измерения срока хранения журнала. <br /><br />-1: БЕСКОНЕЧНЫЙ <br /><br />3: ДЕНЬ <br /><br />4: НЕДЕЛИ <br /><br />5: МЕСЯЦ <br /><br />6: ГОД |  
|history_retention_period_unit_desc|**nvarchar(10)**|**Область применения**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>Текстовое описание типа единицы срока хранения журнала. <br /><br />INFINITE <br /><br />DAY <br /><br />WEEK <br /><br />MONTH <br /><br />YEAR |  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все пользовательские таблицы, у которых нет первичного ключа.  
  
```  
SELECT SCHEMA_NAME(schema_id) AS schema_name  
    ,name AS table_name   
FROM sys.tables   
WHERE OBJECTPROPERTY(object_id,'TableHasPrimaryKey') = 0  
ORDER BY schema_name, table_name;  
GO  
  
```  
  
В следующем примере показано, как связанных темпоральных данных может быть предоставлен.  
   
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].
  
```  
SELECT T1.object_id, T1.name as TemporalTableName, SCHEMA_NAME(T1.schema_id) AS TemporalTableSchema,  
T2.name as HistoryTableName, SCHEMA_NAME(T2.schema_id) AS HistoryTableSchema,  
T1.temporal_type_desc  
FROM sys.tables T1  
LEFT JOIN sys.tables T2   
ON T1.history_table_id = T2.object_id  
ORDER BY T1.temporal_type desc  
```  

В следующем примере показано, как могут быть предоставлены сведения о хранения журнала.  

**Область применения**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].  
  
```  
SELECT DB.is_temporal_history_retention_enabled, SCHEMA_NAME(T1.schema_id) AS TemporalTableSchema, 
T1.name as TemporalTableName, SCHEMA_NAME(T2.schema_id) AS HistoryTableSchema, T2.name as HistoryTableName,
T1.history_retention_period, T1.history_retention_period_unit_desc
FROM sys.tables T1  
OUTER APPLY (select is_temporal_history_retention_enabled from sys.databases where name = DB_NAME()) DB
LEFT JOIN sys.tables T2   
ON T1.history_table_id = T2.object_id WHERE T1.temporal_type = 2 
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [DBCC CHECKTABLE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
