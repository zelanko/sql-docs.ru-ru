---
description: sys.dm_pdw_component_health_status (Transact-SQL)
title: sys.dm_pdw_component_health_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 6c525237b8e2cf92eef038f3cdfe668c8b87af49
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482615"
---
# <a name="sysdm_pdw_component_health_status-transact-sql"></a>sys.dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Содержит сведения о текущей работоспособности компонентов устройства.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Не NULL|  
|component_id|INT|Идентификатор компонента. См. раздел [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, property_id и component_instance_id образуют ключ для этого представления.|Не NULL|  
|property_id|**int**|Идентификатор свойства. См. раздел [sys.pdw_health_component_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Определяет экземпляр компонента. Например, экземпляр ЦП может быть идентифицирован с помощью component_instance_id = ' CPU1 '.<br /><br /> pdw_node_id, component_id, property_id и component_instance_id образуют ключ для этого представления.|NOT NULL|  
|property_value|**nvarchar(255)**|Текущее значение свойства.|NULL|  
|update_time|**datetime**|Время последнего обновления метрики.|NOT NULL|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
