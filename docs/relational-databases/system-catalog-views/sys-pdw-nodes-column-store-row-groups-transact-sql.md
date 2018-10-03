---
title: sys.pdw_nodes_column_store_row_groups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b3c09c2a1771f1fad8640031ea1c1327921f8c82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698242"
---
# <a name="syspdwnodescolumnstorerowgroups-transact-sql"></a>sys.pdw_nodes_column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Предоставляет сведения об индексе кластеризованный индекс columnstore по отдельным сегментам, чтобы помочь администратору принимать решения о сопровождении в системе [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. **sys.pdw_nodes_column_store_row_groups** столбец для общего количества физически хранимых строк (в том числе помечаются как удаленные) и столбцов для числа строк, помечаются как удаленные. Используйте **sys.pdw_nodes_column_store_row_groups** чтобы определить, какую из строк высокий процент удаленных строк и групп должны быть перестроены.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор базовой таблицы. Это физическую таблицу на вычислительном узле, не object_id для логической таблицы в управляющем узле. Например object_id не совпадает с object_id в sys.tables.<br /><br /> Чтобы присоединить с sys.tables, используйте sys.pdw_index_mappings.|  
|**index_id**|**int**|Идентификатор кластеризованного индекса на *object_id* таблицы.|  
|**partition_number**|**int**|Идентификатор секции таблицы, которая содержит группу строк *row_group_id*. Можно использовать *partition_number* для присоединения к этому динамическому административному Представлению для sys.partitions.|  
|**row_group_id**|**int**|Идентификатор этой группы строк. Он уникален внутри секции.|  
|**dellta_store_hobt_id**|**bigint**|Hobt_id для разностных групп строк или значение NULL, если тип группы строк не является разностным. Разностная группа строк — это группа строк для чтения и записи, которая принимает новые записи. Разностная группа строк имеет **ОТКРОЙТЕ** состояния. Разностная группа строк остается в формате rowstore и не сжимается в формат columnstore.|  
|**state**|**tinyint**|Идентификатор, связанный с параметром state_description.<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|Описание сохраняемого состояния группы строк:<br /><br /> OPEN — группа строк для чтения и записи, которая принимает новые записи. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> CLOSED — группа строк, которая была заполнена, но еще не сжата процессом перемещения кортежей.<br /><br /> COMPRESSED — группа строк, которая заполнена и сжата.|  
|**total_rows**|**bigint**|Общее число строк, которые физически хранятся в группе строк. Некоторые из строк могли быть удалены, но хранятся и дальше. Максимальное количество строк в группе — 1 048 576 (FFFFF в шестнадцатеричном формате).|  
|**deleted_rows**|**bigint**|Количество строк, физически хранятся в группе строк, которые помечены для удаления.<br /><br /> Всегда 0 для РАЗНОСТНОЙ группы строк.|  
|**size_in_bytes**|**int**|Общий размер в байтах всех страниц в этой группе строк. Этот размер включает размер, необходимый для хранения метаданных или Общие словари.|  
|**pdw_node_id**|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|  
|**distribution_id**|**int**|Уникальный идентификатор распределения.|
  
## <a name="remarks"></a>Примечания  
 Возвращает одну строку для каждой группы строк columnstore для каждой таблицы с кластеризованным или некластеризованным индексом columnstore.  
  
 Используйте **sys.pdw_nodes_column_store_row_groups** для определения числа строк, входящих в группы строк и размер группы строк.  
  
 Если количество удаленных строк в группе становится большим по отношению к общему числу строк, таблица становится менее эффективной. Перестройте индекс columnstore, чтобы сократить размер таблицы и уменьшить число дисковых операций ввода-вывода, необходимых для чтения таблицы. Для перестроения индекса columnstore используйте **ПЕРЕСТРОИТЬ** параметр **ALTER INDEX** инструкции.  
  
 Обновляемый компонент columnstore сначала вставляет новые данные в **ОТКРОЙТЕ** группа строк, а в формате rowstore, а также иногда называют таблицей разности.  После заполнения открытой группы строк ее состояние меняется на **ЗАКРЫТО**. Закрытая группа строк сжимается в формат columnstore процессом перемещения кортежей и состояние изменяется на **СЖАТАЯ**.  Процесс перемещения кортежей — это фоновый процесс, который периодически активируется и проверяет, существуют ли закрытые группы строк, готовые к сжатию в группу строк columnstore.  Процесс перемещения кортежей также освобождает все группы строк, в которых удалены все строки. Освобождение группы строк, помечаются как **ПРЕКРАЩЕНО**. Чтобы немедленно запустить процесс перемещения кортежей используйте **РЕОРГАНИЗОВАТЬ** параметр **ALTER INDEX** инструкции.  
  
 Когда группа строк columnstore заполняется, она сжимаются и прекращает принимать новые строки. Когда строки удаляются из сжатой группы, они сохраняются в ней, но отмечаются как удаленные. Обновления сжатой группы реализуются как удаление из сжатой группы и вставка в открытую группу.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **VIEW SERVER STATE**.  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример соединяет **sys.pdw_nodes_column_store_row_groups** таблицы с другими системными таблицами для возврата сведений об определенных таблицах. Вычисляемый столбец `PercentFull` — это оценка эффективности группы строк. Поиск сведений в одной таблице, удалите комментарий дефиса в начале предложения WHERE, и задайте имя таблицы.  
  
```  
SELECT IndexMap.object_id,   
  object_name(IndexMap.object_id) AS LogicalTableName,   
  i.name AS LogicalIndexName, IndexMap.index_id, NI.type_desc,   
  IndexMap.physical_name AS PhyIndexNameFromIMap,   
  CSRowGroups.*,  
  100*(ISNULL(deleted_rows,0))/total_rows AS PercentDeletedRows   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.pdw_index_mappings AS IndexMap  
    ON i.object_id = IndexMap.object_id  
    AND i.index_id = IndexMap.index_id  
JOIN sys.pdw_nodes_indexes AS NI  
    ON IndexMap.physical_name = NI.name  
    AND IndexMap.index_id = NI.index_id  
JOIN sys.pdw_nodes_column_store_row_groups AS CSRowGroups  
    ON CSRowGroups.object_id = NI.object_id   
    AND CSRowGroups.pdw_node_id = NI.pdw_node_id  
AND CSRowGroups.index_id = NI.index_id      
--WHERE t.name = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, IndexMap.physical_name, pdw_node_id;  
```  

Следующие [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] пример подсчитывает строки каждой секции, для кластеризованных столбцов также хранятся как много строк находятся в открытым, закрыто или строки сжатых группах:  

```
SELECT
    s.name AS [Schema Name]
    ,t.name AS [Table Name]
    ,rg.partition_number AS [Partition Number]
    ,SUM(rg.total_rows) AS [Total Rows]
    ,SUM(CASE WHEN rg.State = 1 THEN rg.Total_rows Else 0 END) AS [Rows in OPEN Row Groups]
    ,SUM(CASE WHEN rg.State = 2 THEN rg.Total_Rows ELSE 0 END) AS [Rows in Closed Row Groups]
    ,SUM(CASE WHEN rg.State = 3 THEN rg.Total_Rows ELSE 0 END) AS [Rows in COMPRESSED Row Groups]
FROM sys.pdw_nodes_column_store_row_groups rg
JOIN sys.pdw_nodes_tables pt
ON rg.object_id = pt.object_id AND rg.pdw_node_id = pt.pdw_node_id AND pt.distribution_id = rg.distribution_id
JOIN sys.pdw_table_mappings tm
ON pt.name = tm.physical_name
INNER JOIN sys.tables t
ON tm.object_id = t.object_id
INNER JOIN sys.schemas s
ON t.schema_id = s.schema_id
GROUP BY s.name, t.name, rg.partition_number
ORDER BY 1, 2
```
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Создание ИНДЕКСА COLUMNSTORE &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
