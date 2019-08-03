---
title: sp_addlogreader_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addlogreader_agent
- sp_addlogreader_agent_TSQL
helpviewer_keywords:
- sp_addlogreader_agent
ms.assetid: d83096b9-96ee-4789-bde0-940d4765b9ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a50b989afef382a8315c29ea5257ad9b103e124c
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769217"
---
# <a name="spaddlogreaderagent-transact-sql"></a>sp_addlogreader_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Добавляет агент чтения журнала в данную базу данных. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
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
`[ @job_login = ] 'job_login'`Имя входа для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и значение по умолчанию NULL. Для соединения агента с распространителем всегда используется эта учетная запись Windows.  
  
> [!NOTE]
>  Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей [!INCLUDE[msCoName](../../includes/msconame-md.md)] , отличных от, это должно быть одно и то же имя входа, указанное в [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. *job_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
`[ @job_name = ] 'job_name'`Имя существующего задания агента. Аргумент *имя_задания* имеет тип **sysname**и значение по умолчанию NULL. Этот аргумент указывается, только если агент запускается с использованием существующего задания, а не вновь созданного задания (выбор по умолчанию).  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* имеет значение **smallint**и значение по умолчанию **1**. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности, а **1** — проверка подлинности Windows. Значение **0** должно быть указано для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от.  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем. *publisher_login* имеет тип **sysname**и значение по умолчанию NULL. *publisher_login* должен быть указан, если *publisher_security_mode* имеет значение **0**. Если *publisher_login* имеет значение null, а *publisher_security_mode* — **1**, то при соединении с издателем будет использоваться учетная запись Windows, указанная в *job_login* .  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. *publisher_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не храните данные проверки подлинности в файлах скриптов. Для обеспечения лучшей защиты имена входа и пароли должны вводиться в ходе выполнения.  
  
`[ @publisher = ] 'publisher'`Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, не являющегося издателем. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Для издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот аргумент указывать не следует.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_addlogreader_agent** используется в репликации транзакций.  
  
 Необходимо выполнить **sp_addlogreader_agent** , чтобы добавить агент чтения журнала, если была обновлена база данных, для которой была включена репликация в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эту версию перед созданием публикации, которая использовала эту базу данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addlogreader_agent**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addlogreader-agent-tr_1.sql)]  
  
## <a name="see-also"></a>См. также  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changelogreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
