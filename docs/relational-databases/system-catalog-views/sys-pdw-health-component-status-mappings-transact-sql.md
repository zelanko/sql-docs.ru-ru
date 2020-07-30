---
title: sys. pdw_health_component_status_mappings (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: def9dc4a7601e4d5a89794e85f4e209036966f73
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87397124"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>sys. pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Определяет сопоставление между [!INCLUDE[ssDW](../../includes/ssdw-md.md)] состоянием компонента и именами компонентов, определенными производителем.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства.<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|component_id|**int**|Идентификатор компонента. См. раздел [sys. pdw_health_components &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства в соответствии с определением изготовителя.<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|logical_name|**nvarchar(255)**|Имя свойства в соответствии с определением [!INCLUDE[ssDW](../../includes/ssdw-md.md)] .|NOT NULL<br /><br /> 0 — экземпляр устройства уникален.<br /><br /> 1 — экземпляр устройства не является уникальным.|  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
