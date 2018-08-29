---
title: sp_purge_jobhistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ed89736333db4260fe7defe81160935407ec74af
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43091653"
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет записи журнала для задания.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_name=** ] **"***имя_задания***"**  
 Имя задания, для которого удаляются записи журнала. *имя_задания*— **sysname**, значение по умолчанию NULL. Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
> [!NOTE]  
>  Членами **sysadmin** предопределенной роли сервера или членами **SQLAgentOperatorRole** предопределенной роли базы данных могут выполнять процедуру **sp_purge_jobhistory** без указания *имя_задания* или *job_id*. Когда **sysadmin** пользователи не указывают эти аргументы, журнал заданий для всех локальных и многосерверных заданий удаляются в пределах времени, заданного параметром *oldest_date*. Когда **SQLAgentOperatorRole** пользователи не указывают эти аргументы, журнал заданий для всех локальных заданий удаляются в пределах времени, заданного параметром *oldest_date*.  
  
 [  **@job_id=** ] *job_id*  
 Идентификатор задания, для которого удаляются записи. *job_id*— **uniqueidentifier**, значение по умолчанию NULL. Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно. См. Примечание в описании **@job_name** сведения о том, как **sysadmin** или **SQLAgentOperatorRole** пользователи могут использовать этот аргумент.  
  
 [ **@oldest_date** =] *oldest_date*  
 Самая ранняя запись журнала, которую необходимо сохранить. *oldest_date* — **datetime**, значение по умолчанию NULL. Когда *oldest_date* указано, **sp_purge_jobhistory** удаляет только записи, которые являются более старыми, чем указано.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Когда **sp_purge_jobhistory** завершается успешно, возвращается сообщение.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию только члены **sysadmin** предопределенной роли сервера или **SQLAgentOperatorRole** предопределенной роли базы данных может выполнить эту хранимую процедуру. Членами **sysadmin** можно удалять из журнала заданий для всех локальных и многосерверных заданий. Членами **SQLAgentOperatorRole** можно удалять из журнала заданий только любые локальные задания.  
  
 Другим пользователям, в том числе членов **SQLAgentUserRole** и членами **SQLAgentReaderRole**, должны быть явно предоставлено разрешение EXECUTE на **sp_purge_jobhistory**. После предоставления разрешения EXECUTE на эту хранимую процедуру данные пользователи могут удалять из журнала заданий только те задания, владельцами которых они являются.  
  
 **SQLAgentUserRole**, **SQLAgentReaderRole**, и **SQLAgentOperatorRole** предопределенных ролей базы данных находятся в **msdb** базы данных. Сведения об их разрешениях см. в разделе [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
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
>  Только члены **sysadmin** фиксированной серверной роли и члены **SQLAgentOperatorRole** можно удалять журнал для всех заданий. Когда **sysadmin** пользователей выполнения этой хранимой процедуры без параметров, очистка журнала заданий для всех локальных и многосерверных заданий. Когда **SQLAgentOperatorRole** пользователей выполнения этой хранимой процедуры без параметров, удаляется только журнал заданий для всех локальных заданий.  
  
 В следующем примере данная процедура выполняется без указания параметров, и в результате удаляются все записи журнала.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [GRANT, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  
