---
title: Некоторые реплики доступности отключены
description: Возможные причины и решения в случае, если реплика группы доступности отключена для группы доступности Always On SQL Server.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: cawrites
ms.author: chadam
ms.openlocfilehash: cfa9fb0297f4ba3e9cdab859816ecfc4d8fb54bf
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2020
ms.locfileid: "94583892"
---
# <a name="some-availability-replicas-are-disconnected"></a>Некоторые реплики доступности отключены
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние соединения с репликами доступности|  
|**Проблема**|Некоторые реплики доступности отключены.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|группа доступности|  
  
## <a name="description"></a>Description  
 Эта политика опрашивает состояние подключения всех реплик доступности и проверяет наличие реплик, имеющих состояние DISCONNECTED. Эта политика находится в неисправном состоянии, если любая реплика доступности находится в состоянии DISCONNECTED. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Некоторые реплики доступности отключены](https://go.microsoft.com/fwlink/p/?LinkId=220855) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 По крайней мере одна вторичная реплика доступности не подключена к основной реплике в этой группе доступности. Состояние соединения — DISCONNECTED.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплик доступности для поиска реплики доступности с состоянием DISCONNECTED и устраните проблему в реплике доступности.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
