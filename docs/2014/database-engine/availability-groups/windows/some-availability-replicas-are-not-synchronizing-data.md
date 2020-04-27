---
title: Некоторые реплики доступности не выполняют синхронизацию данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0fb7d422687d0bc956937b30bae261b28edb3931
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62788262"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a>Некоторые реплики доступности не выполняют синхронизацию данных
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации данных реплик доступности|  
|**Проблема**|Некоторые реплики доступности не выполняют синхронизацию данных.|  
|**Категория**|**Предупреждение**|  
|**Устанавливают**|группа доступности|  
  
## <a name="description"></a>Описание  
 Эта политика сворачивает состояние синхронизации данных всех реплик доступности в группе доступности и проверяет рабочее состояние синхронизации у всех реплик доступности. Политика находится в нерабочем состоянии, если у какой-либо реплики доступности при синхронизации данных имеется состояние NOT SYNCRONIZING.  
  
 Политика находится в рабочем состоянии, если ни у одной из реплик доступности при синхронизации данных не имеется состояние NOT SYNCRONIZING.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях доступны в разделе [Некоторые реплики доступности не выполняют синхронизацию данных](https://go.microsoft.com/fwlink/p/?LinkId=220852) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 В этой группе доступности по крайней мере у одной вторичной реплики имеется состояние синхронизации NOT SYNCHRONIZING и она не получает данных от первичной реплики.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте состояние политики реплик доступности для поиска реплики доступности с состоянием NOT SYNCHROINIZING и устраните проблему в реплике доступности.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
