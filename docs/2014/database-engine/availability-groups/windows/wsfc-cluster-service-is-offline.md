---
title: WSFC служба кластеров работает в режиме вне сети | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
caps.latest.revision: 14
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: ff8eee20242724487f600e7002a4c9fb3ac291b5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100475"
---
# <a name="wsfc-cluster-service-is-offline"></a>WSFC служба кластеров работает в режиме вне сети
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние кластера WSFC|  
|**Проблема**|Служба кластеров WSFC находится вне сети.|  
|**Категория**|**Критическая**|  
|**Аспект**|Экземпляр SQL Server|  
  
## <a name="description"></a>Описание  
 Эта политика проверяет состояние отказоустойчивого кластера Windows Server (WSFC). Политика находится в неисправном состоянии и выдает предупреждение, если кластер WSFC находится вне сети или в состоянии «принудительный кворум». Все группы доступности, размещенные на этом кластере, находятся в режиме «вне сети», либо требуется процедура аварийного восстановления.  
  
 Эта политика находится в исправном состоянии, если состояние кластера — «нормальный кворум».  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], сведения о возможных причинах проблем и решениях приведены в разделе [Служба кластера WSFC не в сети](http://go.microsoft.com/fwlink/p/?LinkId=220849) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Эта неполадка может возникать из-за неисправности службы кластера либо при потере кворума в кластере.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте администратор кластеров для запуска процедур принудительного кворума или аварийного восстановления. Если проблему не удается устранить при помощи процедур принудительного кворума или аварийного восстановления, обратитесь к администратору кластера за помощью в устранении этой неполадки. Дополнительные сведения см. в разделе [Принудительный запуск кластера WSFC без кворума](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  