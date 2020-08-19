---
description: sys. pdw_nodes_column_store_row_groups (Transact-SQL)
title: sys. pdw_nodes_column_store_row_groups (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 08/05/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8f323ccec312a1d2e11d72b582d1b574c923591f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447888"
---
# <a name="syspdw_nodes_column_store_row_groups-transact-sql"></a>sys. pdw_nodes_column_store_row_groups (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Предоставляет сведения о кластеризованном индексе columnstore для каждого сегмента, чтобы помочь администратору принять решения по управлению системой в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . **sys. pdw_nodes_column_store_row_groups** содержит столбец для общего числа физически хранимых строк (включая те, которые помечены как удаленные) и столбец для числа строк, помеченных как удаленные. Используйте представление **sys. pdw_nodes_column_store_row_groups** , чтобы определить, какие группы строк имеют высокий процент удаленных строк и должны быть перестроены.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор базовой таблицы. Это физическая таблица на кластерном узле, а не object_id логической таблицы на узле управления. Например, object_id не соответствует object_id в sys. Tables.<br /><br /> Для объединения с sys. Tables используйте представление sys. pdw_index_mappings.|  
|**index_id**|**int**|Идентификатор кластеризованного индекса columnstore в *object_id* таблице.|  
|**partition_number**|**int**|Идентификатор секции таблицы, содержащей *row_group_id*группы строк. Чтобы присоединить это динамическое административное представление к sys. partitions, можно использовать *partition_number* .|  
|**row_group_id**|**int**|Идентификатор этой группы строк. Он уникален внутри секции.|  
|**dellta_store_hobt_id**|**bigint**|Hobt_id для разностных групп строк или значение NULL, если тип группы строк не является разностным. Разностная группа строк — это группа строк для чтения и записи, которая принимает новые записи. Дельта-группа строк имеет **открытое** состояние. Разностная группа строк остается в формате rowstore и не сжимается в формат columnstore.|  
|**state**|**tinyint**|Идентификатор, связанный с параметром state_description.<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|Описание сохраняемого состояния группы строк:<br /><br /> ОТКРЫТЬ — группа строк для чтения и записи, которая принимает новые записи. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> ЗАКРЫТо — группа строк, которая была заполнена, но еще не сжата процессом перемещения кортежей.<br /><br /> СЖАТЫЙ — группа строк, которая была заполнена и сжата.|  
|**total_rows**|**bigint**|Общее число строк, которые физически хранятся в группе строк. Некоторые из строк могли быть удалены, но хранятся и дальше. Максимальное количество строк в группе — 1 048 576 (FFFFF в шестнадцатеричном формате).|  
|**deleted_rows**|**bigint**|Количество строк, физически хранящихся в группе строк, которые помечены для удаления.<br /><br /> Значение всегда равно 0 для РАЗНОСТных групп строк.|  
|**size_in_bytes**|**int**|Объединенный размер всех страниц в данной группе строк (в байтах). Этот размер не включает размер, необходимый для хранения метаданных или общих словарей.|  
|**pdw_node_id**|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|  
|**distribution_id**|**int**|Уникальный идентификатор распределения.|
  
## <a name="remarks"></a>Комментарии  
 Возвращает одну строку для каждой группы строк columnstore для каждой таблицы с кластеризованным или некластеризованным индексом columnstore.  
  
 Используйте представление **sys. pdw_nodes_column_store_row_groups** , чтобы определить количество строк, включаемых в группу строк, и размер группы строк.  
  
 Если количество удаленных строк в группе становится большим по отношению к общему числу строк, таблица становится менее эффективной. Перестройте индекс columnstore, чтобы сократить размер таблицы и уменьшить число дисковых операций ввода-вывода, необходимых для чтения таблицы. Для перестроения индекса columnstore используйте параметр **REBUILD** инструкции **ALTER INDEX** .  
  
 Обновляемый columnstore сначала вставляет новые данные в **открытый** группы строк, который находится в формате rowstore, а также иногда называется разностной таблицей.  После заполнения открытого группы строк его состояние меняется на **Closed**. Закрытый группы строк сжимается в формате columnstore с помощью перемещения кортежей, а состояние изменяется на **сжатое**.  Процесс перемещения кортежей — это фоновый процесс, который периодически активируется и проверяет, существуют ли закрытые группы строк, готовые к сжатию в группу строк columnstore.  Процесс перемещения кортежей также освобождает все группы строк, в которых удалены все строки. Освобожденные групп строк помечаются как **снятые**с учета. Для немедленного запуска перемещения кортежей используйте параметр **реорганизовать** инструкции **ALTER INDEX** .  
  
 Когда группа строк columnstore заполняется, она сжимаются и прекращает принимать новые строки. Когда строки удаляются из сжатой группы, они сохраняются в ней, но отмечаются как удаленные. Обновления сжатой группы реализуются как удаление из сжатой группы и вставка в открытую группу.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **VIEW SERVER STATE**.  
  
## <a name="examples-sssdw-and-sspdw"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере таблица **sys. pdw_nodes_column_store_row_groups** соединяется с другими системными таблицами для получения сведений о конкретных таблицах. Вычисляемый столбец `PercentFull` — это оценка эффективности группы строк. Чтобы найти сведения об одной таблице, удалите дефисы в комментариях перед предложением WHERE и укажите имя таблицы.  
  
```sql
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
WHERE total_rows > 0
--WHERE t.name = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, IndexMap.physical_name, pdw_node_id;  
```  

В следующем [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] примере подсчитывается количество строк на секцию для кластеризованных хранилищ столбцов, а также количество строк в открытых, закрытых или сжатых группах строк.  

```sql
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
    ON rg.object_id = pt.object_id
    AND rg.pdw_node_id = pt.pdw_node_id
    AND pt.distribution_id = rg.distribution_id
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
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
 [Создание индекса COLUMNSTORE &#40;&#41;Transact-SQL ](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys. pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys. pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
