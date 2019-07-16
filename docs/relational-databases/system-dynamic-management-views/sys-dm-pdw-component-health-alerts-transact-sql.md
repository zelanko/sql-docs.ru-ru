---
title: sys.dm_pdw_component_health_alerts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 770ddc4d1e182360b13d4f9e27d9e0bbf80cceee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899574"
---
# <a name="sysdmpdwcomponenthealthalerts-transact-sql"></a>sys.dm_pdw_component_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Хранит предыдущие оповещения для компонентов устройства.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] узла.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. См. в разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_id|**int**|Идентификатор для типа оповещений. См. в разделе [sys.pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Определяет экземпляр данного предупреждения.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|previous_value|**nvarchar(255)**|Используется, когда предупреждение имеет тип StatusChange. Это состояние предыдущего компонента. Значение равно NULL для оповещения типа пороговое значение. См. в разделе [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|current_value|**nvarchar(255)**|Используется, когда предупреждение имеет тип StatusChange. Это текущее состояние компонента. Значение равно NULL для оповещения типа пороговое значение. См. в разделе [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|create_time|**datetime**|Время и Дата, когда было выдано оповещение.|NOT NULL|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
