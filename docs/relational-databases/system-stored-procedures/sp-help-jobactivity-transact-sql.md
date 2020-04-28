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
ms.openlocfilehash: 95283eee1a38dbafd9824986188df565103de06c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68054986"
---
# <a name="sp_help_jobactivity-transact-sql"></a>sp_help_jobactivity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет данные о состоянии выполнения заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobactivity { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @session_id = ] session_id ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания. *job_id*имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @session_id = ] session_id`Идентификатор сеанса для передачи сведений о. *session_id* имеет **тип int**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификационный номер сеанса агента.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_name**|**sysname**|Имя задания.|  
|**run_requested_date**|**datetime**|Дата, указанная в запросе для запуска задания.|  
|**run_requested_source**|**sysname**|Источник запроса на выполнение задания. Одно из двух значений:<br /><br /> **1** = запуск по расписанию<br /><br /> **2** = запустить в ответ на предупреждение<br /><br /> **3** = запуск при запуске<br /><br /> **4** = запуск пользователем<br /><br /> **6** = запуск в расписании ПРОСТОя ЦП|  
|**queued_date**|**datetime**|Когда запрос был поставлен в очередь. NULL, если задание было выполнено непосредственно.|  
|**start_execution_date**|**datetime**|Когда задание было назначено потоку, готовому к запуску.|  
|**last_executed_step_id**|**int**|Идентификатор последнего выполненного шага задания.|  
|**last_exectued_step_date**|**datetime**|Время начала последнего выполненного шага задания.|  
|**stop_execution_date**|**datetime**|Время окончания выполнения задания.|  
|**next_scheduled_run_date**|**datetime**|Время следующего выполнения задания по расписанию.|  
|**job_history_id**|**int**|Идентификатор журнала заданий в таблице журналов заданий.|  
|**message**|**nvarchar(1024)**|Сообщение, сформированное во время последнего выполнения задания.|  
|**run_status**|**int**|Состояние, возвращенное во время последнего выполнения задания:<br /><br /> **0** = ошибка не пройдена<br /><br /> **1** = успех<br /><br /> **3** = отменено<br /><br /> **5** = состояние неизвестно|  
|**operator_id_emailed**|**int**|Идентификационный номер оператора, которому по электронной почте было послано оповещение об окончании задания.|  
|**operator_id_netsent**|**int**|ИДЕНТИФИКАЦИОНный номер оператора, уведомленного через **net send** по завершении задания.|  
|**operator_id_paged**|**int**|Идентификационный номер оператора, которому по пейджеру было послано оповещение об окончании задания.|  
  
## <a name="remarks"></a>Remarks  
 Эта хранимая процедура создает моментальный снимок текущего состояния заданий. Возвращаемые результаты представляют собой данные на момент выполнения запроса.  
  
 Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает идентификатор сеанса каждый раз, когда запускается служба агента. Идентификатор сеанса хранится в таблице **msdb. dbo. таблице syssessions**.  
  
 Если *session_id* не указано, выводит сведения о последнем сеансе.  
  
 Если *job_name* или *job_id* не указаны, выводит сведения обо всех заданиях.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эта хранимая процедура может выполняться членами предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **sysadmin** могут просматривать действия для заданий, принадлежащих другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предоставляются сведения о состоянии всех заданий, на просмотр которых текущий пользователь имеет разрешение.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobactivity ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
