---
title: Просмотр сведений и выполнение задач для подписки (монитор репликации) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], viewing information
- subscriptions [SQL Server replication], Replication Monitor tasks
- viewing subscription information
ms.assetid: 54aac83b-6f29-40d7-8901-cf059749867f
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 92c405a4a6999db94a5c51a92f0914d5168d4672
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="view-information-and-perform-tasks-for-a-subscription-replication-monitor"></a>Просмотр сведений и выполнение задач для подписки (монитор репликации)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор репликации содержит следующие вкладки, на которых отображаются сведения о подписках:  
  
-   **Все подписки**  
  
     На этой вкладке отображаются сведения о всех подписках на выбранную публикацию.  
  
-   **Список наблюдения за подписками**  
  
     Эта вкладка предназначена для отображения сведений о подписках из всех публикаций, доступных на выбранном издателе, для которых имеются ошибки, предупреждения или наихудшие показатели производительности. Эта вкладка не отображается для запущенных версий распространителей, предшествующих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Чтобы перейти к дополнительным сведениям о параметрах на каждой вкладке, щелкните вкладку на правой панели, а затем нажмите **Справка** в строке меню. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-all-subscriptions-tab"></a>Просмотр сведений и выполнение задач для подписок на вкладке «Все подписки»  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Для просмотра сведений о подписках щелкните вкладку **Все подписки** . Для просмотра только подписок, находящихся в заданном состоянии, например синхронизирующихся, выберите параметр из раскрывающегося списка **Показать** .  
  
3.  Для просмотра и изменения свойств подписки щелкните подписку правой кнопкой мыши, затем щелкните **Свойства**. На этой вкладке можно также просмотреть другие подробные сведения и выполнить дополнительные задачи. Дополнительные сведения см. в статье [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-subscription-watch-list-tab"></a>Просмотр данных и выполнение задач для подписок на вкладке «Список наблюдения за подписками»  
  
1.  Раскройте группу издателей на левой панели, затем щелкните издателя.  
  
2.  Чтобы просмотреть сведения о подписках, перейдите на вкладку **Список наблюдения за подписками** .  
  
3.  Выберите тип подписки для отображения из раскрывающегося списка **Показать подписки \<тип_подписки>**. Для просмотра только подписок, находящихся в заданном состоянии, например синхронизирующихся, выберите параметр из раскрывающегося списка **Показать** .  
  
4.  Для просмотра и изменения свойств подписки щелкните подписку правой кнопкой мыши, затем щелкните **Свойства**. На этой вкладке можно также просмотреть другие подробные сведения и выполнить дополнительные задачи. Дополнительные сведения см. в статье [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств принудительной подписки](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Просмотр и изменение свойств подписки по запросу](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
