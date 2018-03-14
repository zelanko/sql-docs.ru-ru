---
title: "Просмотр сведений и выполнение задач для агентов публикации | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c55ab9ebc0b393375a552acc26f01018b7c1e23e
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="view-information-and-perform-tasks-for-publication-agents"></a>Просмотр информации и выполнение задач для агентов публикации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор репликации содержит вкладку **Агенты** , на которой приведены сведения об агентах, связанных с выбранной публикацией. Агент распределения и агент слияния ассоциированы с подписками. Дополнительные сведения о них вы найдете в статье [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
 На этой вкладке отображаются сведения о следующих агентах:  
  
-   Агент моментальных снимков, используемый всеми публикациями.  
  
-   Агент чтения журналов, используемый всеми публикациями транзакций.  
  
-   Агент чтения очереди, используемый публикациями транзакций, активированными для подписок, обновляемых посредством очередей.  
  
 Чтобы просмотреть дополнительные сведения о параметрах, доступных на этой вкладке, выберите пункт **Справка** в главном меню. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-publication"></a>Просмотр сведений и выполнение задач для агентов, связанных с публикацией  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Перейдите на вкладку **Агенты** для просмотра сведений об агентах. На этой вкладке можно также просмотреть другие подробные сведения и выполнить дополнительные задачи.  
  
    -   Чтобы просмотреть подробные сведения об агенте (например, информационные сообщения и возможные сообщения об ошибках), щелкните правой кнопкой мыши агент, а затем щелкните **Просмотреть сведения**.  
  
    -   Чтобы просмотреть подробные сведения о задании, запустившем агента (например, расписание, описание шагов задания и т. п.), щелкните правой кнопкой мыши агент, а затем щелкните **Свойства**.  
  
    -   Чтобы управлять профилями агентов, щелкните правой кнопкой мыши агент, затем выберите **Профиль агента**. Дополнительные сведения см. в статье [Работа с профилями агента репликации](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Чтобы запустить агент, который еще не запущен, щелкните правой кнопкой мыши этот агент, а затем щелкните **Запустить агент**.  
  
    -   Чтобы остановить агент, который запущен, щелкните правой кнопкой мыши этот агент, а затем щелкните **Остановить агент**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка пороговых значений и предупреждений в мониторе репликации](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для публикации (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Администрирование агента репликации](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
