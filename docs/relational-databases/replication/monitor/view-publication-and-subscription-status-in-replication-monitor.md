---
title: "Просмотр состояний публикаций и подписок в мониторе репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ea47f9f50242003e4aa933da2e5657bb7e2ed5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>Просмотр состояний публикаций и подписок в мониторе репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Монитор репликации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отображает сведения о состоянии публикаций и подписок:  
  
-   Состояние публикации определяется наиболее приоритетным состоянием ее подписок. Например, если в одной подписке на публикацию содержится ошибка, в другой — проблема с производительностью, для публикации отображается состояние ошибки.  
  
-   Состояние подписки определяется состоянием агентов, обслуживающих подписку. Для репликации слиянием это агент слияния. Для репликации транзакций это либо агент чтения журнала, либо агент распространителя (отображается состояние более высокого приоритета; состояние также может определяться агентом чтения очереди, если используются подписки, обновляемые посредством очередей). Для репликации моментальных снимков это агент моментальных снимков или агент распространителя (отображается состояние более высокого приоритета).  
  
 В таблицах следующих разделов перечислены значения возможных состояний публикаций и подписок. Три из указанных значений состояния отображаются только при достижении или превышении порогового значения.  
  
-   Истекающая подписка  
  
     Данное значение состояния применимо ко всем типам репликации. Дополнительные сведения см. в статье [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   Критическая производительность  
  
     Данное значение состояния применяется к репликации транзакций и репликации слиянием. Дополнительные сведения см. в статье о [наблюдении за производительностью с помощью монитора репликации](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
-   Длительное слияние  
  
     Данное значение состояния применимо к репликации слиянием. Дополнительные сведения см. в статье о [наблюдении за производительностью с помощью монитора репликации](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 Кроме состояния публикаций и подписок, репликация слиянием предоставляет статистику по статьям, что позволяет получить подробные сведения об оставшемся времени на завершение слияния, о времени, затраченном на обработку указанной статьи, о типе соединения, используемом подписчиком, а также другие важные сведения. Статистика отображается в окне агента слияния монитора репликации. Репликация моментальных снимков и репликация транзакций предоставляют подробные сведения об обработке агента распространителя.  
  
 **Просмотр состояния публикации и подписки**  
  
-   Монитор репликации: [Просмотр сведений и выполнение задач для публикации (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md) и [Просмотр сведений и выполнение задач для подписки (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md).  
  
 **Просмотр подробных сведений об агентах**  
  
-   Монитор репликации: [Просмотр сведений и выполнение задач для агентов, ассоциированных с публикацией (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md) и [Просмотр сведений и выполнение задач для агентов, ассоциированных с подпиской (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="publication-status-values"></a>Значения состояния публикации  
 В следующей таблице содержатся значения состояния публикации и соответствующие им значки в порядке приоритета.  
  
|Состояние|Значок|  
|------------|----------|  
|Ошибка|![Значок интерфейса пользователя: ошибка](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Значок интерфейса пользователя: ошибка")|  
|Критическая производительность|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Повтор последней невыполненной команды|![Значок интерфейса пользователя: повторное выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Значок интерфейса пользователя: повторное выполнение агента репликации")|  
|ОК|none|  
  
## <a name="subscription-status-values"></a>Значения состояния подписки  
 В следующей таблице содержатся значения состояния подписки и соответствующие им значки в порядке приоритета. Подписка может находиться одновременно в двух состояниях, например в состоянии **Срок действия скоро истекает или истек** и **Повторное выполнение неудавшейся команды**. При этом выводится состояние с наибольшим приоритетом.  
  
 Значения состояния **Критическое для производительности**, **Срок действия скоро истекает или истек**и **Не инициализировано** являются предупреждениями. Если выводится предупреждение, монитор репликации также показывает, запущен ли агент. Например, состояние может отображаться как **Запущен, Критическое для производительности**.  
  
### <a name="transactional-subscriptions"></a>Подписки на публикацию транзакций  
  
|Состояние|Значок|  
|------------|----------|  
|Ошибка|![Значок интерфейса пользователя: ошибка](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Значок интерфейса пользователя: ошибка")|  
|Критическая производительность|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Срок действия скоро истекает или истек|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Неинициализированная подписка|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Повтор последней невыполненной команды|![Значок интерфейса пользователя: повторное выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Значок интерфейса пользователя: повторное выполнение агента репликации")|  
|Не выполняется|![Значок интерфейса пользователя: остановка агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "Значок интерфейса пользователя: остановка агента репликации")|  
|Запущен|![Значок интерфейса пользователя: выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "Значок интерфейса пользователя: выполнение агента репликации")|  
  
### <a name="merge-subscriptions"></a>Подписки на публикацию слиянием  
  
|Состояние|Значок|  
|------------|----------|  
|Ошибка|![Значок интерфейса пользователя: ошибка](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Значок интерфейса пользователя: ошибка")|  
|Критическая производительность|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Длительное слияние|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Срок действия скоро истекает или истек|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Неинициализированная подписка|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Повтор последней невыполненной команды|![Значок интерфейса пользователя: повторное выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Значок интерфейса пользователя: повторное выполнение агента репликации")|  
|Синхронизация|![Значок интерфейса пользователя: выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "Значок интерфейса пользователя: выполнение агента репликации")|  
|Не синхронизируется|![Значок интерфейса пользователя: остановка агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "Значок интерфейса пользователя: остановка агента репликации")|  
  
### <a name="snapshot-subscriptions"></a>Подписки моментальных снимков  
  
|Состояние|Значок|  
|------------|----------|  
|Ошибка|![Значок интерфейса пользователя: ошибка](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Значок интерфейса пользователя: ошибка")|  
|Срок действия скоро истекает или истек|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Неинициализированная подписка|![Значок интерфейса пользователя: предупреждение](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Значок интерфейса пользователя: предупреждение")|  
|Повтор последней невыполненной команды|![Значок интерфейса пользователя: повторное выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Значок интерфейса пользователя: повторное выполнение агента репликации")|  
|Синхронизация|![Значок интерфейса пользователя: выполнение агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "Значок интерфейса пользователя: выполнение агента репликации")|  
|Не синхронизируется|![Значок интерфейса пользователя: остановка агента репликации](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "Значок интерфейса пользователя: остановка агента репликации")|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
