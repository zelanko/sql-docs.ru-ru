---
title: sp_addlogreader_agent (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_addlogreader_agent
- sp_addlogreader_agent_TSQL
helpviewer_keywords:
- sp_addlogreader_agent
ms.assetid: d83096b9-96ee-4789-bde0-940d4765b9ed
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b7758e5d34570fe6d837a535d14f6bd020934e0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spaddlogreaderagent-transact-sql"></a>sp_addlogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет агент чтения журнала в данную базу данных. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addlogreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@job_login**=] **"***job_login***"**  
 Имя входа для учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается агент. *job_login* — **nvarchar(257)**, значение по умолчанию NULL. Для соединения агента с распространителем всегда используется эта учетная запись Windows.  
  
> [!NOTE]  
>  Для не -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, это должно быть то же имя входа, указанное в [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 [ **@job_password**=] **"***job_password***"**  
 Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
 [ **@job_name**=] **"***job_name***"**  
 Имя существующего задания агента. *job_name* — **sysname**, значение по умолчанию NULL. Этот аргумент указывается, только если агент запускается с использованием существующего задания, а не вновь созданного задания (выбор по умолчанию).  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 Режим безопасности, используемый агентом при установке соединения с издателем. *publisher_security_mode* — **smallint**, значение по умолчанию **1**. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, и **1** указывает проверку подлинности Windows. Значение **0** должен быть указан для отличного[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
 [ **@publisher_login**=] **"***publisher_login***"**  
 Имя входа, используемое для соединения с издателем. *publisher_login* — **sysname**, значение по умолчанию NULL. *publisher_login* должен быть указан, если *publisher_security_mode* — **0**. Если *publisher_login* имеет значение NULL и *publisher_security_mode* — **1**, учетная запись Windows, указанная в *job_login* будет использоваться При соединении с издателем.  
  
 [ **@publisher_password**=] **"***publisher_password***"**  
 Пароль, используемый при соединении с издателем. *publisher_password* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
 [ **@publisher**=] **"***издатель***"**  
 Имя не[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Для издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот аргумент указывать не следует.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addlogreader_agent** используется в репликации транзакций.  
  
 Необходимо выполнить **sp_addlogreader_agent** добавить агент чтения журнала, при обновлении базы данных, которая была включена для репликации в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перед созданием публикация, использовавшая базу данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addlogreader_agent**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addlogreader-agent-tr_1.sql)]  
  
## <a name="see-also"></a>См. также  
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
