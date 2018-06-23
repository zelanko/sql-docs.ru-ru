---
title: Наблюдение за репликацией | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
caps.latest.revision: 38
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7434a211de780ab5a363aeec97b8914bb587f5a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095437"
---
# <a name="monitoring-replication"></a>Наблюдение (репликация)
  Наблюдение за топологией репликации является важным аспектом развертывания репликации. Так как активность репликации является распределенной, важно отслеживать активность и состояние всех компьютеров, участвующих в репликации. Для наблюдения за репликацией можно использовать следующие средства:  
  
-   Монитор репликации[!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]   
  
     Монитор репликации является самым важным средством наблюдения за репликацией, представляющим ориентированное на издателя представление всех действий, связанных с репликацией. Дополнительные сведения см. в разделе [монитор репликации](monitor/monitoring-replication-overview.md).  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]  
  
     Среда[!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] предоставляет доступ к монитору репликации. Здесь тоже существует возможность просмотра текущего состояния и последнего сообщения, записанного в журнал следующими агентами, и можно запускать и останавливать все агенты: агент чтения журнала, агент моментальных снимков, агент слияния и агент распространителя. Дополнительные сведения см. в статье [Monitor Replication Agents](agents/replication-agents.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] и объекты управления репликацией (RMO)  
  
     Оба интерфейса позволяют наблюдать с распространителя за репликациями всех типов. Репликация слиянием также предоставляет возможность наблюдения за репликацией с подписчика.  
  
-   Предупреждения для событий агентов репликации  
  
     Репликации предоставляют ряд предопределенных предупреждений о событиях агентов репликаций. Кроме этого, в случае необходимости можно создать дополнительные предупреждения. Предупреждения используются для запуска автоматического ответа на событие и для уведомления администратора. Дополнительные сведения см. в статье [Использование предупреждений для событий агента репликации](agents/use-alerts-for-replication-agent-events.md).  
  
-   Системный монитор  
  
     Системный монитор может использоваться для наблюдения за производительностью, предоставляя ряд счетчиков для репликаций. Дополнительные сведения см. в статье [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>См. также  
 [Администрирование (репликация)](administration/administration-replication.md)   
 [Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md)   
 [Отслеживание репликации](monitor/monitoring-replication-overview.md)  
  
  