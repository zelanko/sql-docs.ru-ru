---
title: sp_help_jobactivity (Transact-SQL) | Документы Microsoft
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
- sp_help_jobactivity_TSQL
- sp_help_jobactivity
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobactivity
ms.assetid: d344864f-b4d3-46b1-8933-b81dec71f511
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db9d7a3424e94cfdd4bf3292323ec8a494ca02e7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpjobactivity-transact-sql"></a>sp_help_jobactivity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет данные о состоянии выполнения заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobactivity { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @session_id = ] session_id ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id =**] *job_id*  
 Идентификационный номер задания. *Аргумент job_id*— **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name =**] **"***job_name***"**  
 Имя задания. *job_name*— **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@session_id** =] *session_id*  
 Идентификатор сеанса, о котором предоставляются данные. *session_id* — **int**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификационный номер сеанса агента.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_name**|**sysname**|Имя задания.|  
|**run_requested_date**|**datetime**|Дата, указанная в запросе для запуска задания.|  
|**run_requested_source**|**sysname**|Источник запроса на выполнение задания. Может принимать одно из следующих значений.<br /><br /> **1** = запуск по расписанию<br /><br /> **2** = запуск в ответ на предупреждение<br /><br /> **3** = запуск при запуске<br /><br /> **4** = запуск пользователем<br /><br /> **6** = запуск по расписанию бездействия Процессора|  
|**queued_date**|**datetime**|Когда запрос был поставлен в очередь. NULL, если задание было выполнено непосредственно.|  
|**start_execution_date**|**datetime**|Когда задание было назначено потоку, готовому к запуску.|  
|**last_executed_step_id**|**int**|Идентификатор последнего выполненного шага задания.|  
|**last_exectued_step_date**|**datetime**|Время начала последнего выполненного шага задания.|  
|**stop_execution_date**|**datetime**|Время окончания выполнения задания.|  
|**next_scheduled_run_date**|**datetime**|Время следующего выполнения задания по расписанию.|  
|**job_history_id**|**int**|Идентификатор журнала заданий в таблице журналов заданий.|  
|**message**|**nvarchar(1024)**|Сообщение, сформированное во время последнего выполнения задания.|  
|**run_status**|**int**|Состояние, возвращенное во время последнего выполнения задания:<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **3** = отменено<br /><br /> **5** = неизвестное состояние|  
|**operator_id_emailed**|**int**|Идентификационный номер оператора, которому по электронной почте было послано оповещение об окончании задания.|  
|**operator_id_netsent**|**int**|Идентификационный номер оператора, уведомленного о через **net send** по завершении задания.|  
|**operator_id_paged**|**int**|Идентификационный номер оператора, которому по пейджеру было послано оповещение об окончании задания.|  
  
## <a name="remarks"></a>Замечания  
 Эта хранимая процедура создает моментальный снимок текущего состояния заданий. Возвращаемые результаты представляют собой данные на момент выполнения запроса.  
  
 Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает идентификатор сеанса каждый раз, когда запускается служба агента. Идентификатор сеанса хранится в таблице **msdb.dbo.syssessions**.  
  
 Если аргумент *session_id* , выдаются сведения о самом последнем сеансе.  
  
 Если аргумент *job_name* или *job_id* , выдаются сведения обо всех заданиях.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию члены **sysadmin** предопределенной роли сервера можно выполнять эту хранимую процедуру. Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** можно просмотреть активность заданий, принадлежащих другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предоставляются сведения о состоянии всех заданий, на просмотр которых текущий пользователь имеет разрешение.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobactivity ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
