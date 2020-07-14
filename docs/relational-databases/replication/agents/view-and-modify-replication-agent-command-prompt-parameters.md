---
title: Просмотр и изменение параметров командной строки агента
description: Узнайте, как просматривать и изменять параметры командной строки, используемые различными агентами репликации в SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 10ef5b2c2e873d3f17085137134aabd8db57b059
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893795"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters"></a>Просмотр и изменение параметров командной строки агента репликации
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Агенты репликации — это исполняемые файлы, принимающие параметры командной строки. По умолчанию агенты выполняются при выполнении шагов заданий агента [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], поэтому данные параметры можно просматривать и изменять с помощью диалогового окна **Свойства задания — \<Job>** . Доступ к этому диалоговому окну можно получить из папки **Задания** в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и на вкладке **Агенты** монитора репликации. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Изменения параметров агента вступают в действие при следующем запуске агента. Если агент выполняется в непрерывном режиме, следует остановить и перезапустить агент.  
  
 Хотя параметры можно изменять непосредственно, чаще всего их изменяют через профиль агента. Дополнительные сведения см. в статье [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 При доступе к заданиям агента из папки **Задания** для определения имени задания и параметров, доступных для каждого агента, воспользуйтесь следующей таблицей.  
  
|Агент|Имя задания|Для просмотра списка параметров см...|  
|-----------|--------------|------------------------------------|  
|агент моментальных снимков|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|[Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|Агент моментальных снимков для секции публикации слиянием|**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**|[Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|Агент чтения журнала.|**\<Publisher>-\<PublicationDatabase>-\<integer>**|[Агент чтения журнала репликации](../../../relational-databases/replication/agents/replication-log-reader-agent.md)|  
|Агент слияния для подписок по запросу|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|[Replication Merge Agent](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|Агент слияния для принудительных подписок|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[Replication Merge Agent](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|Агент распространителя для принудительных подписок|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[Replication Distribution Agent](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Агент распространителя для подписок по запросу|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>**|[Replication Distribution Agent](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Агент распространителя для принудительных подписок подписчиков серверов, отличных от подписчиков SQL Server|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[Replication Distribution Agent](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Агент чтения очереди.|**[\<Distributor>].\<integer>**|[Replication Queue Reader Agent](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)|  
  
 \*Для принудительных подписок на публикации Oracle это **\<Publisher>-\<Publisher**>, а не **\<Publisher>-\<PublicationDatabase>**  
  
 \*\*Для подписок по запросу на публикации Oracle это **\<Publisher>-\<DistributionDatabase**>, а не **\<Publisher>-\<PublicationDatabase>**  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a>Просмотр и изменение параметров командной строки агента репликации из среды Management Studio  
  
1.  Подключитесь к соответствующему компьютеру в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера:  
  
    -   В случае использования агента распространителя и агента слияния для подписок по запросу подключитесь к подписчику.  
  
    -   Для всех иных агентов подключитесь к распространителю.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Правой кнопкой мыши щелкните задание и выберите **Свойства**.  
  
4.  На странице **Шаги** диалогового окна **Свойства задания — \<Job>** выберите действие **Запустить агент**, а затем нажмите кнопку **Изменить**.  
  
5.  В диалоговом окне **Свойства шага задания — запустить агент** отредактировать поле **Команда** .  
  
6.  Нажмите кнопку **OK** в обоих диалоговых окнах.  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a>Просмотр и изменение параметров командной строки агента распространителя и агента слияния из монитора репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, а затем выберите **Просмотреть сведения**.  
  
4.  В окне **Подписка <имя_подписки>** нажмите кнопку **Действие**, а затем щелкните **Свойства задания \<AgentName>** .  
  
5.  На странице **Шаги** диалогового окна **Свойства задания — \<Job>** выберите действие **Запустить агент**, а затем нажмите кнопку **Изменить**.  
  
6.  В диалоговом окне **Свойства шага задания — запустить агент** отредактировать поле **Команда** .  
  
7.  Нажмите кнопку **OK** в обоих диалоговых окнах.  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a>Просмотр и изменение параметров командной строки агента моментальных снимков, агента чтения журнала и агента чтения очереди из монитора репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Агенты** .  
  
3.  Щелкните правой кнопкой мыши агент в сетке, а затем щелкните **Свойства**.  
  
4.  На странице **Шаги** диалогового окна **Свойства задания — \<Job>** выберите действие **Запустить агент**, а затем нажмите кнопку **Изменить**.  
  
5.  В диалоговом окне **Свойства шага задания — запустить агент** отредактировать поле **Команда** .  
  
6.  Нажмите кнопку **OK** в обоих диалоговых окнах.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование агента репликации](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Replication Agents Overview](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
