---
title: "Реплика доступности не в рабочем состоянии | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b99f1a525cb1475a4aa9e4c66759c0f379de79b9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="availability-replica-does-not-have-a-healthy-role"></a>Доступность репликации не имеет исправной роли
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние роли реплики доступности|  
|**Проблема**|Реплике доступности не назначена допустимая роль.|  
|**Категория**|**Критическая**|  
|**Аспект**|Реплика доступности|  
  
## <a name="description"></a>Описание  
 Эта политика проверяет состояние роли реплики доступности. Политика находится в состоянии неисправности, если роль реплики доступности не является первичной или вторичной. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблемы и ее решении доступны в разделе [Реплика доступности не имеет исправной роли](http://go.microsoft.com/fwlink/p/?LinkId=220856) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Роль этой реплики доступности неисправна. Реплике не назначена роль первичной или вторичной.  
  
## <a name="possible-solution-informationstilltocome"></a>Возможное решение: Information_still_to_come  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

