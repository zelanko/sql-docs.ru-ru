---
title: "sp_purge_jobhistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs: TSQL
helpviewer_keywords: sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8e9706f38a69343ca68000d85d12869b965e2cd3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет записи журнала для задания.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_name=** ] **"***job_name***"**  
 Имя задания, для которого удаляются записи журнала. *job_name*— **sysname**, значение по умолчанию NULL. Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
> [!NOTE]  
>  Члены **sysadmin** предопределенной роли сервера или члены **SQLAgentOperatorRole** предопределенной роли базы данных могут выполнять **sp_purge_jobhistory** без указания *job_name* или *job_id*. Когда **sysadmin** пользователи не указывают эти аргументы, журнал заданий для всех локальных и многосерверных заданий удаляются в диапазоне времени, заданного параметром *oldest_date*. Когда **SQLAgentOperatorRole** пользователи не указывают эти аргументы, в журнале заданий для всех локальных заданий удаляются в диапазоне времени, заданного параметром *oldest_date*.  
  
 [  **@job_id=** ] *job_id*  
 Идентификатор задания, для которого удаляются записи. *Аргумент job_id*— **uniqueidentifier**, значение по умолчанию NULL. Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно. См. Примечание в описании  **@job_name**  сведения о том, как **sysadmin** или **SQLAgentOperatorRole** пользователи могут использовать этот аргумент.  
  
 [  **@oldest_date**  =] *oldest_date*  
 Самая ранняя запись журнала, которую необходимо сохранить. *oldest_date* — **datetime**, значение по умолчанию NULL. Когда *oldest_date* указано, **sp_purge_jobhistory** удаляет только записи, которые являются более старыми, чем указано.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Когда **sp_purge_jobhistory** завершается успешно, возвращается сообщение.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию только члены **sysadmin** предопределенной роли сервера или **SQLAgentOperatorRole** предопределенной роли базы данных может выполнить эту хранимую процедуру. Члены **sysadmin** можно удалять из журнала заданий для всех локальных и многосерверных заданий. Члены **SQLAgentOperatorRole** можно удалять из журнала заданий только любые локальные задания.  
  
 Другим пользователям, в том числе членов **SQLAgentUserRole** и члены **SQLAgentReaderRole**, необходимо явно предоставить разрешение EXECUTE на **sp_purge_jobhistory**. После предоставления разрешения EXECUTE на эту хранимую процедуру данные пользователи могут удалять из журнала заданий только те задания, владельцами которых они являются.  
  
 **SQLAgentUserRole**, **SQLAgentReaderRole**, и **SQLAgentOperatorRole** фиксированных ролей базы данных находятся в **msdb** базы данных. Дополнительные сведения о предоставляемых им разрешениях см. в разделе [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-remove-history-for-a-specific-job"></a>A. Удаление журнала конкретного задания  
 В следующем примере удаляется история задания с именем `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-remove-history-for-all-jobs"></a>Б. Удаление записи журналов для всех заданий  
  
> [!NOTE]  
>  Только члены **sysadmin** фиксированной серверной роли и члены **SQLAgentOperatorRole** можно удалить журнал для всех заданий. Когда **sysadmin** пользователей выполнить эту хранимую процедуру без параметров, в журнале заданий для всех локальных и многосерверных заданий удаляются. Когда **SQLAgentOperatorRole** пользователей выполнить эту хранимую процедуру без параметров, удаляются только в журнале заданий для всех локальных заданий.  
  
 В следующем примере данная процедура выполняется без указания параметров, и в результате удаляются все записи журнала.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_help_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Предоставление разрешений для объекта &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  
