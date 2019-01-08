---
title: Некоторые реплики доступности не имеют исправной роли | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 50518e78585b7e56f62411edc539d0f9ac3db9e9
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360313"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a>Некоторые реплики доступности не имеют исправной роли
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние роли реплик доступности|  
|**Проблема**|Некоторые реплики доступности не имеют исправной роли.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|группа доступности|  
  
## <a name="description"></a>Описание  
 Эта политика опрашивает состояние подключения всех реплик доступности и проверяет наличие реплик, не имеющих исправной роли. Политика имеет неисправное состояние, когда любая из реплик доступности не является первичной или вторичной. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Сведения о возможных причинах проблем и решениях для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]содержатся в разделе [Некоторые реплики доступности не имеют исправной роли](https://go.microsoft.com/fwlink/p/?LinkId=220854) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 По крайней мере одна реплика доступности в этой группе доступности не имеет первичной или вторичной роли.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплик доступности для поиска реплики доступности, роль которой не является первичной или вторичной, после чего устраните неполадку в реплике доступности.  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
