---
description: sp_add_agent_profile (Transact-SQL)
title: sp_add_agent_profile (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords:
- sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 379e418cbca4b93fe38bf640f62cd357ef6b5a48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419398"
---
# <a name="sp_add_agent_profile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает новый профиль для агента репликации. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_agent_profile [ [ @profile_id= ] profile_id OUTPUT ]  
        , [ @profile_name= ] 'profile_name'   
        , [ @agent_type= ] 'agent_type' ]   
    [ , [ @profile_type= ] profile_type ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @default= ] default ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id` Идентификатор, связанный с вновь вставленным профилем. *profile_id* имеет **тип int** и является необязательным выходным параметром. Если он указан, в качестве его значения устанавливается новый идентификатор профиля.  
  
`[ @profile_name = ] 'profile_name'` Имя профиля. Аргумент *profile_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @agent_type = ] 'agent_type'` Тип агента репликации. *agent_type* имеет **тип int**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|агент моментальных снимков|  
|**2**|Агент чтения журнала.|  
|**3**|Агент распространителя|  
|**4**|Агент слияния.|  
|**9**|Агент чтения очереди.|  
  
`[ @profile_type = ] profile_type` Тип профиля. *profile_type* имеет **тип int**и значение по умолчанию **1**.  
  
 значение **0** указывает на системный профиль. **1** указывает на пользовательский профиль. С помощью этой хранимой процедуры можно создавать только пользовательские профили. Поэтому единственным допустимым значением является **1**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Создает только системные профили.  
  
`[ @description = ] 'description'` Описание профиля. *Description* имеет тип **nvarchar (3000)** и не имеет значения по умолчанию.  
  
`[ @default = ] default` Указывает, является ли профиль используемым по умолчанию для *agent_type * *.* *значение по умолчанию* — **bit**и значение по умолчанию **0**. значение **1** указывает, что добавляемый профиль станет новым профилем по умолчанию для агента, указанного в *agent_type*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_add_agent_profile** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Пользовательские профили агента добавляются со значениями параметров агента по умолчанию. Используйте [sp_change_agent_parameter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md) для изменения этих значений по умолчанию или [sp_add_agent_parameter &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md) для добавления дополнительных параметров.  
  
 При выполнении **sp_add_agent_profile** добавляется строка для нового настраиваемого профиля в [MSagent_profiles &#40;таблице&#41;Transact-SQL ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) , а связанные параметры по умолчанию для этого профиля добавляются в таблицу MSAGENT_PARAMETERS &#40;[Transact-SQL ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_add_agent_profile**.  
  
## <a name="see-also"></a>См. также:  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
