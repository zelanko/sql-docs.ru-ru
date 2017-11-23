---
title: "sys.pdw_health_components (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
caps.latest.revision: "6"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab177728085452cb763df8a3198350cca8e44619
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwhealthcomponents-transact-sql"></a>sys.pdw_health_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Хранит сведения о всех компонентами и устройствами, которые существуют в системе. К ним относятся оборудования, устройств хранения и сетевых устройств.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|идентификатор_компонента|**int**|Уникальный идентификатор компонента или устройства.<br /><br /> Ключ для этого представления.|NOT NULL|  
|group_id|**Int**|Логический компонент группы, к которой принадлежит этот компонент. В разделе [sys.pdw_health_components (Parallel Data Warehouse)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|component_name|**nvarchar(255)**|Имя компонента.|NOT NULL|  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
