---
title: Состояние синхронизации данных некоторых баз данных доступности не находится в рабочем состоянии | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 45f1479d96838ce69a7bde35cd2a2fbd9c7e684d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62814252"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a>Состояние синхронизации данных некоторых баз данных доступности не является исправным
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации данных реплики доступности|  
|**Issue**|Состояние синхронизации данных некоторых баз данных доступности не является исправным.|  
|**Категория**|**Предупреждение**|  
|**Устанавливают**|реплика доступности|  
  
## <a name="description"></a>Description  
 Эта политика проверяет состояние синхронизации базы данных доступности (также называемой «реплика базы данных»). Политика находится в неисправном состоянии, когда синхронизация данных приобретает состояние NOT SYNCRONIZING, либо не является SYNCHRONIZED при синхронной фиксации реплики баз данных.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях приведены в разделе [Состояние синхронизации данных некоторых баз данных доступности не является исправным](https://go.microsoft.com/fwlink/p/?LinkId=220863) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Одна или несколько баз данных доступности в этой реплике не находятся в исправном состоянии синхронизации данных. Если это реплика доступности с асинхронной фиксацией, все базы данных доступности должны находиться в состоянии SYNCHRONIZING. Если эта реплика доступности настроена для синхронной фиксации, все базы данных доступности должны быть в состоянии SYNCHRONIZED. Возможны следующие причины этой проблемы.  
  
-   Возможно, эта реплика доступности отключена.  
  
-   Перемещение данных может быть временно приостановлено.  
  
-   База данных может быть недоступна.  
  
-   Возможны некоторые задержки из-за проблем с сетью или нагрузки на основную или дополнительную реплику.  
  
## <a name="possible-solution"></a>Возможное решение  
 Устраните все неполадки, связанные с подключением или приостановкой перемещения данных. Проверьте события, связанные с этой неполадкой при помощи среды SQL Server Management Studio, и найдите ошибку базы данных. Выполните действия по устранению неполадок, предписанные для этой ошибки.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
