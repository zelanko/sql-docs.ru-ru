---
title: Наблюдение за репликацией | Документация Майкрософт
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
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
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f58fb09416bb6cc800c31dffa47e359d361ccaf7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082974"
---
# <a name="monitoring-replication"></a>Наблюдение (репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Наблюдение за топологией репликации является важным аспектом развертывания репликации. Так как активность репликации является распределенной, важно отслеживать активность и состояние всех компьютеров, участвующих в репликации. С помощью различных средств мониторинга можно ответить на такие распространенные вопросы, как: 

-   Исправна ли система репликации?
-   Какие подписки медленные?
-   Насколько запаздывает подписка на публикацию транзакций?
-   Сколько времени понадобится, чтобы только что зафиксированная транзакция была получена подписчиком в репликации транзакций?
-   Почему подписка на публикацию слиянием медленная?
-   Почему агент не запущен?  
  

Для наблюдения за репликацией можно использовать следующие средства:  
  
-   **Монитор репликации SQL Server** является самым важным средством для мониторинга репликации, представляющим ориентированное на издателя представление всех действий, связанных с репликацией. Дополнительные сведения см. в разделе [Monitoring Replication](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md). 
-   **SQL Server Management Studio** предоставляет доступ к монитору репликации Здесь же существует возможность просмотра текущего состояния и последнего сообщения, записанного в журнал следующими агентами, а также здесь можно запускать и останавливать все агенты: агент чтения журнала, агент моментальных снимков, агент слияния и агент распространения. Дополнительные сведения см. в статье [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   **Transact-SQL (T-SQL) и объекты Replication Management Objects (RMO)** — оба интерфейса позволяют наблюдать с распространителя за репликациями всех типов. Репликация слиянием также предоставляет возможность наблюдения за репликацией с подписчика.  
  
-   **Предупреждения для событий агентов репликации** — репликация предоставляет ряд предопределенных предупреждений о событиях агентов репликаций. Кроме этого, в случае необходимости можно создать дополнительные предупреждения. Предупреждения используются для запуска автоматического ответа на событие и для уведомления администратора. Дополнительные сведения см. в статье [Использование предупреждений для событий агента репликации](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   **Системный монитор** — может использоваться для наблюдения за производительностью, предоставляя ряд счетчиков для репликации. Дополнительные сведения см. в статье [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  

## <a name="see-also"></a>См. также:  
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   

  
  
