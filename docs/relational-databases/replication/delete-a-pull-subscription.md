---
title: "Удаление подписки по запросу | Microsoft Docs"
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
  - "удаление подписок"
  - "подписки по запросу [репликация SQL Server], удаление"
  - "подписки [репликация SQL Server], по запросу"
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Удаление подписки по запросу
  В данном разделе описывается удаление подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для удаления подписки по запросу используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Удаление подписки по запросу на издателе (из **Локальные публикации** папки в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) или на подписчике (из **Локальные подписки** папки). При удалении подписки объекты и данные не удаляются из подписки, они должны быть удалены вручную.  
  
#### Удаление подписки по запросу на издателе  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, связанную с удаляемой подпиской.  
  
4.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Удаление**.  
  
5.  В окне подтверждения укажите, надо ли подключаться к подписчику для удаления сведений подписки. Если снять флажок **Соединиться с подписчиком** , то для удаления сведений потребуется соединиться с подписчиком позже.  
  
#### Удаление подписки по запросу на подписчике  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую нужно удалить и нажмите кнопку **Удаление**.  
  
4.  В окне подтверждения укажите, надо ли подключаться к издателю для удаления сведений подписки. Если снять флажок **Соединиться с издателем** , то для удаления сведений потребуется соединиться с издателем позже.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки по запросу могут быть удалены программным путем с помощью хранимых процедур репликации. Какие именно хранимые процедуры будут при этом применяться, зависит от типа публикации, к которой относится подписка.  
  
#### Удаление подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_droppullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md). Укажите **@publication**, **@publisher**, и **@publisher_db**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Укажите параметры **@publication** и **@subscriber**. Задайте значение **all** в параметре **@article**. (Необязательно) Если распространитель недоступен, задайте значение **1** для **@ignore_distributor** для удаления подписки без удаления связанных объектов на распространителе.  
  
#### Удаление подписки по запросу на публикацию слиянием  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_dropmergepullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md). Укажите **@publication**, **@publisher**, и **@publisher_db**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, и **@subscriber_db**. Укажите значение **запросу** для **@subscription_type**. (Необязательно) Если распространитель недоступен, задайте значение **1** для **@ignore_distributor** для удаления подписки без удаления связанных объектов на распространителе.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере производится удаление подписки по запросу на публикацию транзакций. Первый пакет выполняется на подписчике, а второй — на издателе.  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_1.sql)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_2.sql)]  
  
 В следующем примере производится удаление подписки на публикацию слиянием. Первый пакет выполняется на подписчике, а второй — на издателе.  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_3.sql)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_4.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Подписки по запросу можно удалять программно с помощью объектов RMO. Конкретные классы объектов RMO, используемые для удаления подписки по запросу, зависят от типа публикации, которой принадлежит эта подписка по запросу.  
  
#### Удаление подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создание соединения с подписчиком и издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPullSubscription> и задать <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Свойства. Позволяет установить соединение с подписчиком из шага 1 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
3.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться, что подписка существует. Если это свойство имеет значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> метод.  
  
5.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса с помощью соединения с издателем из шага 1. Укажите <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если метод возвращает значение **false**, то либо неверно определены свойства, указанные на шаге 5, либо публикация не существует на сервере.  
  
7.  Вызов <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> метод. Укажите имя подписчика и имя базы данных подписки в параметрах *subscriber* и *subscriberDB* .  
  
#### Удаление подписки по запросу на публикацию слиянием  
  
1.  Создание соединения с подписчиком и издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePullSubscription> и задать <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Свойства. Позволяет задать соединение из шага 1 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
3.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться, что подписка существует. Если это свойство имеет значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> метод.  
  
5.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса с помощью соединения с издателем из шага 1. Укажите <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если метод возвращает значение **false**, то либо неверно определены свойства, указанные на шаге 5, либо публикация не существует на сервере.  
  
7.  Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> метод. Укажите имя подписчика и имя базы данных подписки в параметрах *subscriber* и *subscriberDB* .  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере удаляется подписка по запросу на публикацию транзакций, а также удаляется регистрация подписки на издателе.  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 В этом примере удаляется подписка по запросу на публикацию слиянием, а также удаляется регистрация подписки на издателе.  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## См. также:  
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  