---
title: "Наблюдение (репликация) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "мониторинг производительности [репликация SQL Server], о мониторинге производительности"
  - "репликация транзакций, мониторинг"
  - "наблюдение [репликация SQL Server]"
  - "наблюдение за репликацией слиянием [репликация SQL Server]"
  - "репликация моментального снимка [SQL Server], мониторинг"
  - "репликация [SQL Server], мониторинг"
  - "администрирование репликации, мониторинг"
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Наблюдение (репликация)
  Наблюдение за топологией репликации является важным аспектом развертывания репликации. Так как активность репликации является распределенной, важно отслеживать активность и состояние всех компьютеров, участвующих в репликации. Для наблюдения за репликацией можно использовать следующие средства:  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] монитор репликации  
  
     Монитор репликации является самым важным средством наблюдения за репликацией, представляющим ориентированное на издателя представление всех действий, связанных с репликацией. Дополнительные сведения см. в статье [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] предоставляет доступ к монитору репликации. Здесь тоже существует возможность просмотра текущего состояния и последнего сообщения, записанного в журнал следующими агентами, и можно запускать и останавливать все агенты: агент чтения журнала, агент моментальных снимков, агент слияния и агент распространителя. Дополнительные сведения см. в статье [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] и объекты управления репликацией (RMO)  
  
     Оба интерфейса позволяют наблюдать с распространителя за репликациями всех типов. Репликация слиянием также предоставляет возможность наблюдения за репликацией с подписчика.  
  
-   Предупреждения для событий агентов репликации  
  
     Репликации предоставляют ряд предопределенных предупреждений о событиях агентов репликаций. Кроме этого, в случае необходимости можно создать дополнительные предупреждения. Предупреждения используются для запуска автоматического ответа на событие и для уведомления администратора. Дополнительные сведения см. в разделе [использование оповещений о событиях агентов репликаций](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   Системный монитор  
  
     Системный монитор может использоваться для наблюдения за производительностью, предоставляя ряд счетчиков для репликаций. Дополнительные сведения см. в статье [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  
## См. также:  
 [Администрирование и #40; Репликация & #41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Рекомендации по администрированию репликации](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  