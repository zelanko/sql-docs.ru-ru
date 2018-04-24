---
title: Удаление принудительной подписки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- removing subscriptions
- push subscriptions [SQL Server replication], deleting
- deleting subscriptions
- subscriptions [SQL Server replication], push
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e41a3aec77c0b98fdb1269869d660ae36d1147a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="delete-a-push-subscription"></a>Удаление принудительной подписки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается удаление принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для удаления принудительной подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Удалите принудительную подписку на издателе (из папки **Локальные публикации** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) или на подписчике (из папки **Локальные подписки** ). При удалении подписки объекты и данные не удаляются из подписки, они должны быть удалены вручную.  
  
#### <a name="to-delete-a-push-subscription-at-the-publisher"></a>Удаление принудительной подписки на издателе  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, связанную с удаляемой подпиской.  
  
4.  Правой кнопкой мыши щелкните подписку и затем щелкните **Удалить**.  
  
5.  В окне подтверждения укажите, надо ли подключаться к подписчику для удаления сведений подписки. Если флажок **Соединиться с подписчиком** снят, необходимо позднее соединиться с подписчиком, чтобы удалить данные.  
  
#### <a name="to-delete-a-push-subscription-at-the-subscriber"></a>Удаление принудительной подписки на подписчике  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Правой кнопкой мыши щелкните подписку, которую желаете удалить, и затем щелкните **Удалить**.  
  
4.  В окне подтверждения укажите, надо ли подключаться к издателю для удаления сведений подписки. Если снять флажок **Соединиться с издателем** , то для удаления сведений потребуется соединиться с издателем позже.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Принудительные подписки можно удалять программно с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит подписка.  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Удаление принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  В издателе в базе данных публикации выполните процедуру [sp_dropsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Задайте значения для параметров **@publication** и **@subscriber**. Задайте значение **all** в параметре **@article**. Если распространитель недоступен, задайте значение **1** в параметре **@ignore_distributor** , чтобы удалить подписку без удаления связанных с ней объектов на распространителе (необязательно).  
  
2.  Чтобы удалить все метаданные репликации, оставшиеся в базе данных подписки, выполните в подписчике хранимую процедуру [sp_subscription_cleanup (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md).  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a>Удаление принудительной подписки на публикацию слиянием  
  
1.  В подписчике выполните процедуру [sp_dropmergesubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md), указав параметры **@publication**, **@subscriber** и **@subscriber_db**. Если распространитель недоступен, задайте значение **1** в параметре **@ignore_distributor** , чтобы удалить подписку без удаления связанных с ней объектов на распространителе (необязательно).  
  
2.  В базе данных подписчика в подписчике выполните процедуру [sp_mergesubscription_cleanup (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md). Задайте значения для параметров **@publisher**, **@publisher_db**и **@publication**. Тем самым из базы данных подписки удаляются метаданные слияния.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере удаляется принудительная подписка на публикацию транзакций.  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_1.sql)]  
  
 В этом примере удаляется принудительная подписка на публикацию слиянием.  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Какие именно классы объектов RMO для этого применяются, зависит от типа публикации этой подписки.  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Удаление принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSubscription> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>и <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> .  
  
4.  Задайте соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> с шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что подписка существует. Если это свойство имеет значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> .  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a>Удаление принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscription> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>и <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> .  
  
4.  Задайте соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> с шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что подписка существует. Если это свойство имеет значение **false**, значит, на шаге 2 были неправильно заданы свойства подписки либо подписка не существует.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> .  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 Принудительные подписки могут быть удалены программно с помощью объектов RMO.  
  
 [!code-cs[HowTo#rmo_DropTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## <a name="see-also"></a>См. также:  
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
