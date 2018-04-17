---
title: sys.fulltext_index_fragments (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fulltext_index_fragments
- sys.fulltext_index_fragments_TSQL
- fulltext_index_fragments_TSQL
- sys.fulltext_index_fragments
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], fragments
- full-text indexes [SQL Server], metadata
- troubleshooting [SQL Server], full-text search
- sys.fulltext_index_fragments catalog view
ms.assetid: a82e5018-5d88-45c0-9a47-c251e17a6cdb
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 76f1e3328666b9ce34e219deb85f5a4259d78235
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysfulltextindexfragments-transact-sql"></a>sys.fulltext_index_fragments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Полнотекстовый индекс использует внутренние таблицы, называемые *фрагментов полнотекстового индекса* для хранения данных инвертированного индекса. Это представление может использоваться для запросов к метаданным об этих фрагментах. Представление содержит строку для каждого фрагмента полнотекстового индекса в каждой таблице, содержащей полнотекстовый индекс.  
 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|table_id|**int**|Идентификатор объекта таблицы, содержащей фрагмент полнотекстового индекса.|  
|fragment_object_id|**int**|Идентификатор объекта внутренней таблицы, связанной с данным фрагментом.|  
|fragment_id|**int**|Логический идентификатор фрагмента полнотекстового индекса. Этот идентификатор уникален среди всех фрагментов данной таблицы.|  
|TIMESTAMP|**timestamp**|Отметка времени создания фрагмента. Отметки времени создания более новых фрагментов больше, чем отметки времени более старых фрагментов.|  
|data_size|**int**|Логический размер фрагмента в байтах.|  
|row_count|**int**|Количество индивидуальных строк фрагмента.|  
|status|**int**|Состояние фрагмента одно из следующих:<br /><br /> 0 — только что создан и еще не использован;<br /><br /> 1 — используется для вставки во время заполнения или слияния полнотекстового индекса;<br /><br /> 4 — закрыт. Готов к запросу;<br /><br /> 6 — используется для входа слияния и готов к запросу;<br /><br /> 8 — помечен для удаления. Не будет использоваться для запросов и как вход слияния.<br /><br /> Состояние 4 или 6 означает, что фрагмент является частью логического полнотекстового индекса и могут запрашиваться; он является *запрашиваемым* фрагмента.|  
  
## <a name="remarks"></a>Замечания  
 Представление каталога sys.fulltext_index_fragments можно использовать для запроса о числе фрагментов, составляющих полнотекстовый индекс. Если полнотекстовый запрос работает медленно, можно использовать представление sys.fulltext_index_fragments, чтобы получить число запрашиваемых фрагментов (с состоянием, равным 4 или 6) полнотекстового индекса следующим образом:  
  
```  
SELECT table_id, status FROM sys.fulltext_index_fragments  
   WHERE status=4 OR status=6;  
```  
  
 Если существует много запрашиваемых фрагментов, рекомендуется реорганизовать полнотекстовый каталог, содержащий полнотекстовый индекс, чтобы объединить фрагменты. Для реорганизации использования полнотекстового каталога [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)*имя_каталога* REORGANIZE. Например, чтобы реорганизовать полнотекстовый каталог `ftCatalog` в базе данных `AdventureWorks2012`, введите:  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog REORGANIZE;  
GO  
```  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
