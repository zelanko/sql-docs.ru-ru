---
title: MSdbms_map (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 55f6fa2677ea62579fe62aef604f2cd76a321f81
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="msdbmsmap-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_map** таблица содержит сведения о типе данных источника, а также ссылки на сведения тип данных назначения по умолчанию для пар СУБД источника и назначения. Эта таблица хранится в **msdb** базы данных и используется для разнородных публикаций.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|Уникальным образом идентифицирует сопоставление типа данных.|  
|**src_dbms_id**|**int**|Идентифицирует СУБД-источнике, указав его **dbms_id** в [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) таблицы.|  
|**dest_dbms_id**|**int**|Идентифицирует СУБД назначения, указав его **dbms_id** в [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) таблицы.|  
|**src_datatype_id**|**int**|Идентифицирует **datatype_id** из [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md) таблицы для исходного типа данных.|  
|**src_len_min**|**bigint**|Минимальная длина типа данных в СУБД-источнике; причем значение NULL указывает, что длина не используется.|  
|**src_len_max**|**bigint**|Максимальная длина типа данных в СУБД-источнике; причем значение NULL указывает, что длина не используется.|  
|**src_prec_min**|**bigint**|Минимальная точность типа данных в СУБД-источнике; причем значение NULL указывает, что точность не используется.|  
|**src_prec_max**|**bigint**|Максимальная точность типа данных в СУБД-источнике; причем значение NULL указывает, что точность не используется.|  
|**src_scale_min**|**int**|Минимальный масштаб типа данных в СУБД-источнике; причем значение NULL указывает, что масштаб не используется.|  
|**src_scale_max**|**int**|Максимальный масштаб типа данных в СУБД-источнике; причем значение NULL указывает, что масштаб не используется.|  
|**src_nullable**|**бит**|Показывает, допускает ли целевой столбец в данном сопоставлении значения NULL; причем NULL означает, что это определение не требуется.|  
|**default_datatype_mapping_id**|**int**|Идентифицирует сопоставление типа данных по умолчанию, указав его **map_id** в таблице [MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md).|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
