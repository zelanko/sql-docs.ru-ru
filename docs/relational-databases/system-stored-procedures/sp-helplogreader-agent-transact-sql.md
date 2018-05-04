---
title: sp_helplogreader_agent (Transact-SQL) | Документы Microsoft
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
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e45bef5198bc90cc7838dcdc56147c8d1c3d3551
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelplogreaderagent-transact-sql"></a>sp_helplogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает свойства задания агента чтения журнала для базы данных публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publisher**=] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента.|  
|**name**|**Nvarchar(100)**|Имя агента.|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при соединении с издателем, который может быть одним из следующих:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows.|  
|**publisher_login**|**sysname**|Имя входа в систему, используемое при соединении с издателем.|  
|**publisher_password**|**nvarchar(524)**|По соображениям безопасности значение **\* \* \* \* \* \* \* \* \* \*** всегда возвращается.|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания агента.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, под которой запускается агент чтения журнала, который возвращается в формате *домена*\\*username*.|  
|**job_password**|**sysname**|По соображениям безопасности значение **\* \* \* \* \* \* \* \* \* \*** всегда возвращается.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helplogreader_agent** используется в репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на издателе или члены **db_owner** предопределенной роли базы данных в базе данных публикации могут выполнять процедуру **sp_helplogreader_agent**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
