---
title: "Включение обновляемых подписок для публикации транзакций | Документация Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, enabling
- subscriptions [SQL Server replication], updatable
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: e989a795ff6179bdab183a2c7814f099b0448f38
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="enable-updating-subscriptions-for-transactional-publications"></a>Включение обновляемых подписок для публикаций транзакций
  В этом разделе описывается включение обновляемых подписок для публикаций транзакций в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> **ПРИМЕЧАНИЕ.** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Включение обновляемых подписок для публикаций транзакций производится на странице **Тип публикации** мастера создания публикаций.  
  
 Для использования обновляемых подписок необходимо также настроить параметры в мастере создания подписки.  
  
#### <a name="to-enable-updating-subscriptions"></a>Включение обновляемых подписок  
  
1.  На странице **Тип публикации** мастера создания публикаций выберите **Публикация транзакций с обновляемыми подписками**.  
  
2.  На странице **Безопасность агентов** укажите настройки безопасности агента чтения очереди в дополнение к агенту моментальных снимков и агенту чтения журнала. Дополнительные сведения о разрешениях, необходимых для учетной записи, под которой запускается агент чтения очереди, см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    > **Примечание.** Настройка агента чтения очереди осуществляется даже в том случае, если вы используете только немедленно обновляемые подписки.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 При создании публикации транзакций программным путем при помощи хранимых процедур репликации подписки на нее могут быть настроены как на немедленное обновление, так и на обновление посредством очередей.  
  
#### <a name="to-create-a-publication-that-supports-immediate-updating-subscriptions"></a>Создание публикации с поддержкой немедленно обновляемых подписок  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если вы не уверены, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) в издателе в базе данных публикации. Если результирующий набор пуст, то необходимо создать задание агента чтения журнала.  
  
    -   На издателе выполните процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите в параметрах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] @job_name **@job_name** @password **@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**.  
  
2.  Выполните [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **true** для параметра **@allow_sync_tran**.  
  
3.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 2, в параметре **@publication** , а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **@job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
4.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Создайте на подписчике обновляемую подписку на эту публикацию.   
  
#### <a name="to-create-a-publication-that-supports-queued-updating-subscriptions"></a>Создание публикации с поддержкой обновления подписок посредством очередей  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если вы не уверены, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) в издателе в базе данных публикации. Если результирующий набор пуст, необходимо создать задание агента чтения журнала.  
  
    -   На издателе выполните процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите в параметрах **@job_name** @password **@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**.  
  
2.  Если необходимо, создайте на распространителе задание агента чтения очереди.  
  
    -   Если он уже существует для указанной базы данных распространителя, то перейдите к шагу 3.  
  
    -   Чтобы выяснить, существует ли в базе данных распространителя задание агента чтения очереди, запустите в ней хранимую процедуру [sp_helpqreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md). Если результирующий набор пуст, то задание агента чтения очереди необходимо создать.  
  
    -   В распространителе выполните хранимую процедуру [sp_helpqreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Укажите в параметрах **@job_name** @password **@password**. Указанные учетные данные используются при подключении агента чтения очереди к издателю или подписчику. Дополнительные сведения см. в статье [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
3.  Выполните хранимую процедуру [sp_addpublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **true** в параметре **@allow_queued_tran** и значение **pub wins**, **sub reinit** или **sub wins** в параметре **@conflict_policy**.  
  
4.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 3, в параметре **@publication** , а учетные данные Windows, с которыми работает агент моментальных снимков, — для параметров **@snapshot_job_name** @password **@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** @password **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
5.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Создайте на подписчике обновляемую подписку на эту публикацию.  
  
#### <a name="to-change-the-conflict-policy-for-a-publication-that-allows-queued-updating-subscriptions"></a>Изменение политики разрешения конфликтов для публикации с поддержкой обновления подписок посредством очередей  
  
1.  В издателе в базе данных публикации выполните процедуру [sp_changepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите значение **conflict_policy** в параметре **@property** и задайте режим политики конфликтов, передав значение **pub wins**, **sub reinit**или **sub wins** в параметре **@value**.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В следующем примере создается публикация, поддерживающая оба режима обновления подписок по запросу: немедленное и посредством очередей.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка параметров разрешения конфликтов для обновления посредством очередей](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)   
 [Типы публикации для репликации транзакций](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](create-updatable-subscription-to-transactional-publication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
