---
title: "Синхронизация принудительной подписки | Microsoft Docs"
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
  - "синхронизация [репликация SQL Server], принудительные подписки"
  - "принудительные подписки [репликация SQL Server], отправка"
  - "принудительные подписки [репликация SQL Server], синхронизация"
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Синхронизация принудительной подписки
  В этом разделе описывается синхронизация принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [агенты репликации](../../relational-databases/replication/agents/replication-agents-overview.md), или объекты управления репликацией (RMO).  
  
 **В этом разделе**  
  
-   **Для синхронизации принудительной подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Агенты репликации](#ReplProg)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Подписки синхронизируются агентом распространителя (для репликации моментальных снимков и репликации транзакций) или агентом слияния (для репликации слиянием). Агенты могут работать непрерывно, запускаться по запросу или по расписанию. Дополнительные сведения об указании расписаний синхронизации см. в разделе [Укажите расписания синхронизации](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
 Синхронизируйте подписки по запросу из папок **Локальные публикации** и **Локальные подписки** в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и the **Все подписки** в мониторе репликации. Подписки на публикации Oracle не синхронизируются по запросу подписчика. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Синхронизация принудительной подписки по запросу в среде Management Studio (на издателе)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Разверните публикацию, для которой хотите выполнить синхронизацию подписок.  
  
4.  Щелкните правой кнопкой мыши подписку, которую нужно синхронизировать затем нажмите кнопку **Просмотр состояния синхронизации**.  
  
5.  В **Просмотр состояния синхронизации — \< подписчик>: \< база данных подписки>** диалоговом нажмите кнопку **запустить**. Когда синхронизация будет завершена, появится сообщение **Синхронизация завершена** .  
  
6.  Щелкните **Закрыть**.  
  
#### Синхронизация принудительной подписки по запросу в среде Management Studio (на подписчике)  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую нужно синхронизировать затем нажмите кнопку **Просмотр состояния синхронизации**.  
  
4.  Появится сообщение об установке соединения с распространителем. Нажмите кнопку **ОК**.  
  
5.  В **Просмотр состояния синхронизации — \< подписчик>: \< база данных подписки>** диалоговом нажмите кнопку **запустить**. Когда синхронизация будет завершена, появится сообщение **Синхронизация завершена** .  
  
6.  Щелкните **Закрыть**.  
  
#### Синхронизация принудительной подписки по запросу в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, раскройте нужного издателя, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую нужно синхронизировать затем нажмите кнопку **запустить синхронизацию**.  
  
4.  Чтобы просмотреть ход выполнения синхронизации, щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр сведений о**.  
  
##  <a name="ReplProg"></a> При помощи агентов репликации  
 Принудительные подписки можно синхронизировать программно и по требованию, с помощью вызова из командной строки нужного исполняемого файла агента репликации. Вызываемый исполняемый файл агента репликации зависит от типа публикации, к которой принадлежит принудительная подписка.  
  
#### Запуск агента распространителя для синхронизации принудительной подписки на публикацию транзакций  
  
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
  
#### Запуск агента слияния для синхронизации принудительной подписки на публикацию слиянием  
  
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
  
###  <a name="TsqlExample"></a> Примеры (агенты репликации)  
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
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Принудительные подписки можно синхронизировать программно с помощью объектов RMO и доступа к функциональности агента репликации из управляемого кода. Конкретные классы, используемые для синхронизации, зависят от типа публикации, к которой принадлежит подписка.  
  
> [!NOTE]  
>  Если нужно выполнить синхронизацию, которая выполняется автономно и не влияет на ваше приложение, запустите агент асинхронно. Однако если нужно наблюдать за результатами синхронизации и получать обратные вызовы от агента во время процесса синхронизации (например, если нужно отображать индикатор выполнения), то следует запускать агент синхронно. Для подписчиков [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] также необходимо запускать агент синхронно.  
  
#### Синхронизация принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransSubscription> класса и задайте следующие свойства:  
  
    -   Имя базы данных публикации для <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Имя публикации, к которой принадлежит подписка для <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Имя базы данных подписки для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Имя подписчика для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Соединение, созданное на шаге 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить оставшиеся свойства подписки. Если этот метод возвращает значение **false**, проверьте, существует ли подписка.  
  
4.  На распространителе запустите агент распространителя одним из следующих способов.  
  
    -   Вызов <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> метод экземпляра <xref:Microsoft.SqlServer.Replication.TransSubscription> из шага 2. Этот метод запускает агент распространителя асинхронно, а управление сразу после его вызова передается обратно приложению; задание агента при этом продолжает выполняться. Этот метод нельзя вызывать, если подписка была создана со значением **false** для <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.  
  
    -   Получить экземпляр <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> класса <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> свойство и вызвать <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> метод. Этот метод запускает агент синхронно, и управление не возвращается приложению до тех пор, пока выполнение задания агента не будет завершено. Во время выполнения синхронной обработки <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> событий во время выполнения агента.  
  
#### Синхронизация принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscription> класса и задайте следующие свойства:  
  
    -   Имя базы данных публикации для <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Имя публикации, к которой принадлежит подписка для <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Имя базы данных подписки для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Имя подписчика для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Соединение, созданное на шаге 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить оставшиеся свойства подписки. Если этот метод возвращает значение **false**, проверьте, существует ли подписка.  
  
4.  На распространителе запустите агент слияния одним из следующих способов:.  
  
    -   Вызов <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> метод экземпляра <xref:Microsoft.SqlServer.Replication.MergeSubscription> из шага 2. Этот метод запускает агент слияния асинхронно, а управление сразу после его вызова передается обратно приложению, задание агента при этом продолжает выполняться. Этот метод нельзя вызывать, если подписка была создана со значением **false** для <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.  
  
    -   Получить экземпляр <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> класса <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> свойство и вызвать <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> метод. Этот метод запускает агент слияния синхронно, и управление не возвращается приложению до тех пор, пока не будет закончено выполнение задания агента. Во время синхронного выполнения можно обрабатывать <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> событий во время выполнения агента.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере синхронизируется принудительная подписка на публикацию транзакций, в которой агент запускается асинхронно через задание агента.  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 В следующем примере синхронизируется принудительная подписка на публикацию транзакций, в которой агент запускается синхронно.  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 В следующем примере синхронизируется принудительная подписка на публикацию слиянием, в которой агент запускается асинхронно через задание агента.  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 В следующем примере синхронизируется принудительная подписка на публикацию слиянием, в которой агент запускается синхронно.  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## См. также:  
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  