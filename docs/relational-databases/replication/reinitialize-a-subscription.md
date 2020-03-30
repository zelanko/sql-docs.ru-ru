---
title: Повторная инициализация подписки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 733e63f6dd01c09fd007a7176721533f7a1c57d3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "70846515"
---
# <a name="reinitialize-a-subscription"></a>Повторная инициализация подписки
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В данном разделе описывается повторная инициализация подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO. Отдельные подписки можно помечать для повторной инициализации, чтобы во время следующей синхронизации применялся новый моментальный снимок.  
  
[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]


  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Повторная инициализация подписки — это процесс, состоящий из двух частей:  
  
1.  Одна или все подписки на публикацию *помечаются* для повторной инициализации. Подписки помечаются для повторной инициализации в диалоговом окне **Повторная инициализация подписок**, доступ к которому можно получить в папках **Локальные публикации** и **Локальные подписки** в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Все подписки можно также пометить на вкладке **Все подписки** и в узле публикаций монитора репликации. Сведения о запуске монитора репликации см. в [этой статье](../../relational-databases/replication/monitor/start-the-replication-monitor.md). При пометке подписки для повторной инициализации доступны следующие параметры.  
  
     **Использовать текущий моментальный снимок**  
     Выберите, чтобы применить текущий моментальный снимок к подписчику при следующем запуске агента распространителя или агента слияния. Если допустимый моментальный снимок отсутствует, этот параметр выбрать нельзя.  
  
     **Использовать новый моментальный снимок**  
     Выберите, чтобы выполнить повторную инициализацию подписки с новым моментальным снимком. Этот моментальный снимок можно применять к подписчику только после того, как он был сформирован агентом моментальных снимков. Если агент моментальных снимков настроен на запуск по расписанию, подписка не инициализируется повторно до следующего запланированного запуска агента моментальных снимков. Выберите **Создать новый моментальный снимок** для немедленного запуска агента моментальных снимков.  
  
     **Передать несинхронизированные изменения перед повторной инициализацией**  
     Только репликация слиянием. Выберите, чтобы передать все ожидающие обработки изменения из базы данных подписки, прежде чем данные подписчика будут перезаписаны моментальным снимком.  
  
     Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
2.  Подписка повторно инициализируется при следующей синхронизации: агент распространителя (для репликации транзакций) или агент слияния (для репликации слиянием) применяет самый последний моментальный снимок к каждому подписчику, имеющему подписку, отмеченную для повторной инициализации. Дополнительные сведения о синхронизации подписок см. в разделах [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) и [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-management-studio-at-the-publisher"></a>Пометка для повторной инициализации одной принудительной подписки или подписки по запросу в Management Studio (на издателе)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, имеющую подписку, которую нужно повторно инициализировать.  
  
4.  Щелкните подписку правой кнопкой мыши и выберите **Повторно инициализировать**.  
  
5.  В диалоговом окне **Повторная инициализация подписок** выберите параметры и щелкните **Пометить для повторной инициализации**.  
  
#### <a name="to-mark-a-single-pull-subscription-for-reinitialization-in-management-studio-at-the-subscriber"></a>Пометка для повторной инициализации одной принудительной подписки в Management Studio (на подписчике)  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните подписку правой кнопкой мыши и выберите **Повторно инициализировать**.  
  
4.  В появившемся окне подтверждения нажмите кнопку **Да**.  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-management-studio"></a>Пометить для повторной инициализации все подписки в Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию с подписками, которые необходимо повторно инициализировать, и выберите **Повторно инициализировать все подписки**.  
  
4.  В диалоговом окне **Повторная инициализация подписок** выберите параметры и щелкните **Пометить для повторной инициализации**.  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-replication-monitor"></a>Пометка для повторной инициализации одной принудительной подписки или подписки по запросу в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, раскройте нужного издателя, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, для которой нужно выполнить повторную инициализацию, и выберите **Повторно инициализировать подписку**.  
  
4.  В диалоговом окне **Повторная инициализация подписок** выберите параметры и щелкните **Пометить для повторной инициализации**.  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-replication-monitor"></a>Пометка для повторной инициализации всех подписок в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.  
  
2.  Щелкните правой кнопкой мыши публикацию с подписками, которые необходимо повторно инициализировать, и выберите **Повторно инициализировать все подписки**.  
  
3.  В диалоговом окне **Повторная инициализация подписок** выберите параметры и щелкните **Пометить для повторной инициализации**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки можно повторно инициализировать программно с помощью хранимых процедур репликации. Используемая хранимая процедура зависит от типа подписки (принудительная или по запросу) и типа публикации, которой принадлежит подписка.  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a>Повторная инициализация подписки по запросу на публикацию транзакций  
  
1.  В базе данных подписчика на подписчике выполните процедуру [sp_reinitpullsubscription_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql.md). Задайте значения для параметров **\@publisher**, **\@publisher_db** и **\@publication**. В результате подписка будет помечена к повторной инициализации при следующем запуске агента распространителя.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент распространителя на подписчике. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a>Повторная инициализация принудительной подписки на публикацию транзакций  
  
1.  Выполните процедуру [sp_reinitpullsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql.md) на издателе. Укажите значения параметров **\@publication**, **\@subscriber** и **\@destination_db**. В результате подписка будет помечена к повторной инициализации при следующем запуске агента распространителя.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент распространителя на распространителе. Дополнительные сведения см. в статье [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a>Повторная инициализация подписки по запросу на публикацию слиянием  
  
1.  В базе данных подписчика на подписчике выполните процедуру [sp_reinitmergepullsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md). Задайте значения для параметров **\@publisher**, **\@publisher_db** и **\@publication**. Чтобы передать изменения с подписчика перед повторной инициализацией, задайте значение **true** в параметре **\@upload_first**. Помечает подписку для повторной инициализации при следующем запуске агента слияния.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент слияния на подписчике. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a>Повторная инициализация принудительной подписки на публикацию слиянием  
  
1.  Выполните процедуру [sp_reinitmergesubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql.md) на издателе. Задайте значения для параметров **\@publication**, **\@subscriber** и **\@subscriber_db**. Чтобы передать изменения с подписчика перед повторной инициализацией, задайте значение **true** в параметре **\@upload_first**. В результате подписка будет помечена к повторной инициализации при следующем запуске агента распространителя.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
2.  (Необязательно) Чтобы синхронизировать подписку, запустите агент слияния на распространителе. Дополнительные сведения см. в статье [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### <a name="to-set-the-reinitialization-policy-when-creating-a-new-merge-publication"></a>Установка политики повторной инициализации при создании публикации слиянием  
  
1.  В издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), указав одно из следующих значений в параметре **\@automatic_reinitialization_policy**:  
  
    -   **1** — изменения передаются с подписчика до автоматической повторной инициализации подписки, выполняемой в результате изменения публикации.  
  
    -   **0** — изменения на подписчике отменяются, когда происходит автоматическая повторная инициализация подписки, выполняемая в результате изменения публикации.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
     Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-change-the-reinitialization-policy-for-an-existing-merge-publication"></a>Изменение политики повторной инициализации для существующей публикации слиянием  
  
1.  В издателе в базе данных публикации выполните хранимую процедуру [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав значение **automatic_reinitialization_policy** в параметре **\@property** и одно из следующих значений в параметре **\@value**:  
  
    -   **1** — изменения передаются с подписчика до автоматической повторной инициализации подписки, выполняемой в результате изменения публикации.  
  
    -   **0** — изменения на подписчике отменяются, когда происходит автоматическая повторная инициализация подписки, выполняемая в результате изменения публикации.  
  
    > [!IMPORTANT]  
    >  Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
     Дополнительные сведения см. в статье [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Отдельные подписки можно помечать для повторной инициализации, чтобы во время следующей синхронизации применялся новый моментальный снимок. Подписки можно повторно инициализировать программно с помощью объектов RMO. Используемые классы зависят от типа публикации, которой принадлежит подписка, и типа подписки (принудительная или по запросу).  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a>Повторная инициализация подписки по запросу на публикацию транзакций  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> , задайте свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, а затем задайте соединение из шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> .  
  
    > [!NOTE]  
    >  Если этот метод возвращает значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка по запросу не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> . Этот метод помечает подписку для повторной инициализации.  
  
5.  Выполните синхронизацию подписки по запросу. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a>Повторная инициализация принудительной подписки на публикацию транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSubscription> , задайте свойства <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, а затем задайте соединение из шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> .  
  
    > [!NOTE]  
    >  Если этот метод возвращает значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо принудительная подписка не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> . Этот метод помечает подписку для повторной инициализации.  
  
5.  Выполните синхронизацию принудительной подписки. Дополнительные сведения см. в статье [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a>Повторная инициализация подписки по запросу на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> , задайте свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, а затем задайте соединение из шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> .  
  
    > [!NOTE]  
    >  Если этот метод возвращает значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка по запросу не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> . Передайте значение **true** , чтобы передать изменения на подписчике перед повторной инициализацией, или значение **false** , чтобы выполнить повторную инициализацию с потерей всех изменений, ожидающих на подписчике. Этот метод помечает подписку для повторной инициализации.  
  
    > [!NOTE]  
    >  Нельзя передать изменения, если срок действия подписки истек. Дополнительные сведения см. в статье [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Выполните синхронизацию подписки по запросу. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a>Повторная инициализация принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscription> , задайте свойства <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, а затем задайте соединение из шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> .  
  
    > [!NOTE]  
    >  Если этот метод возвращает значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо принудительная подписка не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> . Передайте значение **true** , чтобы передать изменения на подписчике перед повторной инициализацией, или значение **false** , чтобы выполнить повторную инициализацию с потерей всех изменений, ожидающих на подписчике. Этот метод помечает подписку для повторной инициализации.  
  
    > [!NOTE]  
    >  Нельзя передать изменения, если срок действия подписки истек. Дополнительные сведения см. в статье [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Выполните синхронизацию принудительной подписки. Дополнительные сведения см. в статье [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере повторно инициализируется подписка по запросу на публикацию транзакций.  
  
 [!code-cs[HowTo#rmo_ReinitTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 В этом примере повторно инициализируется подписка по запросу на публикацию слиянием после передачи ожидающих изменений на подписчик.  
  
 [!code-cs[HowTo#rmo_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## <a name="see-also"></a>См. также:  
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
