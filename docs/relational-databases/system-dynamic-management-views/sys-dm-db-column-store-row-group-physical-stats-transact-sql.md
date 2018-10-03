---
title: sys.dm_db_column_store_row_group_physical_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/04/2017
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cbc4b71c75eab2699bccd5f83f68a621b4ea1fc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624182"
---
# <a name="sysdmdbcolumnstorerowgroupphysicalstats-transact-sql"></a>sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Предоставляет последнюю информацию на уровне группы строк обо всех индексов columnstore в текущей базе данных.  
  
 При этом расширяется в представление каталога [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор базовой таблицы.|  
|**index_id**|**int**|Идентификатор этого индекса columnstore на *object_id* таблицы.|  
|**partition_number**|**int**|Идентификатор секции таблицы, которая содержит *row_group_id*. Partition_number можно использовать для соединения этого динамического административного представления с представлением sys.partitions.|  
|**row_group_id**|**int**|Идентификатор этой группы строк. Для секционированных таблиц является уникальным в пределах секции.<br /><br /> -1 для заключительного фрагмента в памяти.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id для группы строк в разностном хранилище.<br /><br /> Имеет значение NULL, если группа строк не в разностном хранилище.<br /><br /> Значение NULL для заключительного фрагмента таблицы в памяти.|  
|**state**|**tinyint**|Идентификационный номер, связанный *параметром state_description*.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = ОТМЕТКИ ПОЛНОГО УДАЛЕНИЯ<br /><br /> COMPRESSED — это единственное состояние, которое применяется к таблицам в памяти.|  
|**state_desc**|**nvarchar(60)**|Описание состояния группы строк:<br /><br /> НЕВИДИМЫЕ — группу строк, которое создается. Пример: <br />Группа строк в columnstore является НЕВИДИМЫМ, пока данные сжимаются. После завершения изменения метаданных switch сжатие состояние строки columnstore группы из НЕВИДИМОГО для СЖАТЫХ и состояния группы строк deltastore с ЗАКРЫТО для объекта-ЗАХОРОНЕНИЯ.<br /><br /> OPEN — группа строк deltastore, которая принимает новые строки. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> CLOSED — группа строк в разностном хранилище, содержащее максимальное количество строк и ожидает процесса перемещения кортежей для сжатия в columnstore.<br /><br /> COMPRESSED — группа строк, с помощью сжатия columnstore и хранятся в columnstore.<br /><br /> TOMBSTONE — группа строк, которая ранее называлась в deltastore и больше не используется.|  
|**total_rows**|**bigint**|Количество физических строк, хранимых в группе строк. Для групп сжатых строк такие, которые помечены удаляемых строк.|  
|**deleted_rows**|**bigint**|Количество строк, физически хранятся в сжатой группе строк, которые помечены для удаления.<br /><br /> 0 для групп строк, которые находятся в разностном хранилище.|  
|**size_in_bytes**|**bigint**|Общий размер в байтах всех страниц в этой группе строк. Этот размер включает размер, необходимый для хранения метаданных или Общие словари.|  
|**trim_reason**|**tinyint**|Причины, вызвавшей группы строк COMPRESSED Чтобы меньше, чем максимальное количество строк.<br /><br /> 0 — UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1 - NO_TRIM<br /><br /> 2 - BULKLOAD<br /><br /> 3 — REORG<br /><br /> 4 — DICTIONARY_SIZE<br /><br /> 5 – MEMORY_LIMITATION<br /><br /> 6 — RESIDUAL_ROW_GROUP<br /><br /> 7 - STATS_MISMATCH<br /><br /> 8 - ПЕРЕБРОСКИ|  
|**trim_reason_desc**|**nvarchar(60)**|Описание *trim_reason*.<br /><br /> 0 — UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION: произошла при обновлении с предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 - NO_TRIM: Группы строк не усекаются. Группа строк была сжата с максимально 1,048,476 строк.  Число строк, может быть меньше, если subsset строк был удален после закрытия разностной группы строк<br /><br /> 2 — BULKLOAD: Размер пакета массовой загрузки из ограниченного числа строк.<br /><br /> 3 — REORG: Принудительное сжатие как часть команды REORG.<br /><br /> 4 — DICTIONARY_SIZE: Размер словаря увеличились слишком велик для сжатия всех строк друг с другом.<br /><br /> 5 – MEMORY_LIMITATION: Недостаточно памяти для сжатия всех строк друг с другом.<br /><br /> 6 — RESIDUAL_ROW_GROUP: Закрыто в составе последней группы строк с помощью строк < 1 миллиона во время построения индекса<br /><br /> STATS_MISMATCH: только для индекса columnstore для таблицы в памяти. Если статистика неправильно указано, > = 1 миллион строк полное в заключительный фрагмент, но мы нашли меньшее число, функция сжатую группу строк будет иметь < 1 миллион строк<br /><br /> ПЕРЕБРОСКИ: только для индекса columnstore для таблицы в памяти. Если заключительного > 1 миллион отмеченные строки, оставшиеся строки последнего пакета будут сжаты, если число равно между 100 тыс. и 1 миллион|  
|**transition_to_compressed_state**|TINYINT|Показано, как эту группу строк перемещались из deltastore в сжатом состоянии columnstore.<br /><br /> 1 - NOT_APPLICABLE<br /><br /> 2 — INDEX_BUILD<br /><br /> 3 — TUPLE_MOVER<br /><br /> 4 — REORG_NORMAL<br /><br /> 5 – REORG_FORCED<br /><br /> 6 - BULKLOAD<br /><br /> 7 - СЛИЯНИЯ|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE — операция не применяется в deltastore. Или группа строк была сжата перед обновлением до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] в этом случае журнал не сохраняется.<br /><br /> Создание индекса INDEX_BUILD — или перестроение индекса в сжатые группы строк.<br /><br /> TUPLE_MOVER — процесс перемещения кортежей в фоновом режиме сжатые группы строк. Это происходит после группы строк изменяет состояние из ОТКРЫТОГО ЗАКРЫТО.<br /><br /> REORG_NORMAL — операция реорганизации, ALTER INDEX... REORG, перемещен ЗАКРЫТУЮ группу строк из deltastore в columnstore. Это произошло раньше времени для перемещения группы строк, кортежей.<br /><br /> REORG_FORCED — этой группы строк был открыт в deltastore и принудительно раньше, чем его полное число строк в columnstore.<br /><br /> BULKLOAD — операции массовой загрузки сжатые группы строк напрямую без использования deltastore.<br /><br /> СЛИЯНИЕ — операция слияния консолидированных один или несколько групп строк в эту группу строк и затем выполнить сжатие columnstore.|  
|**has_vertipaq_optimization**|bit|Оптимизация Vertipaq улучшает сжатие columnstore путем изменения порядка строк в группе строк, чтобы добиться более эффективного сжатия. Эта оптимизация выполняется автоматически в большинстве случаев. Существует два случая оптимизации Vertipaq не используется.<br/>  A. Когда перемещает разностная группа строк в columnstore и один или несколько некластеризованных индексов в индексе columnstore - в этом случае оптимизации Vertipaq пропускается для сводит к минимуму изменения в индекс сопоставления;<br/> Б. для индексов columnstore в таблицах, оптимизированных для памяти. <br /><br /> 0 = нет<br /><br /> 1 = да|  
|**Создание**|BIGINT|Строки группы поколение, связанное с этой группой строк.|  
|**created_time**|datetime2|Время для создания этой группы строк.<br /><br /> NULL — для индекса columnstore в таблице в памяти.|  
|**closed_time**|datetime2|Время для закрытия этой группы строк.<br /><br /> NULL — для индекса columnstore в таблице в памяти.|  
  
## <a name="results"></a>Результаты  
 Возвращает одну строку для каждой группы строк в текущей базе данных.  
  
## <a name="permissions"></a>Разрешения  
 Требуются следующие разрешения:  
  
-   Разрешение CONTROL на таблицу.  
  
-   Разрешение VIEW DATABASE STATE в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calculate-fragmentaton-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. Вычислите fragmentaton для принятия решения о реорганизации или перестроения индекса columnstore.  
 Применительно к индексам columnstore процент удаленных строк является хорошей мерой для фрагментации в группе строк. Если фрагментация составляет 20% или более мы рекомендуем удалить удаленные строки.  Примеры, см. в разделе [дефрагментация индексов Columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md).  
  
 В этом примере соединяет **sys.dm_db_column_store_row_group_physical_stats** с другими системными таблицы, а затем вычисляет `Fragmentation` столбца для оценки эффективности каждой из групп строк в текущей базе данных.     Чтобы найти сведения об одной таблице, удалите комментарий дефисы в начале **ГДЕ** предложения и укажите имя таблицы.  
  
```sql  
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
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Руководство по индексам columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
