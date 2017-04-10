---
title: "Доступность репликации не имеет исправной роли | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.arp1rolehealthy.issues.f1"
helpviewer_keywords: 
  - "группы доступности [SQL Server], политики"
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
caps.latest.revision: 13
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 13
---
# Доступность репликации не имеет исправной роли
    
## Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние роли реплики доступности|  
|**Проблема**|Реплике доступности не назначена допустимая роль.|  
|**Категория**|**Критическая**|  
|**Аспект**|Реплика доступности|  
  
## Описание  
 Эта политика проверяет состояние роли реплики доступности. Политика находится в состоянии неисправности, если роль реплики доступности не является первичной или вторичной. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] сведения о возможных причинах проблемы и ее решении доступны в разделе [Реплика доступности не имеет исправной роли](http://go.microsoft.com/fwlink/p/?LinkId=220856) в TechNet Wiki.  
  
## Возможные причины  
 Роль этой реплики доступности неисправна. Реплике не назначена роль первичной или вторичной.  
  
## Возможное решение: Information_still_to_come  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  