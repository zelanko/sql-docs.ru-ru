---
title: sp_addqueued_artinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords:
- sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 25f91084afe2c2bdfc27bc0b2ad874bd87447b67
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769009"
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  Вместо **sp_addqueued_artinfo**следует использовать процедуру [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) . [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) создает скрипт, содержащий вызовы **sp_addqueued_artinfo** и **sp_addsynctrigger** .  
  
 Создает таблицу [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) на подписчике, которая используется для трассировки сведений о подписке статьи (обновление посредством очередей и немедленное обновление с обновлением посредством очередей при отработке отказа). Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addqueued_artinfo [ @artid= ] 'artid'  
        , [ @article= ] 'article'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @dest_table= ] 'dest_table'  
        , [ @owner = ] 'owner'  
        , [ @cft_table= ] 'cft_table'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @artid = ] 'artid'`Имя идентификатора статьи. *artid* имеет **тип int**и не имеет значения по умолчанию  
  
`[ @article = ] 'article'`Имя статьи, для которой создается скрипт. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию  
  
`[ @publisher = ] 'publisher'`Имя сервера издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации, для которой создается скрипт. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @dest_table = ] _'dest_table'`Имя целевой таблицы. *dest_table* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 **[@owner =** ] **"** _владелец_ **"**  
 Владелец подписки. Аргумент *owner* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @cft_table = ] 'cft_table'`Имя таблицы конфликтов обновления посредством очередей для этой статьи. *cft_table*имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_addqueued_artinfo** используется агент распространения в процессе инициализации подписки. Эта хранимая процедура, как правило, не запускается пользователями, но может быть полезна в случае, когда необходимо вручную установить подписку.  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) вместо **sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
