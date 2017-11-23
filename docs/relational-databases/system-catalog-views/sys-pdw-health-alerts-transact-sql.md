---
title: "sys.pdw_health_alerts (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f7e05ccc9cc264faf5d4d7f563d1df028969309
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Хранилище свойств для различных предупреждений, которые могут возникнуть на компьютере. Это таблица каталога для оповещений.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Уникальный идентификатор предупреждения.<br /><br /> Ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента, с которым применяется это предупреждение. Компонент — это идентификатор общего компонента, такие как «Источник питания» и не относится к установке. В разделе [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Имя предупреждения.|NOT NULL|  
|state|**nvarchar(32)**|Состояние предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> 'Operational'<br /><br /> «Неработающая»<br /><br /> «Деградация»<br /><br /> «Сбой»|  
|severity|**nvarchar(32)**|Серьезность предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> «Информационное»<br /><br /> «Предупреждение»<br /><br /> «Ошибка»|  
|Тип|**nvarchar(32)**|Тип предупреждения.|NOT NULL<br /><br /> Возможные значения:<br /><br /> StatusChange - изменение состояния устройства.<br /><br /> Пороговое значение — значение было превышено пороговое значение.|  
|description|**nvarchar(4000)**|Описание предупреждения.|NOT NULL|  
|условия|**nvarchar(255)**|Если тип = пороговое значение. Определяет, как вычисляется порога предупреждения.|NULL|  
|status|**nvarchar(32)**|Состояние оповещения|NULL|  
|condition_value|**bit**|Указывает, разрешено ли предупреждения во время работы системы.|NULL<br /><br /> Возможные значения<br /><br /> 0 — предупреждение не создается.<br /><br /> 1 — предупреждение.|  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
