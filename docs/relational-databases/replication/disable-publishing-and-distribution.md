---
title: "Отключение публикации и распространения | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c50f547288b6139cc9793381531204ee32f36ce0
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="disable-publishing-and-distribution"></a>Отключение публикации и распространения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается отключение публикации и распространения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
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
  
-   Для отключения публикации и распространения все базы данных распространителей и публикаций должны находиться в режиме «в сети». Если для баз данных распространителя или публикации существуют какие-либо *моментальные снимки базы данных* , то их необходимо удалить до отключения публикации и распространения. Моментальный снимок базы данных — это копия базы данных вне сети, доступная только для чтения и не связанная с моментальным снимком репликации. Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Отключить публикацию и распространение можно с помощью мастера отключения публикации и распространения.  
  
#### <a name="to-disable-publishing-and-distribution"></a>Отключение публикации и распространения  
  
1.  Подключитесь к издателю или распространителю, который необходимо отключить, в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** и выберите **Отключить публикацию и распространение**.  
  
3.  Выполните шаги, предлагаемые мастером отключения публикации и распространителя.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикацию и распространение можно отключить программно с помощью хранимых процедур репликации.  
  
#### <a name="to-disable-publishing-and-distribution"></a>Отключение публикации и распространения  
  
1.  Остановите все задания, связанные с репликацией. Список имен задач см. в подразделе «Безопасность агентов при работе с агентом SQL Server» раздела [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
2.  На каждом подписчике в базе данных подписки выполните хранимую процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) , чтобы удалить объекты репликации из базы данных. Эта хранимая процедура не удаляет задания репликации на распространителе.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) , чтобы удалить объекты репликации из базы данных.  
  
4.  Если издатель использует удаленный распространитель, выполните хранимую процедуру [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md).  
  
5.  На распространителе выполните хранимую процедуру [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md). Эта хранимая процедура должна запускаться по разу для каждого издателя, зарегистрированного на распространителе.  
  
6.  На распространителе выполните хранимую процедуру [sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) , чтобы удалить базу данных распространителя. Эта хранимая процедура должна запускаться на распространителе, по одному разу для каждой базы данных распространителя. При этом также удаляются любые задания агента чтения очереди, связанные с базой данных распространителя.  
  
7.  На распространителе выполните хранимую процедуру [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) , чтобы удалить с сервера обозначение распространителя.  
  
    > [!NOTE]  
    >  Если все объекты публикации репликации и распространения не удалены перед выполнением хранимых процедур [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md) и [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md), эти процедуры возвратят ошибку. Чтобы удалить при удалении издателя и распространителя все объекты, связанные с репликацией, в параметре **@no_checks** должно быть задано значение **1**. Если издатель или распространитель находятся в режиме «вне сети» или недоступны, в параметре **@ignore_distributor** можно задать значение **1** , чтобы их можно было удалить; однако любые оставшиеся объекты публикации и распространения придется удалять вручную.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере скрипта удаляются объекты репликации из базы данных подписки.  
  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_1.sql)]  
  
 В этом примере скрипта отключается публикация и распространение на сервере, являющемся издателем и распространителем, и удаляется база данных распространителя.  
  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### <a name="to-disable-publishing-and-distribution"></a>Отключение публикации и распространения  
  
1.  Удалите все подписки на публикации, которые используют распространитель. Дополнительные сведения см. в разделах [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md) и [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md).  
  
2.  Удалите все публикации, которые используют распространитель, и отключите публикацию для всех баз данных, если издатель и распространитель находятся на одном сервере. Дополнительные сведения см. в разделе [Delete a Publication](../../relational-databases/replication/publish/delete-a-publication.md).  
  
3.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionPublisher> . Укажите свойство <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> и передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 3.  
  
5.  (Необязательно) Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы получить свойства объекта и убедиться, что издатель существует. Если метод возвращает значение **false**, то имя издателя, установленное на шаге 4, неверно или издатель не используется этим распространителем.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> . Передайте значение **true** в параметре *force* , если издатель и распространитель расположены на разных серверах и если издатель нужно удалить с распространителя, не проверяя, существуют ли публикации на издателе.  
  
7.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer> . Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 3.  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> . Передайте значение **true** для *force* , чтобы удалить все объекты репликации с распространителя, не проверяя, отключены ли все локальные базы данных публикации и удалены ли базы данных распространителя.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере удаляется как регистрация издателя на распространителе, так и база данных распространителя, а также удаляется распространитель.  
  
 [!code-cs[HowTo#rmo_DropDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 В этом примере распространитель удаляется без отключения локальных баз данных публикации или удаления базы данных распространителя.  
  
 [!code-cs[HowTo#rmo_DropDistPubForce](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a>См. также:  
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Основные понятия системных хранимых процедур репликации](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
