---
title: sp_update_jobstep (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobstep
- sp_update_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobstep
ms.assetid: e158802c-c347-4a5d-bf75-c03e5ae56e6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7914e3b56dd02d96c02835bf6b4dcc5eb90e8f4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68084880"
---
# <a name="sp_update_jobstep-transact-sql"></a>sp_update_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет настройку шага задания, которое используется для выполнения автоматических действий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_jobstep   
     {   [@job_id =] job_id   
       | [@job_name =] 'job_name' } ,  
     [@step_id =] step_id  
     [ , [@step_name =] 'step_name' ]  
     [ , [@subsystem =] 'subsystem' ]   
     [ , [@command =] 'command' ]  
     [ , [@additional_parameters =] 'parameters' ]  
     [ , [@cmdexec_success_code =] success_code ]  
     [ , [@on_success_action =] success_action ]   
     [ , [@on_success_step_id =] success_step_id ]  
     [ , [@on_fail_action =] fail_action ]   
     [ , [@on_fail_step_id =] fail_step_id ]  
     [ , [@server =] 'server' ]   
     [ , [@database_name =] 'database' ]  
     [ , [@database_user_name =] 'user' ]   
     [ , [@retry_attempts =] retry_attempts ]  
     [ , [@retry_interval =] retry_interval ]   
     [ , [@os_run_priority =] run_priority ]  
     [ , [@output_file_name =] 'file_name' ]   
     [ , [@flags =] flags ]  
     [ ,  {   [ @proxy_id = ] proxy_id   
            | [ @proxy_name = ] 'proxy_name' }   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания, которому принадлежит шаг. *job_id*имеет тип **uniqueidentifier**и значение по умолчанию NULL. Необходимо указать либо *job_id* , либо *job_name* , но не указывать оба значения.  
  
`[ @job_name = ] 'job_name'`Имя задания, к которому относится шаг. Аргумент *job_name*имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *job_id* , либо *job_name* , но не указывать оба значения.  
  
`[ @step_id = ] step_id`Идентификационный номер изменяемого шага задания. Этот номер не может быть изменен. *step_id*имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @step_name = ] 'step_name'`Новое имя для шага. Аргумент *step_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subsystem = ] 'subsystem'`Подсистема, используемая агентом Microsoft SQL Server для выполнения *команды*. *подсистема* имеет тип **nvarchar (40)** и значение по умолчанию NULL.  
  
`[ @command = ] 'command'`Команды, выполняемые через *подсистему*. *команда* имеет тип **nvarchar (max)** и значение по умолчанию NULL.  
  
`[ @additional_parameters = ] 'parameters'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @cmdexec_success_code = ] success_code`Значение, возвращаемое командой подсистемы **CmdExec** , чтобы указать, что *команда* выполнена успешно. *success_code* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @on_success_action = ] success_action`Действие, выполняемое, если шаг выполнен. *success_action* имеет тип **tinyint**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**1**|Завершить с успешным выполнением.|  
|**2**|Завершить с ошибкой.|  
|**3**|Перейти к следующему шагу.|  
|**4**|Перейдите к шагу *success_step_id.*|  
  
`[ @on_success_step_id = ] success_step_id`Идентификационный номер шага в этом задании, который будет выполнен, если шаг выполнен, а *success_action* — **4**. *success_step_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @on_fail_action = ] fail_action`Действие, выполняемое в случае сбоя шага. *fail_action* имеет тип **tinyint**, значение по умолчанию NULL и может иметь одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**1**|Завершить с успешным выполнением.|  
|**2**|Завершить с ошибкой.|  
|**3**|Перейти к следующему шагу.|  
|**4**|Перейдите к шагу *fail_step_id * *.*|  
  
`[ @on_fail_step_id = ] fail_step_id`Идентификационный номер шага в этом задании, которое должно быть выполнено, если шаг завершается ошибкой, а *fail_action* — **4**. *fail_step_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @server = ] 'server'`[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *Server* имеет тип **nvarchar (128)** и значение по умолчанию NULL.  
  
`[ @database_name = ] 'database'`Имя базы данных, в которой будет выполняться [!INCLUDE[tsql](../../includes/tsql-md.md)] шаг. *база данных*имеет тип **sysname**. Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Значение по умолчанию — NULL.  
  
`[ @database_user_name = ] 'user'`Имя учетной записи пользователя, используемой при выполнении [!INCLUDE[tsql](../../includes/tsql-md.md)] шага. Аргумент *User*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @retry_attempts = ] retry_attempts`Количество повторных попыток использования в случае сбоя этого шага. *retry_attempts*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @retry_interval = ] retry_interval`Количество времени в минутах между повторными попытками. *retry_interval* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @os_run_priority = ] run_priority` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @output_file_name = ] 'file_name'`Имя файла, в котором сохраняется выходные данные этого шага. *file_name* имеет тип **nvarchar (200)** и значение по умолчанию NULL. Данный аргумент действителен только с командами, запущенными в подсистемах [!INCLUDE[tsql](../../includes/tsql-md.md)] или CmdExec.  
  
 Чтобы присвоить output_file_name значение NULL, необходимо присвоить параметру *output_file_name* пустую строку ("") или строку пустых символов, но нельзя использовать функцию **char (32)** . Например, установление данного аргумента равным пустой строке производится следующим образом:  
  
 **@output_file_name= ' '**  
  
`[ @flags = ] flags`Параметр, управляющий поведением. *Флаги* имеют **тип int**и могут принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|Переписать выходной файл.|  
|**2**|Добавить к выходному файлу.|  
|**4**|Записать вывод шага задания Transact-SQL в журнал шагов.|  
|**8**|Записать журнал в таблицу (переписать существующий журнал).|  
|**16**|Записать журнал в таблицу (добавить к существующему журналу).|  
  
`[ @proxy_id = ] proxy_id`ИДЕНТИФИКАЦИОНный номер учетной записи-посредника, от имени которой выполняется шаг задания. *proxy_id* имеет тип **int**и значение по умолчанию NULL. Если *proxy_id* не указано, *proxy_name* не указана и *user_name* не указана, шаг задания выполняется как учетная запись службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
`[ @proxy_name = ] 'proxy_name'`Имя учетной записи-посредника, от имени которой выполняется шаг задания. *proxy_name* имеет тип **sysname**и значение по умолчанию NULL. Если *proxy_id* не указано, *proxy_name* не указана и *user_name* не указана, шаг задания выполняется как учетная запись службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_update_jobstep** должны запускаться из базы данных **msdb** .  
  
 Обновление шага задания увеличивает номер версии задания.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **sysadmin** могут обновлять шаг задания, принадлежащий другому пользователю.  
  
 Если шаг задания требует доступа к учетной записи-посреднику, создатель шага задания должен обеспечить ему доступ к такой записи. Все подсистемы, за исключением Transact-SQL, требуют учетную запись-посредник. Члены **роли sysadmin** имеют доступ ко всем учетным записям-посредникам и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут использовать учетную запись службы агента для прокси.  
  
## <a name="examples"></a>Примеры  
 Следующий пример изменяет количество повторных попыток для первого шага задания `Weekly Sales Data Backup`. После выполнения данного примера количество повторных попыток будет равно `10`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1,  
    @retry_attempts = 10 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
