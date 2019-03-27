---
title: sp_addmergepullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords:
- sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 59e639c1dd319d7db074d692d3776105abe89f0f
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493746"
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
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'` — Имя издателя. *Издатель* — **sysname**, значение по умолчанию имя локального сервера. Издатель должен быть действительным сервером.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL.  
  
`[ @subscriber_type = ] 'subscriber_type'` — Это тип подписчика. *subscriber_type* — **nvarchar(15)** и может быть **глобального**, **локального** или **анонимный**. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях локальные подписки называются клиентскими подписками, а глобальные подписки — серверными подписками.  
  
`[ @subscription_priority = ] subscription_priority` — Это приоритет подписки. *subscription_priority*— **реальных**, значение по умолчанию NULL. Для локальных и анонимных подписок приоритет равен **0,0**. При обнаружении конфликтов применяемый по умолчанию сопоставитель выбирает победителя исходя из приоритетов. Для глобальных подписчиков приоритет подписки должен быть меньше 100, который является приоритетом издателя.  
  
`[ @sync_type = ] 'sync_type'` — Это тип синхронизации подписки. *sync_type*— **nvarchar(15)**, значение по умолчанию **автоматического**. Может быть **автоматического** или **none**. Если **автоматического**, схема и начальные данные для опубликованных таблиц передаются подписчику сначала. Если **none**, он считается подписчик уже имеет схему и начальные данные для опубликованных таблиц. Системные таблицы и данные переносятся всегда.  
  
> [!NOTE]  
>  Мы не рекомендуем значение **none**.  
  
`[ @description = ] 'description'` Представляет собой краткое описание этой подписки по запросу. *Описание*— **nvarchar(255)**, значение по умолчанию NULL. Это значение отображается в мониторе репликации в **понятное имя** столбец, который может использоваться для сортировки подписок для контролируемой публикации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepullsubscription** используется для репликации слиянием.  
  
 При использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента для синхронизации подписки, [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) хранимая процедура должна выполняться на подписчике для создания агента и задания для синхронизации с публикацией.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergepullsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
