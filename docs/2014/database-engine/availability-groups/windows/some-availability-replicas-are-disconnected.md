---
title: Некоторые реплики доступности отключены | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7393fe6d415f8b68758d75fafba91c9ab0a420c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788419"
---
# <a name="some-availability-replicas-are-disconnected"></a>Некоторые реплики доступности отключены
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние соединения с репликами доступности|  
|**Проблема**|Некоторые реплики доступности отключены.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|группа доступности|  
  
## <a name="description"></a>Описание  
 Эта политика опрашивает состояние подключения всех реплик доступности и проверяет наличие реплик, имеющих состояние DISCONNECTED. Эта политика находится в неисправном состоянии, если любая реплика доступности находится в состоянии DISCONNECTED. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Некоторые реплики доступности отключены](https://go.microsoft.com/fwlink/p/?LinkId=220855) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 По крайней мере одна вторичная реплика доступности не подключена к основной реплике в этой группе доступности. Состояние соединения — DISCONNECTED.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплик доступности для поиска реплики доступности с состоянием DISCONNECTED и устраните проблему в реплике доступности.  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
