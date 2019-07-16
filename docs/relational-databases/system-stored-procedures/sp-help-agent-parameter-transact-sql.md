---
title: sp_help_agent_parameter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_agent_parameter
- sp_help_agent_parameter_TSQL
helpviewer_keywords:
- sp_help_agent_parameter
ms.assetid: 8fb4a9c3-19af-4a34-8004-572729ba3d15
author: stevestein
ms.author: sstein
ms.openlocfilehash: 616e5547c4acf59f88dc67c5aabc507eb30fe251
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055300"
---
# <a name="sphelpagentparameter-transact-sql"></a>sp_help_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает все параметры профиля из [MSagent_parameters &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) системная таблица. Эта хранимая процедура выполняется на распространителе в любой базе данных с запущенным агентом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_agent_parameter [ [ @profile_id = ] profile_id ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id` Идентификатор профиля из [MSagent_parameters &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) таблицы. *profile_id* — **int**, значение по умолчанию **-1**, которое возвращает все параметры.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|Идентификатор профиля агента.|  
|**parameter_name**|**sysname**|Имя параметра.|  
|**value**|**nvarchar(255)**|Значение параметра.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_help_agent_parameter** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **replmonitor** предопределенной роли базы данных могут выполнять процедуру **sp_help_agent_parameter**.  
  
## <a name="see-also"></a>См. также  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
