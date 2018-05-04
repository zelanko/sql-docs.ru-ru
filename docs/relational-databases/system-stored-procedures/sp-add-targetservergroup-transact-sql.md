---
title: sp_add_targetservergroup (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_targetservergroup
- sp_add_targetservergroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_targetservergroup
ms.assetid: acb69343-d766-46ff-b771-0c7655c5231a
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 901ad941d3791a66be19cb5faf693ba703fa0d8f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddtargetservergroup-transact-sql"></a>sp_add_targetservergroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет указанную группу серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_targetservergroup [ @name = ] 'name'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@name=**] **"***имя***"**  
 Имя создаваемой серверной группы. *имя* — **sysname**, не имеет значения по умолчанию. *имя* не может содержать запятые.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Группы целевых серверов обеспечивают простой способ поиска задания в коллекции целевых серверов. Дополнительные сведения см. в разделе [sp_apply_job_to_targets](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнить эту процедуру.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует создание группы целевых серверов с именем `Servers Processing Customer Orders`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_targetservergroup  
    'Servers Processing Customer Orders' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_help_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
