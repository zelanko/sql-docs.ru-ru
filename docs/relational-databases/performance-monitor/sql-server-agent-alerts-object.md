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
manager: craigg
ms.openlocfilehash: ca1234a9b70c3da26ed9146e4c5eda51ca431f80
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379875"
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
  
  
