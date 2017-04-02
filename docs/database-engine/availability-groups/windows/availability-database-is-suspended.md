---
title: "База данных доступности приостановлена | Microsoft Docs"
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
  - "sql13.swb.agdashboard.drp1notsuspended.issues.f1"
helpviewer_keywords: 
  - "группы доступности [SQL Server], политики"
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# База данных доступности приостановлена
    
## Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние приостановки базы данных доступности|  
|**Проблема**|База данных доступности приостановлена.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|База данных доступности|  
  
## Описание  
 Эта политика проверяет состояние перемещения данных базы данных-получателя (которая также называется «реплика базы данных-получателя»). Эта политика находится в нерабочем состоянии, если перемещение данных приостановлено. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] сведения о возможных причинах проблем и решениях доступны в разделе [База данных доступности приостановлена](http://go.microsoft.com/fwlink/p/?LinkId=220860) в TechNet Wiki.  
  
## Возможные причины  
 Возможны следующие причины приостановки синхронизации данных в этой базе данных доступности:  
  
-   Из-за ошибки система могла приостановить синхронизацию данных.  
  
-   Администратор базы данных мог приостановить синхронизацию данных для выполнения задач технического обслуживания.  
  
## Возможное решение  
 Восстановите синхронизацию данных. При повторном возникновении проблемы проверьте группу доступности в журнале событий, а затем с помощью диагностики определите причину приостановки перемещения данных системой.  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  