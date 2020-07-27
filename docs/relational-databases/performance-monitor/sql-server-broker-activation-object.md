---
title: Объект активации брокера (SQL Server) | Документация Майкрософт
description: Сведения об объекте производительности SQLServer:BrokerActivation, который содержит счетчики производительности, возвращающие сведения об активации хранимых процедур.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 74031fb95207c1bb0a4916aa512893dd38aeb7b4
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458151"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server, объект Broker Activation
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект производительности **SQLServer:BrokerActivation** содержит счетчики производительности, возвращающие сведения об активации хранимых процедур. В следующей таблице перечислены счетчики этого объекта.  
  
|Счетчики SQL Server Broker Activation|Описание|  
|-------------------------------------------|-----------------|  
|**Количество вызовов хранимых процедур/сек**|Этот счетчик возвращает общее количество хранимых процедур активации, вызываемых мониторами очереди в этом экземпляре за секунду.|  
|**Достигнут предел задач**|Этот счетчик возвращает общее число раз, когда монитор очереди должен был запустить новую задачу, но не сделал этого, так как уже выполнялось максимальное число задач для очереди.|  
|**Достигнут предел задач/сек**|Этот счетчик сообщает, сколько раз в секунду монитор очереди должен был запустить новую задачу, но не сделал этого, так как уже выполнялось максимальное число задач для очереди.|  
|**Прервано задач/сек**|Этот счетчик возвращает число задач хранимых процедур активации, завершившихся с ошибкой, либо тех, которые были прерваны монитором очереди из-за невозможности получать сообщения.|  
|**Задач работает**|Этот счетчик возвращает число хранимых процедур активации, работающих в настоящий момент.|  
|**Задач запущено/сек**|Этот счетчик возвращает число хранимых процедур активации, запущенных за секунду всеми мониторами очереди в этом экземпляре.|  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_broker_activated_tasks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql.md)   
 [sys.dm_broker_queue_monitors (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
