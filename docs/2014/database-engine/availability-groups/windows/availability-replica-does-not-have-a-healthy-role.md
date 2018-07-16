---
title: Реплика доступности не в рабочем состоянии | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93a65b23bffcb99fb5440fbc86489147ed87b40a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308194"
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
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
