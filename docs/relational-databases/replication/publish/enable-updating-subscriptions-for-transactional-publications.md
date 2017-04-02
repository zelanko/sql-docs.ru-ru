---
title: "Включение обновляемых подписок для публикаций транзакций | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "репликация транзакций, обновляемые подписки"
  - "обновляемые подписки, включение"
  - "подписки [репликация SQL Server], обновляемые"
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Включение обновляемых подписок для публикаций транзакций
  В этом разделе описывается включение обновляемых подписок для публикаций транзакций в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> **ПРИМЕЧАНИЕ.** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Включение обновляемых подписок для публикаций транзакций производится на странице **Тип публикации** мастера создания публикаций.  
  
 Для использования обновляемых подписок необходимо также настроить параметры в мастере создания подписки.  
  
#### Включение обновляемых подписок  
  
1.  На странице **Тип публикации** мастера создания публикаций выберите **Публикация транзакций с обновляемыми подписками**.  
  
2.  На странице **Безопасность агентов** укажите настройки безопасности агента чтения очереди в дополнение к агенту моментальных снимков и агенту чтения журнала. Дополнительные сведения о разрешениях, необходимых для учетной записи, под которой запускается агент чтения очереди, см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    > **Примечание:** настроен агент чтения очереди, даже при использовании только подписок, обновляемых немедленно.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 При создании публикации транзакций программным путем при помощи хранимых процедур репликации подписки на нее могут быть настроены как на немедленное обновление, так и на обновление посредством очередей.  
  
#### Создание публикации с поддержкой немедленно обновляемых подписок  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если вы не знаете, существует ли задание агента чтения журнала для опубликованной базы данных, выполнение [sp_helplogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) на издателе в базе данных публикации. Если результирующий набор пуст, то необходимо создать задание агента чтения журнала.  
  
    -   На издателе, хранимую [sp_addlogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите [!INCLUDE[msCoName](../../../includes/msconame-md.md)] учетные данные Windows, под которыми работает агент **@job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**.  
  
2.  Выполнение [sp_addpublication &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **true** для параметра **@allow_sync_tran**.  
  
3.  На издателе, хранимую [sp_addpublication_snapshot &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 2 для **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
4.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Создайте на подписчике обновляемую подписку на эту публикацию.   
  
#### Создание публикации с поддержкой обновления подписок посредством очередей  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если вы не знаете, существует ли задание агента чтения журнала для опубликованной базы данных, выполнение [sp_helplogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) на издателе в базе данных публикации. Если результирующий набор пуст, необходимо создать задание агента чтения журнала.  
  
    -   На издателе, хранимую [sp_addlogreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите учетные данные Windows, под которыми работает агент **@job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**.  
  
2.  Если необходимо, создайте на распространителе задание агента чтения очереди.  
  
    -   Если он уже существует для указанной базы данных распространителя, то перейдите к шагу 3.  
  
    -   Если вы не знаете, существует ли задание агента чтения очереди для базы данных распространителя, выполните [sp_helpqreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md) на распространителе в базе данных распространителя. Если результирующий набор пуст, то задание агента чтения очереди необходимо создать.  
  
    -   На распространителе выполните хранимую процедуру [sp_addqreader_agent &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Укажите учетные данные Windows, под которыми работает агент **@job_name** и **@password**. Указанные учетные данные используются при подключении агента чтения очереди к издателю или подписчику. Дополнительные сведения см. в статье [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
3.  Выполнение [sp_addpublication &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **true** для параметра **@allow_queued_tran** и значение **pub wins**, **sub reinit**, или **sub wins** для **@conflict_policy**.  
  
4.  На издателе, хранимую [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 3 для **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@snapshot_job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
5.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Создайте на подписчике обновляемую подписку на эту публикацию.  
  
#### Изменение политики разрешения конфликтов для публикации с поддержкой обновления подписок посредством очередей  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changepublication &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите значение **conflict_policy** для **@property** и задайте режим политики конфликтов из **pub wins**, **sub reinit**, или **sub wins** для **@value**.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В следующем примере создается публикация, поддерживающая оба режима обновления подписок по запросу: немедленное и посредством очередей.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## См. также:  
 [Задание параметров разрешения конфликтов в очереди обновления &#40; SQL Server Management Studio &#41;](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)   
 [Типы публикации для репликации транзакций](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [Обновляемые подписки для репликации транзакций](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Создание обновляемых подписок для публикаций транзакций](https://msdn.microsoft.com/library/mt740635.aspx)   
 [Обновляемые подписки для репликации транзакций](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  