---
title: Синхронизация принудительной подписки | Документация Майкрософт
description: Узнайте, как синхронизировать принудительную подписку в SQL Server с помощью SQL Server Management Studio, агентов репликации или объектов Replication Management Objects.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], synchronizing
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 67434f137137a443dc0ef7e8708f8d7f37811abd
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921422"
---
# <a name="synchronize-a-push-subscription"></a>Синхронизация принудительной подписки
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  В данном разделе описывается синхронизация принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)или объектов RMO.  
  
[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Подписки синхронизируются агентом распространителя (для репликации моментальных снимков и репликации транзакций) или агентом слияния (для репликации слиянием). Агенты могут работать непрерывно, запускаться по запросу или по расписанию. Дополнительные сведения о настройке расписаний синхронизации см. в [этой статье](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
 Синхронизируйте подписки по запросу из папок **Локальные публикации** и **Локальные подписки** в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и **Все подписки** в мониторе репликации. Подписки на публикации Oracle не синхронизируются по запросу подписчика. Сведения о запуске монитора репликации см. в [этой статье](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-publisher"></a>Синхронизация принудительной подписки по запросу в среде Management Studio (на издателе)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Разверните публикацию, для которой хотите выполнить синхронизацию подписок.  
  
4.  Щелкните подписку правой кнопкой мыши и выберите **Просмотреть состояние синхронизации**.  
  
5.  В диалоговом окне **Просмотр состояния синхронизации — \<Subscriber>:\<SubscriptionDatabase>** нажмите кнопку **Пуск**. Когда синхронизация будет завершена, появится сообщение **Синхронизация завершена** .  
  
6.  Щелкните **Закрыть**.  

#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-subscriber"></a>Синхронизация принудительной подписки по запросу в среде Management Studio (на подписчике)  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните подписку правой кнопкой мыши и выберите **Просмотреть состояние синхронизации**.  
  
4.  Появится сообщение об установке соединения с распространителем. Нажмите кнопку **ОК**.  
  
5.  В диалоговом окне **Просмотр состояния синхронизации — \<Subscriber>:\<SubscriptionDatabase>** нажмите кнопку **Пуск**. Когда синхронизация будет завершена, появится сообщение **Синхронизация завершена** .  
  
6.  Щелкните **Закрыть**.  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-replication-monitor"></a>Синхронизация принудительной подписки по запросу в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, раскройте нужного издателя, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую хотите синхронизировать, а затем щелкните **Запустить синхронизацию**.  
  
4.  Чтобы просмотреть ход выполнения синхронизации, щелкните правой кнопкой мыши подписку, а затем щелкните **Просмотреть подробности**.  
  
##  <a name="using-replication-agents"></a><a name="ReplProg"></a> При помощи агентов репликации  
 Принудительные подписки можно синхронизировать программно и по требованию, с помощью вызова из командной строки нужного исполняемого файла агента репликации. Вызываемый исполняемый файл агента репликации зависит от типа публикации, к которой принадлежит принудительная подписка.  
  
#### <a name="to-start-the-distribution-agent-to-synchronize-a-push-subscription-to-a-transactional-publication"></a>Запуск агента распространителя для синхронизации принудительной подписки на публикацию транзакций  
  
1.  Выполните программу **distrib.exe**из командной строки или из пакетного файла на распространителе. Укажите следующие аргументы командной строки.  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     При использовании проверки подлинности SQL Server необходимо также указать следующие аргументы.  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### <a name="to-start-the-merge-agent-to-synchronize-a-push-subscription-to-a-merge-publication"></a>Запуск агента слияния для синхронизации принудительной подписки на публикацию слиянием  
  
1.  Выполните программу **replmerg.exe**из командной строки или из пакетного файла на распространителе. Укажите следующие аргументы командной строки.  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Publication**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     При использовании проверки подлинности SQL Server необходимо также указать следующие аргументы.  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> Примеры (агенты репликации)  
 В следующем примере агент распространителя запускается для синхронизации принудительной подписки.  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4  
  
```  
  
 В следующем примере агент слияния запускается для синхронизации принудительной подписки.  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1  
  
```  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Принудительные подписки можно синхронизировать программно с помощью объектов RMO и доступа к функциональности агента репликации из управляемого кода. Конкретные классы, используемые для синхронизации, зависят от типа публикации, к которой принадлежит подписка.  
  
> [!NOTE]
>  Если нужно выполнить синхронизацию, которая выполняется автономно и не влияет на ваше приложение, запустите агент асинхронно. Однако если нужно наблюдать за результатами синхронизации и получать обратные вызовы от агента во время процесса синхронизации (например, если нужно отображать индикатор выполнения), то следует запускать агент синхронно. Для подписчиков [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] также необходимо запускать агент синхронно.  
  
#### <a name="to-synchronize-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Синхронизация принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSubscription> и укажите следующие свойства:  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>;  
  
    -   имя публикации, к которой принадлежит подписка, в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>;  
  
    -   имя подписчика в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>;  
  
    -   соединение, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы получить остальные свойства подписки. Если этот метод возвращает значение **false**, проверьте, существует ли подписка.  
  
4.  На распространителе запустите агент распространителя одним из следующих способов.  
  
    -   Вызовите метод <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> экземпляра класса <xref:Microsoft.SqlServer.Replication.TransSubscription> , созданного на шаге 2. Этот метод запускает агент распространителя асинхронно, а управление сразу после его вызова передается обратно приложению; задание агента при этом продолжает выполняться. Этот метод нельзя вызвать, если при создании подписки свойству **false** for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.  
  
    -   Получите экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> из свойства <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> и вызовите метод <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> . Этот метод запускает агент синхронно, и управление не возвращается приложению до тех пор, пока выполнение задания агента не будет завершено. При синхронном выполнении во время работы агента можно обрабатывать события <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> .  
  
#### <a name="to-synchronize-a-push-subscription-to-a-merge-publication"></a>Синхронизация принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscription> и укажите следующие свойства:  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>;  
  
    -   имя публикации, к которой принадлежит подписка, в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>;  
  
    -   имя подписчика в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>;  
  
    -   соединение, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы получить остальные свойства подписки. Если этот метод возвращает значение **false**, проверьте, существует ли подписка.  
  
4.  На распространителе запустите агент слияния одним из следующих способов:.  
  
    -   Вызовите метод <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> экземпляра класса <xref:Microsoft.SqlServer.Replication.MergeSubscription> , созданного на шаге 2. Этот метод запускает агент слияния асинхронно, а управление сразу после его вызова передается обратно приложению, задание агента при этом продолжает выполняться. Этот метод нельзя вызвать, если при создании подписки свойству **false** for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.  
  
    -   Получите экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> из свойства <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> и вызовите метод <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> . Этот метод запускает агент слияния синхронно, и управление не возвращается приложению до тех пор, пока не будет закончено выполнение задания агента. При синхронном выполнении в процессе работы агента можно обрабатывать событие <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> .  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере синхронизируется принудительная подписка на публикацию транзакций, в которой агент запускается асинхронно через задание агента.  
  
 [!code-cs[HowTo#rmo_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 В следующем примере синхронизируется принудительная подписка на публикацию транзакций, в которой агент запускается синхронно.  
  
 [!code-cs[HowTo#rmo_SyncTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 В следующем примере синхронизируется принудительная подписка на публикацию слиянием, в которой агент запускается асинхронно через задание агента.  
  
 [!code-cs[HowTo#rmo_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 В следующем примере синхронизируется принудительная подписка на публикацию слиянием, в которой агент запускается синхронно.  
  
 [!code-cs[HowTo#rmo_SyncMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## <a name="see-also"></a>См. также:  
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
