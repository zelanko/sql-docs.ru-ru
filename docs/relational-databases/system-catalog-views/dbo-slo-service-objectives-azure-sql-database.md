---
title: "dbo.slo_service_objectives (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
f1_keywords:
- dbo.slo_service_objectives
- dbo.slo_service_objectives_TSQL
- slo_service_objectives
- slo_service_objectives_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_service_objectives
- slo_service_objectives
ms.assetid: d5dd7ed9-440a-4432-ad45-644e4e72318f
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f91dccf478821047e4c3a25ea19d35d1a2774fd
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="dbosloserviceobjectives-azure-sql-database"></a>dbo.slo_service_objectives (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  Этот компонент находится в состоянии предварительной версии и рекомендуется к использованию в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] версии 12. Не полагайтесь на конкретную реализацию этого компонента, так как он может быть изменен или удален в следующей версии.  
  
 Возвращает сведения о цели уровня обслуживания (SLO) на текущем сервере.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11.|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|objective_id|**uniqueidentifier**|Идентификатор цели уровня обслуживания.|  
|NAME|**sysname**|Имя цели уровня обслуживания.|  
|description|**nvarchar**|Описание цели уровня обслуживания.|  
|create_date|**datetimeoffset(7)**|Дата создания объекта уровня обслуживания на сервере.|  
|is_system|**bit**|1 = системная цель уровня обслуживания|  
|is_default|**bit**|1 = цель уровня обслуживания является SLO по умолчанию.|  
|state|**tinyint**|1 = цель уровня обслуживания включена.<br /><br /> 2 = цель уровня обслуживания отключена.|  
|state_desc|**nvarchar**|Описание цели уровня обслуживания.|  
|metadata_version|**decimal**|Версия цели уровня обслуживания.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Управление расширенными базами данных](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
