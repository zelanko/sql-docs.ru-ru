---
title: Наблюдение за репликацией с помощью системного монитора | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], System Monitor
- System Monitor [SQL Server], replication
- performance counters [SQL Server replication]
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 029f497a8010d6d1b3c332bd8080bf6f6e0d93f7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="monitoring-replication-with-system-monitor"></a>Наблюдение за репликацией с помощью системного монитора
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Системный монитор Windows[!INCLUDE[msCoName](../../../includes/msconame-md.md)] позволяет использовать графики, диаграммы и отчеты для измерения производительности компьютера, предоставляет возможность проведения диагностики и устранения причин возможных проблем (например, несбалансированное использование ресурсов, недостаток аппаратных средств или плохой алгоритм программы), а также поддерживает планирование дополнительных потребностей в аппаратных средствах. Дополнительные сведения см. в статье [Наблюдение за использованием ресурсов (системный монитор)](../../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 Системный монитор использует объекты и счетчики производительности, предоставляющие информацию о производительности различных процессов. Производительность репликации можно оценить с помощью счетчиков, связанных с агентами репликации:  
  
|Агент|Объект производительности|Счетчик|Description|  
|-----------|------------------------|-------------|-----------------|  
|Все агенты|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: агенты репликации|Запущен|Число агентов репликации, запущенных в данный момент времени.|  
|агент моментальных снимков|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: моментальный снимок репликации|Snapshot: Delivered Cmds/sec|Число команд, доставленных распространителю в секунду.|  
|агент моментальных снимков|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: моментальный снимок репликации|Моментальный снимок: доставлено транзакций/с|Количество транзакций, доставленных распространителю за секунду.|  
|Агент чтения журнала.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: средство чтения журнала репликации|Logreader: Delivered Cmds/sec|Число команд, доставленных распространителю в секунду.|  
|Агент чтения журнала.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: средство чтения журнала репликации|Logreader: Delivered Trans/sec|Количество транзакций, доставленных распространителю за секунду.|  
|Агент чтения журнала.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: средство чтения журнала репликации|Logreader: Delivery Latency|Текущее количество времени, в миллисекундах, прошедшего с момента применения транзакций на издателе до момента доставки транзакций распространителю.|  
|Агент распространителя|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: распространитель репликации.|Dist: Delivered Cmds/sec|Количество команд, доставленных подписчику за секунду.|  
|Агент распространителя|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: распространитель репликации.|Dist: Delivered Trans/sec|Количество транзакций, доставленных подписчику за секунду.|  
|Агент распространителя|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: распространитель репликации.|Dist: Delivery Latency|Текущее количество времени, в миллисекундах, прошедшего с момента доставки транзакций распространителю до момента применения транзакций у подписчика.|  
|Агент слияния.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: слияние репликации|Конфликтов/сек|Число конфликтов в секунду во время процесса слияния.|  
|Агент слияния.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: слияние репликации|Загружено изменений/сек|Число строк в секунду, реплицированных с издателя на подписчик.|  
|Агент слияния.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: слияние репликации|Выгружено изменений/сек|Число строк в секунду, реплицируемых с подписчика на издатель.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
