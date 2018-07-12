---
title: SQL Server, объект Latches | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 19b5d3f6cca79241d18c6bc5a91826a4cc590331
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150635"
---
# <a name="sql-server-latches-object"></a>SQL Server, объект Latches
  Объект **SQLServer:Latches** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет счетчики для контроля за блокировками внутренних ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Контроль над кратковременными блокировками с целью определения деятельности пользователей и распределения ресурсов помогает обнаружить узкие места в производительности системы.  
  
 В данной таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **в** .  
  
|Счетчики кратковременных блокировок в SQL Server|Описание|  
|---------------------------------|-----------------|  
|**Среднее время ожидания кратковременной блокировки (мс)**|Средняя длительность ожидания кратковременной блокировки запроса (в миллисекундах)|  
|**Ожиданий кратковременных блокировок в секунду**|Количество запросов на кратковременную блокировку, при которых блокировка не была предоставлена немедленно.|  
|**Количество кратких блокировок по схеме «superlatch»**|Текущее количество кратковременных блокировок по схеме «superlatch».|  
|**Переключений из режима краткой блокировки по схеме «superlatch», в секунду**|Количество блокировок по схеме «superlatch», пониженных до обычных кратковременных блокировок в течение последней секунды.|  
|**Переключений в режим краткой блокировки по схеме «superlatch», в секунду**|Количество кратковременных блокировок по схеме «superlatch» в течение последней секунды.|  
|**Общее время ожидания кратковременной блокировки (мс)**|Общая длительность ожидания (в миллисекундах) после запросов кратковременной блокировки в течение последней секунды.|  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)  
  
  
