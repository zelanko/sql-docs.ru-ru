---
title: Параметр конфигурации сервера "blocked process threshold" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 95033e6bf87c78808bcfd1d9ce5b892604418ec7
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40406548"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>Параметр конфигурации сервера «blocked process threshold»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **blocked process threshold** определяет пороговое значение (в секундах), в течение которого блокированный процесс порождает сообщения. Пороговое значение может быть задано в диапазоне от 0 до 86 400. По умолчанию отчеты о заблокированных процессах не создаются. Это событие не формируется для системных задач и для задач, которые ожидают ресурсы, не производящие отслеживаемых взаимоблокировок.  
  
 При формировании данного события можно выдать [предупреждение](../../ssms/agent/alerts.md) . Например, можно выдать администратору на пейджер сообщение о необходимости разобраться с блокировкой.  
  
 Мониторинг порога блокировки процесса использует фоновый поток отслеживания взаимоблокировок, который просматривает список задач, ожидающих выполнения в течение времени, превышающего указанное в настройках пороговое значение. Это событие формируется один раз в течение отчетного интервала для каждой из заблокированных задач.  
  
 Отчет о блокированном процессе выполняется по принципу оптимальных затрат. Нет никакой гарантии, что он будет выдаваться в реальном времени или хотя бы достаточно быстро.  
  
 Новые настройки вступают в силу сразу же, без остановки или перезапуска сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере параметр `blocked process threshold` устанавливается в значение `20` секунд, выдавая отчет о заблокированных процессах.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Класс событий Blocked Process Report](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
