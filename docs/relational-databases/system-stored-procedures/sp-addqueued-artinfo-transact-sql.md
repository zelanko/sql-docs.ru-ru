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
manager: craigg
ms.openlocfilehash: c326a8e3a5fa2bd95f536d434ff9782952ba70d3
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590899"
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) процедура должна использоваться вместо **sp_addqueued_artinfo**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) формирует скрипт, который содержит **sp_addqueued_artinfo** и **sp_addsynctrigger** вызовов.  
  
 Создает [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) таблицы на подписчике, который используется для отслеживания сведений о подписке статью (обновление посредством очередей и немедленное обновление с очередями переход на другой ресурс). Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
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
 [  **@artid=** ] **"**_artid_**"**  
 Имя идентификатора статьи. *artid* — **int**, не имеет значения по умолчанию  
  
 [  **@article=**] **"**_статье_**"**  
 Имя статьи, для которой создается скрипт. *статья* — **sysname**, не имеет значения по умолчанию  
  
 [  **@publisher=**] **"**_издателя_**"**  
 Имя сервера издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=**] **"**_publisher_db_**"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication=**] **"**_публикации_**"**  
 Имя публикации, для которой создается скрипт. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@dest_table=** ] _"dest_table_**"**  
 Имя целевой таблицы. *dest_table* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@owner =** ] **"**_владельца_**"**  
 Владелец подписки. *владелец* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@cft_table=** ] **"**_cft_table_**"**  
 Имя таблицы конфликтов обновления посредством очереди для данной статьи. *cft_table*— **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addqueued_artinfo** используется агентом распространителя как часть инициализации подписки. Эта хранимая процедура, как правило, не запускается пользователями, но может быть полезна в случае, когда необходимо вручную установить подписку.  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) вместо **sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
