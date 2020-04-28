---
title: sys. pdw_health_component_status_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ec631e9008cc37a7b4f91ed3f530e5388bdf9c0d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127499"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>sys. pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Определяет сопоставление между состоянием [!INCLUDE[ssDW](../../includes/ssdw-md.md)] компонента и именами компонентов, определенными производителем.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства.<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|component_id|**int**|Идентификатор компонента. См. раздел [sys. pdw_health_components &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства в соответствии с определением изготовителя.<br /><br /> property_id, component_id и physical_name образуют ключ для этого представления.|NOT NULL|  
|logical_name|**nvarchar(255)**|Имя свойства в соответствии с [!INCLUDE[ssDW](../../includes/ssdw-md.md)]определением.|NOT NULL<br /><br /> 0 — экземпляр устройства уникален.<br /><br /> 1 — экземпляр устройства не является уникальным.|  
  
## <a name="see-also"></a>См. также:  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
