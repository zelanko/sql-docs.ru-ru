---
title: "sys.internal_partitions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
dev_langs: TSQL
ms.assetid: 0262df2b-5ba7-4715-b17b-3d9ce470a38e
caps.latest.revision: "13"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83cb1a2bc846f21a12b3d83b0499edf70b404656
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysinternalpartitions-transact-sql"></a>sys.internal_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого набора строк, который отслеживает внутренние данные для индексов columnstore для таблиц на диске. Эти наборы строк являются внутренними для индексов columnstore и отслеживания удалены строки, сопоставления группы строк и изменений хранения групп строк. Они позволяют отслеживать данные для каждого для каждой секции таблицы; Каждая таблица имеет по крайней мере одну секцию. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]повторное создание наборов строк при каждом перестраивает индекс columnstore.   
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Идентификатор секции для этой секции. Является уникальным в пределах базы данных.|  
|object_id|**int**|Идентификатор объекта для таблицы, содержащей секцию.|  
|index_id|**int**|Идентификатор индекса для индекса columnstore, определенные для таблицы.<br /><br /> 1 = кластеризованный индекс columnstore<br /><br /> 2 = некластеризованный индекс columnstore|  
|partition_number|**int**|Номер секции.<br /><br /> 1 = первой секции секционированной таблицы или отдельной его секции несекционированной таблицы.<br /><br /> 2 = второй раздел и т. д.|  
|internal_object_type|**tinyint**|Объекты набора строк, которые отслеживают внутренние данные для индекса columnstore.<br /><br /> 2 = COLUMN_STORE_DELETE_BITMAP<br /><br /> 3 = COLUMN_STORE_DELTA_STORE<br /><br /> 4 = COLUMN_STORE_DELETE_BUFFER<br /><br /> 5 = COLUMN_STORE_MAPPING_INDEX|  
|internal_object_type_desc|**nvarchar(60)**|COLUMN_STORE_DELETE_BITMAP — это индекс битовой карты отслеживает строк, помеченных как удаленные из columnstore. Точечный рисунок — для каждой группы строк, поскольку секции могут иметь строк в несколько групп строк. Строки являются, по-прежнему физически присутствует и в результате образуется в columnstore.<br /><br /> COLUMN_STORE_DELTA_STORE — хранилищ группы строк, называемые группами строк, в хранилище столбцов не сжаты. Каждой секции таблицы может иметь ноль или более группы строк deltastore.<br /><br /> COLUMN_STORE_DELETE_BUFFER — поддержка удаления обновляемые некластеризованные индексы columnstore. Когда запрос удаляет строки из базовой таблицы rowstore, буфер удаления отслеживает удаления из columnstore. Когда 1048576 превышает количество удаленных строк, они объединяются обратно в точечный рисунок delete фоновый поток кортежей или команда выполняется явно Reorganize.  В любой момент времени объединение delete точечный рисунок и буфера удаления представляет все удаленные строки.<br /><br /> COLUMN_STORE_MAPPING_INDEX — используется только в том случае, если кластеризованный индекс есть дополнительный некластеризованный индекс. Некластеризованный индекс ключей сопоставляется правильные группы строк и идентификатор строки в columnstore. Она только хранит ключи в строках, переместить в другой группе строк; Это происходит, когда разностная группа строк сжимается в columnstore, а операция слияния объединяет строки из двух разных групп строк.|  
|Row_group_id|**int**|Идентификатор группы строк deltastore. Каждой секции таблицы может иметь ноль или более группы строк deltastore.|  
|hobt_id|**bigint**|Идентификатор объекта внутренней набора строк. Это хороший ключ для соединения с другими динамическими административными представлениями, чтобы получить дополнительные сведения о физических характеристик внутреннего набора строк.|  
|rows|**bigint**|Приблизительное количество строк в данной секции.|  
|data_compression|**tinyint**|Состояние сжатия для набора строк:<br /><br /> 0 = нет<br /><br /> 1 = ROW<br /><br /> 2 = PAGE|  
|data_compression_desc|**nvarchar(60)**|Состояние сжатия для каждой секции. Возможные значения для таблиц rowstore: NONE, ROW и PAGE. Возможные значения для таблиц columnstore: COLUMNSTORE и COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="general-remarks"></a>Общие замечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]повторно создает новые индексы внутренней columnstore каждый раз, он создает или перестраивает индекс columnstore.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-view-all-of-the-internal-rowsets-for-a-table"></a>A. Просмотр всех внутренних наборов строк для таблицы  
 Этот пример возвращает все наборы строк внутренней columnstore для таблицы. Можно также использовать hobt_id для получения дополнительных сведений о конкретных строк.  
  
```  
SELECT i.object_id, i.index_id, i.name, p.hobt_id, p.internal_object_type_id, p.internal_object_type_desc  
FROM sys.internal_partitions AS p  
JOIN sys.indexes AS i  
on i.object_id = p.object_id  
WHERE p.object_id = OBJECT_ID ( '<table name' ) ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
