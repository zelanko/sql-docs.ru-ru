---
title: MSdbms_map (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad9106bb9cde64953643e86bf81e72684858bd65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817120"
---
# <a name="msdbmsmap-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_map** таблица содержит сведения о типе данных источника, а также ссылки на сведения типа данных назначения по умолчанию для пар СУБД источника и назначения. Эта таблица хранится в **msdb** базы данных и используется для разнородных публикаций.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|Уникальным образом идентифицирует сопоставление типа данных.|  
|**src_dbms_id**|**int**|Идентифицирует СУБД-источнике, указывая его **dbms_id** в [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) таблицы.|  
|**dest_dbms_id**|**int**|Идентифицирует СУБД назначения, указав его **dbms_id** в [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) таблицы.|  
|**src_datatype_id**|**int**|Идентифицирует **datatype_id** из [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md) таблицы для исходного типа данных.|  
|**src_len_min**|**bigint**|Минимальная длина типа данных в СУБД-источнике; причем значение NULL указывает, что длина не используется.|  
|**src_len_max**|**bigint**|Максимальная длина типа данных в СУБД-источнике; причем значение NULL указывает, что длина не используется.|  
|**src_prec_min**|**bigint**|Минимальная точность типа данных в СУБД-источнике; причем значение NULL указывает, что точность не используется.|  
|**src_prec_max**|**bigint**|Максимальная точность типа данных в СУБД-источнике; причем значение NULL указывает, что точность не используется.|  
|**src_scale_min**|**int**|Минимальный масштаб типа данных в СУБД-источнике; причем значение NULL указывает, что масштаб не используется.|  
|**src_scale_max**|**int**|Максимальный масштаб типа данных в СУБД-источнике; причем значение NULL указывает, что масштаб не используется.|  
|**src_nullable**|**bit**|Показывает, допускает ли целевой столбец в данном сопоставлении значения NULL; причем NULL означает, что это определение не требуется.|  
|**default_datatype_mapping_id**|**int**|Идентифицирует сопоставление типа данных по умолчанию, указав его **map_id** в таблице [MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md).|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
