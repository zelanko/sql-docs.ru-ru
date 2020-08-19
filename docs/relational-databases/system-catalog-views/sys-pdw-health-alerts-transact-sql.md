---
description: sys. pdw_health_alerts (Transact-SQL)
title: sys. pdw_health_alerts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3b2da23d973042638f39e52ed7c1173422a97eeb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475414"
---
# <a name="syspdw_health_alerts-transact-sql"></a>sys. pdw_health_alerts (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Хранит свойства для различных предупреждений, которые могут возникать в системе; Это таблица каталога для оповещений.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Уникальный идентификатор предупреждения.<br /><br /> Ключ для этого представления.|NOT NULL|  
|component_id|**int**|Идентификатор компонента, к которому применяется это оповещение. Компонент является общим идентификатором компонента, например "источник питания", и не зависит от установки. См. раздел [sys. pdw_health_components &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Имя оповещения.|NOT NULL|  
|Состояние|**nvarchar(32)**|Состояние оповещения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> Рабочего<br /><br /> "Неработающий"<br /><br /> Пониженной функциональности<br /><br /> Ошибок|  
|severity|**nvarchar(32)**|Серьезность оповещения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> Извещен<br /><br /> !<br /><br /> План|  
|тип|**nvarchar(32)**|Тип оповещения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> StatusChange — состояние устройства изменилось.<br /><br /> Threshold — значение превысило пороговое значение.|  
|description|**nvarchar(4000)**|Описание оповещения.|NOT NULL|  
|condition|**nvarchar(255)**|Используется, если Type = threshold. Определяет, как вычисляется пороговое значение оповещения.|NULL|  
|status|**nvarchar(32)**|Состояние оповещения|NULL|  
|condition_value|**bit**|Указывает, может ли предупреждение происходить во время работы системы.|NULL<br /><br /> Возможные значения<br /><br /> 0 — предупреждение не создается.<br /><br /> 1 — создано оповещение.|  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
