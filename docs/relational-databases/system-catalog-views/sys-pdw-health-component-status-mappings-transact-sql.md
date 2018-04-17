---
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 00837177a25110063966208442d03392365b7db6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Определяет сопоставление между [!INCLUDE[ssDW](../../includes/ssdw-md.md)] состояния компонента и имена производителя определенных компонентов.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства.<br /><br /> идентификатором, идентификатор_компонента и physical_name формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. В разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> идентификатором, идентификатор_компонента и physical_name формируют ключ для этого представления.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства в соответствии с определением производителя.<br /><br /> идентификатором, идентификатор_компонента и physical_name формируют ключ для этого представления.|NOT NULL|  
|logical_name|**nvarchar(255)**|Имя свойства в соответствии с определением [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0 — экземпляр устройства уникален.<br /><br /> 1 — устройства экземпляр не является уникальным.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
