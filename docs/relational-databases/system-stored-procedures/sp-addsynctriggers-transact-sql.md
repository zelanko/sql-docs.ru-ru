---
description: sp_addsynctriggers (Transact-SQL)
title: sp_addsynctriggers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords:
- sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 400b6ef96cd841c2115fcb13bd5e8b782816ce43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486279"
---
# <a name="sp_addsynctriggers-transact-sql"></a>sp_addsynctriggers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Создает триггеры на подписчике, которые используются всеми типами обновляемых подписок (немедленного обновления, обновления посредством очередей и немедленного обновления с переходом на обновление посредством очередей при отработке отказа). Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
> [!IMPORTANT]  
>  Вместо **sp_addsynctrigger**следует использовать [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) процедуру. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) создает скрипт, содержащий вызовы **sp_addsynctrigger** .  
  
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
`[ @sub_table = ] 'sub_table'` Имя таблицы подписчика. Аргумент *sub_table* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @sub_table_owner = ] 'sub_table_owner'` Имя владельца таблицы подписчика. Аргумент *sub_table_owner* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'` Имя сервера издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию. Если значение равно NULL, используется текущая база данных.  
  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @ins_proc = ] 'ins_proc'` Имя хранимой процедуры, которая поддерживает синхронные вставки транзакций на издателе. Аргумент *ins_proc* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @upd_proc = ] 'upd_proc'` Имя хранимой процедуры, поддерживающей синхронные обновления транзакций на издателе. Аргумент *ins_proc* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @del_proc = ] 'del_proc'` Имя хранимой процедуры, поддерживающей синхронное удаление транзакций на издателе. Аргумент *ins_proc* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @cftproc = ] 'cftproc'` Имя автоматически создаваемой процедуры, используемой публикациями, допускающими обновление посредством очередей. *кфтпрок* имеет тип **sysname**и не имеет значения по умолчанию. Для публикаций, поддерживающих немедленное обновление, значением этого аргумента является NULL. Этот параметр относится к публикациям, поддерживающим обновление посредством очередей (обновление посредством очередей и немедленное обновление с переходом на обновление посредством очередей при отработке отказа).  
  
`[ @proc_owner = ] 'proc_owner'` Указывает учетную запись пользователя на издателе, для которой были созданы автоматически создаваемые хранимые процедуры для обновления публикации (в очереди и (или) интерпретации). *proc_owner* имеет тип **sysname** и не имеет значения по умолчанию.  
  
`[ @identity_col = ] 'identity_col'` Имя столбца идентификаторов на издателе. Аргумент *identity_col* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @ts_col = ] 'timestamp_col'` Имя столбца **меток времени** на издателе. Аргумент *timestamp_col* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @filter_clause = ] 'filter_clause'` Предложение ограничения (WHERE), определяющее горизонтальный фильтр. При вводе предложения ограничения опустите ключевое слово WHERE. *filter_clause*имеет тип **nvarchar (4000)** и значение по умолчанию NULL.  
  
`[ @primary_key_bitmap = ] 'primary_key_bitmap'` Является битовой картой первичных ключевых столбцов в таблице. *primary_key_bitmap* имеет тип **varbinary (4000)** и не имеет значения по умолчанию.  
  
`[ @identity_support = ] identity_support` Включает и отключает автоматическую обработку диапазона идентификаторов при использовании обновления посредством очередей. *identity_support* является **битом**и имеет значение по умолчанию **0**. **0** означает отсутствие поддержки диапазона идентификаторов, **1** включает автоматическую обработку диапазона идентификаторов.  
  
`[ @independent_agent = ] independent_agent` Указывает, существует ли один агент распространения (независимый агент) для этой публикации или один агент распространения на каждую базу данных публикации и пару баз данных подписки (общий агент). Это значение отражает значение свойства independent_agent для публикации, определенной на издателе. *independent_agent* является битом со значением по умолчанию **0**. Если значение **равно 0**, агент является общим агентом. Если значение равно **1**, то агент является независимым.  
  
`[ @distributor = ] 'distributor'` Имя распространителя. Аргумент *распространитель* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @pubversion = ] pubversion` Указывает версию издателя. *пубверсион* имеет **тип int**и значение по умолчанию 1. **1** означает, что версия издателя — [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] пакет обновления 2 (SP2) или более ранняя; **2** означает, что издатель является [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] пакетом обновления 3 (SP3) или более поздней версии. для *пубверсион* необходимо явно задать значение **2** , если версия издателя — [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SP3 или более поздняя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_addsynctriggers** используется агент распространения как часть инициализации подписки. Как правило, пользователи не запускают эту хранимую процедуру, но она может быть полезной при необходимости ручной установки подписки без синхронизации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addsynctriggers**.  
  
## <a name="see-also"></a>См. также:  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
