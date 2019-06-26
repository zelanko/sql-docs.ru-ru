---
title: sys.internal_partitions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0262df2b-5ba7-4715-b17b-3d9ce470a38e
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5795ec9feaef483dd3ee9b5f3e31dbb619a89331
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388342"
---
# <a name="sysinternalpartitions-transact-sql"></a>sys.internal_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого набора строк, который отслеживает внутренние данные для индексов columnstore в таблицах на диске. Эти наборы строк являются внутренними для индексов columnstore и отслеживания удалены строки, сопоставления группы строк и разностные хранения групп строк. Они отслеживают данные для каждого для каждой секции таблицы; Каждая таблица имеет по крайней мере одну секцию. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторно создает наборы строк каждый раз, перестроением индекса columnstore.   
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Идентификатор секции для этой секции. Является уникальным в пределах базы данных.|  
|object_id|**int**|Идентификатор объекта для таблицы, содержащей секцию.|  
|index_id|**int**|Идентификатор индекса для индекса columnstore, определенные для таблицы.<br /><br /> 1 = кластеризованный индекс columnstore<br /><br /> 2 = некластеризованный индекс columnstore|  
|partition_number|**int**|Номер секции.<br /><br /> 1 = первой секции секционированной таблицы или секции одной несекционированной таблицы.<br /><br /> 2 = второго раздела и т. д.|  
|internal_object_type|**tinyint**|Объекты набора строк, которые отслеживают внутренние данные для индекса columnstore.<br /><br /> 2 = COLUMN_STORE_DELETE_BITMAP<br /><br /> 3 = COLUMN_STORE_DELTA_STORE<br /><br /> 4 = COLUMN_STORE_DELETE_BUFFER<br /><br /> 5 = COLUMN_STORE_MAPPING_INDEX|  
|internal_object_type_desc|**nvarchar(60)**|COLUMN_STORE_DELETE_BITMAP - этот индекс точечного рисунка отслеживает строки, помеченные как удаленные из индекса columnstore. Точечный рисунок бывает для каждой группы строк, поскольку секции могут иметь строк в нескольких группах строк. Строки являются, которые по-прежнему физически присутствует и занимая место в columnstore.<br /><br /> COLUMN_STORE_DELTA_STORE - хранилищ группы строк, называемые группами строк, не сжаты в хранилище столбцов. Каждой секции таблицы может содержать ноль или более групп строк deltastore.<br /><br /> COLUMN_STORE_DELETE_BUFFER - для поддержания удаление для обновляемые некластеризованные индексы columnstore. Когда запрос удаляет строку из таблицы rowstore, буфера удаления отслеживает удаления из индекса columnstore. Если число удаленных строк превышает 1048576, они объединяются обратно в точечный рисунок delete фонового потока кортежей или явной команды Reorganize.  В любой момент времени объединение delete точечный рисунок и буфера удаления представляет все удаленные строки.<br /><br /> COLUMN_STORE_MAPPING_INDEX - использовать только в том случае, если кластеризованный индекс columnstore имеет дополнительный некластеризованный индекс. Некластеризованный индекс ключи сопоставляется правильные группы строк и идентификатор строки в columnstore. Она только хранит ключи для строк, которые перемещают в разные группы строк; Это происходит, когда разностная группа строк сжимается в columnstore, а операция слияния объединяет строки из двух разных групп строк.|  
|Row_group_id|**int**|Идентификатор группы строк deltastore. Каждой секции таблицы может содержать ноль или более групп строк deltastore.|  
|hobt_id|**bigint**|Идентификатор объекта, внутреннего набора строк. Это подходящий ключ для объединения с помощью других динамических административных представлений, чтобы получить дополнительные сведения о физических характеристик внутреннего набора строк.|  
|rows|**bigint**|Приблизительное количество строк в данной секции.|  
|data_compression|**tinyint**|Состояние сжатия для набора строк:<br /><br /> 0 = нет<br /><br /> 1 = ROW<br /><br /> 2 = PAGE|  
|data_compression_desc|**nvarchar(60)**|Состояние сжатия для каждой секции. Возможные значения для таблиц rowstore: NONE, ROW и PAGE. Возможные значения для таблиц columnstore: COLUMNSTORE и COLUMNSTORE_ARCHIVE.|  
|optimize_for_sequential_key|**bit**|1 = секция имеет включена оптимизация вставки последней страницы.<br><br>0 = значение по умолчанию. Секция имеет отключена оптимизация вставки последней страницы.|
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="general-remarks"></a>Общие замечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторно создает новый внутренний индексы columnstore каждый раз, он создает или перестраивает индекс columnstore.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-view-all-of-the-internal-rowsets-for-a-table"></a>A. Просмотреть все из внутренних наборов строк для таблицы  
 Этот пример возвращает все наборы строк внутренней columnstore для таблицы. Hobt_id также можно найти дополнительные сведения о конкретных строк.  
  
```  
SELECT i.object_id, i.index_id, i.name, p.hobt_id, p.internal_object_type_id, p.internal_object_type_desc  
FROM sys.internal_partitions AS p  
JOIN sys.indexes AS i  
on i.object_id = p.object_id  
WHERE p.object_id = OBJECT_ID ( '<table name' ) ;  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
