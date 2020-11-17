---
title: Некоторые синхронные реплики не синхронизированы
description: Описание некоторых возможных причин и решений в случае, когда синхронная реплика не синхронизируется для группы доступности Always On.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: cawrites
ms.author: chadam
ms.openlocfilehash: a8e5fc7b3aa708acc3542082ece0d980c938eb34
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2020
ms.locfileid: "94583867"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Некоторые синхронные реплики не синхронизированы
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации данных синхронных реплик|  
|**Проблема**|Некоторые синхронные реплики не синхронизированы.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|группа доступности|  
  
## <a name="description"></a>Описание  
 Эта политика сворачивает состояние синхронизации данных всех реплик доступности и проверяет наличие реплик доступности, состояние синхронизации которых отличается от ожидаемого. Политика находится в неисправном состоянии, если любая асинхронная реплика не находится в состоянии SYNCHRONIZING, а любая синхронная реплика не находится в состоянии SYNCHRONIZED. Состояние политики исправно при других условиях.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблемы и ее решении доступны в разделе [Некоторые синхронные реплики не синхронизированы](https://go.microsoft.com/fwlink/p/?LinkId=220853) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 В этой группе доступности не синхронизирована по меньшей мере одна реплика доступности. Состояние синхронизации реплики может быть либо SYNCHONIZING, либо NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплики доступности для поиска реплики доступности с неверным состоянием синхронизации, после чего устраните неполадку в реплике доступности.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
