---
title: Реплика доступности не присоединена к группе доступности
description: Определение возможных причин, по которым реплика доступности может быть не присоединена к группе доступности Always On.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a0902212b2f1ab8cf7d7c16c1d1e0c811b6d6b78
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896194"
---
# <a name="availability-replica-is-not-joined-to-an-always-on-availability-group"></a>Реплика доступности не присоединена к группе доступности Always On
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
    
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
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Реплика доступности не присоединена](https://go.microsoft.com/fwlink/p/?LinkId=220859) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Вторичная реплика не присоединена к группе доступности. Реплика доступности успешно присоединена к группе доступности, когда она имеет состояние присоединения «Присоединенный автономный экземпляр» (1) или «Присоединенный отказоустойчивый кластер» (2).  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте Transact-SQL, PowerShell или среду SQL Server Management Studio для присоединения вторичной реплики к группе доступности. Дополнительные сведения о присоединении вторичных реплик к группам доступности приведены в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](https://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx).  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
