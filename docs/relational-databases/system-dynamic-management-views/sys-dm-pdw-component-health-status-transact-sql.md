---
title: "sys.dm_pdw_component_health_status (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
caps.latest.revision: "6"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d87c8ef38185e3194da1d13f8a9732991023f0ab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о состоянии компонентов устройства.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Не NULL|  
|идентификатор_компонента|int|Идентификатор компонента. В разделе [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, идентификатором и component_instance_id формируют ключ для этого представления.|Не NULL|  
|property_id|**int**|Идентификатор свойства. В разделе [sys.pdw_health_component_properties &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Идентифицирует экземпляр компонента. Например, ЦП экземпляра может быть идентифицирована component_instance_id = «CPU1».<br /><br /> pdw_node_id, идентификатор_компонента, идентификатором и component_instance_id формируют ключ для этого представления.|NOT NULL|  
|property_value|**nvarchar(255)**|Текущее значение свойства.|NULL|  
|update_time|**datetime**|Последнее время обновления метрику.|NOT NULL|  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
