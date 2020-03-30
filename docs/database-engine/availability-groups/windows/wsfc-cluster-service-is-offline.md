---
title: WSFC служба кластеров работает в режиме вне сети | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: c0d069601c36ba46be3c1950300c16b8808c264f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68013356"
---
# <a name="wsfc-cluster-service-is-offline"></a>WSFC служба кластеров работает в режиме вне сети

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние кластера WSFC|  
|**Проблема**|Служба кластеров WSFC находится вне сети.|  
|**Категория**|**Критическая**|  
|**Аспект**|Экземпляр SQL Server|  
  
## <a name="description"></a>Description  
 Эта политика проверяет состояние отказоустойчивого кластера Windows Server (WSFC). Политика находится в неисправном состоянии и выдает предупреждение, если кластер WSFC находится вне сети или в состоянии «принудительный кворум». Все группы доступности, размещенные на этом кластере, находятся в режиме «вне сети», либо требуется процедура аварийного восстановления.  
  
 Эта политика находится в исправном состоянии, если состояние кластера — «нормальный кворум».  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], сведения о возможных причинах проблем и решениях приведены в разделе [Служба кластера WSFC не в сети](https://go.microsoft.com/fwlink/p/?LinkId=220849) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Эта неполадка может возникать из-за неисправности службы кластера либо при потере кворума в кластере.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте администратор кластеров для запуска процедур принудительного кворума или аварийного восстановления. Если проблему не удается устранить при помощи процедур принудительного кворума или аварийного восстановления, обратитесь к администратору кластера за помощью в устранении этой неполадки. Дополнительные сведения см. в разделе [Принудительный запуск кластера WSFC без кворума](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
