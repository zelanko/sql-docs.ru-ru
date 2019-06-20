---
title: sys.fulltext_indexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_indexes
- fulltext_indexes_TSQL
- sys.fulltext_indexes_TSQL
- sys.fulltext_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_indexes catalog view
- full-text indexes [SQL Server], properties
ms.assetid: 7fc10fdc-370f-4927-bba0-b76108a7508e
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b9d6f7aafe405b29db5457f470a99efac2e23e92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "64945679"
---
# <a name="sysfulltextindexes-transact-sql"></a>sys.fulltext_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого полнотекстового индекса табличного объекта.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит данный полнотекстовый индекс.|  
|**unique_index_id**|**int**|Идентификатор соответствующего уникального индекса (не полнотекстового), который используется для связи полнотекстового индекса и строк.|  
|**fulltext_catalog_id**|**int**|Идентификатор полнотекстового каталога, в котором находится полнотекстовый индекс.|  
|**is_enabled**|**bit**|1 = полнотекстовый индекс включен.|  
|**change_tracking_state**|**char(1)**|Состояние отслеживания изменений.<br /><br /> M = вручную<br /><br /> A = автоматически<br /><br /> O = отключено|  
|**change_tracking_state_desc**|**nvarchar(60)**|Описание состояния отслеживания изменений.<br /><br /> MANUAL<br /><br /> AUTO<br /><br /> OFF|  
|**has_crawl_completed**|**bit**|Последнее сканирование (заполнение) полнотекстового индекса завершено.|  
|**crawl_type**|**char(1)**|Тип текущего или последнего сканирования.<br /><br /> F = полное сканирование<br /><br /> I = постепенное сканирование на основе отметки времени<br /><br /> U = сканирование обновления на основе уведомлений<br /><br /> P = полное сканирование приостановлено.|  
|**crawl_type_desc**|**nvarchar(60)**|Описание типа текущего или последнего сканирования.<br /><br /> FULL_CRAWL<br /><br /> INCREMENTAL_CRAWL<br /><br /> UPDATE_CRAWL<br /><br /> PAUSED_FULL_CRAWL|  
|**crawl_start_date**|**datetime**|Начало текущего или последнего сканирования.<br /><br /> NULL = Нет.|  
|**crawl_end_date**|**datetime**|Окончание текущего или последнего сканирования.<br /><br /> NULL = Нет.|  
|**incremental_timestamp**|**binary(8)**|Значение отметки времени для использования при следующем постепенном сканировании.<br /><br /> NULL = Нет.|  
|**stoplist_id**|**int**|Идентификатор [списка стоп-слов](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md) , связанного с данным индексом для полнотекстового поиска.|  
|**data_space_id**|**int**|Файловая группа, в которой расположен полнотекстовый индекс.|  
|**property_list_id**|**int**|Идентификатор списка свойств поиска, связанного с данным полнотекстовым индексом. Значение NULL указывает на отсутствие списка свойств поиска, связанного с данным полнотекстовым индексом. Чтобы получить дополнительные сведения об этом списке свойств поиска, используйте [sys.registered_search_property_lists &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) представления каталога.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется полнотекстовый индекс для таблицы `HumanResources.JobCandidate` образца базы данных `AdventureWorks2012`. В примере возвращается идентификатор объекта таблицы, идентификатор списка свойств поиска и идентификатор списка стоп-слов, используемого полнотекстовым индексом.  
  
> [!NOTE]  
>  В примере кода, создающего данный полнотекстовый индекс, см. в разделе «Примеры» из [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT object_id, property_list_id, stoplist_id FROM sys.fulltext_indexes  
    where object_id = object_id('HumanResources.JobCandidate');   
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys.fulltext_index_fragments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)   
 [sys.fulltext_index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Создание и управление полнотекстовыми индексами](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [DROP FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
  
