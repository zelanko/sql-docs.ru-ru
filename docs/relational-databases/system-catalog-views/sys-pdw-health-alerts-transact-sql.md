---
title: sys.pdw_health_alerts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c47bcc342bf8a052aed93649ca0ad8475d937608
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127543"
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Сохраняет свойства для оповещений, которые могут возникнуть в системе; Это таблица каталога для оповещений.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Уникальный идентификатор оповещения.<br /><br /> Ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента, к которым применяется это предупреждение. Компонент — это идентификатор общего компонента, например «Источника питания» и не относится к установке. См. в разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Имя предупреждения.|NOT NULL|  
|state|**nvarchar(32)**|Состояние оповещения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> 'Operational'<br /><br /> «Связанными»<br /><br /> «Деградация»<br /><br /> «Сбой»|  
|severity|**nvarchar(32)**|Серьезность предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> «Информация»<br /><br /> «Предупреждение»<br /><br /> «Ошибка»|  
|type|**nvarchar(32)**|Тип предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> StatusChange - состояние устройства изменилось.<br /><br /> Пороговое значение: значение превышает пороговое значение.|  
|description|**nvarchar(4000)**|Описание оповещения.|NOT NULL|  
|условие|**nvarchar(255)**|Используется, если ввести = пороговое значение. Определяет, как вычисляется порога предупреждения.|NULL|  
|status|**nvarchar(32)**|Состояние оповещения|NULL|  
|condition_value|**bit**|Указывает, может ли оповещение при работе системы.|NULL<br /><br /> Возможные значения<br /><br /> 0 — предупреждение не создается.<br /><br /> 1 — предупреждение.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
