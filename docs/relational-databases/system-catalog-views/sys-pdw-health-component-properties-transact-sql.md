---
title: sys.pdw_health_component_properties (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 628432368c30d81f8a89b97baf1534ce9502403b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит свойства, описывающие устройства. Некоторые свойства отображения состояния устройства и некоторые свойства описания само устройство.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства компонента.<br /><br /> идентификатором и идентификатор_компонента формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. В разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> идентификатором и идентификатор_компонента формируют ключ для этого представления.|NOT NULL|  
|property_name|**nvarchar(255)**|Имя свойства.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства в соответствии с определением производителя.|NOT NULL|  
|is_key|**бит**|Определяет, является ли экземпляр устройства уникальным или неуникальным.|NOT NULL<br /><br /> 0 — экземпляр устройства уникален.<br /><br /> 1 — устройства экземпляр не является уникальным.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
