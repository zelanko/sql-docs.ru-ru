---
title: sp_help_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_schedule
- sp_help_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_schedule
ms.assetid: b2fc4ce1-0a8e-44d2-b206-7dc7b258d8c9
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a77859fd5c113d9b40832c81472e62aaef05fcda
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394163"
---
# <a name="sphelpschedule-transact-sql"></a>sp_help_schedule (Transact-SQL)
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
 [ **@schedule_id =** ] *id*  
 Идентификатор расписания, сведения о котором следует возвратить. *schedule_name* — **int**, не имеет значения по умолчанию. Либо *schedule_id* или *schedule_name* может быть указан.  
  
 [  **@schedule_name =** ] **"***schedule_name***"**  
 Имя расписания, сведения о котором следует возвратить. *schedule_name* — **sysname**, не имеет значения по умолчанию. Либо *schedule_id* или *schedule_name* может быть указан.  
  
 [ **@attached_schedules_only** =] *этот аргумент* ]  
 Этот аргумент указывает, следует ли возвратить информацию только о расписаниях, связанных с заданиями. *Этот аргумент* — **бит**, значение по умолчанию **0**. Когда *этот аргумент* — **0**, всех расписаниях. Когда *этот аргумент* — **1**, результирующий набор содержит только те расписания, подключенные к заданию.  
  
 [ **@include_description** =] *этот аргумент*  
 Этот аргумент указывает, следует ли включить в результирующий набор описания. *Этот аргумент* — **бит**, значение по умолчанию **0**. Когда *этот аргумент* — **0**, *schedule_description* столбец результирующего набора содержит заполнитель. Когда *этот аргумент* — **1**, в результирующий набор включается описание расписания.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Данная процедура возвращает следующий результирующий набор:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификационный номер расписания.|  
|**schedule_uid**|**uniqueidentifier**|Идентификатор расписания.|  
|**schedule_name**|**sysname**|Имя расписания.|  
|**включен**|**int**|Расписание задействовано (**1**) или не включено (**0**).|  
|**freq_type**|**int**|Значение, указывающее, когда должно выполняться задание.<br /><br /> **1** = однократно<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячно, относительно **freq_interval**<br /><br /> **64** = запуск при запуске службы SQLServerAgent.|  
|**freq_interval**|**int**|Дни, в которые выполняется задание. Значение зависит от значения **freq_type**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Единицы измерения для **freq_subday_interval**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Число **freq_subday_type** периодов должно пройти между выполнениями задания. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Запланированные задания **freq_interval** в каждом месяце. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**int**|Число месяцев между выполнениями задания по расписанию.|  
|**active_start_date**|**int**|Дата, когда начинает действовать расписание.|  
|**active_end_date**|**int**|Дата, когда прекращает действовать расписание.|  
|**active_start_time**|**int**|Время суток, когда начинает действовать расписание.|  
|**active_end_time**|**int**|Время суток, когда прекращает действовать расписание.|  
|**date_created**|**datetime**|Дата создания расписания.|  
|**schedule_description**|**nvarchar(4000)**|Описание расписания на английском языке (если запрошено).|  
|**job_count**|**int**|Число заданий, ссылающихся на данное расписание.|  
  
## <a name="remarks"></a>Примечания  
 Если параметры не указаны, **sp_help_schedule** выводит сведения о всех расписаниях в экземпляре.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Членами **SQLAgentUserRole** могут только просматривать принадлежащие им расписания.  
  
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
 [процедуру sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
