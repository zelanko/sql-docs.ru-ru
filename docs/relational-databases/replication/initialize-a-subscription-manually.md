---
title: "Инициализация подписки вручную | Документация Майкрософт"
ms.custom: 
ms.date: 08/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: df662985251521fb62d92103b75c13d83cd86a0a
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="initialize-a-subscription-manually"></a>Инициализация подписки вручную
  В этом разделе описывается инициализация подписки вручную в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Обычно инициализация подписки производится через исходный моментальный снимок, однако подписку на публикацию можно инициализировать и другим способом. Для этого необходимо, чтобы на подписчике уже имелась схема и исходные данные.  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если в базе данных, опубликованной с использованием репликации транзакций, между копированием данных и схемы на подписчик и ручной инициализацией подписки выполнялись какие-либо действия, то возникшие в результате этих действий изменения данных могут не реплицироваться на подписчик.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Ручная инициализация подписки на публикацию производится путем копирования схемы (а также обычно данных) в базу данных подписки. Схема и данные должны соответствовать базе данных публикации. Затем на странице **Инициализация подписок** мастера создания подписок нужно указать, что для подписки не нужны схема и данные. Дополнительные сведения о доступе к этому мастеру см. в разделах [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) и [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
 При первой синхронизации подписки объекты и метаданные, необходимые для репликации, копируются в базу данных подписки.  
  
#### <a name="to-initialize-a-subscription-to-a-publication-manually"></a>Инициализация подписки на публикацию вручную  
  
1.  Убедитесь, что схема и данные скопированы в базу данных подписки.  
  
2.  Снимите флажок **Инициализировать** на странице **Инициализация подписок** мастера создания подписок. Это действие необходимо выполнить для каждой подписки, требующей копирования только объектов и метаданных репликации.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки можно инициализированы вручную с помощью хранимых процедур репликации.  
  
#### <a name="to-manually-initialize-a-pull-subscription-to-a-transactional-publication"></a>Ручная инициализация подписки по запросу на публикацию транзакций  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Дополнительные сведения см. в статье [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Задайте параметры **@publication**, **@subscriber**, укажите имя базы данных подписчика, содержащей публикуемые данные, в параметре **@destination_db**, значение **pull** в параметре **@subscription_type**, а также значение **replication support only** в параметре **@sync_type**. Дополнительные сведения см. в статье [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  Выполните процедуру [sp_addpullsubscription](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)на подписчике. Сведения об обновлении подписок см. в разделе [Create an Updatable Subscription to a Transactional Publication](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx).  
  
4.  Выполните процедуру [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)на подписчике. Дополнительные сведения см. в статье [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
5.  Запустите агент распространителя, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-manually-initialize-a-push-subscription-to-a-transactional-publication"></a>Ручная инициализация принудительной подписки на публикацию транзакций  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Дополнительные сведения см. в статье [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Укажите имя базы данных подписчика, содержащей публикуемые данные, в параметре **@destination_db**, значение **push** в параметре **@subscription_type**, а также значение **replication support only** в параметре **@sync_type**. Сведения об обновлении подписок см. в разделе [Create an Updatable Subscription to a Transactional Publication](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
4.  Запустите агент распространителя, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### <a name="to-manually-initialize-a-pull-subscription-to-a-merge-publication"></a>Ручная инициализация подписки по запросу на публикацию слиянием  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Это можно сделать путем восстановления резервной копии базы данных публикации на подписчике.  
  
2.  Выполните процедуру [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)на издателе. Задайте параметры **@publication**, **@subscriber**, **@subscriber_db**, а также значение **pull** в параметре **@subscription_type**. После этого подписка по запросу будет зарегистрирована.  
  
3.  На подписчике в базе данных, содержащей публикуемые данные, выполните хранимую процедуру [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). В параметре **@sync_type** в параметре **@sync_type**.  
  
4.  Выполните процедуру [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)на подписчике. Дополнительные сведения см. в статье [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
5.  Запустите агент слияния, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### <a name="to-manually-initialize-a-push-subscription-to-a-merge-publication"></a>Ручная инициализация принудительной подписки на публикацию слиянием  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Это можно сделать путем восстановления резервной копии базы данных публикации на подписчике.  
  
2.  В базе данных публикации на издателе выполните процедуру [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Укажите имя базы данных подписчика, содержащей публикуемые данные, в параметре **@subscriber_db**, значение **push** в параметре **@subscription_type**, а также значение **@sync_type** в параметре **@sync_type**.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
4.  Запустите агент слияния, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
## <a name="see-also"></a>См. также:  
 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)   
 [Создание резервных копий реплицируемых баз данных и восстановление из них](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  

