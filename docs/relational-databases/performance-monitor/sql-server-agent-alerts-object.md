---
title: Объект предупреждений (агент SQL Server) | Документация Майкрософт
description: Сведения об объекте производительности Alerts агента SQL Server, который содержит счетчики производительности, предоставляющие сведения о предупреждениях агента SQL Server.
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
ms.openlocfilehash: 9fe293b70b074322380dc55f4294971908c106ee
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457471"
---
# <a name="sql-server-agent-alerts-object"></a>Агент SQL Server, объект Alerts
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект производительности **Alerts** агента SQL Server содержит счетчики производительности, которые предоставляют сведения о предупреждениях агента SQL Server. В следующей таблице перечислены счетчики этого объекта.  
  
 В таблице ниже перечислены счетчики **SQLAgent:Alerts** .  
  
|Имя|Описание|  
|----------|-----------------|  
|**Активированные предупреждения**|Этот счетчик показывает полное число предупреждений, которые активировал агент SQL Server со своего последнего перезапуска.|  
|**Предупреждения, активированные за минуту**|Этот счетчик показывает количество предупреждений, активированных агентом SQL Server за последнюю минуту.|  
  
> [!NOTE]  
>  Чтобы использовать этот объект агента SQL Server, необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [Alerts](../../ssms/agent/alerts.md)   
 [Использование объектов производительности](../../ssms/agent/use-performance-objects.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
