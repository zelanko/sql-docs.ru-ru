---
title: Синхронизация подписки по запросу | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8a7a607221599d599438352eab5add1cc94e5d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186231"
---
# <a name="synchronize-a-pull-subscription"></a>Синхронизация подписки по запросу
  В данном разделе описывается синхронизация подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [агентов репликации](agents/replication-agents-overview.md)или объектов RMO.  
  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Подписки синхронизируются агентом распространителя (для репликации моментальных снимков и репликации транзакций) или агентом слияния (для репликации слиянием). Агенты могут работать непрерывно, запускаться по запросу или по расписанию. Дополнительные сведения о настройке расписаний синхронизации см. в [этой статье](specify-synchronization-schedules.md).  
  
 Синхронизируйте подписку по запросу из папки **Локальные подписки** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a>Синхронизация по запросу подписки по запросу в среде Management Studio  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните подписку правой кнопкой мыши и выберите **Просмотреть состояние синхронизации**.  
  
4.  В диалоговом окне **Просмотр состояния синхронизации — \<подписчик>:\<база_данных_подписки>** нажмите кнопку **Запустить**. Когда синхронизация будет завершена, появится сообщение **Синхронизация завершена** .  
  
5.  Щелкните **Закрыть**.  
  
##  <a name="ReplProg"></a> Replication Agents  
 Подписки по запросу могут синхронизироваться программно и по требованию, с помощью вызова из командной строки нужного исполняемого файла агента репликации. Вызываемый исполняемый файл агента репликации зависит от типа публикации, к которой принадлежит подписка по запросу. Дополнительные сведения см. в разделе [Replication Agents](agents/replication-agents-overview.md).  
  
> [!NOTE]  
>  Агенты репликации подключаются к локальному серверу, используя учетные данные проверки подлинности Windows пользователя, запустившего агент из командной строки. Эти учетные данные Windows также применяются при соединении с удаленными серверами с использованием встроенной проверки подлинности Windows.  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a>Запуск агента распространителя из командной строки или из пакетного файла  
  
1.  Из командной строки или из пакетного файла запустите [агент распространения репликации](agents/replication-distribution-agent.md) , вызвав программу **distrib.exe**со следующими параметрами командной строки.  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Distributor**  
  
    -   **-DistributorSecurityMode** = **1**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriberSecurityMode** = **1**  
  
    -   **-SubscriptionType** = **1**  
  
     При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо также указать следующие аргументы.  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode** = **0**  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a>Запуск агента слияния из командной строки или из пакетного файла  
  
1.  Из командной строки или из пакетного файла запустите [агент слияния репликации](agents/replication-merge-agent.md) , вызвав программу **replmerg.exe**со следующими параметрами командной строки.  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-PublisherSecurityMode** = **1**  
  
    -   **-Publication**  
  
    -   **-Distributor**  
  
    -   **-DistributorSecurityMode** = **1**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberSecurityMode** = **1**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType** = **1**  
  
     При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо также указать следующие аргументы.  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Примеры (агенты репликации)  
 В следующем примере запускается агент распространителя для синхронизации подписки по запросу. Все соединения устанавливаются с использованием проверки подлинности Windows.  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 В следующем примере запускается агент слияния для синхронизации подписки по запросу. Все соединения устанавливаются с использованием проверки подлинности Windows.  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Подписки по запросу можно синхронизировать программно с помощью объектов RMO и доступа к функциональности агента репликации из управляемого кода. Конкретные классы, используемые для синхронизации, зависят от типа публикации, к которой принадлежит подписка.  
  
> [!NOTE]  
>  Если нужно выполнить синхронизацию, которая выполняется автономно и не влияет на ваше приложение, запустите агент асинхронно. Однако если нужно наблюдать за результатами синхронизации и получать обратные вызовы от агента во время процесса синхронизации (например, если нужно отображать индикатор выполнения), то следует запускать агент синхронно. Для подписчиков [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] также необходимо запускать агент синхронно.  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Синхронизация подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> и укажите следующие свойства:  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>;  
  
    -   имя публикации, к которой принадлежит подписка, в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>;  
  
    -   Имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   имя издателя в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>;  
  
    -   соединение, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы получить остальные свойства подписки. Если этот метод возвращает значение `false`, проверьте, существует ли подписка.  
  
4.  На распространителе запустите агент распространителя одним из следующих способов.  
  
    -   Вызовите метод <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> экземпляра класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> , созданного на шаге 2. Этот метод запускает агент распространителя асинхронно, а управление сразу после его вызова передается обратно приложению; задание агента при этом продолжает выполняться. Этот метод нельзя вызывать для подписчиков [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)], а так же в том случае, если подписка была создана со значением `false` свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (значение по умолчанию).  
  
    -   Получите экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> из свойства <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> и вызовите метод <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> . Этот метод запускает агент синхронно, и управление не возвращается приложению до тех пор, пока выполнение задания агента не будет завершено. При синхронном выполнении в процессе работы агента можно обрабатывать событие <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> .  
  
        > [!NOTE]  
        >  Если указано значение `false` для <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (по умолчанию) при создании подписки по запросу, необходимо также указать <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>и при необходимости <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> и <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> так, как задание агента, связанных с метаданные для этой подписки недоступна в [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a>Синхронизация подписки по запросу на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> и укажите следующие свойства:  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>;  
  
    -   имя публикации, к которой принадлежит подписка, в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>;  
  
    -   имя опубликованной базы данных в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>;  
  
    -   имя издателя в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>;  
  
    -   соединение, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы получить остальные свойства подписки. Если этот метод возвращает значение `false`, проверьте, существует ли подписка.  
  
4.  На подписчике запустите агент слияния одним из следующих способов:.  
  
    -   Вызовите метод <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> экземпляра класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> , созданного на шаге 2. Этот метод запускает агент слияния асинхронно, а управление сразу после его вызова передается обратно приложению, задание агента при этом продолжает выполняться. Этот метод нельзя вызывать для подписчиков [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)], а так же в том случае, если подписка была создана со значением `false` свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (значение по умолчанию).  
  
    -   Получите экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> из свойства <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> и вызовите метод <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> . Этот метод запускает агент слияния синхронно, и управление не возвращается приложению до тех пор, пока не будет закончено выполнение задания агента. При синхронном выполнении в процессе работы агента можно обрабатывать событие <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> .  
  
        > [!NOTE]  
        >  Если указано значение `false` для <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (по умолчанию) при создании подписки по запросу, необходимо также указать <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>, и При необходимости <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, и <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> так, как заданию агента, связанные с ними метаданные подписки недоступна в [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере синхронизируется подписка по запросу на публикацию транзакций, в которой агент запускается асинхронно через задание агента.  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 В следующем примере синхронизируется подписка по запросу на публикацию транзакций, в которой агент запускается синхронно.  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 В следующем примере синхронизируется подписка по запросу на публикацию слиянием, в которой агент запускается асинхронно через задание агента.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 В следующем примере синхронизируется подписка по запросу на публикацию слиянием, в которой агент запускается синхронно.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 В следующем примере синхронизируется подписка по запросу на публикацию слиянием с использованием веб-синхронизации. Данная подписка создается без задания агента и соответствующих метаданных подписки, поэтому агент должен быть запущен синхронно с указанием дополнительных сведений о подписке.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a>См. также  
 [Синхронизация данных](synchronize-data.md)   
 [Создание подписки по запросу](create-a-pull-subscription.md)   
 [Рекомендации по защите репликации](security/replication-security-best-practices.md)  
  
  
