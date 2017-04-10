---
title: "Повторная инициализация подписки | Microsoft Docs"
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
  - "инициализация подписок [репликация SQL Server], повторная инициализация"
  - "подписки [репликация SQL Server], повторная инициализация"
  - "повторная инициализация подписок"
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Повторная инициализация подписки
  В данном разделе описывается повторная инициализация подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO. Отдельные подписки можно помечать для повторной инициализации, чтобы во время следующей синхронизации применялся новый моментальный снимок.  
  
 **В этом разделе**  
  
-   **Для повторной инициализации подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Повторная инициализация подписки — это процесс, состоящий из двух частей:  
  
1.  Одна или все подписки на публикацию *помечаются* для повторной инициализации. Подписки помечаются для повторной инициализации в **Повторная инициализация подписок** диалоговое окно доступно из **Локальные публикации** папки и **Локальные подписки** папки в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Все подписки можно также пометить на вкладке **Все подписки** и в узле публикаций монитора репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md). При пометке подписки для повторной инициализации доступны следующие параметры.  
  
     **Использовать текущий моментальный снимок**  
     Выберите, чтобы применить текущий моментальный снимок к подписчику при следующем запуске агента распространителя или агента слияния. Если допустимый моментальный снимок отсутствует, этот параметр выбрать нельзя.  
  
     **Использовать новый моментальный снимок**  
     Выберите, чтобы выполнить повторную инициализацию подписки с новым моментальным снимком. Этот моментальный снимок можно применять к подписчику только после того, как он был сформирован агентом моментальных снимков. Если агент моментальных снимков настроен на запуск по расписанию, подписка не инициализируется повторно до следующего запланированного запуска агента моментальных снимков. Выберите **Создать новый моментальный снимок** для немедленного запуска агента моментальных снимков.  
  
     **Передать несинхронизированные изменения перед повторной инициализацией**  
     Только репликация слиянием. Выберите, чтобы передать все ожидающие обработки изменения из базы данных подписки, прежде чем данные подписчика будут перезаписаны моментальным снимком.  
  
     Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
2.  Подписка повторно инициализируется при следующей синхронизации: агент распространителя (для репликации транзакций) или агент слияния (для репликации слиянием) применяет самый последний моментальный снимок к каждому подписчику, имеющему подписку, отмеченную для повторной инициализации. Дополнительные сведения о синхронизации подписок см. в разделе [синхронизации принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md) и [синхронизации подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Пометка для повторной инициализации одной принудительной подписки или подписки по запросу в Management Studio (на издателе)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, имеющую подписку, которую нужно повторно инициализировать.  
  
4.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **повторно инициализировать**.  
  
5.  В **Повторная инициализация подписок** диалоговом выберите параметры и нажмите кнопку **Пометить для повторной инициализации**.  
  
#### Пометка для повторной инициализации одной принудительной подписки в Management Studio (на подписчике)  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **повторно инициализировать**.  
  
4.  В появившемся окне подтверждения нажмите кнопку **Да**.  
  
#### Пометить для повторной инициализации все подписки в Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию с подписками, необходимо повторно инициализировать и нажмите кнопку **повторно инициализировать все подписки**.  
  
4.  В **Повторная инициализация подписок** диалоговом выберите параметры и нажмите кнопку **Пометить для повторной инициализации**.  
  
#### Пометка для повторной инициализации одной принудительной подписки или подписки по запросу в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, раскройте нужного издателя, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую нужно повторно инициализировать и нажмите кнопку **повторно инициализировать подписку**.  
  
4.  В **Повторная инициализация подписок** диалоговом выберите параметры и нажмите кнопку **Пометить для повторной инициализации**.  
  
#### Пометка для повторной инициализации всех подписок в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.  
  
2.  Щелкните правой кнопкой мыши публикацию с подписками, необходимо повторно инициализировать и нажмите кнопку **повторно инициализировать все подписки**.  
  
3.  В **Повторная инициализация подписок** диалоговом выберите параметры и нажмите кнопку **Пометить для повторной инициализации**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки можно повторно инициализировать программно с помощью хранимых процедур репликации. Используемая хранимая процедура зависит от типа подписки (принудительная или по запросу) и типа публикации, которой принадлежит подписка.  
  
#### Повторная инициализация подписки по запросу на публикацию транзакций  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_reinitpullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql.md). Укажите **@publisher**, **@publisher_db**, и **@publication**. В результате подписка будет помечена к повторной инициализации при следующем запуске агента распространителя.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент распространителя на подписчике. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Повторная инициализация принудительной подписки на публикацию транзакций  
  
1.  На издателе, хранимую [sp_reinitsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, и **@destination_db**. В результате подписка будет помечена к повторной инициализации при следующем запуске агента распространителя.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент распространителя на распространителе. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Повторная инициализация подписки по запросу на публикацию слиянием  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_reinitmergepullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md). Укажите **@publisher**, **@publisher_db**, и **@publication**. Чтобы передать изменения с подписчика перед повторной инициализацией, укажите значение **true** для **@upload_first**. Помечает подписку для повторной инициализации при следующем запуске агента слияния.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент слияния на подписчике. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Повторная инициализация принудительной подписки на публикацию слиянием  
  
1.  На издателе, хранимую [sp_reinitmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, и **@subscriber_db**. Чтобы передать изменения с подписчика перед повторной инициализацией, укажите значение **true** для **@upload_first**. В результате подписка будет помечена к повторной инициализации при следующем запуске агента распространителя.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент слияния на распространителе. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Установка политики повторной инициализации при создании публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), указав одно из следующих значений для **@automatic_reinitialization_policy**:  
  
    -   **1** -изменения передаются с подписчика перед автоматической повторной инициализации подписки, если это требуется изменения публикации.  
  
    -   **0** -изменения на подписчике удаляются, когда подписка повторно инициализируется автоматически, если это требуется изменения публикации.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
     Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Изменение политики повторной инициализации для существующей публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав **automatic_reinitialization_policy** для **@property** и одно из следующих значений для **@value**:  
  
    -   **1** -изменения передаются с подписчика перед автоматической повторной инициализации подписки, если это требуется изменения публикации.  
  
    -   **0** -изменения на подписчике удаляются, когда подписка повторно инициализируется автоматически, если это требуется изменения публикации.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
     Дополнительные сведения см. в статье [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Отдельные подписки можно помечать для повторной инициализации, чтобы во время следующей синхронизации применялся новый моментальный снимок. Подписки можно повторно инициализировать программно с помощью объектов RMO. Используемые классы зависят от типа публикации, которой принадлежит подписка, и типа подписки (принудительная или по запросу).  
  
#### Повторная инициализация подписки по запросу на публикацию транзакций  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPullSubscription> и задать <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, и соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта.  
  
    > [!NOTE]  
    >  Если этот метод возвращает **false**, были неправильно заданы свойства подписки на шаге 2 или подписки по запросу не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> метод. Этот метод помечает подписку для повторной инициализации.  
  
5.  Выполните синхронизацию подписки по запросу. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Повторная инициализация принудительной подписки на публикацию транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransSubscription> и задать <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, и соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта.  
  
    > [!NOTE]  
    >  Если этот метод возвращает **false**, были неправильно заданы свойства подписки на шаге 2 или принудительной подписки не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> метод. Этот метод помечает подписку для повторной инициализации.  
  
5.  Выполните синхронизацию принудительной подписки. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Повторная инициализация подписки по запросу на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePullSubscription> и задать <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, и соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта.  
  
    > [!NOTE]  
    >  Если этот метод возвращает **false**, были неправильно заданы свойства подписки на шаге 2 или подписки по запросу не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> метод. Передайте значение **true** , чтобы передать изменения на подписчике перед повторной инициализацией, или значение **false** , чтобы выполнить повторную инициализацию с потерей всех изменений, ожидающих на подписчике. Этот метод помечает подписку для повторной инициализации.  
  
    > [!NOTE]  
    >  Нельзя передать изменения, если срок действия подписки истек. Дополнительные сведения см. в статье [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Выполните синхронизацию подписки по запросу. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Повторная инициализация принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscription> и задать <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, и соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта.  
  
    > [!NOTE]  
    >  Если этот метод возвращает **false**, были неправильно заданы свойства подписки на шаге 2 или принудительной подписки не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> метод. Передайте значение **true** , чтобы передать изменения на подписчике перед повторной инициализацией, или значение **false** , чтобы выполнить повторную инициализацию с потерей всех изменений, ожидающих на подписчике. Этот метод помечает подписку для повторной инициализации.  
  
    > [!NOTE]  
    >  Нельзя передать изменения, если срок действия подписки истек. Дополнительные сведения см. в статье [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Выполните синхронизацию принудительной подписки. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере повторно инициализируется подписка по запросу на публикацию транзакций.  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 В этом примере повторно инициализируется подписка по запросу на публикацию слиянием после передачи ожидающих изменений на подписчик.  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## См. также:  
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  