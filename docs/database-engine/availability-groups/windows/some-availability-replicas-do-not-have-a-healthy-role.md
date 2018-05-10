---
title: Некоторые реплики доступности не имеют исправной роли | Документы Майкрософт
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
- sql13.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 514c7ea9779dd590fd702ee6f4364c6b50fe9dec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a>Некоторые реплики доступности не имеют исправной роли
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние роли реплик доступности|  
|**Проблема**|Некоторые реплики доступности не имеют исправной роли.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|группа доступности|  
  
## <a name="description"></a>Description  
 Эта политика опрашивает состояние подключения всех реплик доступности и проверяет наличие реплик, не имеющих исправной роли. Политика имеет неисправное состояние, когда любая из реплик доступности не является первичной или вторичной. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Сведения о возможных причинах проблем и решениях для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]содержатся в разделе [Некоторые реплики доступности не имеют исправной роли](http://go.microsoft.com/fwlink/p/?LinkId=220854) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 По крайней мере одна реплика доступности в этой группе доступности не имеет первичной или вторичной роли.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплик доступности для поиска реплики доступности, роль которой не является первичной или вторичной, после чего устраните неполадку в реплике доступности.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
