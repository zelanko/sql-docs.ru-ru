---
title: "sp_addmergepullsubscription (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords: sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64af301fda7ee871c30611698b1385fa8bd318f0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет подписку по запросу к публикации слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepullsubscription [ @publication= ] 'publication'   
    [ , [ @publisher= ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @subscriber_type= ] 'subscriber_type' ]   
    [ , [ @subscription_priority= ] subscription_priority ]   
    [ , [ @sync_type= ] 'sync_type' ]   
    [ , [ @description= ] 'description' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher=**] **"***издатель***"**  
 Имя издателя. *Издатель* — **sysname**, значение по умолчанию имя локального сервера. Издатель должен быть действительным сервером.  
  
 [  **@publisher_db =**] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_type=**] **"***subscriber_type***"**  
 Тип подписчика. *subscriber_type* — **nvarchar(15)**и может быть **глобальной**, **локального** или **анонимный**. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях локальные подписки называются клиентскими подписками, а глобальные подписки — серверными подписками.  
  
 [  **@subscription_priority=**] *subscription_priority*  
 Приоритет подписки. *subscription_priority*— **реальные**, значение по умолчанию NULL. Для локальных и анонимных подписок приоритет равен **0,0**. При обнаружении конфликтов применяемый по умолчанию сопоставитель выбирает победителя исходя из приоритетов. Для глобальных подписчиков приоритет подписки должен быть меньше 100, который является приоритетом издателя.  
  
 [  **@sync_type=**] **"***sync_type***"**  
 Тип синхронизации подписки. *sync_type*— **nvarchar(15)**, значение по умолчанию **автоматического**. Может быть **автоматического** или **нет**. Если **автоматического**, схема и начальные данные для опубликованных таблиц переносятся подписчику сначала. Если **нет**, предполагается, что подписчик уже имеет схему и начальные данные для опубликованных таблиц. Системные таблицы и данные переносятся всегда.  
  
> [!NOTE]  
>  Не рекомендуется указывать значение **нет**.  
  
 [  **@description=**] **"***описание***"**  
 Краткое описание этой подписки по запросу. *Описание*— **nvarchar(255)**, значение по умолчанию NULL. Это значение отображается в мониторе репликации в **понятное имя** столбец, который может использоваться для сортировки подписок для контролируемой публикации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addmergepullsubscription** используется для репликации слиянием.  
  
 При использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента для синхронизации подписки, [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) хранимая процедура должна выполняться на стороне подписчика для создания агента и задания для синхронизации с публикацией.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addmergepullsubscription**.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
