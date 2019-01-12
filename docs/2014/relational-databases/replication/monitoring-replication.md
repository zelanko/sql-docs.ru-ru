---
title: Наблюдение за репликацией | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: e2b3441d98bc9226abce3a49fd28820df6ec99ab
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54134304"
---
# <a name="monitoring-replication"></a>Наблюдение (репликация)
  Наблюдение за топологией репликации является важным аспектом развертывания репликации. Так как активность репликации является распределенной, важно отслеживать активность и состояние всех компьютеров, участвующих в репликации. Для наблюдения за репликацией можно использовать следующие средства:  
  
-   Монитор репликации[!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]   
  
     Монитор репликации является самым важным средством наблюдения за репликацией, представляющим ориентированное на издателя представление всех действий, связанных с репликацией. Дополнительные сведения см. в разделе [мониторинг производительности с помощью монитора репликации](monitor/monitor-performance-with-replication-monitor.md).  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]  
  
     Среда[!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] предоставляет доступ к монитору репликации. Здесь же существует возможность просмотра текущего состояния и последнего сообщения, записанного в журнал следующими агентами, а так же здесь можно запускать и останавливать все агенты: агент чтения журнала, агент моментальных снимков и агент распространителя. Дополнительные сведения см. в статье [Monitor Replication Agents](monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] и объекты управления репликацией (RMO)  
  
     Оба интерфейса позволяют наблюдать с распространителя за репликациями всех типов. Репликация слиянием также предоставляет возможность наблюдения за репликацией с подписчика.  
  
-   Предупреждения для событий агентов репликации  
  
     Репликации предоставляют ряд предопределенных предупреждений о событиях агентов репликаций. Кроме этого, в случае необходимости можно создать дополнительные предупреждения. Предупреждения используются для запуска автоматического ответа на событие и для уведомления администратора. Дополнительные сведения см. в статье [Использование предупреждений для событий агента репликации](agents/use-alerts-for-replication-agent-events.md).  
  
-   Системный монитор  
  
     Системный монитор может использоваться для наблюдения за производительностью, предоставляя ряд счетчиков для репликаций. Дополнительные сведения см. в статье [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>См. также  
 [Администрирование репликации часто задаваемые вопросы](administration/frequently-asked-questions-for-replication-administrators.md)   
 [Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md)   

  
  
