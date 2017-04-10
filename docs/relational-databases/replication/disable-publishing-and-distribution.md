---
title: "Отключение публикации и распространения | Microsoft Docs"
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
  - "отключение публикации"
  - "публикация [репликация SQL Server], отключение"
  - "отключение распространения [репликация SQL Server]"
  - "удаление репликации"
  - "репликация [SQL Server], удаление"
  - "отключение репликации"
  - "отключение распространения"
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Отключение публикации и распространения
  В данном разделе описывается отключение публикации и распространения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 Можно сделать следующее.  
  
-   Удалите все базы данных распространителя на распространителе.  
  
-   Отключите все издатели, использующие данный распространитель, и удалите все публикации на этих издателях.  
  
-   Удалите все подписки на публикации. Данные баз данных публикации и подписки удалены не будут; однако они потеряют отношения синхронизации с любыми базами данных публикации. Если нужно удалить данные на подписчике, то их следует удалять вручную.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
-   **Для отключения публикации и распространения используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Для отключения публикации и распространения все базы данных распространителей и публикаций должны находиться в режиме «в сети». Если для баз данных распространителя или публикации существуют какие-либо *моментальные снимки базы данных* , то их необходимо удалить до отключения публикации и распространения. Моментальный снимок базы данных — это копия базы данных вне сети, доступная только для чтения и не связанная с моментальным снимком репликации. Дополнительные сведения см. в разделе [моментальные снимки базы данных & #40; SQL Server & #41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Отключить публикацию и распространение можно с помощью мастера отключения публикации и распространения.  
  
#### Отключение публикации и распространения  
  
1.  Подключитесь к издателю или распространителю, который необходимо отключить, в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши **репликации** папку и выберите пункт **отключить публикацию и распространение**.  
  
3.  Выполните шаги, предлагаемые мастером отключения публикации и распространителя.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикацию и распространение можно отключить программно с помощью хранимых процедур репликации.  
  
#### Отключение публикации и распространения  
  
1.  Остановите все задания, связанные с репликацией. Список имен задач см. в подразделе «Безопасность агентов при работе с агентом SQL Server» раздела [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
2.  На каждом подписчике в базе данных подписки выполните [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) для удаления объектов репликации из базы данных. Эта хранимая процедура не удаляет задания репликации на распространителе.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) для удаления объектов репликации из базы данных.  
  
4.  Если издатель использует удаленный распространитель, выполните [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md).  
  
5.  На распространителе выполните хранимую процедуру [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md). Эта хранимая процедура должна запускаться по разу для каждого издателя, зарегистрированного на распространителе.  
  
6.  На распространителе выполните хранимую процедуру [sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) для удаления базы данных распространителя. Эта хранимая процедура должна запускаться на распространителе, по одному разу для каждой базы данных распространителя. При этом также удаляются любые задания агента чтения очереди, связанные с базой данных распространителя.  
  
7.  На распространителе выполните хранимую процедуру [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) для удаления с сервера обозначение распространителя.  
  
    > [!NOTE]  
    >  Если все объекты публикации и распространения репликации не удаляются перед выполнением [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md) и [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md), эти процедуры будет возвращена ошибка. Чтобы удалить все относящиеся к репликации объектов при удалении издателя или распространителя **@no_checks** параметра должно быть установлено значение **1**. Если издатель или распространитель работает автономно или недоступен, **@ignore_distributor** может быть присвоено **1** таким образом, чтобы их можно было удалить; тем не менее, все публикации и распространения оставшиеся объекты должны быть удалены вручную.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере скрипта удаляются объекты репликации из базы данных подписки.  
  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_1.sql)]  
  
 В этом примере скрипта отключается публикация и распространение на сервере, являющемся издателем и распространителем, и удаляется база данных распространителя.  
  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### Отключение публикации и распространения  
  
1.  Удалите все подписки на публикации, которые используют распространитель. Дополнительные сведения см. в разделах [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md) и [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md).  
  
2.  Удалите все публикации, которые используют распространитель, и отключите публикацию для всех баз данных, если издатель и распространитель находятся на одном сервере. Дополнительные сведения см. в разделе [Delete a Publication](../../relational-databases/replication/publish/delete-a-publication.md).  
  
3.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
4.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.DistributionPublisher> класса. Укажите <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> Свойства и передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 3.  
  
5.  (Необязательно) Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта и убедитесь, что издатель существует. Если метод возвращает значение **false**, то имя издателя, установленное на шаге 4, неверно или издатель не используется этим распространителем.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> метод. Передайте значение **true** в параметре *force* , если издатель и распространитель расположены на разных серверах и если издатель нужно удалить с распространителя, не проверяя, существуют ли публикации на издателе.  
  
7.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationServer> класса. Передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 3.  
  
8.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> метод. Передайте значение **true** для *force* , чтобы удалить все объекты репликации с распространителя, не проверяя, отключены ли все локальные базы данных публикации и удалены ли базы данных распространителя.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере удаляется как регистрация издателя на распространителе, так и база данных распространителя, а также удаляется распространитель.  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 В этом примере распространитель удаляется без отключения локальных баз данных публикации или удаления базы данных распространителя.  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## См. также:  
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Основные понятия системных хранимых процедур репликации](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  