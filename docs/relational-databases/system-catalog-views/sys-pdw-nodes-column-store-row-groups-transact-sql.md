---
title: "sys.pdw_nodes_column_store_row_groups (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75e4229fde3cae66cdd2172c0f2bea0cbf63bf10
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwnodescolumnstorerowgroups-transact-sql"></a>sys.pdw_nodes_column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Предоставляет сведения об индексе кластеризованный индекс columnstore по отдельным сегментам, что позволяет администратору принимать решения о сопровождении в системе [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. **sys.pdw_nodes_column_store_row_groups** столбца общего количества физически хранимых строк (включая отмеченные как удаленные) и столбцов для числа строк, помечаются как удаленные. Используйте **sys.pdw_nodes_column_store_row_groups** определить, какая строка группы имеют высокий процент удаленных строк и должен быть перестроен.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор базовой таблицы. Это физическую таблицу на вычислительном узле, а не object_id для логической таблицы на узел элемента управления. Например object_id не совпадает с object_id в sys.tables.<br /><br /> Для соединения с sys.tables, используйте sys.pdw_index_mappings.|  
|**index_id**|**int**|Идентификатор кластеризованный индекс columnstore на *object_id* таблицы.|  
|**partition_number**|**int**|Идентификатор секции таблицы, содержащий группы строк *row_group_id*. Можно использовать *partition_number* для соединения этого динамического административного Представления с представлением sys.partitions.|  
|**row_group_id**|**int**|Идентификатор этой группы строк. Он уникален внутри секции.|  
|**dellta_store_hobt_id**|**bigint**|Hobt_id для разностных групп строк или значение NULL, если тип группы строк не является разностным. Разностная группа строк — это группа строк для чтения и записи, которая принимает новые записи. Разностная группа строк имеет **ОТКРОЙТЕ** состояния. Разностная группа строк остается в формате rowstore и не сжимается в формат columnstore.|  
|**state**|**tinyint**|Идентификатор, связанный с параметром state_description.<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|Описание сохраняемого состояния группы строк:<br /><br /> OPEN — группа строк для чтения и записи, которая принимает новые записи. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> CLOSED — группа строк, которая была заполнена, но еще не сжата процессом перемещения кортежей.<br /><br /> COMPRESSED — группа строк, которая заполнена и сжата.|  
|**total_rows**|**bigint**|Общее число строк, которые физически хранятся в группе строк. Некоторые из строк могли быть удалены, но хранятся и дальше. Максимальное количество строк в группе — 1 048 576 (FFFFF в шестнадцатеричном формате).|  
|**deleted_rows**|**bigint**|Число строк, физически хранятся в группе строк, помеченных для удаления.<br /><br /> Всегда 0 для РАЗНОСТНЫЕ группы строк.|  
|**size_in_bytes**|**int**|Общий размер в байтах всех страниц в этой группе строк. Этот размер включает размер, необходимый для хранения метаданных или Общие словари.|  
|**pdw_node_id**|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|  
|**distribution_id**|**int**|Уникальный идентификатор распределения.|
  
## <a name="remarks"></a>Remarks  
 Возвращает одну строку для каждой группы строк columnstore для каждой таблицы с кластеризованным или некластеризованным индексом columnstore.  
  
 Используйте **sys.pdw_nodes_column_store_row_groups** для определения числа строк, включенных в группу строк и размер группы строк.  
  
 Если количество удаленных строк в группе становится большим по отношению к общему числу строк, таблица становится менее эффективной. Перестройте индекс columnstore, чтобы сократить размер таблицы и уменьшить число дисковых операций ввода-вывода, необходимых для чтения таблицы. Для перестроения индекса columnstore используйте **ПЕРЕСТРОИТЬ** параметр **ALTER INDEX** инструкции.  
  
 Обновляемые columnstore сначала вставляет новые данные в **ОТКРОЙТЕ** группа строк в формате rowstore, а также иногда называют таблицей разности.  После заполнения открытой группы строк ее состояние меняется на **ЗАКРЫТО**. Закрытая группа строк сжимается в формате columnstore, кортежей и состояние изменяется на **СЖАТАЯ**.  Процесс перемещения кортежей — это фоновый процесс, который периодически активируется и проверяет, существуют ли закрытые группы строк, готовые к сжатию в группу строк columnstore.  Процесс перемещения кортежей также освобождает все группы строк, в которых удалены все строки. Освобождение группы строк, помечаются как **удалено**. Чтобы немедленно запустить кортежей, используйте **РЕОРГАНИЗОВАТЬ** параметр **ALTER INDEX** инструкции.  
  
 Когда группа строк columnstore заполняется, она сжимаются и прекращает принимать новые строки. Когда строки удаляются из сжатой группы, они сохраняются в ней, но отмечаются как удаленные. Обновления сжатой группы реализуются как удаление из сжатой группы и вставка в открытую группу.  
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW SERVER STATE** разрешение.  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример соединяет **sys.pdw_nodes_column_store_row_groups** таблицы с другими системными таблицами для получения сведений об определенных таблицах. Вычисляемый столбец `PercentFull` — это оценка эффективности группы строк. Поиск сведений в одной таблице, удалите комментарий дефиса в начале предложения WHERE, и введите имя таблицы.  
  
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

Следующие [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] пример подсчитывает строки каждой секции для кластеризованного столбце также хранятся как много строк находятся в группах Open, закрыто или строку, сжатая:  

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
 [СОЗДАТЬ индекс COLUMNSTORE &#40; Transact-SQL &#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
