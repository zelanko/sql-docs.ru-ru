---
title: "sp_help_jobserver (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83de0b76e66e08571a53e3ea62c665ba595a6572
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpjobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о сервере, на котором выполняется заданное задание.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id=** ] *job_id*  
 Идентификационный номер задания, для которого возвращаются сведения. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name=** ] **"***job_name***"**  
 Имя задания, для которого возвращаются сведения. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@show_last_run_details=** ] *show_last_run_details*  
 Включать ли сведения о выполнении последнего запуска в результирующий набор. *show_last_run_details* — **tinyint**, значение по умолчанию **0**. **0** не включают сведения о последнем запуске, и **1** does.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификационный номер целевого сервера.|  
|**имя_сервера**|**nvarchar(30)**|Имя компьютера целевого сервера.|  
|**enlist_date**|**datetime**|Дата прикрепления целевого сервера к главному серверу.|  
|**last_poll_date**|**datetime**|Дата последнего опроса главного сервера целевым сервером.|  
  
 Если **sp_help_jobserver** выполняется с *show_last_run_details* значение **1**, результирующий набор имеет следующие дополнительные столбцы.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Дата последнего запуска задания на выполнение на данном целевом сервере.|  
|**last_run_time**|**int**|Время выполнения последнего запуска задания на данном целевом сервере.|  
|**last_run_duration**|**int**|Продолжительность задания при последнем его выполнении на целевом сервере (в секундах).|  
|**last_outcome_message**|**nvarchar(1024)**|Описание последнего результата задания.|  
|**last_run_outcome**|**int**|Результат последнего выполнения задания на данном сервере:<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
  
## <a name="permissions"></a>Permissions  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** могут только просматривать сведения о заданиях, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о задании `NightlyBackups`, включая данные о последнем запуске.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobserver  
    @job_name = N'NightlyBackups',  
    @show_last_run_details = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_add_jobserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
