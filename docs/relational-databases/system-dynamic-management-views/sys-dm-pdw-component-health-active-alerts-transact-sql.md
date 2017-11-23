---
title: "sys.dm_pdw_component_health_active_alerts (Transact-SQL) | Документы Microsoft"
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
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c88fd88a8545e5fa375732377f0afdbf92b70f96
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Сохраняет активные предупреждения о [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] компонентов.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] узла.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. В разделе [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_id|**int**|Идентификатор для типа оповещений. В разделе [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Идентифицирует экземпляр данного предупреждения.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|current_value|**nvarchar(255)**|Используется, когда оповещение относится к типу StatusChange. Это текущее состояние компонента. Значение равно NULL для оповещений типа пороговое значение. В разделе [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|previous_value|**nvarchar(255)**|Используется, когда оповещение относится к типу StatusChange. Это состояние предыдущего компонента. Значение равно NULL для оповещений типа пороговое значение. В разделе [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|create_time|**datetime**|Время и Дата, когда было выдано оповещение.|NOT NULL|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
