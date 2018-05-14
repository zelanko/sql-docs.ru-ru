---
title: Реплика доступности не присоединена | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ab5079c7efcf04dd6f5461504d6bb97f9d2b548d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="availability-replica-is-not-joined"></a>Реплика доступности не присоединена
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние присоединения реплики доступности|  
|**Проблема**|Реплика доступности не присоединена.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|Реплика доступности|  
  
## <a name="description"></a>Description  
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
  
  
