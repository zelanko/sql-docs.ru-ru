---
title: sp_update_schedule (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
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
- sp_update_schedule
- sp_update_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_schedule
ms.assetid: 97b3119b-e43e-447a-bbfb-0b5499e2fefe
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 23d1d4b4cfdc7fb19cffff63de8cae84b2606d6e
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="spupdateschedule-transact-sql"></a>sp_update_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет установки для расписания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_schedule   
    {   [ @schedule_id = ] schedule_id   
      | [ @name = ] 'schedule_name' }  
    [ , [ @new_name = ] new_name ]  
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@schedule_id =** ] *schedule_id*  
 Идентификатор изменяемого расписания. *schedule_id* — **int**, не имеет значения по умолчанию. Либо *schedule_id* или *schedule_name* должен быть указан.  
  
 [  **@name =** ] **"***schedule_name***"**  
 Имя изменяемого расписания. *schedule_name*— **sysname**, не имеет значения по умолчанию. Либо *schedule_id* или *schedule_name* должен быть указан.  
  
 [ **@new_name**=] *новое_имя*  
 Новое имя расписания. *новое_имя* — **sysname**, значение по умолчанию NULL. Когда *новое_имя* имеет значение NULL, имя расписания не меняется.  
  
 [  **@enabled =** ] *включена*  
 Отображает текущее состояние расписания. *включить*— **tinyint**, значение по умолчанию **1** (включено). Если **0**, расписание не включено. Когда расписание не включено, никакие задания не будут запускаться по расписанию.  
  
 [ **@freq_type =** ] *freq_type*  
 Значение, указывающее, когда должно выполняться задание. *freq_type*— **int**, значение по умолчанию **0**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно, относительно *freq интервал*|  
|**64**|Запустить, когда запускается служба SQLServerAgent|  
|**128**|Запускать, когда компьютер простаивает|  
  
 [  **@freq_interval =** ] *freq_interval*  
 Дни, когда выполняется задание. *freq_interval* — **int**, значение по умолчанию **0**и зависит от значения *freq_type*.  
  
|Значение *freq_type*|Воздействие на *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (один раз)|*freq_interval* не используется.|  
|**4** (ежедневно)|Каждый *freq_interval* дней.|  
|**8** (еженедельно)|*freq_interval* — один или несколько из следующих (объединены с **или** логический оператор):<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **4** = Вторник<br /><br /> **8** = среда<br /><br /> **16** = четверг<br /><br /> **32** = Пятница<br /><br /> **64** = суббота|  
|**16** (ежемесячно)|На *freq_interval* день месяца.|  
|**32** (относительно ежемесячно)|*freq_interval* является одним из следующих:<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **3** = Вторник<br /><br /> **4** = среда<br /><br /> **5** = четверг<br /><br /> **6** = Пятница<br /><br /> **7** = суббота<br /><br /> **8** = день<br /><br /> **9** = рабочий день<br /><br /> **10** = выходной день|  
|**64** (когда запускается служба SQLServerAgent)|*freq_interval* не используется.|  
|**128**|*freq_interval* не используется.|  
  
 [ **@freq_subday_type =** ] *freq_subday_type*  
 Указывает единицы изменения для *freq_subday_interval **.* *freq_subday_type*— **int**, значение по умолчанию **0**, и может принимать одно из следующих значений.  
  
|Значение|Описание (единица измерения)|  
|-----------|--------------------------|  
|**0x1**|В указанное время|  
|**0x2**|Секунды|  
|**0x4**|Минуты|  
|**0x8**|Часы|  
  
 [ **@freq_subday_interval =** ] *freq_subday_interval*  
 Число *freq_subday_type* периодов должно пройти между выполнениями задания. *freq_subday_interval*— **int**, значение по умолчанию **0**.  
  
 [ **@freq_relative_interval =** ] *freq_relative_interval*  
 Задание вхождения *freq_interval* в каждом месяце, если *freq_interval* — **32** (относительно ежемесячно). *freq_relative_interval*— **int**, значение по умолчанию **0**, и может принимать одно из следующих значений.  
  
|Значение|Описание (единица измерения)|  
|-----------|--------------------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
 [  **@freq_recurrence_factor =** ] *freq_recurrence_factor*  
 Число недель или месяцев между запланированными выполнениями задания. *freq_recurrence_factor* используется только в том случае, если *freq_type* — **8**, **16**, или **32**. *freq_recurrence_factor*— **int**, значение по умолчанию **0**.  
  
 [  **@active_start_date =** ] *active_start_date*  
 Дата, когда может начаться выполнение задания. *active_start_date*— **int**, и значение по умолчанию NULL, которое указывает текущую дату. Формат даты: ГГГГMMДД. Если *active_start_date* не равно NULL, дата должна быть больше или равна 19900101.  
  
 После создания расписания проверьте дату начала и убедитесь, что она задана правильно. Дополнительные сведения см в разделе «Планирование даты начала» [Создание и присоединение расписаний к заданиям](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5).  
  
 [ **@active_end_date =** ] *active_end_date*  
 Дата, когда может быть остановлено выполнение задания. *active_end_date*— **int**, значение по умолчанию **99991231**, что означает 31 декабря 9999 года. Используется формат ГГГГММДД.  
  
 [  **@active_start_time =** ] *active_start_time*  
 Время в любой день между *active_start_date* и *active_end_date* для начала выполнения задания. *active_start_time*— **int**, значение по умолчанию 000000, которое соответствует 12:00:00 по в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [ **@active_end_time =** ] *active_end_time*  
 Время в любой день между *active_start_date* и *active_end_date* завершения выполнения задания. *active_end_time*— **int**, значение по умолчанию **235959**, что означает 23:59:59. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [ **@owner_login_name**= ] **'***owner_login_name***'**]  
 Имя сервера-участника, владеющего расписанием. *owner_login_name* — **sysname**, и значение по умолчанию NULL, которое указывает, что расписание будет владеет его создатель.  
  
 [ **@automatic_post =**] *automatic_post*  
 Зарезервировано.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Все задания, которые используют расписание, немедленно используют новые установки. Однако изменение расписания не останавливает выполнение заданий.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** можно изменить расписание, принадлежащий другому пользователю.  
  
## <a name="examples"></a>Примеры  
 Следующий пример изменяет состояние расписания `NightlyJobs` на состояние `0` и устанавливает владельцем `terrid`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_schedule  
    @name = 'NightlyJobs',  
    @enabled = 0,  
    @owner_login_name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Создание и присоединение расписаний к заданиям](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)   
 [Планирование задания](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)   
 [Создание расписания](http://msdn.microsoft.com/library/8c7ef3b3-c06d-4a27-802d-ed329dc86ef3)   
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
