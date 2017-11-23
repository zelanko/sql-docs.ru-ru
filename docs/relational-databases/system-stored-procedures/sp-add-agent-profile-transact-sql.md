---
title: "sp_add_agent_profile (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords: sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 83fd104a70e8cda855bc13dcedfbb589af5034fb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spaddagentprofile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@profile_id=** ] *profile_id*  
 Идентификатор, связанный с вновь вставленным профилем. *profile_id* — **int** и является необязательным ВЫХОДНЫМ параметром. Если он указан, в качестве его значения устанавливается новый идентификатор профиля.  
  
 [  **@profile_name=** ] **"***profile_name***"**  
 Имя профиля. *profile_name* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@agent_type=** ] **"***agent_type***"**  
 Тип агента репликации. *agent_type* — **int**, без значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|агент моментальных снимков|  
|**2**|Агент чтения журнала.|  
|**3**|Агент распространителя|  
|**4**|Агент слияния.|  
|**9**|Агент чтения очереди.|  
  
 [  **@profile_type=** ] *profile_type*  
 — Тип профиля. *profile_type* — **int**, значение по умолчанию **1**.  
  
 **0** обозначает системный профиль. **1** обозначает пользовательский профиль. Только пользовательские профили могут быть созданы с помощью этой хранимой процедуры; поэтому единственным допустимым значением является **1**. Только [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает профили системы.  
  
 [  **@description=** ] **"***описание***"**  
 Описание профиля. *Описание* — **nvarchar(3000)**, не имеет значения по умолчанию.  
  
 [  **@default=** ] *по умолчанию*  
 Указывает, является ли профиль по умолчанию для *agent_type**.* *по умолчанию* — **бит**, значение по умолчанию **0**. **1** указывает, что при добавлении профиля станет профилем по умолчанию для агента, задаваемого аргументом *agent_type*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_add_agent_profile** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Пользовательские профили агента добавляются со значениями параметров агента по умолчанию. Используйте [хранимая процедура sp_change_agent_parameter &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md) изменить эти значения по умолчанию или [sp_add_agent_parameter &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md) для добавления дополнительных параметров.  
  
 Когда **sp_add_agent_profile** — выполняется, создается строка для нового пользовательского профиля в [MSagent_profiles &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) таблицы и соответствующие параметры по умолчанию для этого профиля добавляются [MSagent_parameters &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) таблицы.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_add_agent_profile**.  
  
## <a name="see-also"></a>См. также:  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [Хранимая процедура sp_change_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [Хранимая процедура sp_change_agent_profile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_drop_agent_profile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [sp_help_agent_profile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
