---
description: sp_help_jobserver (Transact-SQL)
title: sp_help_jobserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7e59691a44353826f47550bb67c7a7872fcc4200
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546105"
---
# <a name="sp_help_jobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @job_id = ] job_id` Идентификационный номер задания, для которого возвращаются сведения. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` Имя задания, для которого возвращаются сведения. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @show_last_run_details = ] show_last_run_details` Указывает, является ли информация о выполнении последнего запуска частью результирующего набора. *show_last_run_details* имеет тип **tinyint**и значение по умолчанию **0**. **0** не включает сведения о последнем запуске, а **1** —.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификационный номер целевого сервера.|  
|**server_name**|**nvarchar(30)**|Имя компьютера целевого сервера.|  
|**enlist_date**|**datetime**|Дата прикрепления целевого сервера к главному серверу.|  
|**last_poll_date**|**datetime**|Дата последнего опроса главного сервера целевым сервером.|  
  
 Если **sp_help_jobserver** выполняется с *show_last_run_details* , для которого задано значение **1**, то результирующий набор будет содержать эти дополнительные столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Дата последнего запуска задания на выполнение на данном целевом сервере.|  
|**last_run_time**|**int**|Время выполнения последнего запуска задания на данном целевом сервере.|  
|**last_run_duration**|**int**|Продолжительность задания при последнем его выполнении на целевом сервере (в секундах).|  
|**last_outcome_message**|**nvarchar(1024)**|Описание последнего результата задания.|  
|**last_run_outcome**|**int**|Результат последнего выполнения задания на данном сервере:<br /><br /> **0** = сбой<br /><br /> **1** = успех<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены группы **SQLAgentUserRole** могут только просматривать сведения о заданиях, которыми они владеют.  
  
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
  
  
