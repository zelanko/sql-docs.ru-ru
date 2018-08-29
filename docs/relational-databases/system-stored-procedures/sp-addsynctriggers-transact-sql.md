---
title: sp_addsynctriggers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords:
- sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 229daeed8cc9c38fc1379565d3f1acffd83317ec
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032574"
---
# <a name="spaddsynctriggers-transact-sql"></a>sp_addsynctriggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает триггеры на подписчике, которые используются всеми типами обновляемых подписок (немедленного обновления, обновления посредством очередей и немедленного обновления с переходом на обновление посредством очередей при отработке отказа). Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
> [!IMPORTANT]  
>  [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) процедура должна использоваться вместо **sp_addsynctrigger**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) формирует скрипт, который содержит **sp_addsynctrigger** вызовов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addsynctriggers [ @sub_table = ] 'sub_table'  
        , [ @sub_table_owner = ] 'sub_table_owner'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @ins_proc = ] 'ins_proc'   
        , [ @upd_proc = ] 'upd_proc'   
        , [ @del_proc = ] 'del_proc'   
        , [ @cftproc = ] 'cftproc'  
        , [ @proc_owner = ] 'proc_owner'  
    [ , [ @identity_col = ] 'identity_col' ]  
    [ , [ @ts_col = ] 'timestamp_col' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]   
        , [ @primary_key_bitmap = ] 'primary_key_bitmap'  
    [ , [ @identity_support = ] identity_support ]  
    [ , [ @independent_agent = ] independent_agent ]  
        , [ @distributor = ] 'distributor'   
    [ , [ @pubversion = ] pubversion  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@sub_table=**] **"***sub_table***"**  
 Имя таблицы подписчика. *sub_table* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@sub_table_owner=**] **"***sub_table_owner***"**  
 Имя владельца таблицы подписчика. *sub_table_owner* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher=**] **"***издателя***"**  
 Имя сервера издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, не имеет значения по умолчанию. Если значение равно NULL, используется текущая база данных.  
  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@ins_proc=**] **"***ins_proc***"**  
 Имя хранимой процедуры, которая поддерживает синхронные вставки транзакций на издателе. *ins_proc* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@upd_proc=**] **"***upd_proc***"**  
 Имя хранимой процедуры, которая поддерживает синхронные обновления транзакций на издателе. *ins_proc* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@del_proc=**] **"***del_proc***"**  
 Имя хранимой процедуры, которая поддерживает синхронные удаления транзакций на издателе. *ins_proc* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@cftproc =** ] **"***cftproc***"**  
 Имя автоматически формируемой процедуры, используемой публикациями, поддерживающими обновление посредством очереди. *cftproc* — **sysname**, не имеет значения по умолчанию. Для публикаций, поддерживающих немедленное обновление, значением этого аргумента является NULL. Этот параметр относится к публикациям, поддерживающим обновление посредством очередей (обновление посредством очередей и немедленное обновление с переходом на обновление посредством очередей при отработке отказа).  
  
 [  **@proc_owner =** ] **"***proc_owner***"**  
 Указывает учетную запись пользователя на издателе, от имени которой создаются все автоматически формируемые хранимые процедуры для обновления публикации (посредством очереди или немедленно). *proc_owner* — **sysname** не имеет значения по умолчанию.  
  
 [  **@identity_col=**] **"***identity_col***"**  
 Имя столбца идентификаторов на издателе. *identity_col* — **sysname**, значение по умолчанию NULL.  
  
 [  **@ts_col=**] **"***timestamp_col***"**  
 Имя **timestamp** столбца на издателе. *timestamp_col* — **sysname**, значение по умолчанию NULL.  
  
 [  **@filter_clause=**] **"***filter_clause***"**  
 Предложение ограничения (WHERE), которое задает горизонтальный фильтр. При вводе предложения ограничения опустите ключевое слово WHERE. *filter_clause*— **nvarchar(4000)**, значение по умолчанию NULL.  
  
 [  **@primary_key_bitmap =**] **"***primary_key_bitmap***"**  
 Битовая схема столбцов первичного ключа в таблице. *primary_key_bitmap* — **varbinary(4000)**, не имеет значения по умолчанию.  
  
 [  **@identity_support =** ] *identity_support*  
 Включает и выключает автоматическую обработку диапазона идентификаторов при использовании обновления посредством очереди. *identity_support* — **бит**, значение по умолчанию **0**. **0** поддержки, диапазона означает, что удостоверение не **1** включает автоматическую обработку диапазона идентификаторов.  
  
 [  **@independent_agent =** ] *independent_agent*  
 Указывает, используется ли для данной публикации отдельный агент распространителя (независимый агент) или используется один агент распространителя для каждой пары базы данных публикации и базы данных подписки (общий агент). Это значение отражает значение свойства independent_agent для публикации, определенной на издателе. *independent_agent* имеет тип bit и значение по умолчанию **0**. Если **0**, агент является общим. Если **1**, агент является независимым.  
  
 [  **@distributor =** ] **"***распространителя***"**  
 Имя распространителя. *распространитель* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@pubversion**=] *pubversion*  
 Указывает версию издателя. *pubversion* — **int**, значение по умолчанию 1. **1** означает, что версия издателя — [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] пакет обновления 2 или более ранних версий; **2** означает, что издатель является [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] пакет обновления 3 (SP3) или более поздней версии. *pubversion* необходимо явно присвоить **2** Если версия издателя — [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SP3 или более поздней версии.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addsynctriggers** используется агентом распространителя как часть инициализации подписки. Как правило, пользователи не запускают эту хранимую процедуру, но она может быть полезной при необходимости ручной установки подписки без синхронизации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addsynctriggers**.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
