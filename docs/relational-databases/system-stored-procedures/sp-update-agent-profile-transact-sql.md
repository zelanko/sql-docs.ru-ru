---
title: sp_update_agent_profile (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_update_agent_profile_TSQL
- sp_update_agent_profile
helpviewer_keywords:
- sp_update_agent_profile
ms.assetid: cc81f227-0df3-4151-bb4d-4f45ea997b71
author: stevestein
ms.author: sstein
ms.openlocfilehash: 730f996a35e7ea2e31518322d710b197cf31f38b
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632825"
---
# <a name="sp_update_agent_profile-transact-sql"></a>sp_update_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет профиль, используемый агентом репликации. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_agent_profile [@agent_type=] agent_type, [ @agent_id= ] agent_id, [ @profile_id= ] profile_id  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @agent_type = ] 'agent_type'` — это тип агента. *agent_type* имеет **тип int**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Агент моментальных снимков.|  
|**2**|Агент чтения журнала.|  
|**3**|Агент распространителя.|  
|**4**|Агент слияния.|  
|**9**|Агент чтения очереди.|  
  
`[ @agent_id = ] 'agent_id'` — идентификатор агента. *agent_id* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @profile_id = ] 'profile_id'` — это идентификатор профиля, который должен использовать агент. *profile_id* имеет **тип int**и не имеет значения по умолчанию. Чтобы просмотреть список профилей, определенных для каждого агента, используйте [sp_help_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Дополнительные сведения о системных профилях см. в разделе [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_update_agent_profile** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_update_agent_profile**.  
  
## <a name="see-also"></a>См. также статью  
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)  
 [sp_change_agent_profile &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)  
 [sp_drop_agent_profile &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)  
 [sp_help_agent_profile &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
