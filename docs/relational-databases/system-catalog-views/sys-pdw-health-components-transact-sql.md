---
title: sys. pdw_health_components (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5205c1ac6248f5aadee01410b4ba5e8f00332a73
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127490"
---
# <a name="syspdw_health_components-transact-sql"></a>sys. pdw_health_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Хранит сведения обо всех компонентах и устройствах, имеющихся в системе. К ним относятся оборудование, запоминающие устройства и сетевые устройства.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|Уникальный идентификатор компонента или устройства.<br /><br /> Ключ для этого представления.|NOT NULL|  
|group_id|**Int**|Группа логических компонентов, к которой принадлежит этот компонент. См. раздел [sys. pdw_health_components (Parallel Data Warehouse)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|component_name|**nvarchar(255)**|Имя компонента.|NOT NULL|  
  
## <a name="see-also"></a>См. также:  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
