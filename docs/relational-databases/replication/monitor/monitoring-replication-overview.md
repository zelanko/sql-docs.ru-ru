---
title: "Наблюдение за репликацией | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 47eb736bd150252f9081184ba589b8033b750c7f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="monitoring-replication-overview"></a>Обзор наблюдения за репликацией
  Монитор репликации[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] представляет собой графический инструмент для наблюдения за исправностью топологии репликации. Монитор репликации предоставляет детальные сведения о состоянии и производительности публикаций и подписок, позволяющие получать ответы на следующие общие вопросы:  
  
-   Исправна ли система репликации?  
  
-   Какие подписки медленные?  
  
-   Насколько запаздывает подписка на публикацию транзакций?  
  
-   Сколько времени понадобится, чтобы только что зафиксированная транзакция была получена подписчиком в репликации транзакций?  
  
-   Почему подписка на публикацию слиянием медленная?  
  
-   Почему агент не запущен?  
  
 Для наблюдения за репликацией пользователь должен быть членом предопределенной роли сервера **sysadmin** на распространителе или членом предопределенной роли базы данных **replmonitor** в базе данных распространителя. Системный администратор может добавить любого пользователя в роль **replmonitor** , которая позволяет пользователю наблюдать операции репликации в мониторе репликации. Однако такой пользователь не может управлять репликацией.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах содержатся сведения о возможностях монитора репликации.  
  
 [Обзор интерфейса монитора репликации](../../../relational-databases/replication/monitor/overview-of-the-replication-monitor-interface.md)  
 Описываются все окна и вкладки в мониторе репликации, и предоставляются сведения, позволяющие ответить на приведенные выше вопросы.  
  
 [Запуск монитора репликации](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)  
 Описывается запуск монитора репликации.  
  
 [Предоставление пользователям без прав администратора разрешений на использование монитора репликации](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
 Описывается выдача разрешений пользователю без прав администратора на использование монитора репликации.  
  
 [Добавление и удаление издателей в мониторе репликации](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)  
 Описывается добавление или удаление издателей из монитора репликации.  
  
 [Обновление данных в мониторе репликации](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md)  
 Описывается обновление данных в мониторе репликации.  
  
 [Наблюдение за производительностью с помощью монитора репликации](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
 Описывается способ наблюдения за производительностью в мониторе репликации, включая сведения об установке порогов производительности. Содержатся сведения о статистике уровня статьи по репликации слиянием, позволяющие получить подробное представление об обработке.  
  
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
 Описываются трассировочные токены, которые позволяют измерять производительность для топологии репликации транзакций.  
  
 [Наблюдение за агентами репликации](../../../relational-databases/replication/monitor/monitor-replication-agents.md)  
 Описываются способы поиска сведений о каждом агенте репликации.  
  
 [Настройка пороговых значений и предупреждений в мониторе репликации](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
 Описываются предупреждения, пороги и оповещения, которые можно установить в мониторе репликации. Рекомендуется включить предупреждения для используемой топологии, чтобы своевременно получать сведения о состоянии и производительности репликации.  
  
 [Кэширование, обновление и производительность монитора репликации](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)  
 Описываются кэширование данных монитором репликации и вычисления для повышения производительности. Объясняется связь обновления интерфейса пользователя с обновлением кэша.  
  
 [Просмотр состояний публикаций и подписок в мониторе репликации](../../../relational-databases/replication/monitor/view-publication-and-subscription-status-in-replication-monitor.md)  
 Описывается просмотр сведений о состоянии публикации или подписки с помощью монитора репликации.  
  
 [Просмотр сведений и выполнение задач для издателя (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 Описывается просмотр сведений и выполнение задач для издателя с помощью монитора репликации.  
  
 [Просмотр сведений и выполнение задач для публикации (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 Описывается просмотр сведений и выполнение задач для публикации с помощью монитора репликации.  
  
 [Просмотр сведений и выполнение задач для агентов, связанных с публикацией (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)  
 Описывается просмотр сведений и выполнение задач для агентов, связанных с публикацией, с помощью монитора репликации.  
  
 [Просмотр сведений и выполнение задач для подписки (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 Описывается просмотр сведений и выполнение задач для подписки с помощью монитора репликации.  
  
 [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)  
 Описывается просмотр сведений и выполнение задач для агентов, связанных с подпиской, с помощью монитора репликации.  
  
  
