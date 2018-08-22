---
title: sp_help_jobserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fdaa9481c51188767834679031b6cdc9084f969d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395360"
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
 Идентификационный номер задания, для которого возвращаются сведения. *job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name=** ] **"***имя_задания***"**  
 Имя задания, для которого возвращаются сведения. *имя_задания* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@show_last_run_details=** ] *show_last_run_details*  
 Включать ли сведения о выполнении последнего запуска в результирующий набор. *show_last_run_details* — **tinyint**, значение по умолчанию **0**. **0** отсутствуют сведения последнего запуска и **1** does.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификационный номер целевого сервера.|  
|**server_name**|**nvarchar(30)**|Имя компьютера целевого сервера.|  
|**enlist_date**|**datetime**|Дата прикрепления целевого сервера к главному серверу.|  
|**last_poll_date**|**datetime**|Дата последнего опроса главного сервера целевым сервером.|  
  
 Если **sp_help_jobserver** выполняется с *show_last_run_details* присвоено **1**, результирующий набор имеет следующие дополнительные столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Дата последнего запуска задания на выполнение на данном целевом сервере.|  
|**last_run_time**|**int**|Время выполнения последнего запуска задания на данном целевом сервере.|  
|**last_run_duration**|**int**|Продолжительность задания при последнем его выполнении на целевом сервере (в секундах).|  
|**last_outcome_message**|**nvarchar(1024)**|Описание последнего результата задания.|  
|**last_run_outcome**|**int**|Результат последнего выполнения задания на данном сервере:<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Членами **SQLAgentUserRole** могут только просматривать сведения о заданиях, которыми они владеют.  
  
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
  
## <a name="see-also"></a>См. также  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
