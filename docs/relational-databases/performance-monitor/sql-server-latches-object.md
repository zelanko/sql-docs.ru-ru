---
title: SQL Server, объект Latches | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 36cc64688cb78febb3e023e2b11e6e3da204ad1b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939521"
---
# <a name="sql-server-latches-object"></a>SQL Server, объект Latches
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект **SQLServer:Latches** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет счетчики для контроля за блокировками внутренних ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Контроль над кратковременными блокировками с целью определения деятельности пользователей и распределения ресурсов помогает обнаружить узкие места в производительности системы.  
  
 В данной таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **в** .  
  
|Счетчики кратковременных блокировок в SQL Server|Описание|  
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
  
  
