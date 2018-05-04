---
title: sp_manage_jobs_by_login (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_manage_jobs_by_login
- sp_manage_jobs_by_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_manage_jobs_by_login
ms.assetid: 832ec15a-6e92-4eb5-8c4a-af4dba79fbaa
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b00d4295463a75faed0dd767b69ac58cf2558229
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spmanagejobsbylogin-transact-sql"></a>sp_manage_jobs_by_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет или переназначает задания, принадлежащие указанному имени входа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_manage_jobs_by_login  
     [ @action = ] 'action'  
     [, [@current_owner_login_name = ] 'current_owner_login_name']  
     [, [@new_owner_login_name = ] 'new_owner_login_name']  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@action=** ] **"***действия***"**  
 Действие, предпринимаемое для указанного имени входа. *Действие* — **varchar(10)**, не имеет значения по умолчанию. Когда *действия*— **удаление**, **sp_manage_jobs_by_login** удаляет все задания, принадлежащие *current_owner_login_name*. Когда *действия* — **ПЕРЕНАЗНАЧИТЬ**, все задания назначаются *new_owner_login_name*.  
  
 [ **@current_owner_login_name=** ] **'***current_owner_login_name***'**  
 Имя входа текущего владельца задания. *current_owner_login_name* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@new_owner_login_name=** ] **'***new_owner_login_name***'**  
 Имя входа нового владельца задания. Используйте этот параметр, только если *действия* — **ПЕРЕНАЗНАЧИТЬ**. *new_owner_login_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователь должен обладать **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится передача всех заданий от пользователя `danw` пользователю `françoisa`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_manage_jobs_by_login  
    @action = N'REASSIGN',  
    @current_owner_login_name = N'danw',  
    @new_owner_login_name = N'françoisa' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
