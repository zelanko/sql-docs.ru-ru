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
ms.openlocfilehash: 1b0a20e2bc7a167698353db31e7c0411fb1a6961
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769143"
---
# <a name="spaddmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Параметр *Publisher* имеет тип **sysname**и имя локального сервера по умолчанию. Издатель должен быть действительным сервером.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. *publisher_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_type = ] 'subscriber_type'`Тип подписчика. *subscriber_type* имеет тип **nvarchar (15)** и может быть **глобальным**, **локальным** или **анонимным**. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях локальные подписки называются клиентскими подписками, а глобальные подписки — серверными подписками.  
  
`[ @subscription_priority = ] subscription_priority`Приоритет подписки. *subscription_priority*является **реальным**и имеет значение по умолчанию NULL. Для локальных и анонимных подписок приоритет равен **0,0**. При обнаружении конфликтов применяемый по умолчанию сопоставитель выбирает победителя исходя из приоритетов. Для глобальных подписчиков приоритет подписки должен быть меньше 100, который является приоритетом издателя.  
  
`[ @sync_type = ] 'sync_type'`Тип синхронизации подписки. *sync_type*имеет тип **nvarchar (15)** и значение по умолчанию **Automatic**. Может быть **автоматическим** или **нет**. При **автоматическом**создании схемы и начальные данные для опубликованных таблиц сначала передаются подписчику. Если **нет**, предполагается, что подписчик уже имеет схему и начальные данные для опубликованных таблиц. Системные таблицы и данные переносятся всегда.  
  
> [!NOTE]  
>  Не рекомендуется указывать значение **None**.  
  
`[ @description = ] 'description'`Краткое описание этой подписки по запросу. *Description*имеет тип **nvarchar (255)** и значение по умолчанию NULL. Это значение отображается монитором репликации в столбце Понятное **имя** , который можно использовать для сортировки подписок для отслеживаемой публикации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepullsubscription** используется для репликации слиянием.  
  
 Если для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синхронизации подписки используется агент, хранимая процедура [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) должна выполняться на подписчике, чтобы создать агент и задание для синхронизации с публикацией.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergepullsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
