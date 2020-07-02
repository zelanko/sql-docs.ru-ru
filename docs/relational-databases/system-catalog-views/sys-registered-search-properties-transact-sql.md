---
title: sys. registered_search_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.registered_search_properties
- registered_search_properties
- sys.registered_search_properties_TSQL
- registered_search_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search properties [SQL Server]
- property searching [SQL Server], viewing registered properties
- search property lists [SQL Server], viewing registered properties
- sys.registered_search_properties catalog view
ms.assetid: 1b9a7a5c-8c05-4819-83c3-7487dd08fcf7
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 09b95722f47442b2d5d749d8ba36888fb9605f58
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717618"
---
# <a name="sysregistered_search_properties-transact-sql"></a>sys.registered_search_properties (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Содержит строку для каждого свойства поиска, которое содержится в списке свойств поиска в текущей базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**property_list_id**|**int**|Идентификатор списка свойств поиска, к которому принадлежит свойство.|  
|**property_set_guid**|**uniqueidentifier**|Глобальный уникальный идентификатор (GUID), определяющий набор свойств, к которому принадлежит свойство поиска.|  
|**property_int_id**|**int**|Целое число, определяющее свойство поиска в наборе свойств. **property_int_id** уникален в пределах набора свойств.|  
|**property_name**|**nvarchar (64)**|Имя, однозначно определяющие свойство поиска в списке свойств поиска.<br /><br /> Примечание. для поиска по свойству укажите имя этого свойства в предикате [Contains](../../t-sql/queries/contains-transact-sql.md) .|  
|**property_description**|**nvarchar(512)**|Описание свойства.|  
|**property_id**|**int**|Внутренний идентификатор свойства свойства поиска в списке свойств поиска, определяемом значением **property_list_id** .<br /><br /> После добавления свойства к данному списку свойств поиска механизм полнотекстового поиска регистрирует это свойство и назначает ему внутренний идентификатор свойства, относящийся к указанному списку свойств. Внутренний идентификатор свойства, являющийся целым числом, не повторяется в заданном списке свойств поиска. Если данное свойство зарегистрировано в нескольких списках свойств поиска, каждому списку свойств поиска может быть назначен отдельный внутренний идентификатор свойств.<br /><br /> Примечание. идентификатор внутреннего свойства отличается от целочисленного идентификатора свойства, указанного при добавлении свойства в список свойств поиска. Дополнительные сведения см. в статье [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).<br /><br /> Чтобы просмотреть все содержимое, связанное со свойством, в полнотекстовом индексе: <br />                  [sys.dm_fts_index_keywords_by_property (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о списках свойств поиска см. в статье [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="permissions"></a>Разрешения  
 Видимость метаданных свойств поиска ограничивается свойствами, включенными в списки свойств поиска, которыми пользователь владеет или на которые ему было предоставлено разрешение REFERENCE.  
  
> [!NOTE]  
>  Владелец списка свойств поиска может предоставить разрешения REFERENCE и CONTROL на список. Пользователи с разрешением CONTROL также могут предоставлять разрешение REFERENCE другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере перечислены все метаданные зарегистрированных свойств поиска.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.registered_search_properties;   
GO  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER FULLTEXT INDEX &#40;&#41;Transact-SQL](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [sys. fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [Поиск свойств документа с помощью списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
