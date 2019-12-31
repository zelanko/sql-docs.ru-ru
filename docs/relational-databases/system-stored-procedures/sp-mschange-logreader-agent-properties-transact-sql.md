---
title: sp_MSchange_logreader_agent_properties (T-SQL)
description: Описывает sp_MSchange_logreader_agent_properties хранимую процедуру, используемую для изменения свойств агент чтения журнала для топологии Репликация SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords:
- sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 37a36218b4e9e93a761c776e76a6596f40a6c0eb
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322291"
---
# <a name="sp_mschange_logreader_agent_properties-transact-sql"></a>sp_MSchange_logreader_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства задания агент чтения журнала, выполняемого на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] распространителе или более поздней версии. Эта хранимая процедура используется для изменения свойств, если издатель запущен на экземпляре [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [соглашения о синтаксисе Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_MSchange_logreader_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Режим безопасности, используемый агентом при соединении с издателем. *publisher_security_mode* имеет значение **smallint**и не имеет значения по умолчанию.  
  
 **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности.  
  
 **1** указывает проверку подлинности Windows.  
  
`[ @publisher_login = ] 'publisher_login'`Имя входа, используемое при соединении с издателем. Аргумент *publisher_login* имеет тип **sysname**и не имеет значения по умолчанию. необходимо указать *publisher_login* , если *publisher_security_mode* равен **0**. Если *publisher_login* имеет значение null, а *publisher_security_mode* равен **1**, то при соединении с издателем будет использоваться учетная запись Windows, указанная в *job_login* .  
  
`[ @publisher_password = ] 'publisher_password'`Пароль, используемый при соединении с издателем. Аргумент *publisher_password* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @job_login = ] 'job_login'`Имя входа для учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и не имеет значения по умолчанию. *Его нельзя изменить для издателя, отличного от* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*  
  
`[ @job_password = ] 'job_password'`Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_type = ] 'publisher_type'`Указывает тип издателя, если издатель не выполняется в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *publisher_type* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Используется издатель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**СУБД**|Задает стандартного издателя Oracle.|  
|**ORACLE GATEWAY.**|Используется издатель Oracle Gateway.|  
  
 Дополнительные сведения о различиях между издателем Oracle и издателем шлюза Oracle см. в разделе [Общие сведения о публикации Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="remarks"></a>Замечания  
 **sp_MSchange_logreader_agent_properties** используется в репликации транзакций.  
  
 При выполнении **sp_MSchange_logreader_agent_properties**необходимо указать все параметры. Выполните [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) , чтобы получить текущие свойства задания агент чтения журнала.  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
 При запуске издателя на экземпляре [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии следует использовать [sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md) для изменения свойств агент чтения журнала.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на распространителе могут выполнять **sp_MSchange_logreader_agent_properties**.  
  
## <a name="see-also"></a>См. также  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
