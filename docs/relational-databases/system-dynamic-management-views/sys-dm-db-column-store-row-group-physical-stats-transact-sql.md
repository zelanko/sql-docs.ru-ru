---
title: sys. DM _db_column_store_row_group_physical_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 836f8b8152e5801ab6bfc382c09a675b3c1e464f
ms.sourcegitcommit: 594cee116fa4ee321e1f5e5206f4a94d408f1576
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70009413"
---
# <a name="sysdm_db_column_store_row_group_physical_stats-transact-sql"></a>sys. DM _db_column_store_row_group_physical_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Предоставляет текущие сведения на уровне группы строк о всех индексах columnstore в текущей базе данных.  
  
 Это расширяет представление каталога [sys. column_store_row_groups &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор базовой таблицы.|  
|**index_id**|**int**|ИДЕНТИФИКАТОР этого индекса columnstore в таблице *object_id* .|  
|**partition_number**|**int**|Идентификатор секции таблицы, содержащей *row_group_id*. Partition_number можно использовать для соединения этого динамического административного представления с представлением sys.partitions.|  
|**row_group_id**|**int**|Идентификатор этой группы строк. Для секционированных таблиц это значение уникально в пределах секции.<br /><br /> -1 для хвоста в памяти.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id для группы строк в разностном хранилище.<br /><br /> Значение NULL, если группа строк не находится в разностном хранилище.<br /><br /> Значение NULL для заключительного фрагмента таблицы в памяти.|  
|**state**|**tinyint**|ИДЕНТИФИКАЦИОНный номер, связанный *state_description*.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = ЗАХОРОНЕНИЕ<br /><br /> Сжатие является единственным состоянием, которое применяется к таблицам в памяти.|  
|**state_desc**|**nvarchar(60)**|Описание состояния группы строк:<br /><br /> Невидимая — группа строк, которая строится. Пример: <br />Группа строк в columnstore невидима во время сжатия данных. После завершения сжатия параметр метаданных изменяет состояние группы строк columnstore с невидимого на сжатый и состояние группы строк deltastore с "ЗАКРЫТо" на "ЗАХОРОНЕНие".<br /><br /> OPEN — deltastore группа строк, которая принимает новые строки. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> ЗАКРЫТо — группа строк в разностном хранилище, которая содержит максимальное количество строк, и ожидает, пока процесс перемещения кортежа сжимает его в columnstore.<br /><br /> СЖАТЫЙ — группа строк, которая сжимается с помощью сжатия columnstore и хранится в columnstore.<br /><br /> ЗАХОРОНЕНие — группа строк, которая ранее была в deltastore и больше не используется.|  
|**total_rows**|**bigint**|Количество строк, физически хранимых в группе строк. Для сжатых групп строк сюда входят строки, помеченные как удаленные.|  
|**deleted_rows**|**bigint**|Количество строк, физически хранящихся в сжатой группе строк и помеченных для удаления.<br /><br /> 0 для групп строк, которые находятся в разностном хранилище.|  
|**size_in_bytes**|**bigint**|Объединенный размер всех страниц в данной группе строк (в байтах). Этот размер не включает размер, необходимый для хранения метаданных или общих словарей.|  
|**trim_reason**|**tinyint**|Причина, по которой СЖАТая группа строк была активирована, меньше максимального количества строк.<br /><br /> 0 — UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1 — NO_TRIM<br /><br /> 2 — BULKLOAD<br /><br /> 3 — REORG<br /><br /> 4 — DICTIONARY_SIZE<br /><br /> 5 — MEMORY_LIMITATION<br /><br /> 6 — RESIDUAL_ROW_GROUP<br /><br /> 7 — STATS_MISMATCH<br /><br /> 8 — ПЕРЕБРОСКИ|  
|**trim_reason_desc**|**nvarchar(60)**|Описание *trim_reason*.<br /><br /> 0 — UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION: Произошла ошибка при обновлении предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 — NO_TRIM: Группа строк не обрезается. Группа строк была сжата до 1 048 476 строк.  Число строк может быть меньше, если подмножество строк было удалено после закрытия разностного группы строк<br /><br /> 2 — BULKLOAD: Размер пакета с пакетной загрузкой ограничивает количество строк.<br /><br /> 3 — REORG:  Принудительное сжатие как часть команды REORG.<br /><br /> 4 — DICTIONARY_SIZE: Размер словаря слишком велик для сжатия всех строк вместе.<br /><br /> 5 — MEMORY_LIMITATION: Недостаточно свободной памяти для сжатия всех строк.<br /><br /> 6 — RESIDUAL_ROW_GROUP:  Закрывается как часть последней группы строк со строками < 1 000 000 во время операции построения индекса<br /><br /> STATS_MISMATCH: Только для columnstore в таблице в памяти. Если статистика неправильно указывает > = 1 000 000 уточняющих строк в заключительном фрагменте, но было обнаружено меньшее число, сжатая группы строк будет содержать < 1 000 000 строк.<br /><br /> ПЕРЕБРОСКИ Только для columnstore в таблице в памяти. Если в хвосте имеется > 1 000 000 подходящих строк, то оставшиеся строки оставшихся пакетов сжимаются, если число составляет от 100 КБ до 1 000 000|  
|**transition_to_compressed_state**|tinyint|Показывает, как этот группы строк был перемещен из deltastore в сжатое состояние в columnstore.<br /><br /> 1 — NOT_APPLICABLE<br /><br /> 2 — INDEX_BUILD<br /><br /> 3 — TUPLE_MOVER<br /><br /> 4 — REORG_NORMAL<br /><br /> 5 — REORG_FORCED<br /><br /> 6 — BULKLOAD<br /><br /> 7\. СЛИЯНИЕ|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE — операция не применяется к deltastore. Или группы строк был сжат до обновления до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] , в этом случае журнал не сохраняется.<br /><br /> INDEX_BUILD — индекс создания или перестроения индекса сжат группы строк.<br /><br /> TUPLE_MOVER — задача перемещения кортежей, выполняемая в фоновом режиме, сжатом группы строк. Это происходит после того, как состояние группы строк изменится с OPEN на CLOSED.<br /><br /> REORG_NORMAL — операция реорганизации, ALTER INDEX... REORG, перемещен закрытый группы строк из deltastore в columnstore. Это произошло до того, как в процессе перемещения по кортежам пришло время на перемещение группы строк.<br /><br /> REORG_FORCED — этот группы строк был открыт в deltastore и был принудительно передан в columnstore до того, как в нем было указано полное число строк.<br /><br /> BULKLOAD — операция массовой загрузки сжимает группы строк напрямую без использования deltastore.<br /><br /> MERGE — Операция Merge, объединяющая один или несколько групп строк в этот группы строк, а затем выполнила сжатие columnstore.|  
|**has_vertipaq_optimization**|bit|Оптимизация VertiPaq улучшает сжатие columnstore путем изменения порядка строк в группы строк для достижения более высокого сжатия. В большинстве случаев такая оптимизация выполняется автоматически. В двух случаях оптимизация VertiPaq не используется:<br/>  1\. Если Дельта-группы строк перемещается в columnstore и имеется один или несколько некластеризованных индексов в индексе columnstore, то оптимизация VertiPaq пропускается для сворачивания изменений в индексе сопоставления.<br/> 2\. для индексов columnstore в таблицах, оптимизированных для памяти. <br /><br /> 0 = нет<br /><br /> 1 = да|  
|**поколения**|bigint|Создание группы строк, связанной с этой группой строк.|  
|**created_time**|datetime2|Время создания группы строк.<br /><br /> NULL — для индекса columnstore в таблице в памяти.|  
|**closed_time**|datetime2|Время, когда группы строк был закрыт.<br /><br /> NULL — для индекса columnstore в таблице в памяти.|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="results"></a>Результаты  
 Возвращает по одной строке для каждого группы строк в текущей базе данных.  
  
## <a name="permissions"></a>Разрешения  
Требуется `CONTROL` разрешение на таблицу и `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calculate-fragmentation-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. Вычислите фрагментацию, чтобы решить, когда следует реорганизовать или перестроить индекс columnstore.  
 Для индексов columnstore процент удаленных строк является хорошей мерой для фрагментации в группы строк. Если фрагментация составляет 20% или более, рекомендуется удалить удаленные строки. Дополнительные примеры см. в разделе [реорганизация и перестроение индексов](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 В этом примере показано соединение **sys. DM _db_column_store_row_group_physical_stats** с другими системными таблицами, а `Fragmentation` затем столбец вычисляется как оценка эффективности каждой группы строк в текущей базе данных. Чтобы найти сведения об одной таблице, удалите дефисы в комментариях перед предложением **WHERE** и укажите имя таблицы.  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/NULLIF(total_rows,0) AS 'Fragmentation'
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)      
 [Архитектура индексов columnstore](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)         
 [Запросы к системному каталогу SQL Server вопросы и ответы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. ALL _columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys. computed_columns &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md) [sys. column_store_dictionaries &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
