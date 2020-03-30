---
title: Состояние синхронизации данных баз данных доступности не является исправным
description: Определите возможные причины, по которым состояние синхронизации данных у баз данных в группе доступности Always On — "неработоспособны".
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
manager: erikre
ms.openlocfilehash: ff7b069ebde75185b0e500bc7052edc6e99fc927
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68265353"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy-for-an-always-on-availability-group"></a>Состояние синхронизации данных базы данных доступности для группы доступности Always On не в рабочем состоянии
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации базы данных доступности|  
|**Проблема**|Состояние синхронизации данных некоторых баз данных доступности не является рабочим.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|База данных доступности|  
  
## <a name="description"></a>Description  
 Эта политика выполняет сведение состояния синхронизации данных для всех баз данных доступности (которые также называются «реплики баз данных») в реплике доступности. Политика находится в нерабочем состоянии при нахождении какой-либо из реплик баз данных в непредвиденном состоянии синхронизации данных. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях доступны в разделе [Состояние синхронизации данных некоторых баз данных доступности не является исправным](https://go.microsoft.com/fwlink/p/?LinkId=220858) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Состояние синхронизации данных некоторых баз данных доступности не является рабочим. Если это реплика доступности с асинхронной фиксацией, все базы данных доступности должны находиться в состоянии SYNCHRONIZING. При синхронной фиксации реплик доступности у всех баз данных доступности должно быть состояние SYNCHRONIZED.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте политику реплик баз данных для поиска реплики баз данных с нерабочим состоянием синхронизации данных и устраните проблему в реплике базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](~/database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  


