---
title: sp_help_jobactivity (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobactivity_TSQL
- sp_help_jobactivity
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobactivity
ms.assetid: d344864f-b4d3-46b1-8933-b81dec71f511
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0cf6feb850bbc898d69b01c897d1be295c378566
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47763262"
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
 Идентификационный номер задания. *job_id*— **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name =**] **"***имя_задания***"**  
 Имя задания. *имя_задания*— **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
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
|**run_requested_source**|**sysname**|Источник запроса на выполнение задания. Может принимать одно из следующих значений.<br /><br /> **1** = запуск по расписанию<br /><br /> **2** = запуск в ответ на оповещение<br /><br /> **3** = запуск при запуске<br /><br /> **4** = запуск пользователем<br /><br /> **6** = запуск по расписанию бездействия Процессора|  
|**queued_date**|**datetime**|Когда запрос был поставлен в очередь. NULL, если задание было выполнено непосредственно.|  
|**start_execution_date**|**datetime**|Когда задание было назначено потоку, готовому к запуску.|  
|**last_executed_step_id**|**int**|Идентификатор последнего выполненного шага задания.|  
|**last_exectued_step_date**|**datetime**|Время начала последнего выполненного шага задания.|  
|**stop_execution_date**|**datetime**|Время окончания выполнения задания.|  
|**next_scheduled_run_date**|**datetime**|Время следующего выполнения задания по расписанию.|  
|**job_history_id**|**int**|Идентификатор журнала заданий в таблице журналов заданий.|  
|**message**|**nvarchar(1024)**|Сообщение, сформированное во время последнего выполнения задания.|  
|**run_status**|**int**|Состояние, возвращенное во время последнего выполнения задания:<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **3** = отменено<br /><br /> **5** = состояние неизвестно|  
|**operator_id_emailed**|**int**|Идентификационный номер оператора, которому по электронной почте было послано оповещение об окончании задания.|  
|**operator_id_netsent**|**int**|Идентификационный номер оператора, уведомленного о через **команды net send** по завершении задания.|  
|**operator_id_paged**|**int**|Идентификационный номер оператора, которому по пейджеру было послано оповещение об окончании задания.|  
  
## <a name="remarks"></a>Примечания  
 Эта хранимая процедура создает моментальный снимок текущего состояния заданий. Возвращаемые результаты представляют собой данные на момент выполнения запроса.  
  
 Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает идентификатор сеанса каждый раз, когда запускается служба агента. Идентификатор сеанса хранится в таблице **msdb.dbo.syssessions**.  
  
 Если аргумент *session_id* предоставлен, выдаются сведения о самом последнем сеансе.  
  
 Если аргумент *имя_задания* или *job_id* предоставлен, выдаются сведения обо всех заданиях.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию, члены **sysadmin** предопределенной роли сервера могут выполнять эту хранимую процедуру. Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **sysadmin** можно просматривать состояния заданий, принадлежащих другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предоставляются сведения о состоянии всех заданий, на просмотр которых текущий пользователь имеет разрешение.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobactivity ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
