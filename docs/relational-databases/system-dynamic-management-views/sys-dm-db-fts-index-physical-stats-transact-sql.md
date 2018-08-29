---
title: sys.dm_db_fts_index_physical_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5728813e5a591c45238372e9278e6f1d4c415a79
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43059822"
---
# <a name="sysdmdbftsindexphysicalstats-transact-sql"></a>sys.dm_db_fts_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого индекса полнотекстового или семантического поиска в каждой таблице, имеющей связанный полнотекстовый или семантический индекс.  
  
||||  
|-|-|-|  
|**Имя столбца**|**Тип**|**Описание**|  
|**object_id**|ssNoversion|Идентификатор объекта таблицы, содержащего индекс.|  
|**fulltext_index_page_count**|**bigint**|Логический размер извлечения, определяемый количеством страниц индекса.|  
|**keyphrase_index_page_count**|**bigint**|Логический размер извлечения, определяемый количеством страниц индекса.|  
|**similarity_index_page_count**|**bigint**|Логический размер извлечения, определяемый количеством страниц индекса.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [управление и мониторинг семантического поиска](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Для получения сведений о состоянии семантического индексирования выполните запрос к следующим динамическим административным представлениям:  
  
-   [sys.dm_fts_index_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="examples"></a>Примеры  
 В этом примере показано, как выполнить запрос, сообщающий логические размеры каждого из полнотекстовых и семантических индексов в каждой из таблиц, у которых имеются связанные индексы полнотекстового поиска или семантические индексы:  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
