---
title: sys.pdw_health_component_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 66abdb548b09d2f38d3b57274ad3ea52cee3acc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717832"
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Сохраняет свойства, описывающие устройства. Некоторые свойства отображения состояния устройства и некоторые свойства описания само устройство.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Уникальный идентификатор свойства компонента.<br /><br /> идентификатором и идентификатор_компонента формируют ключ для этого представления.|NOT NULL|  
|идентификатор_компонента|**int**|Идентификатор компонента. См. в разделе [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> идентификатором и идентификатор_компонента формируют ключ для этого представления.|NOT NULL|  
|property_name|**nvarchar(255)**|Имя свойства.|NOT NULL|  
|physical_name|**nvarchar(32)**|Имя свойства, как определено производителем.|NOT NULL|  
|is_key|**bit**|Определяет, является ли экземпляр устройство уникальным или неуникальным.|NOT NULL<br /><br /> 0 — экземпляр устройства является уникальным.<br /><br /> 1 — экземпляр устройство не является уникальным.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
