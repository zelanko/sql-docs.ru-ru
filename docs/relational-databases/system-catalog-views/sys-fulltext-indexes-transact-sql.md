---
title: sys. fulltext_indexes (Transact-SQL) | Документация Майкрософт
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca20bc73e071fea4a1a0f01acf2c0701b15aca25
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764697"
---
# <a name="sysfulltext_indexes-transact-sql"></a>sys.fulltext_indexes (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Содержит по одной строке для каждого полнотекстового индекса табличного объекта.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит данный полнотекстовый индекс.|  
|**unique_index_id**|**int**|Идентификатор соответствующего уникального индекса (не полнотекстового), который используется для связи полнотекстового индекса и строк.|  
|**fulltext_catalog_id**|**int**|Идентификатор полнотекстового каталога, в котором находится полнотекстовый индекс.|  
|**is_enabled**|**bit**|1 = полнотекстовый индекс включен.|  
|**change_tracking_state**|**char (1)**|Состояние отслеживания изменений.<br /><br /> M = вручную<br /><br /> A = автоматически<br /><br /> O = отключено|  
|**change_tracking_state_desc**|**nvarchar(60)**|Описание состояния отслеживания изменений.<br /><br /> MANUAL<br /><br /> AUTO<br /><br /> OFF|  
|**has_crawl_completed**|**bit**|Последнее сканирование (заполнение) полнотекстового индекса завершено.|  
|**crawl_type**|**char (1)**|Тип текущего или последнего сканирования.<br /><br /> F = полное сканирование<br /><br /> I = постепенное сканирование на основе отметки времени<br /><br /> U = сканирование обновления на основе уведомлений<br /><br /> P = полное сканирование приостановлено.|  
|**crawl_type_desc**|**nvarchar(60)**|Описание типа текущего или последнего сканирования.<br /><br /> FULL_CRAWL<br /><br /> INCREMENTAL_CRAWL<br /><br /> UPDATE_CRAWL<br /><br /> PAUSED_FULL_CRAWL|  
|**crawl_start_date**|**datetime**|Начало текущего или последнего сканирования.<br /><br /> NULL = Нет.|  
|**crawl_end_date**|**datetime**|Окончание текущего или последнего сканирования.<br /><br /> NULL = Нет.|  
|**incremental_timestamp**|**Binary (8)**|Значение отметки времени для использования при следующем постепенном сканировании.<br /><br /> NULL = Нет.|  
|**stoplist_id**|**int**|Идентификатор [списка стоп-слов](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md) , связанного с данным полнотекстовым индексом.|  
|**data_space_id**|**int**|Файловая группа, в которой расположен полнотекстовый индекс.|  
|**property_list_id**|**int**|Идентификатор списка свойств поиска, связанного с данным полнотекстовым индексом. Значение NULL указывает на отсутствие списка свойств поиска, связанного с данным полнотекстовым индексом. Чтобы получить дополнительные сведения об этом списке свойств поиска, используйте представление каталога [&#41;инструкции sys. registered_search_property_lists &#40;Transact-SQL](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) .|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется полнотекстовый индекс для таблицы `HumanResources.JobCandidate` образца базы данных `AdventureWorks2012`. В примере возвращается идентификатор объекта таблицы, идентификатор списка свойств поиска и идентификатор списка стоп-слов, используемого полнотекстовым индексом.  
  
> [!NOTE]  
>  Пример кода, который создает этот полнотекстовый индекс, см. в подразделе "примеры" статьи [CREATE FULLTEXT index &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT object_id, property_list_id, stoplist_id FROM sys.fulltext_indexes  
    where object_id = object_id('HumanResources.JobCandidate');   
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys. fulltext_index_fragments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)   
 [sys. fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [sys. fulltext_index_catalog_usages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)   
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Создание и управление полнотекстовыми индексами](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [DROP ПОЛНОТЕКСТОВЫЙ индекс &#40;&#41;Transact-SQL](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
  
