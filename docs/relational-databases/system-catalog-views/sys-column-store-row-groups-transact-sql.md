---
title: "sys.column_store_row_groups (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.column_store_row_groups_TSQL
- column_store_row_groups
- sys.column_store_row_groups
- column_store_row_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_row_groups catalog view
ms.assetid: 76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ea17802f24a60df24fdc4107f52a5170ca4f0ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnstorerowgroups-transact-sql"></a>sys.column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о кластеризованных индексах columnstore по отдельным сегментам, что позволяет администратору принимать решения о сопровождении системы. **sys.column_store_row_groups** столбца общего количества физически хранимых строк (включая отмеченные как удаленные) и столбцов для числа строк, помечаются как удаленные. Используйте **sys.column_store_row_groups** определить, какая строка группы имеют высокий процент удаленных строк и должен быть перестроен.  
   
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы, для которой определен индекс.|  
|**index_id**|**int**|Идентификатор индекса таблицы, в которой содержится этот индекс columnstore.|  
|**partition_number**|**int**|Идентификатор секции таблицы, содержащей идентификатор row_group_id группы строк. Partition_number можно использовать для соединения этого динамического административного представления с представлением sys.partitions.|  
|**row_group_id**|**int**|Номер группы строк, связанный с этой группой строк. Он уникален внутри секции.<br /><br /> -1 = резервная копия заключительного таблицы в памяти.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id для ОТКРЫТАЯ группа строк в разностном хранилище.<br /><br /> Имеет значение NULL, если группа строк не разностного хранилища.<br /><br /> Значение NULL для заключительного фрагмента таблицы в памяти.|  
|**состояние**|**tinyint**|Идентификатор, связанный с параметром state_description.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN;<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED <br /><br /> 4 = ОТМЕТКА ПОЛНОГО УДАЛЕНИЯ|  
|**state_description**|**nvarchar(60)**|Описание сохраняемого состояния группы строк:<br /><br /> INVISIBLE — скрытый сжатый сегмент, который строится из данных разностного хранилища. Операции чтения будут использовать разностное хранилище до момента построения скрытого сжатого сегмента. Когда новый сегмент станет видимым, исходное разностное хранилище будет удалено.<br /><br /> OPEN — группа строк для чтения и записи, которая принимает новые записи. Открытая группа строк остается в формате rowstore и не сжимается в формат columnstore.<br /><br /> CLOSED — группа строк, которая была заполнена, но еще не сжата процессом перемещения кортежей.<br /><br /> COMPRESSED — группа строк, которая заполнена и сжата.|  
|**total_rows**|**bigint**|Общее число строк, которые физически хранятся в группе строк. Некоторые из строк могли быть удалены, но хранятся и дальше. Максимальное количество строк в группе — 1 048 576 (FFFFF в шестнадцатеричном формате).|  
|**deleted_rows**|**bigint**|Общее число строк в группе строк, которые отмечены как удаленные. Это значение всегда равно 0 для групп строк DELTA.|  
|**size_in_bytes**|**bigint**|Размер в байтах всех данных в этой группе строк (не включая метаданные или общие словари), как для групп строк DELTA и COLUMNSTORE.|  
  
## <a name="remarks"></a>Замечания  
 Возвращает одну строку для каждой группы строк columnstore для каждой таблицы с кластеризованным или некластеризованным индексом columnstore.  
  
 Используйте **sys.column_store_row_groups** для определения числа строк, включенных в группу строк и размер группы строк.  
  
 Если количество удаленных строк в группе становится большим по отношению к общему числу строк, таблица становится менее эффективной. Перестройте индекс columnstore, чтобы сократить размер таблицы и уменьшить число дисковых операций ввода-вывода, необходимых для чтения таблицы. Для перестроения индекса columnstore используйте **ПЕРЕСТРОИТЬ** параметр **ALTER INDEX** инструкции.  
  
 Обновляемые columnstore сначала вставляет новые данные в **ОТКРОЙТЕ** группа строк в формате rowstore, а также иногда называют таблицей разности.  После заполнения открытой группы строк ее состояние меняется на **ЗАКРЫТО**. Закрытая группа строк сжимается в формате columnstore, кортежей и состояние изменяется на **СЖАТАЯ**.  Процесс перемещения кортежей — это фоновый процесс, который периодически активируется и проверяет, существуют ли закрытые группы строк, готовые к сжатию в группу строк columnstore.  Процесс перемещения кортежей также освобождает все группы строк, в которых удалены все строки. Освобождение группы строк, помечаются как **ЗАХОРОНЕНИЯ**. Чтобы немедленно запустить кортежей, используйте **РЕОРГАНИЗОВАТЬ** параметр **ALTER INDEX** инструкции.  
  
 Когда группа строк columnstore заполняется, она сжимаются и прекращает принимать новые строки. Когда строки удаляются из сжатой группы, они сохраняются в ней, но отмечаются как удаленные. Обновления сжатой группы реализуются как удаление из сжатой группы и вставка в открытую группу.  
  
## <a name="permissions"></a>Permissions  
 Возвращает сведения о таблице, если у пользователя есть **VIEW DEFINITION** разрешение на таблицу.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример соединяет **sys.column_store_row_groups** таблицы с другими системными таблицами для получения сведений об определенных таблицах. Вычисляемый столбец `PercentFull` — это оценка эффективности группы строк. Чтобы найти сведения об одной таблице, удалите комментарий дефисы перед **ГДЕ** предложения и введите имя таблицы.  
  
```  
SELECT i.object_id, object_name(i.object_id) AS TableName,   
i.name AS IndexName, i.index_id, i.type_desc,   
CSRowGroups.*,   
100*(total_rows - ISNULL(deleted_rows,0))/total_rows AS PercentFull    
FROM sys.indexes AS i  
JOIN sys.column_store_row_groups AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id  
AND i.index_id = CSRowGroups.index_id   
--WHERE object_name(i.object_id) = '<table_name>'   
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
  
  

