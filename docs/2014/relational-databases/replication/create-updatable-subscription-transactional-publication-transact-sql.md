---
title: Создание обновляемой подписки на публикацию транзакций, с помощью Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- updatable transactional subscriptions, T-SQL
ms.assetid: 670e1ea0-ffda-4d84-b4cd-f15a331035b9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ca1fe049e243fc94d07707564dde501e646597d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082064"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-using-transact-sql"></a>Создание обновляемой подписки для публикации транзакций с использованием Transact-SQL

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
Репликация транзакций позволяет распространять изменения, выполненные на подписчике, обратно на издатель с помощью немедленно обновляемых подписок или обновляемых посредством очередей подписок. Можно создать обновляемую подписку программно с помощью хранимых процедур репликации. (См. также раздел [Создание обновляемой подписки для публикации транзакций (среда Management Studio)](publish/create-an-updatable-subscription-to-a-transactional-publication.md).) 

## <a name="to-create-an-immediate-updating-pull-subscription"></a>Создание немедленно обновляемой подписки по запросу ##

1. Проверьте на издателе, что публикация поддерживает немедленное обновление подписок. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `1`, то публикация поддерживает немедленное обновление подписок.

    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `0`, публикацию необходимо создать заново с включенной возможностью немедленного обновления подписок.

2. Проверьте на издателе, что публикация поддерживает подписки по запросу. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_pull` в результирующем наборе равно `1`, то публикация поддерживает подписки по запросу.

    * Если `allow_pull` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение `allow_pull` для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)на подписчике. Задайте `@publisher` и `@publication`, а также установите одно из следующих значений для `@update_mode`:

    * `sync tran` — включает подписку для немедленного обновления;

    * `failover` — включает для подписки немедленное обновление, с обновлением посредством очередей в случае отработки отказа;

    > [!NOTE]  
>  `failover` — требует, чтобы для публикации были включены обновляемые посредством очередей подписки. 
 
4. Выполните процедуру [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)на подписчике. Укажите следующее.

    * Параметры `@publisher`, `@publisher_db`и `@publication` . 

    * Учетные данные пользователя Microsoft Windows, от имени которого на подписчике запускается агент распространителя, в качестве значений параметров `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент соединяется с распространителем с использованием встроенной проверки подлинности Windows. 
 
    * (Необязательно) Значение `0` для параметра `@distributor_security_mode` и данные входа Microsoft SQL Server для параметров `@distributor_login` и `@distributor_password`, если для соединения с распространителем нужно использовать проверку подлинности SQL Server. 

    * Расписание задания агента распространителя для этой подписки. 

5. В базе данных подписки на подписчике выполните процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Укажите параметр `@publisher`, параметр `@publication`, имя базы данных публикации в параметре `@publisher_db`и одно из следующих значений параметра `@security_mode`. 

    * `0` — Использовать проверку подлинности SQL Server при выполнении обновлений на издателе. При этом необходимо указать допустимое имя входа на издатель в параметрах `@login` и `@password`.

    * `1` — При соединении с издателем использовать контекст безопасности пользователя, выполняющего изменения на подписчике. Связанные с этим режимом безопасности ограничения см. в разделе [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) .

    * `2` — Использовать существующее определенное пользователем имя входа на связанный сервер, созданное с помощью процедуры [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).

6. Выполните на издателе хранимую процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) , указав параметры `@publication`, `@subscriber`, `@destination_db`, значение pull в параметре `@subscription_type`и значение, указанное в шаге 3, в параметре `@update_mode`.

Подписка по запросу на издателе будет зарегистрирована. 


## <a name="to-create-an-immediate-updating-push-subscription"></a>Создание немедленно обновляемой принудительной подписки ##

1. Проверьте на издателе, что публикация поддерживает немедленное обновление подписок. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `1`, то публикация поддерживает немедленное обновление подписок.

    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `0`, публикацию необходимо создать заново с включенной возможностью немедленного обновления подписок.

2. Проверьте на издателе, что публикация поддерживает принудительные подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_push` в результирующем наборе равно `1`, то публикация поддерживает принудительные подписки.

    * Если `allow_push` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение `allow_push` для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)на издателе. Задайте `@publication`, `@subscriber`и `@destination_db`, а также установите одно из следующих значений для `@update_mode`:

    * `sync tran` — включает поддержку немедленного обновления;

    * `failover` — включает поддержку немедленного обновления с обновлением посредством очередей при отработке отказа;

    > [!NOTE]  
>  `failover` — требует, чтобы для публикации были включены обновляемые посредством очередей подписки. 
 
4. Выполните процедуру [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)на издателе. Укажите значения следующих параметров.

    * `@subscriber`, `@subscriber_db`и `@publication`. 

    * Учетные данные Windows, с которыми будет запускаться агент распространителя на распространителе, в параметрах `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows; 

    * (Необязательно) Значение `0` для параметра `@subscriber_security_mode` и данные входа SQL Server для параметров `@subscriber_login` и `@subscriber_password`, если для соединения с подписчиком нужно использовать проверку подлинности SQL Server. 

    * Расписание задания агента распространителя для этой подписки.

5. В базе данных подписки на подписчике выполните процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Укажите параметр `@publisher`, параметр `@publication`, имя базы данных публикации в параметре `@publisher_db`и одно из следующих значений параметра `@security_mode`. 

     * `0` — Использовать проверку подлинности SQL Server при выполнении обновлений на издателе. При этом необходимо указать допустимое имя входа на издатель в параметрах `@login` и `@password`.

     * `1` — При соединении с издателем использовать контекст безопасности пользователя, выполняющего изменения на подписчике. Связанные с этим режимом безопасности ограничения см. в разделе [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) .

     * `2` — Использовать существующее определенное пользователем имя входа на связанный сервер, созданное с помощью процедуры [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).


## <a name="to-create-a-queued-updating-pull-subscription"></a>Создание обновляемой посредством очередей подписки по запросу ##

1. Проверьте на издателе, что публикация поддерживает обновляемые посредством очередей подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение параметра `allow_queued_tran` в результирующем наборе равно `1`, то публикация поддерживает немедленное обновление подписок.

    * Если значение параметра `allow_queued_tran` в результирующем наборе равно `0`, публикацию необходимо создать заново с включенной возможностью обновления подписок посредством очередей.

2. Проверьте на издателе, что публикация поддерживает подписки по запросу. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_pull` в результирующем наборе равно `1`, то публикация поддерживает подписки по запросу.

    * Если `allow_pull` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение `allow_pull` для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)на подписчике. Задайте `@publisher` и `@publication`, а также установите одно из следующих значений для `@update_mode`:

    * `queued tran` — включает возможность обновления подписок посредством очередей;

    * `queued failover` — включает поддержку обновления посредством очередей с немедленным обновлением в качестве варианта для отработки отказа;

    > [!NOTE]  
>  `queued failover` — требует, чтобы для публикации также были включены немедленно обновляемые подписки. Чтобы переключиться на немедленное обновление, необходимо использовать процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) для определения учетных данных, с которыми изменения на подписчике реплицируются на издатель.
 
4. Выполните процедуру [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)на подписчике. Укажите значения следующих параметров.

    * @publisher, `@publisher_db`и `@publication`. 

    * Учетные данные Windows, с которыми будет запускаться агент распространителя на подписчике, в параметрах `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент соединяется с распространителем с использованием встроенной проверки подлинности Windows. 
 
    * (Необязательно) Значение `0` для параметра `@distributor_security_mode` и данные входа SQL Server для параметров `@distributor_login` и `@distributor_password`, если для соединения с распространителем нужно использовать проверку подлинности SQL Server. 

    * Расписание задания агента распространителя для этой подписки.

5. Выполните на издателе хранимую процедуру [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) для регистрации подписчика на издателе, указав параметры `@publication`, `@subscriber`, `@destination_db`, значение pull в параметре `@subscription_type`и значение, указанное в шаге 3, в параметре `@update_mode`.

Подписка по запросу на издателе будет зарегистрирована. 


## <a name="to-create-a-queued-updating-push-subscription"></a>Создание принудительной подписки, обновляемой посредством очередей ##

1. Проверьте на издателе, что публикация поддерживает обновляемые посредством очередей подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение allow_queued_tran в результирующем наборе равно 1, то публикация поддерживает немедленное обновление подписок.

    * Если значение allow_queued_tran в результирующем наборе равно 0, публикацию необходимо создать заново с включенной возможностью обновления подписок посредством очередей. Дополнительные сведения см. в разделе "Включение обновляемых подписок для публикаций транзакций (программирование репликации на языке Transact-SQL)".

2. Проверьте на издателе, что публикация поддерживает принудительные подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_push` в результирующем наборе равно `1`, то публикация поддерживает принудительные подписки.

    * Если `allow_push` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение allow_push для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)на издателе. Задайте `@publication`, `@subscriber`и `@destination_db`, а также установите одно из следующих значений для `@update_mode`:

    * `queued tran` — включает возможность обновления подписок посредством очередей;

    * `queued failover` — включает поддержку обновления посредством очередей с немедленным обновлением в качестве варианта для отработки отказа;

    > [!NOTE]  
>  Параметр queued failover требует, чтобы для публикации также были включены немедленно обновляемые подписки. Чтобы переключиться на немедленное обновление, необходимо использовать процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) для определения учетных данных, с которыми изменения на подписчике реплицируются на издатель.

4. Выполните процедуру [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)на издателе. Укажите значения следующих параметров.

    * `@subscriber`, `@subscriber_db`и `@publication`. 

    * Учетные данные Windows, с которыми будет запускаться агент распространителя на распространителе, в параметрах `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику с помощью встроенной проверки подлинности Windows. 
 
    * (Необязательно) Значение `0` для параметра `@subscriber_security_mode` и данные входа SQL Server для параметров `@subscriber_login` и `@subscriber_password`, если для соединения с подписчиком нужно использовать проверку подлинности SQL Server. 

    * Расписание задания агента распространителя для этой подписки.


## <a name="example"></a>Пример ##

В этом примере создается немедленно обновляемая подписка по запросу на публикацию, поддерживающую немедленно обновляемые подписки. Имя входа и пароль предоставляются во время выполнения переменными сценария sqlcmd.

> [!NOTE]  
>  Этот скрипт использует переменные скрипта sqlcmd. Они представлены в виде `$(MyVariable)`. Сведения об использовании переменных скрипта в командной строке и среде SQL Server Management Studio см. в подразделе **Выполнение скриптов репликации** раздела [Основные понятия системных хранимых процедур репликации](concepts/replication-system-stored-procedures-concepts.md).

```
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="see-also"></a>См. также ##

[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)

[Использование программы sqlcmd с переменными скрипта](../scripting/sqlcmd-use-with-scripting-variables.md)

[Создание обновляемой подписки для публикации транзакций (среда Management Studio)](publish/create-an-updatable-subscription-to-a-transactional-publication.md)
