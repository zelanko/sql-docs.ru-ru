---
title: "Реплика доступности не присоединена | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords: Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33dfbf41a6a8f0576439b3fbd05d10501a1ad1e1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="availability-replica-is-not-joined"></a>Реплика доступности не присоединена
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние присоединения реплики доступности|  
|**Проблема**|Реплика доступности не присоединена.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|Реплика доступности|  
  
## <a name="description"></a>Описание  
 Эта политика проверяет состояние присоединения реплики доступности. Политика находится в состоянии неисправности, когда реплика доступности добавлена в группу доступности, но она не присоединена с соблюдением всех требований. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Реплика доступности не присоединена](http://go.microsoft.com/fwlink/p/?LinkId=220859) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Вторичная реплика не присоединена к группе доступности. Реплика доступности успешно присоединена к группе доступности, когда она имеет состояние присоединения «Присоединенный автономный экземпляр» (1) или «Присоединенный отказоустойчивый кластер» (2).  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте Transact-SQL, PowerShell или среду SQL Server Management Studio для присоединения вторичной реплики к группе доступности. Дополнительные сведения о присоединении вторичных реплик к группам доступности приведены в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx).  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
