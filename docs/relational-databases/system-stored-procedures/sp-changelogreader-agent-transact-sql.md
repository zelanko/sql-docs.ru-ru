---
title: sp_changelogreader_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changelogreader_agent
- sp_changelogreader_agent_TSQL
helpviewer_keywords:
- sp_changelogreader_agent
ms.assetid: 929b2fa7-1267-41d0-8b69-e9ab26a62c0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf2a18543f6f5db30e36965c9e399968402292e1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68768880"
---
# <a name="sp_changelogreader_agent-transact-sql"></a>sp_changelogreader_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Изменяет свойства безопасности для агента чтения журнала. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changelogreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи, под которой выполняется агент. *job_login* имеет тип **nvarchar (257)** и значение по умолчанию NULL. На Управляемый экземпляр Базы данных SQL Azure используйте учетную запись SQL Server. *Его нельзя изменить для издателя, отличного от* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи, под которой выполняется агент. Аргумент *job_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* является **smallint**и ЗНАЧЕНИЕМ по умолчанию NULL. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности, а **1** — проверка подлинности Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем. Аргумент *publisher_login* имеет тип **sysname**и значение по умолчанию NULL. необходимо указать *publisher_login* , если *publisher_security_mode* равен **0**. Если *publisher_login* имеет значение null, а *publisher_security_mode* равен **1**, то при соединении с издателем используется учетная запись Windows, указанная в *job_login* .  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Не используйте пустые пароли. Выбирайте надежные пароли. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL. Этот аргумент поддерживается только для издателей, не являющихся издателями SQL Server.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changelogreader_agent** используется в репликации транзакций.  
  
 **sp_changelogreader_agent** используется для изменения учетной записи Windows, с которой запускается агент чтения журнала. Можно изменить пароль существующего имени входа в систему Windows или ввести новое имя пользователя Windows и пароль.  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_changelogreader_agent**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)   
 [sp_addlogreader_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
