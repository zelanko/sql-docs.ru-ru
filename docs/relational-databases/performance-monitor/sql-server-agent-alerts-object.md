---
title: Объект предупреждений (агент SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3776ba97213564b36630c82845b0620b6d2cacd8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852991"
---
# <a name="sql-server-agent-alerts-object"></a>Агент SQL Server, объект Alerts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
