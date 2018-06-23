---
title: Состояние синхронизации данных базы данных доступности не в рабочем состоянии | Документы Майкрософт
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
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 5b9a55fe0e2bcd28c75b979eb1e275095e0d14ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192970"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>Состояние синхронизации данных баз данных доступности не является исправным
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации базы данных доступности|  
|**Проблема**|Состояние синхронизации данных некоторых баз данных доступности не является рабочим.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|База данных доступности|  
  
## <a name="description"></a>Описание  
 Эта политика выполняет сведение состояния синхронизации данных для всех баз данных доступности (которые также называются «реплики баз данных») в реплике доступности. Политика находится в нерабочем состоянии при нахождении какой-либо из реплик баз данных в непредвиденном состоянии синхронизации данных. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях доступны в разделе [Состояние синхронизации данных некоторых баз данных доступности не является исправным](http://go.microsoft.com/fwlink/p/?LinkId=220858) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Состояние синхронизации данных некоторых баз данных доступности не является рабочим. Если это реплика доступности с асинхронной фиксацией, все базы данных доступности должны находиться в состоянии SYNCHRONIZING. При синхронной фиксации реплик доступности у всех баз данных доступности должно быть состояние SYNCHRONIZED.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте политику реплик баз данных для поиска реплики баз данных с нерабочим состоянием синхронизации данных и устраните проблему в реплике базы данных.  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  