---
title: sp_MSchange_merge_agent_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_merge_agent_properties_TSQL
- sp_MSchange_merge_agent_properties
helpviewer_keywords:
- sp_MSchange_merge_agent_properties
ms.assetid: f775fa0f-28c7-4863-89ce-7bcfa1ab8b5e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 84c517fe891052ff6e12ee6e92a2d16d912a140b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905196"
---
# <a name="sp_mschange_merge_agent_properties-transact-sql"></a>sp_MSchange_merge_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства задания агент слияния, выполняемого на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] распространителе или более поздней версии. Эта хранимая процедура используется для изменения свойств, если издатель запущен на экземпляре [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_MSchange_merge_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @property = ] 'property'   
        , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber_db = ] 'subscriber_db'`Имя базы данных подписки. Аргумент *subscriber_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @property = ] 'property'`Изменяемое свойство публикации. Аргумент *Property* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @value = ] 'value'`Новое значение свойства. *value* имеет тип **nvarchar (524)** и значение по умолчанию NULL.  
  
 В данной таблице описаны свойства задания агента слияния, которые можно изменить, и ограничения на значения этих свойств.  
  
|Свойство|Значение|Описание|  
|--------------|-----------|-----------------|  
|**nописание**||Краткое описание подписки.|  
|**merge_job_login**||Имя входа учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой выполняется агент.|  
|**merge_job_password**||Пароль учетной записи Windows, под которой запускается задание агента.|  
|**publisher_login**||Имя входа, используемое при подключении к издателю для синхронизации подписки.|  
|**publisher_password**||Пароль издателя.<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**publisher_security_mode**|**1**|Проверка подлинности Windows.<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**;|Проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**subscriber_login**||Имя входа, используемое при подключении к подписчику для синхронизации подписки.|  
|**subscriber_password**||Пароль подписчика.<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**subscriber_security_mode**|**1**|Проверка подлинности Windows.<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**;|Проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
> [!NOTE]  
>  После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_MSchange_merge_agent_properties** используется в репликации слиянием.  
  
 При запуске издателя на экземпляре [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии следует использовать [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md) для изменения свойств задания агент слияния, которое синхронизирует принудительную подписку, которая выполняется на распространителе.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на распространителе могут выполнять **sp_MSchange_merge_agent_properties**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)   
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)  
  
  
