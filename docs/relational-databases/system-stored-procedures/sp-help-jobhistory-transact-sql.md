---
title: sp_help_jobhistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2229da0158f746928be16ac190ecae2e36726da5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730048"
---
# <a name="sp_help_jobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Предоставляет сведения о заданиях серверов в многосерверном административном домене.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @step_id = ] step_id`Идентификационный номер шага. *step_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @sql_message_id = ] sql_message_id`Идентификационный номер сообщения об ошибке, возвращенного Microsoft SQL Server при выполнении задания. *sql_message_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @sql_severity = ] sql_severity`Степень серьезности сообщения об ошибке, возвращаемого SQL Server при выполнении задания. *sql_severity* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @start_run_date = ] start_run_date`Дата запуска задания. *start_run_date*имеет **тип int**и значение по умолчанию NULL. *start_run_date* должны быть указаны в формате ГГГГММДД, где YYYY — год из четырех символов, mm — имя месяца из двух символов, а дд — двузначное имя дня.  
  
`[ @end_run_date = ] end_run_date`Дата завершения задания. *end_run_date* имеет **тип int**и значение по умолчанию NULL. *end_run_date*необходимо указать в формате ГГГГММДД, где гггг — это четырехзначный год, а mm — имя месяца из двух символов, а дд — двузначное имя дня.  
  
`[ @start_run_time = ] start_run_time`Время запуска задания. *start_run_time* имеет **тип int**и значение по умолчанию NULL. *start_run_time*должны быть указаны в формате ЧЧММСС, где ЧЧ — 2-символьный час дня, mm — это две минуты дня, а SS — двузначное значение дня.  
  
`[ @end_run_time = ] end_run_time`Время завершения выполнения задания. *end_run_time* имеет **тип int**и значение по умолчанию NULL. *end_run_time*должны быть указаны в формате ЧЧММСС, где ЧЧ — 2-символьный час дня, mm — это две минуты дня, а SS — двузначное значение дня.  
  
`[ @minimum_run_duration = ] minimum_run_duration`Минимальный период времени для завершения задания. *minimum_run_duration* имеет **тип int**и значение по умолчанию NULL. *minimum_run_duration*должны быть указаны в формате ЧЧММСС, где ЧЧ — 2-символьный час дня, mm — это две минуты дня, а SS — двузначное значение дня.  
  
`[ @run_status = ] run_status`Состояние выполнения задания. *run_status* имеет **тип int**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**0**|Ошибка|  
|**1**|Успешно|  
|**2**|Повторить (только для этапа)|  
|**3**|Отменено|  
|**4**|Сообщение о проценте выполнения|  
|**5**|Неизвестно|  
  
`[ @minimum_retries = ] minimum_retries`Минимальное число повторных попыток выполнения задания. *minimum_retries* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @oldest_first = ] oldest_first`Указывает, следует ли выводить выходные данные сначала с самыми старыми заданиями. *oldest_first* имеет **тип int**и значение по умолчанию **0**, которое сначала представляет последние задания. **1** в первую очередь представляет самые старые задания.  
  
`[ @server = ] 'server'`Имя сервера, на котором было выполнено задание. *Server* имеет тип **nvarchar (30)** и значение по умолчанию NULL.  
  
`[ @mode = ] 'mode'`Определяет, будет ли SQL Server печатать все столбцы в результирующем наборе (**полная**) или сводку по столбцам. *mode* имеет тип **varchar (7)** и значение по умолчанию **Summary**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Реальный список столбцов зависит от значения *mode*. Наиболее полный набор столбцов показан ниже и возвращается, если *режим* заполнен.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Идентификационный номер записи журнала.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_name**|**sysname**|Имя задания.|  
|**step_id**|**int**|Идентификационный номер шага (для журнала заданий будет **равен 0** ).|  
|**step_name**|**sysname**|Имя этапа (NULL для журнала заданий).|  
|**sql_message_id**|**int**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] — самый последний номер ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)], обнаруженный при выполнении команды.|  
|**sql_severity**|**int**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] — самая высокая степень серьезности ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)], обнаруженная при выполнении команды.|  
|**message**|**nvarchar(1024)**|Запись в журнале о задании или этапе.|  
|**run_status**|**int**|Результат задания или этапа.|  
|**run_date**|**int**|Дата начала выполнения задания или этапа.|  
|**run_time**|**int**|Дата начала выполнения задания или этапа.|  
|**run_duration**|**int**|Время, прошедшее с момента запуска задания или этапа в формате «ЧЧММСС».|  
|**operator_emailed**|**nvarchar (20)**|Оператор, которому было отправлено электронное письмо относительно этого задания (NULL для журнала этапов). |  
|**operator_netsent**|**nvarchar (20)**|Оператор, которому было отправлено сетевое сообщение относительно этого задания (NULL для журнала этапов).|  
|**operator_paged**|**nvarchar (20)**|Оператор, которому было отправлено сообщение на пейджер относительно этого задания (NULL для журнала этапов).|  
|**retries_attempted**|**int**|Количество повторных попыток запуска этапа (всегда 0 для журнала заданий).|  
|**server**|**nvarchar(30)**|Сервер, на котором выполняется задание или этап. Всегда имеет (**Local**).|  
  
## <a name="remarks"></a>Примечания  
 **sp_help_jobhistory** возвращает отчет с историей указанных запланированных заданий. Если не указаны параметры, отчет содержит журнал всех заданий в расписании.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены роли базы данных **SQLAgentUserRole** могут только просматривать журнал для заданий, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. Вывод всех сведений о задании  
 В следующем примере отображаются все сведения о задании `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>Б. Вывод сведений о заданиях, которые соответствуют определенным условиям  
 Следующий пример иллюстрирует вывод всех сведений о шагах заданий, завершившихся неудачно с кодом ошибки `50100` (пользовательская ошибка) и уровнем серьезности `20`.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
