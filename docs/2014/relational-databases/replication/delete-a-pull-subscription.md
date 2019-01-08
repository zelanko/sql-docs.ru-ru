---
title: Удаление подписки по запросу | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ac5d4f7d199e3ee3de6ffb43e2c43e232681b0d3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52785116"
---
# <a name="delete-a-pull-subscription"></a>Удаление подписки по запросу
  В данном разделе описывается удаление подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для удаления подписки по запросу используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Удалите подписку по запросу на издателе (из папки **Локальные публикации** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) или на подписчике (из папки **Локальные подписки** ). При удалении подписки объекты и данные не удаляются из подписки, они должны быть удалены вручную.  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a>Удаление подписки по запросу на издателе  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, связанную с удаляемой подпиской.  
  
4.  Правой кнопкой мыши щелкните подписку и затем щелкните **Удалить**.  
  
5.  В окне подтверждения укажите, надо ли подключаться к подписчику для удаления сведений подписки. Если снять флажок **Соединиться с подписчиком** , то для удаления сведений потребуется соединиться с подписчиком позже.  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a>Удаление подписки по запросу на подписчике  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Правой кнопкой мыши щелкните подписку, которую желаете удалить, и затем щелкните **Удалить**.  
  
4.  В окне подтверждения укажите, надо ли подключаться к издателю для удаления сведений подписки. Если снять флажок **Соединиться с издателем** , то для удаления сведений потребуется соединиться с издателем позже.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки по запросу могут быть удалены программным путем с помощью хранимых процедур репликации. Какие именно хранимые процедуры будут при этом применяться, зависит от типа публикации, к которой относится подписка.  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Удаление подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  В базе данных подписчика в подписчике выполните процедуру [sp_addmergepushsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql). Задайте значения для параметров **@publication**, **@publisher**и **@publisher_db**.  
  
2.  В издателе в базе данных публикации выполните процедуру [sp_dropsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql). Задайте значения для параметров **@publication** и **@subscriber**. Задайте значение **all** в параметре **@article**. Если распространитель недоступен, задайте значение **1** в параметре **@ignore_distributor** , чтобы удалить подписку без удаления связанных с ней объектов на распространителе (необязательно).  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a>Удаление подписки по запросу на публикацию слиянием  
  
1.  В базе данных подписчика в подписчике выполните процедуру [sp_dropmergepullsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql). Задайте значения для параметров **@publication**, **@publisher**и **@publisher_db**.  
  
2.  В издателе в базе данных публикации выполните процедуру [sp_dropmergesubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql). Задайте значения для параметров **@publication**, **@subscriber**и **@subscriber_db**. Задайте значение **@subscription_type** в параметре **@subscription_type**. Если распространитель недоступен, задайте значение **1** в параметре **@ignore_distributor** , чтобы удалить подписку без удаления связанных с ней объектов на распространителе (необязательно).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере производится удаление подписки по запросу на публикацию транзакций. Первый пакет выполняется на подписчике, а второй — на издателе.  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptranpullsubscription)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 В следующем примере производится удаление подписки на публикацию слиянием. Первый пакет выполняется на подписчике, а второй — на издателе.  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergepullsubscription)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Подписки по запросу можно удалять программно с помощью объектов RMO. Конкретные классы объектов RMO, используемые для удаления подписки по запросу, зависят от типа публикации, которой принадлежит эта подписка по запросу.  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Удаление подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединения с подписчиком и издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> и задайте свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> . Чтобы установить свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> , используется соединение подписчика из шага 1.  
  
3.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что подписка существует. Если это свойство имеет значение `false`, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A>.  
  
5.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если метод возвращает значение `false`, то либо неверно определены свойства, указанные на шаге 5, либо публикация не существует на сервере.  
  
7.  Вызовите метод <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A>. Укажите имя подписчика и имя базы данных подписки в параметрах *subscriber* и *subscriberDB* .  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a>Удаление подписки по запросу на публикацию слиянием  
  
1.  Создайте соединения с подписчиком и издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> и задайте свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> . Чтобы установить свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> , используется соединение из шага 1.  
  
3.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что подписка существует. Если это свойство имеет значение `false`, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A>.  
  
5.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если метод возвращает значение `false`, то либо неверно определены свойства, указанные на шаге 5, либо публикация не существует на сервере.  
  
7.  Вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A>. Укажите имя подписчика и имя базы данных подписки в параметрах *subscriber* и *subscriberDB* .  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере удаляется подписка по запросу на публикацию транзакций, а также удаляется регистрация подписки на издателе.  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 В этом примере удаляется подписка по запросу на публикацию слиянием, а также удаляется регистрация подписки на издателе.  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a>См. также  
 [Подписка на публикации](subscribe-to-publications.md)   
 [Рекомендации по защите репликации](security/replication-security-best-practices.md)  
  
  
