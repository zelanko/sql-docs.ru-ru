---
title: "sys.dm_pdw_component_health_alerts (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 51360614a6939c64b005a93cd178b2e6ff22e4e2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwcomponenthealthalerts-transact-sql"></a>sys.dm_pdw_component_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Хранит предыдущие предупреждения на компонентах устройства.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] узла.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|component_id|**int**|Идентификатор компонента. В разделе [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_id|**int**|Идентификатор для типа оповещений. В разделе [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Идентифицирует экземпляр данного предупреждения.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|previous_value|**nvarchar(255)**|Используется, когда оповещение относится к типу StatusChange. Это состояние предыдущего компонента. Значение равно NULL для оповещений типа пороговое значение. В разделе [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|current_value|**nvarchar(255)**|Используется, когда оповещение относится к типу StatusChange. Это текущее состояние компонента. Значение равно NULL для оповещений типа пороговое значение. В разделе [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|create_time|**datetime**|Время и Дата, когда было выдано оповещение.|NOT NULL|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
