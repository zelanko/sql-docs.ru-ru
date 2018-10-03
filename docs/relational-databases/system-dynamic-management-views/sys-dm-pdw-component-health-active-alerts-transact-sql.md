---
title: sys.dm_pdw_component_health_active_alerts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bb050494a71d897f49bf00a9aca37af7dbcf97c4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617962"
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Сохраняет активные предупреждения на [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] компонентов.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] узла.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. См. в разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_id|**int**|Идентификатор для типа оповещений. См. в разделе [sys.pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Определяет экземпляр данного предупреждения.<br /><br /> pdw_node_id, идентификатор_компонента, component_instance_id, alert_id и alert_instance_id формируют ключ для этого представления.|NOT NULL|  
|current_value|**nvarchar(255)**|Используется, когда предупреждение имеет тип StatusChange. Это текущее состояние компонента. Значение равно NULL для оповещения типа пороговое значение. См. в разделе [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|previous_value|**nvarchar(255)**|Используется, когда предупреждение имеет тип StatusChange. Это состояние предыдущего компонента. Значение равно NULL для оповещения типа пороговое значение. См. в разделе [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) список типов оповещений.|NULL|  
|create_time|**datetime**|Время и Дата, когда было выдано оповещение.|NOT NULL|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
