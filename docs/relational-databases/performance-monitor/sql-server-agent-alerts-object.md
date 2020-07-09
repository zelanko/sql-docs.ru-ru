---
title: Объект предупреждений (агент SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 425a2330f8ecb3f33380cf0500de32e82463634e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787393"
---
# <a name="sql-server-agent-alerts-object"></a>Агент SQL Server, объект Alerts
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект производительности **Alerts** агента SQL Server содержит счетчики производительности, которые предоставляют сведения о предупреждениях агента SQL Server. В следующей таблице перечислены счетчики этого объекта.  
  
 В таблице ниже перечислены счетчики **SQLAgent:Alerts** .  
  
|Имя|Description|  
|----------|-----------------|  
|**Активированные предупреждения**|Этот счетчик показывает полное число предупреждений, которые активировал агент SQL Server со своего последнего перезапуска.|  
|**Предупреждения, активированные за минуту**|Этот счетчик показывает количество предупреждений, активированных агентом SQL Server за последнюю минуту.|  
  
> [!NOTE]  
>  Чтобы использовать этот объект агента SQL Server, необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [Alerts](../../ssms/agent/alerts.md)   
 [Использование объектов производительности](../../ssms/agent/use-performance-objects.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
