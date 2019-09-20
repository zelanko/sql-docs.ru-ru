---
title: Включение обновляемых подписок для публикации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, enabling
- subscriptions [SQL Server replication], updatable
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e10891c4627c881f9ef8f9cb9c9ae81b61c8f17
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846729"
---
# <a name="enable-updating-subscriptions-for-transactional-publications"></a>Включение обновляемых подписок для публикаций транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается включение обновляемых подписок для публикаций транзакций в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> **ПРИМЕЧАНИЕ.** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Включение обновляемых подписок для публикаций транзакций производится на странице **Тип публикации** мастера создания публикаций.  
  
 Для использования обновляемых подписок необходимо также настроить параметры в мастере создания подписки.  
  
#### <a name="to-enable-updating-subscriptions"></a>Включение обновляемых подписок  
  
1.  На странице **Тип публикации** мастера создания публикаций выберите **Публикация транзакций с обновляемыми подписками**.  
  
2.  На странице **Безопасность агентов** укажите настройки безопасности агента чтения очереди в дополнение к агенту моментальных снимков и агенту чтения журнала. Дополнительные сведения о разрешениях, необходимых для учетной записи, под которой запускается агент чтения очереди, см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    > **NOTE:** The Queue Reader Agent is configured even if you use only immediate updating subscriptions.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 При создании публикации транзакций программным путем при помощи хранимых процедур репликации подписки на нее могут быть настроены как на немедленное обновление, так и на обновление посредством очередей.  
  
#### <a name="to-create-a-publication-that-supports-immediate-updating-subscriptions"></a>Создание публикации с поддержкой немедленно обновляемых подписок  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если неизвестно, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) на издателе в базе данных издателя. Если результирующий набор пуст, то необходимо создать задание агента чтения журнала.  
  
    -   На издателе выполните процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите в параметрах **\@job_name** и **\@password** учетные данные [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, с которыми работает агент. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**.  
  
2.  Выполните [sp_addpublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **true** для параметра **\@allow_sync_tran**.  
  
3.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, используемое в шаге 2, в параметре **\@publication**, а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **\@job_name** и **\@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
4.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Создайте на подписчике обновляемую подписку на эту публикацию.   
  
#### <a name="to-create-a-publication-that-supports-queued-updating-subscriptions"></a>Создание публикации с поддержкой обновления подписок посредством очередей  
  
1.  В случае необходимости создайте задание агента чтения журнала для базы данных публикации.  
  
    -   Если задание агента чтения журнала для базы данных публикации уже существует, переходите к шагу 2.  
  
    -   Если вы не уверены, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) в издателе в базе данных публикации. Если результирующий набор пуст, необходимо создать задание агента чтения журнала.  
  
    -   На издателе выполните процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите в параметрах **\@job_name** и **\@password** учетные данные Windows, с которыми работает агент. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**.  
  
2.  Если необходимо, создайте на распространителе задание агента чтения очереди.  
  
    -   Если он уже существует для указанной базы данных распространителя, то перейдите к шагу 3.  
  
    -   Чтобы выяснить, существует ли в базе данных распространителя задание агента чтения очереди, запустите в ней хранимую процедуру [sp_helpqreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md). Если результирующий набор пуст, то задание агента чтения очереди необходимо создать.  
  
    -   В распространителе выполните хранимую процедуру [sp_helpqreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Укажите в параметрах **\@job_name** и **\@password** учетные данные Windows, с которыми работает агент. Указанные учетные данные используются при подключении агента чтения очереди к издателю или подписчику. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
3.  Выполните хранимую процедуру [sp_addpublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **true** в параметре **\@allow_queued_tran** и значение **pub wins**, **sub reinit** или **sub wins** в параметре **\@conflict_policy**.  
  
4.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся в шаге 3, в параметре **\@publication**, а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **\@snapshot_job_name** и **\@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
5.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Создайте на подписчике обновляемую подписку на эту публикацию.  
  
#### <a name="to-change-the-conflict-policy-for-a-publication-that-allows-queued-updating-subscriptions"></a>Изменение политики разрешения конфликтов для публикации с поддержкой обновления подписок посредством очередей  
  
1.  В издателе в базе данных публикации выполните процедуру [sp_changepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите значение **conflict_policy** в параметре **\@property** и нужный режим политики конфликтов **pub wins**, **sub reinit** или **sub wins** в параметре **\@value**.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается публикация, поддерживающая оба режима обновления подписок по запросу: немедленное и посредством очередей.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка параметров разрешения конфликтов для обновления посредством очередей](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Репликация транзакций](../../../relational-databases/replication/transactional/transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
