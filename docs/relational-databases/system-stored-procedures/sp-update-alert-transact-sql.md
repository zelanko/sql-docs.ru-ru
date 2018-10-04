---
title: Хранимая процедура sp_update_alert (Transact-SQL) | Документация Майкрософт
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24cd1864fc31524dcd661cd9eb108d8cb4fa1b77
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846732"
---
# <a name="spupdatealert-transact-sql"></a>Хранимая процедура sp_update_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@name =**] **"***имя***"**  
 Имя обновляемого предупреждения. *имя* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@new_name =**] **"***новое_имя***"**  
 Новое имя предупреждения. Имя должно быть уникальным. *новое_имя* — **sysname**, значение по умолчанию NULL.  
  
 [  **@enabled =**] *включена*  
 Указывает, включено ли предупреждение (**1**) или не включено (**0**). *включить* — **tinyint**, значение по умолчанию NULL. Сработать может только активированное предупреждение.  
  
 [  **@message_id =**] *message_id*  
 Новое сообщение или номер ошибки, определяющие предупреждение. Как правило *message_id* соответствует номеру ошибки в **sysmessages** таблицы. *message_id* — **int**, значение по умолчанию NULL. Сообщение, идентификатор может использоваться только в том случае, если уровень серьезности для предупреждения является **0**.  
  
 [  **@severity =**] *серьезности*  
 Новый уровень серьезности (от **1** через **25**) для определения предупреждения. Любой [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщение, отправленное в журнал приложений Windows с заданным уровнем серьезности, будет активировать предупреждение. *уровень серьезности* — **int**, значение по умолчанию NULL. Уровень серьезности может использоваться только в том случае, если параметр идентификатор сообщения для предупреждения может быть **0**.  
  
 [ **@delay_between_responses =**] *delay_between_responses*  
 Новый период ожидания (в секундах) между ответами на предупреждение. *delay_between_responses* — **int**, значение по умолчанию NULL.  
  
 [  **@notification_message =**] **"***notification_message***"**  
 Измененный текст дополнительного сообщения, отправляемое оператору как часть сообщения электронной почты, **команды net send**, или уведомления на пейджер. *notification_message* — **nvarchar(512)**, значение по умолчанию NULL.  
  
 [  **@include_event_description_in =**] *include_event_description_in*  
 Указывает, следует ли включить в текст сообщения уведомления описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из журнала приложений Windows. *include_event_description_in* — **tinyint**, значение по умолчанию NULL, и может иметь одно или несколько из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|None|  
|**1**|электронная почта|  
|**2**|Пейджер|  
|**4**|**команда net send.**|  
|**7**|All|  
  
 [  **@database_name =**] **"***базы данных***"**  
 Имя базы данных, в которой должна произойти ошибка, для которой срабатывает предупреждение. *База данных* является **sysname.** Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Значение по умолчанию — NULL.  
  
 [ **@event_description_keyword =**] **'***event_description_keyword***'**  
 Последовательность символов, которая должна присутствовать в описании ошибки в журнале сообщений об ошибках. Могут использоваться символы-шаблоны выражений [!INCLUDE[tsql](../../includes/tsql-md.md)] LIKE. *event_description_keyword* — **nvarchar(100)**, значение по умолчанию NULL. Этот параметр полезен для фильтрации имен объектов (например, **% customer_table %**).  
  
 [  **@job_id =**] *job_id*  
 Идентификационный номер задания. *job_id* — **uniqueidentifier**, значение по умолчанию NULL. Если *job_id* указано, *имя_задания* необходимо пропустить.  
  
 [  **@job_name =**] **"***имя_задания***"**  
 Имя задания, выполняющегося при срабатывании данного предупреждения. *имя_задания* — **sysname**, значение по умолчанию NULL. Если *имя_задания* указано, *job_id* необходимо пропустить.  
  
 [  **@occurrence_count =** ] *occurrence_count*  
 Сбрасывает количество появлений предупреждения. *occurrence_count* — **int**, значение по умолчанию NULL ему можно присвоить только значение **0**.  
  
 [ **@count_reset_date =**] *count_reset_date*  
 Сбрасывает дату последнего сброса счетчика предупреждений. *count_reset_date* — **int**, значение по умолчанию NULL.  
  
 [ **@count_reset_time =**] *count_reset_time*  
 Сбрасывает время последнего сброса счетчика предупреждений. *count_reset_time* — **int**, значение по умолчанию NULL.  
  
 [ **@last_occurrence_date =**] *last_occurrence_date*  
 Сбрасывает дату последнего возникновения предупреждения. *last_occurrence_date* — **int**, значение по умолчанию NULL ему можно присвоить только значение **0**.  
  
 [ **@last_occurrence_time =**] *last_occurrence_time*  
 Сбрасывает время последнего возникновения предупреждения. *last_occurrence_time* — **int**, значение по умолчанию NULL ему можно присвоить только значение **0**.  
  
 [ **@last_response_date =**] *last_response_date*  
 Сбрасывает дату последнего ответа на предупреждение от службы SQLServerAgent. *last_response_date* — **int**, значение по умолчанию NULL ему можно присвоить только значение **0**.  
  
 [ **@last_response_time =**] *last_response_time*  
 Сбрасывает время последнего ответа на предупреждение от службы SQLServerAgent. *last_response_time* — **int**, значение по умолчанию NULL ему можно присвоить только значение **0**.  
  
 [ **@raise_snmp_trap =**] *raise_snmp_trap*  
 Зарезервировано.  
  
 [  **@performance_condition =**] **"***performance_condition***"**  
 Значение, выраженное в формате **"***itemcomparatorvalue***"**. *performance_condition* — **nvarchar(512)**, значение по умолчанию NULL и состоит из следующих элементов.  
  
|Элемент формата|Описание|  
|--------------------|-----------------|  
|*Элемент*|Объект производительности, счетчик производительности или именованный экземпляр счетчика.|  
|*Оператор сравнения*|Один из этих операторов: **>**, **<**, **=**|  
|*Value*|Числовое значение счетчика|  
  
 [  **@category_name =**] **"***категории***"**  
 Имя категории предупреждения. *Категория* — **sysname** значение по умолчанию NULL.  
  
 [ **@wmi_namespace**=] **"***wmi_namespace***"**  
 Пространство имен WMI для запроса событий. *wmi_namespace* — **sysname**, значение по умолчанию NULL.  
  
 [ **@wmi_query**=] **"***wmi_query***"**  
 Запрос, указывающий событие WMI для предупреждения. *wmi_query* — **nvarchar(512)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Только **sysmessages** записываемый [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнал приложений Windows могут активировать предупреждения.  
  
 **Хранимая процедура sp_update_alert** изменяет только те оповещения установки, о параметрах которого предоставляются значения. Если параметр пропущен, сохраняется текущая настройка.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры, пользователи должны входить в **sysadmin** предопределенной роли сервера.  
  
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
  
## <a name="see-also"></a>См. также  
 [sp_add_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
