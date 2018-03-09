---
title: "SQL Server, объект Latches | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
caps.latest.revision: "23"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2436c5bc7dc7e4c9acad39acf1697fae5cf3425
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-latches-object"></a>SQL Server, объект Latches
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект **SQLServer:Latches** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет счетчики для контроля над блокировками внутренних ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], называемыми кратковременными блокировками. Контроль над кратковременными блокировками с целью определения деятельности пользователей и распределения ресурсов помогает обнаружить узкие места в производительности системы.  
  
 В данной таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **в** .  
  
|Счетчики кратковременных блокировок в SQL Server|Description|  
|---------------------------------|-----------------|  
|**Среднее время ожидания кратковременной блокировки (мс)**|Средняя длительность ожидания кратковременной блокировки запроса (в миллисекундах)|  
|**Базовое время ожидания кратковременной блокировки**|Только для внутреннего применения.| 
|**Ожиданий кратковременных блокировок в секунду**|Количество запросов на кратковременную блокировку, при которых блокировка не была предоставлена немедленно.|  
|**Количество кратких блокировок по схеме «superlatch»**|Текущее количество кратковременных блокировок по схеме «superlatch».|  
|**Переключений из режима краткой блокировки по схеме «superlatch», в секунду**|Количество блокировок по схеме «superlatch», пониженных до обычных кратковременных блокировок в течение последней секунды.|  
|**Переключений в режим краткой блокировки по схеме «superlatch», в секунду**|Количество кратковременных блокировок по схеме «superlatch» в течение последней секунды.|  
|**Общее время ожидания кратковременной блокировки (мс)**|Общая длительность ожидания (в миллисекундах) после запросов кратковременной блокировки в течение последней секунды.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
