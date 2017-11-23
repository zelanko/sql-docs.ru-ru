---
title: "sys.dm_db_column_store_row_group_physical_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
caps.latest.revision: "15"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e1c1e25181ff25d354ad29dcd2db4f5210ce1b2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbcolumnstorerowgroupphysicalstats-transact-sql"></a>sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Предоставляет последнюю информацию на уровне группы строк обо всех индексов columnstore в текущей базе данных.  
  
 При этом расширяется в представление каталога [sys.column_store_row_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор базовой таблицы.|  
|**index_id**|**int**|Идентификатор этого индекса columnstore на *object_id* таблицы.|  
|**partition_number**|**int**|Идентификатор секции таблицы, которая содержит *row_group_id*. Partition_number можно использовать для соединения этого динамического административного представления с представлением sys.partitions.|  
|**row_group_id**|**int**|Идентификатор этой группы строк. Для секционированных таблиц является уникальным в пределах секции.<br /><br /> -1 для заключительного в памяти.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id для группы строк в разностном хранилище.<br /><br /> Имеет значение NULL, если группа строк не разностного хранилища.<br /><br /> Значение NULL для заключительного фрагмента таблицы в памяти.|  
|**состояние**|**tinyint**|Идентификационный номер, связанный *state_description*.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = ОТМЕТКА ПОЛНОГО УДАЛЕНИЯ<br /><br /> СЖАТАЯ имеет единственное состояние, которое применяется к таблицам в памяти.|  
|**state_desc**|**nvarchar(60)**|Описание состояния группы строк:<br /><br /> НЕВИДИМЫЕ — группой строк, построение которого выполняется. Например: <br />Группа строк в columnstore является НЕВИДИМЫМ во время сжатия данных. После завершения изменения метаданных коммутатора сжатие состояние строки columnstore право НЕВИДИМОЙ COMPRESSED и входит в группу строк deltastore закрыт для отметки полного удаления.<br /><br /> OPEN — группа строк deltastore, которая принимает новые строки. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> CLOSED — группа строк в разностном хранилище, содержащее максимальное число строк и ожидает процесса перемещения кортежей для его сжатия в columnstore.<br /><br /> COMPRESSED — группа строк, с помощью сжатия columnstore и храниться в columnstore.<br /><br /> TOMBSTONE — группа строк, которая раньше была в deltastore и больше не используется.|  
|**total_rows**|**bigint**|Число строк физической, хранимых в группе строк. Для групп сжатая строка в нем, помеченные удаляемых строк.|  
|**deleted_rows**|**bigint**|Число строк, физически хранятся в группе сжатых строк, помеченных для удаления.<br /><br /> 0 для группы строк, которые находятся в разностного хранилища.|  
|**size_in_bytes**|**bigint**|Общий размер в байтах всех страниц в этой группе строк. Этот размер включает размер, необходимый для хранения метаданных или Общие словари.|  
|**trim_reason**|**tinyint**|Причины, вызвавшей группы строк COMPRESSED иметь меньше, чем максимальное число строк.<br /><br /> 0 — UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1 - NO_TRIM<br /><br /> 2 - МАССОВОЙ ЗАГРУЗКИ<br /><br /> 3 — REORG<br /><br /> 4 — DICTIONARY_SIZE<br /><br /> 5 — MEMORY_LIMITATION<br /><br /> 6 — RESIDUAL_ROW_GROUP<br /><br /> 7 - STATS_MISMATCH<br /><br /> 8 - ПОДГОНЯТЬСЯ ПО РАЗМЕРУ|  
|**trim_reason_desc**|**nvarchar(60)**|Описание *trim_reason*.<br /><br /> 0 — UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION: произошла при обновлении с предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 - NO_TRIM: Группы строк не усекаются. Группа строк была сжата с максимально 1,048,476 строк.  Число строк, может быть меньше, если subsset строк было удалено, после закрытия разностную группу строк<br /><br /> 2 — массовой загрузки: Число строк ограничено размер пакета для массовой загрузки.<br /><br /> 3 — REORG: Принудительное сжатие во время выполнения команды REORG.<br /><br /> 4 — DICTIONARY_SIZE: Размер словаря увеличился слишком велик для сжатия всех строк друг с другом.<br /><br /> 5 — MEMORY_LIMITATION: Недостаточно памяти для сжатия всех строк друг с другом.<br /><br /> 6 — RESIDUAL_ROW_GROUP: Закрыто в рамках последней группы строк с строки < 1 миллион во время построения индекса<br /><br /> STATS_MISMATCH: только для columnstore в таблице в памяти. Если статистика неправильно указано, > = 1 миллион строк полное в заключительный фрагмент, но мы нашли меньшее число, сжатой группы строк будут иметь < 1 миллион строк<br /><br /> Подгоняться по РАЗМЕРУ: только для columnstore в таблице в памяти. Если резервная копия заключительного > 1 млн строк на полное, оставшиеся строки последнего пакета сжаты, если число между 100 КБ и 1 миллион|  
|**transition_to_compressed_state**|tinyint|Показывает, как это группы строк они не перемещались дельта-хранилища в сжатый состояние в columnstore.<br /><br /> 1 - NOT_APPLICABLE<br /><br /> 2 — INDEX_BUILD<br /><br /> 3 — TUPLE_MOVER<br /><br /> 4 — REORG_NORMAL<br /><br /> 5 — REORG_FORCED<br /><br /> 6 - МАССОВОЙ ЗАГРУЗКИ<br /><br /> 7 - СЛИЯНИЯ|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE — операция неприменима к deltastore. Или группа строк была сжата перед обновлением до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] в этом случае журнал не сохраняется.<br /><br /> Перестроение индекса в сжатые группы строк или INDEX_BUILD — создание индекса.<br /><br /> TUPLE_MOVER — кортежей в фоновом режиме сжатые группы строк. Это происходит после группы строк изменяет состояние из ОТКРЫТОГО ЗАКРЫТО.<br /><br /> REORG_NORMAL — операция реорганизации, ALTER INDEX... REORG перемещать ЗАКРЫТОЙ группы строк из deltastore в columnstore. Это произошло раньше времени на перемещение группы строк, кортежей.<br /><br /> REORG_FORCED — это группа строк была открыта в deltastore и принудительного раньше, чем его полное число строк в columnstore.<br /><br /> BULKLOAD — операции массовой загрузки сжатые группы строк напрямую без использования deltastore.<br /><br /> СЛИЯНИЕ — операции merge объединять один или несколько групп строк в этой группе строк и затем выполнить сжатие columnstore.|  
|**has_vertipaq_optimization**|bit|Оптимизация Vertipaq улучшает сжатие columnstore изменять порядок строк в группе строк, чтобы добиться более эффективного сжатия. Эта оптимизация происходит автоматически в большинстве случаев. Существует два варианта Vertipaq оптимизация не используется:<br/>  а. Когда перемещает разностной группы строк в columnstore и один или несколько некластеризованных индексов на основе индекса columnstore - в этом случае оптимизации Vertipaq пропущено до сводит к минимуму изменения в индекс сопоставления;<br/> б. для индексов columnstore для таблиц, оптимизированных для памяти. <br /><br /> 0 = нет<br /><br /> 1 = да|  
|**Создание**|bigint|Строки группы поколение, связанное с этой группой строк.|  
|**created_time**|datetime2|Время для создания этой группы строк.<br /><br /> NULL — для индекса columnstore в таблице в памяти.|  
|**closed_time**|datetime2|Время для закрытия этой группы строк.<br /><br /> NULL — для индекса columnstore в таблице в памяти.|  
  
## <a name="results"></a>Результаты  
 Возвращает по одной строке для каждой группы строк в текущей базе данных.  
  
## <a name="permissions"></a>Permissions  
 Требуются следующие разрешения.  
  
-   Разрешение CONTROL на таблицу.  
  
-   Разрешение VIEW DATABASE STATE в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calculate-fragmentaton-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. Расчет fragmentaton принятия решения о реорганизации или перестроения индекса columnstore.  
 Для индексов columnstore процент удаленных строк служит хорошей мерой для фрагментации в группе строк. Если фрагментация — 20% или более рекомендуется удаления удаленных строк.  Примеры см. в разделе [дефрагментация индексов Columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md).  
  
 В этом примере соединяет **sys.dm_db_column_store_row_group_physical_stats** с другими системными таблицы, а затем вычисляет `Fragmentation` столбца для оценки эффективности каждой группы строк в текущей базе данных.     Чтобы найти сведения об одной таблице, удалите комментарий дефисы перед **ГДЕ** предложения и введите имя таблицы.  
  
```tsql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/total_rows AS 'Fragmentation'  
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Руководство по индексам columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_dictionaries &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
