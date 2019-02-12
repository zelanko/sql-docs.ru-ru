---
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 02771656dfdb0b7396e62a5bde364b0eea324aa0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031195"
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Определяет сопоставление между [!INCLUDE[ssDW](../../includes/ssdw-md.md)] состояния компонента и имена определенных производителя компонента.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства.<br /><br /> идентификатором, идентификатор_компонента и physical_name формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. См. в разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> идентификатором, идентификатор_компонента и physical_name формируют ключ для этого представления.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства, как определено производителем.<br /><br /> идентификатором, идентификатор_компонента и physical_name формируют ключ для этого представления.|NOT NULL|  
|logical_name|**nvarchar(255)**|Имя свойства в соответствии с определением [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0 — экземпляр устройства является уникальным.<br /><br /> 1 — экземпляр устройство не является уникальным.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
