---
title: "Некоторые реплики доступности отключены | Документы Майкрософт"
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
- sql13.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1d60f039b8f67cc3cfc3edd72a8c35d6aabb05ab
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="some-availability-replicas-are-disconnected"></a>Некоторые реплики доступности отключены
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние соединения с репликами доступности|  
|**Проблема**|Некоторые реплики доступности отключены.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|Группа доступности|  
  
## <a name="description"></a>Описание  
 Эта политика опрашивает состояние подключения всех реплик доступности и проверяет наличие реплик, имеющих состояние DISCONNECTED. Эта политика находится в неисправном состоянии, если любая реплика доступности находится в состоянии DISCONNECTED. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Некоторые реплики доступности отключены](http://go.microsoft.com/fwlink/p/?LinkId=220855) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 По крайней мере одна вторичная реплика доступности не подключена к основной реплике в этой группе доступности. Состояние соединения — DISCONNECTED.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплик доступности для поиска реплики доступности с состоянием DISCONNECTED и устраните проблему в реплике доступности.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

