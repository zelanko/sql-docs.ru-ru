---
description: Хранимая процедура sp_update_alert (Transact-SQL)
title: sp_update_alert (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_alert_TSQL
- sp_update_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_alert
ms.assetid: 4bbaeaab-8aca-4c9e-abc1-82ce73090bd3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7abcc7d0f4ad148f18e90a29a8f411804e0d4a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446726"
---
# <a name="sp_update_alert-transact-sql"></a>Хранимая процедура sp_update_alert (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Обновляет параметры существующего предупреждения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_alert   
     [ @name =] 'name'   
     [ , [ @new_name =] 'new_name']   
     [ , [ @enabled =] enabled]   
     [ , [ @message_id =] message_id]   
     [ , [ @severity =] severity]   
     [ , [ @delay_between_responses =] delay_between_responses]   
     [ , [ @notification_message =] 'notification_message']   
     [ , [ @include_event_description_in =] include_event_description_in]   
     [ , [ @database_name =] 'database']   
     [ , [ @event_description_keyword =] 'event_description_keyword']   
     [ , [ @job_id =] job_id | [@job_name =] 'job_name']   
     [ , [ @occurrence_count = ] occurrence_count]   
     [ , [ @count_reset_date =] count_reset_date]   
     [ , [ @count_reset_time =] count_reset_time]   
     [ , [ @last_occurrence_date =] last_occurrence_date]   
     [ , [ @last_occurrence_time =] last_occurrence_time]   
     [ , [ @last_response_date =] last_response_date]   
     [ , [ @last_response_time =] last_response _time]  
     [ , [ @raise_snmp_trap =] raise_snmp_trap]  
     [ , [ @performance_condition =] 'performance_condition' ]   
     [ , [ @category_name =] 'category']  
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'name'` Имя обновляемого оповещения. Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @new_name = ] 'new_name'` Новое имя предупреждения. Имя должно быть уникальным. Аргумент *new_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @enabled = ] enabled` Указывает, включено ли оповещение (**1**) или не включено (**0**). *Enabled* имеет тип **tinyint**и значение по умолчанию NULL. Сработать может только активированное предупреждение.  
  
`[ @message_id = ] message_id` Новое сообщение или номер ошибки для определения предупреждения. Как правило, *message_id* соответствует номеру ошибки в таблице **sysmessages** . *message_id* имеет **тип int**и значение по умолчанию NULL. Идентификатор сообщения можно использовать только в том случае, если для предупреждения задан уровень серьезности **0**.  
  
`[ @severity = ] severity` Новый уровень серьезности (от **1** до **25**) для определения предупреждения. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Предупреждение будет активировано любым сообщением, отправленным в журнал приложений Windows с заданной степенью серьезности. *уровень серьезности* — **int**, значение по умолчанию NULL. Степень серьезности может использоваться, только если параметр идентификатора сообщения для предупреждения равен **0**.  
  
`[ @delay_between_responses = ] delay_between_responses` Новый период ожидания (в секундах) между ответами на предупреждение. *delay_between_responses* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @notification_message = ] 'notification_message'` Измененный текст дополнительного сообщения, отправленного оператору как часть уведомления электронной почты, **команды net send**или пейджера. *notification_message* имеет тип **nvarchar (512)** и значение по умолчанию NULL.  
  
`[ @include_event_description_in = ] include_event_description_in` Указывает, следует ли включать описание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибки из журнала приложений Windows в сообщение уведомления. *include_event_description_in* имеет тип **tinyint**, значение по умолчанию NULL и может принимать одно или несколько из этих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Нет|  
|**1**|электронная почта;|  
|**2**|Пейджер|  
|**4**|**команда net send.**|  
|**7**|Все|  
  
`[ @database_name = ] 'database'` Имя базы данных, в которой должна произойти ошибка для срабатывания предупреждения. *база данных* имеет тип **sysname.** Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Значение по умолчанию — NULL.  
  
`[ @event_description_keyword = ] 'event_description_keyword'` Последовательность символов, которая должна быть найдена в описании ошибки в журнале сообщений об ошибках. Могут использоваться символы-шаблоны выражений [!INCLUDE[tsql](../../includes/tsql-md.md)] LIKE. *event_description_keyword* имеет тип **nvarchar (100)** и значение по умолчанию NULL. Этот параметр полезен для фильтрации имен объектов (например, **% customer_table%**).  
  
`[ @job_id = ] job_id` Идентификационный номер задания. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL. Если указано *job_id* , *job_name* необходимо опустить.  
  
`[ @job_name = ] 'job_name'` Имя задания, которое выполняется в ответ на это предупреждение. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL. Если указано *job_name* , *job_id* необходимо опустить.  
  
`[ @occurrence_count = ] occurrence_count` Сбрасывает число попыток возникновения предупреждения. *occurrence_count* имеет **тип int**, значение по умолчанию NULL и может быть задано только равным **0**.  
  
`[ @count_reset_date = ] count_reset_date` Сбрасывает дату последнего сброса счетчика вхождений. *count_reset_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @count_reset_time = ] count_reset_time` Сбрасывает время последнего сброса счетчика вхождений. *count_reset_time* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @last_occurrence_date = ] last_occurrence_date` Сбрасывает дату последнего возникновения предупреждения. *last_occurrence_date* имеет **тип int**, значение по умолчанию NULL и может быть задано только равным **0**.  
  
`[ @last_occurrence_time = ] last_occurrence_time` Сбрасывает время последнего возникновения предупреждения. *last_occurrence_time* имеет **тип int**, значение по умолчанию NULL и может быть задано только равным **0**.  
  
`[ @last_response_date = ] last_response_date` Сбрасывает дату последнего ответа на предупреждение службой SQLServerAgent. *last_response_date* имеет **тип int**, значение по умолчанию NULL и может быть задано только равным **0**.  
  
`[ @last_response_time = ] last_response_time` Сбрасывает время последнего ответа на предупреждение службой SQLServerAgent. *last_response_time* имеет **тип int**, значение по умолчанию NULL и может быть задано только равным **0**.  
  
`[ @raise_snmp_trap = ] raise_snmp_trap` Процессу.  
  
`[ @performance_condition = ] 'performance_condition'` Значение, выраженное в формате **"**_итемкомпараторвалуе_**"**. *performance_condition* имеет тип **nvarchar (512)**, значение по умолчанию NULL и состоит из этих элементов.  
  
|Элемент формата|Описание|  
|--------------------|-----------------|  
|*Элемент*|Объект производительности, счетчик производительности или именованный экземпляр счетчика.|  
|*Сравнения*|Один из следующих операторов: **>** , **<** , **=**|  
|*Значение*|Числовое значение счетчика|  
  
`[ @category_name = ] 'category'` Имя категории оповещений. *Category* имеет тип **sysname** и значение по умолчанию NULL.  
  
`[ @wmi_namespace = ] 'wmi_namespace'` Пространство имен WMI для запроса событий. Аргумент *wmi_namespace* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @wmi_query = ] 'wmi_query'` Запрос, указывающий событие WMI для предупреждения. *wmi_query* имеет тип **nvarchar (512)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 Предупреждение может создаваться только в таблице **sysmessages** , записанной в [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнал приложений Windows.  
  
 **sp_update_alert** изменяет только те параметры оповещений, для которых указаны значения параметров. Если параметр пропущен, сохраняется текущая настройка.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователи должны быть членами предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере значение параметра активирования предупреждения `Test Alert` меняется на `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_alert  
    @name = N'Test Alert',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_add_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
