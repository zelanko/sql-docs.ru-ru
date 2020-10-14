---
description: sys.pdw_health_component_status_mappings (Transact-SQL)
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 583790fa6b14660f2e48f39ca44c06fbbfb9ff5b
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92034827"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Определяет сопоставление между [!INCLUDE[ssDW](../../includes/ssdw-md.md)] состоянием компонента и именами компонентов, определенными производителем.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства.<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|component_id|**int**|Идентификатор компонента. См. раздел [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства в соответствии с определением изготовителя.<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|logical_name|**nvarchar(255)**|Имя свойства в соответствии с определением [!INCLUDE[ssDW](../../includes/ssdw-md.md)] .|NOT NULL<br /><br /> 0 — экземпляр устройства уникален.<br /><br /> 1 — экземпляр устройства не является уникальным.|  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога Azure Synapse Analytics и Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
