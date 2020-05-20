---
title: sp_help_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_schedule
- sp_help_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_schedule
ms.assetid: b2fc4ce1-0a8e-44d2-b206-7dc7b258d8c9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ce8c1514a0c62eeb11743d86dd6922cf4995c63c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828413"
---
# <a name="sp_help_schedule-transact-sql"></a>sp_help_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает информацию о расписаниях.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_schedule   
     [ @schedule_id = ] id ,  
     [ @schedule_name = ] 'schedule_name'   
     [ , [ @attached_schedules_only = ] attached_schedules_only ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @schedule_id = ] id`Идентификатор расписания для перечисления. *schedule_name* имеет **тип int**и не имеет значения по умолчанию. Можно указать либо *schedule_id* , либо *schedule_name* .  
  
`[ @schedule_name = ] 'schedule_name'`Имя расписания для перечисления. Аргумент *schedule_name* имеет тип **sysname**и не имеет значения по умолчанию. Можно указать либо *schedule_id* , либо *schedule_name* .  
  
`[ @attached_schedules_only = ] attached_schedules_only ]`Указывает, следует ли отображать только расписания, к которым присоединено задание. *attached_schedules_only* имеет **бит**и значение по умолчанию **0**. Если значение *attached_schedules_only* равно **0**, отображаются все расписания. Если *attached_schedules_only* равен **1**, результирующий набор содержит только те расписания, которые присоединены к заданию.  
  
`[ @include_description = ] include_description`Указывает, следует ли включать описания в результирующий набор. *include_description* имеет **бит**и значение по умолчанию **0**. Если значение *include_description* равно **0**, столбец *schedule_description* результирующего набора содержит заполнитель. Если *include_description* равен **1**, описание расписания включается в результирующий набор.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Данная процедура возвращает следующий результирующий набор:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификационный номер расписания.|  
|**schedule_uid**|**uniqueidentifier**|Идентификатор расписания.|  
|**schedule_name**|**sysname**|Имя расписания.|  
|**доступной**|**int**|Включено ли расписание (**1**) или не включено (**0**).|  
|**freq_type**|**int**|Значение, указывающее, когда должно выполняться задание.<br /><br /> **1** = один раз<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячно относительно **freq_interval**<br /><br /> **64** = запуск при запуске службы SQLServerAgent.|  
|**freq_interval**|**int**|Дни, в которые выполняется задание. Значение зависит от значения **freq_type**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Единицы для **freq_subday_interval**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Число периодов **freq_subday_type** , которые должны быть выполнены между выполнением задания. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Вхождение **freq_interval** запланированного задания в каждый месяц. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**int**|Число месяцев между выполнениями задания по расписанию.|  
|**active_start_date**|**int**|Дата, когда начинает действовать расписание.|  
|**active_end_date**|**int**|Дата, когда прекращает действовать расписание.|  
|**active_start_time**|**int**|Время суток, когда начинает действовать расписание.|  
|**active_end_time**|**int**|Время суток, когда прекращает действовать расписание.|  
|**date_created**|**datetime**|Дата создания расписания.|  
|**schedule_description**|**nvarchar(4000)**|Описание расписания на английском языке (если запрошено).|  
|**job_count**|**int**|Число заданий, ссылающихся на данное расписание.|  
  
## <a name="remarks"></a>Примечания  
 Если параметры не указаны, **sp_help_schedule** выводит сведения обо всех расписаниях в экземпляре.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены **SQLAgentUserRole** могут просматривать только те расписания, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-information-for-all-schedules-in-the-instance"></a>A. Вывод сведений обо всех расписаниях в экземпляре  
 Следующий пример выводит информацию о всех расписаниях в экземпляре.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-schedule"></a>Б. Вывод сведений о конкретном расписании  
 Следующий пример выводит информацию о расписании `NightlyJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
