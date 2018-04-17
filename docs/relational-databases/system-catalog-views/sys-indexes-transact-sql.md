---
title: sys.indexes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 04/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.indexes
- indexes
- sys.indexes_TSQL
- indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes catalog view
ms.assetid: 066bd9ac-6554-4297-88fe-d740de1f94a8
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f251924f2e13c8834ff01f1f5ecc66b884c22675
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysindexes-transact-sql"></a>sys.indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит строку для каждого индекса или кучи табличного объекта, такого как таблица, представление или функция с табличным значением.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит данный индекс.|  
|**name**|**sysname**|Имя индекса. **имя** уникально только в пределах объекта.<br /><br /> NULL = куча.|  
|**index_id**|**int**|Идентификатор индекса. **index_id** уникально только в пределах объекта.<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = некластеризованный индекс|  
|**type**|**tinyint**|Тип индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный<br /><br /> 2 = некластеризованный.<br /><br /> 3 = XML.<br /><br /> 4 = пространственный.<br /><br /> 5 = кластеризованный индекс columnstore. **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 6 = некластеризованный индекс columnstore. **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 7 = некластеризованный хэш-индекс. **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**type_desc**|**nvarchar(60)**|Описание типа индекса.<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> XML<br /><br /> SPATIAL<br /><br /> КЛАСТЕРИЗОВАННЫЙ индекс COLUMNSTORE - **применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> НЕКЛАСТЕРИЗОВАННЫЙ COLUMNSTORE - **применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> НЕКЛАСТЕРИЗОВАННЫЙ ХЭШ: НЕКЛАСТЕРИЗОВАННЫЕ хэш-индексы поддерживаются только в таблицах, оптимизированных для памяти. Представление sys.hash_indexes отображает текущие хэш-индексы и свойства хэша. Дополнительные сведения см. в разделе [sys.hash_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md). **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_unique**|**бит**|1 = индекс уникален.<br /><br /> 0 = индекс не уникален.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**data_space_id**|**int**|Идентификатор пространства данных этого индекса. Пространством данных может быть или файловая группа, или схема секционирования.<br /><br /> 0 = **object_id** табличной функции или индекса в памяти.|  
|**IGNORE_DUP_KEY**|**бит**|1 = параметр IGNORE_DUP_KEY имеет значение ON.<br /><br /> 0 = параметр IGNORE_DUP_KEY имеет значение OFF.|  
|**is_primary_key**|**бит**|1 = индекс является частью ограничения PRIMARY KEY.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**is_unique_constraint**|**бит**|1 = индекс является частью ограничения UNIQUE.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**fill_factor**|**tinyint**|> 0 = процентный показатель FILLFACTOR, использованный при создании или повторном создании индекса.<br /><br /> 0 = значение по умолчанию.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**is_padded**|**бит**|1 = параметр PADINDEX имеет значение ON.<br /><br /> 0 = параметр PADINDEX имеет значение OFF.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**is_disabled**|**бит**|1 = индекс отключен.<br /><br /> 0 = индекс не отключен.|  
|**is_hypothetical**|**бит**|1 = индекс является гипотетическим и не может быть использован непосредственно как путь доступа к данным. Гипотетические индексы содержат статистику уровня столбцов.<br /><br /> 0 = индекс не является гипотетическим.|  
|**ALLOW_ROW_LOCKS**|**бит**|1 = индекс допускает блокировки строк.<br /><br /> 0 = индекс не допускает блокировки строк.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**allow_page_locks**|**бит**|1 = индекс допускает блокировки страниц.<br /><br /> 0 = индекс не допускает блокировки страниц.<br /><br /> Всегда равен 0 для кластеризованных индексов columnstore.|  
|**has_filter**|**бит**|1 = индекс с фильтром; содержит строки, удовлетворяющие определению фильтра.<br /><br /> 0 = индекс без фильтра.|  
|**filter_definition**|**nvarchar(max)**|Выражение для подмножества строк, включенного в фильтруемый индекс.<br /><br /> Имеет значение NULL для кучи или нефильтруемого индекса.|  
|**auto_created**|**бит**|1 = индекс был создан путем автоматической настройки.<br /><br />0 = индекс был создан пользователем.
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все индексы для таблицы `Production.Product` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT i.name AS index_name  
    ,i.type_desc  
    ,is_unique  
    ,ds.type_desc AS filegroup_or_partition_scheme  
    ,ds.name AS filegroup_or_partition_scheme_name  
    ,ignore_dup_key  
    ,is_primary_key  
    ,is_unique_constraint  
    ,fill_factor  
    ,is_padded  
    ,is_disabled  
    ,allow_row_locks  
    ,allow_page_locks  
FROM sys.indexes AS i  
INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
WHERE is_hypothetical = 0 AND i.index_id <> 0   
AND i.object_id = OBJECT_ID('Production.Product');  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.filegroups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.partition_schemes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
