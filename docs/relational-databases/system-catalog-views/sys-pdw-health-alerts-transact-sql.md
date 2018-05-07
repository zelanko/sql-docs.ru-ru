---
title: sys.pdw_health_alerts (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6f8281d520f64580af8432dbf2004227ce628d41
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Хранилище свойств для различных предупреждений, которые могут возникнуть на компьютере. Это таблица каталога для оповещений.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Уникальный идентификатор предупреждения.<br /><br /> Ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента, с которым применяется это предупреждение. Компонент — это идентификатор общего компонента, такие как «Источник питания» и не относится к установке. В разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Имя предупреждения.|NOT NULL|  
|state|**nvarchar(32)**|Состояние предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> 'Operational'<br /><br /> «Неработающая»<br /><br /> «Деградация»<br /><br /> «Сбой»|  
|severity|**nvarchar(32)**|Серьезность предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> «Информационное»<br /><br /> «Предупреждение»<br /><br /> «Ошибка»|  
|Тип|**nvarchar(32)**|Тип предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> StatusChange - изменение состояния устройства.<br /><br /> Пороговое значение — значение было превышено пороговое значение.|  
|description|**nvarchar(4000)**|Описание предупреждения.|NOT NULL|  
|условия|**nvarchar(255)**|Если тип = пороговое значение. Определяет, как вычисляется порога предупреждения.|NULL|  
|status|**nvarchar(32)**|Состояние оповещения|NULL|  
|condition_value|**бит**|Указывает, разрешено ли предупреждения во время работы системы.|NULL<br /><br /> Возможные значения<br /><br /> 0 — предупреждение не создается.<br /><br /> 1 — предупреждение.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
