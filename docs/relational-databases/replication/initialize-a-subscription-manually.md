---
title: "Инициализация подписки вручную | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ручная инициализация подписки [репликация SQL Server]"
  - "подписки [репликация SQL Server], инициализация"
  - "инициализация подписок [репликация SQL Server], без моментальных снимков"
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Инициализация подписки вручную
  В этом разделе описывается инициализация подписки вручную в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Обычно инициализация подписки производится через исходный моментальный снимок, однако подписку на публикацию можно инициализировать и другим способом. Для этого необходимо, чтобы на подписчике уже имелась схема и исходные данные.  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если в базе данных, опубликованной с использованием репликации транзакций, между копированием данных и схемы на подписчик и ручной инициализацией подписки выполнялись какие-либо действия, то возникшие в результате этих действий изменения данных могут не реплицироваться на подписчик.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Ручная инициализация подписки на публикацию производится путем копирования схемы (а также обычно данных) в базу данных подписки. Схема и данные должны соответствовать базе данных публикации. Затем на странице **Инициализация подписок** мастера создания подписок нужно указать, что для подписки не нужны схема и данные. Дополнительные сведения об использовании этого мастера см. в разделе [инициализировать транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) и [Создать подписку по запросу](../../relational-databases/replication/create-a-pull-subscription.md).  
  
 При первой синхронизации подписки объекты и метаданные, необходимые для репликации, копируются в базу данных подписки.  
  
#### Инициализация подписки на публикацию вручную  
  
1.  Убедитесь, что схема и данные скопированы в базу данных подписки.  
  
2.  Снимите флажок **Инициализировать** на странице **Инициализация подписок** мастера создания подписок. Это действие необходимо выполнить для каждой подписки, требующей копирования только объектов и метаданных репликации.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки можно инициализированы вручную с помощью хранимых процедур репликации.  
  
#### Ручная инициализация подписки по запросу на публикацию транзакций  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Дополнительные сведения см. в разделе [инициализировать транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, имя базы данных на подписчике, содержащей публикуемые данные для **@destination_db**, значение **запросу** для **@subscription_type**, а значение **только поддержка репликации** для **@sync_type**. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  Выполните процедуру [sp_addpullsubscription](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) на подписчике. Обновляемые подписки, в разделе [Создание обновляемых подписок на публикацию транзакций](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx).  
  
4.  Выполните процедуру [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) на подписчике. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
5.  Запустите агент распространителя, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Ручная инициализация принудительной подписки на публикацию транзакций  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Дополнительные сведения см. в разделе [инициализировать транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Укажите имя базы данных на подписчике, содержащей публикуемые данные для **@destination_db**, значение **push** для **@subscription_type**, а значение **только поддержка репликации** для **@sync_type**. Обновляемые подписки, в разделе [Создание обновляемых подписок на публикацию транзакций](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
4.  Запустите агент распространителя, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Ручная инициализация подписки по запросу на публикацию слиянием  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Это можно сделать путем восстановления резервной копии базы данных публикации на подписчике.  
  
2.  На издателе, хранимую [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, **@subscriber_db**, а значение **запросу** для **@subscription_type**. После этого подписка по запросу будет зарегистрирована.  
  
3.  На подписчике в базе данных, содержащей публикуемые данные, выполнять [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Укажите значение **Нет** для **@sync_type**.  
  
4.  На подписчике, выполните [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
5.  Запустите агент слияния, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### Ручная инициализация принудительной подписки на публикацию слиянием  
  
1.  Убедитесь, что схема и данные существуют в базе данных подписки. Это можно сделать путем восстановления резервной копии базы данных публикации на подписчике.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Укажите имя базы данных на подписчике, содержащей публикуемые данные для **@subscriber_db**, значение **push** для **@subscription_type**, а значение **Нет** для **@sync_type**.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
4.  Запустите агент слияния, чтобы передать объекты репликации и загрузить последние изменения с издателя. Дополнительные сведения см. в статье [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
## См. также:  
 [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)   
 [Создание резервной копии и восстановление из копий реплицируемых баз данных](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  