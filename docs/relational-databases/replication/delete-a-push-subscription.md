---
title: "Удаление принудительной подписки | Microsoft Docs"
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
  - "удаление подписок"
  - "принудительные подписки [репликация SQL Server], удаление"
  - "удаление подписок"
  - "принудительные подписки [репликация SQL Server], отправка"
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Удаление принудительной подписки
  В данном разделе описывается удаление принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для удаления принудительной подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Удаление принудительной подписки на издателе (из **Локальные публикации** папки в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) или на подписчике (из **Локальные подписки** папки). При удалении подписки объекты и данные не удаляются из подписки, они должны быть удалены вручную.  
  
#### Удаление принудительной подписки на издателе  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, связанную с удаляемой подпиской.  
  
4.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Удаление**.  
  
5.  В окне подтверждения укажите, надо ли подключаться к подписчику для удаления сведений подписки. Если флажок **Соединиться с подписчиком** снят, необходимо позднее соединиться с подписчиком, чтобы удалить данные.  
  
#### Удаление принудительной подписки на подписчике  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую нужно удалить и нажмите кнопку **Удаление**.  
  
4.  В окне подтверждения укажите, надо ли подключаться к издателю для удаления сведений подписки. Если снять флажок **Соединиться с издателем** , то для удаления сведений потребуется соединиться с издателем позже.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Принудительные подписки можно удалять программно с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит подписка.  
  
#### Удаление принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Укажите параметры **@publication** и **@subscriber**. Задайте значение **all** в параметре **@article**. (Необязательно) Если распространитель недоступен, задайте значение **1** для **@ignore_distributor** для удаления подписки без удаления связанных объектов на распространителе.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_subscription_cleanup & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) Чтобы удалить метаданные репликации в базе данных подписки.  
  
#### Удаление принудительной подписки на публикацию слиянием  
  
1.  На издателе, хранимую [sp_dropmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md), указав **@publication**, **@subscriber** и **@subscriber_db**. (Необязательно) Если распространитель недоступен, задайте значение **1** для **@ignore_distributor** для удаления подписки без удаления связанных объектов на распространителе.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_mergesubscription_cleanup & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md). Укажите **@publisher**, **@publisher_db**, и **@publication**. Тем самым из базы данных подписки удаляются метаданные слияния.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере удаляется принудительная подписка на публикацию транзакций.  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_1.sql)]  
  
 В этом примере удаляется принудительная подписка на публикацию слиянием.  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Какие именно классы объектов RMO для этого применяются, зависит от типа публикации этой подписки.  
  
#### Удаление принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransSubscription> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, и <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> Свойства.  
  
4.  Задайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться, что подписка существует. Если это свойство имеет значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> метод.  
  
#### Удаление принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscription> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, и <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> Свойства.  
  
4.  Задайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться, что подписка существует. Если это свойство имеет значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> метод.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 Принудительные подписки могут быть удалены программно с помощью объектов RMO.  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## См. также:  
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  