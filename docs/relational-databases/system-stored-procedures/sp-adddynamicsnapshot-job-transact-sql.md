---
title: "Хранимая процедура sp_adddynamicsnapshot_job (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_adddynamicsnapshot_job
- sp_adddynamicsnapshot_job_TSQL
helpviewer_keywords: sp_adddynamicsnapshot_job
ms.assetid: ef50ccf6-e360-4e4b-91b9-6706b8fabefa
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3b2201611c5b58b795063dd06ecc7c0918c57f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spadddynamicsnapshotjob-transact-sql"></a>Хранимая процедура sp_adddynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает задание агента, которое формирует моментальный снимок отфильтрованных данных для публикации с параметризированными фильтрами строк. Эта хранимая процедура выполняется на издателе в базе данных публикации. Эта хранимая процедура используется администратором, чтобы вручную создавать задания моментальных снимков отфильтрованных данных для подписчиков.  
  
> [!NOTE]  
>  Чтобы создать задание моментального снимка отфильтрованных данных, необходимо существование стандартного задания моментальных снимков для публикации.  
  
 Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adddynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]   
    [ , [ @host_name = ] 'host_name' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' OUTPUT ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' OUTPUT ]   
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, к которой требуется добавить задание создания моментального снимка отфильтрованных данных. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@suser_sname** =] **"***suser_sname***"**  
 Значение, используемое во время создания моментального снимка отфильтрованных данных для подписки, отсортированной по значению [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на стороне подписчика. *функция SUSER_SNAME* — **sysname**, не имеет значения по умолчанию. *функция SUSER_SNAME* должен иметь значение NULL, если эта функция не используется для динамической фильтрации публикации.  
  
 [  **@host_name** =] **"***host_name***"**  
 Значение, используемое во время создания моментального снимка отфильтрованных данных для подписки, отсортированной по значению [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на стороне подписчика. *HOST_NAME* — **sysname**, не имеет значения по умолчанию. *HOST_NAME* должен иметь значение NULL, если эта функция не используется для динамической фильтрации публикации.  
  
 [  **@dynamic_snapshot_jobname** =] **"***dynamic_snapshot_jobname***"**  
 Имя созданного задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobname* — **sysname**, по умолчанию NULL, и является необязательным ВЫХОДНЫМ параметром. Если указано, *dynamic_snapshot_jobname* должно разрешаться к созданию уникального задания на распространителе. Если аргумент не указан, имя задания будет автоматически сформировано и возвращено в результирующем наборе, причем имя создается следующим образом:  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
> [!NOTE]  
>  При формировании имени для задания динамического моментального снимка можно усекать имя стандартного задания моментальных снимков.  
  
 [  **@dynamic_snapshot_jobid** =] **"***dynamic_snapshot_jobid***"**  
 Идентификатор созданного задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobid* — **uniqueidentifier**, по умолчанию NULL, и является необязательным ВЫХОДНЫМ параметром.  
  
 [  **@frequency_type=**] *frequency_type*  
 Частота, с которой необходимо выполнять задание создания моментального снимка отфильтрованных данных. *frequency_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|по запросу|  
|**4** (по умолчанию)|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно с относительной датой|  
|**64**|Автозапуск|  
|**128**|Повторяющееся задание|  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 Период (в днях), в течение которого выполняется задание создания моментального снимка отфильтрованных данных. *frequency_interval* — **int**, значение по умолчанию 1 и зависит от значения *frequency_type*.  
  
|Значение *frequency_type*|Воздействие на *frequency_interval*|  
|--------------------------------|-------------------------------------|  
|**1**|*frequency_interval* не используется.|  
|**4** (по умолчанию)|Каждый *frequency_interval* дней, по умолчанию ежедневно.|  
|**8**|*frequency_interval* — один или несколько из следующих (объединены с [&#124; &#40; Побитовый оператор или &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/bitwise-or-transact-sql.md) логический оператор):<br /><br /> **1** = воскресенье &#124; **2** = понедельник &#124; **4** = вторник &#124; **8** = среда &#124; **16** = четверг &#124; **32** = пятница &#124; **64** = суббота|  
|**16**|На *frequency_interval* день месяца.|  
|**32**|*frequency_interval* является одним из следующих:<br /><br /> **1** = воскресенье &#124; **2** = понедельник &#124; **3** = вторник &#124; **4** = среда &#124; **5** = четверг &#124; **6** = пятница &#124; **7** = суббота &#124; **8** = день &#124; **9** = рабочий день &#124; **10** = выходной день|  
|**64**|*frequency_interval* не используется.|  
|**128**|*frequency_interval* не используется.|  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Указывает единицы изменения для *frequency_subday_interval*. *frequency_subday* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Число *frequency_subday* периоды, когда пройти между выполнениями задания. *frequency_subday_interval* — **int**, значение по умолчанию 5.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Количество выполнений задания моментальных снимков отфильтрованных данных в каждом месяце. Этот параметр используется при *frequency_type* равно **32** (относительно ежемесячно). *frequency_relative_interval* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Коэффициент повторения, используемый аргументом *frequency_type*. *frequency_recurrence_factor* — **int**, значение по умолчанию 0.  
  
 [  **@active_start_date=**] *active_start_date*  
 Дата, когда впервые запланировано выполнение задания создания моментального снимка отфильтрованных данных, в формате ГГГГММДД. *active_start_date* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_date=**] *active_end_date*  
 Дата окончания выполнения задания создания моментального снимка отфильтрованных данных, в формате ГГГГММДД. *active_end_date* — **int**, значение по умолчанию NULL.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Время дня, когда впервые запланировано выполнение задания создания моментального снимка отфильтрованных данных, в формате ЧЧММСС. *active_start_time_of_day* — **int**, значение по умолчанию NULL.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Время дня, когда завершается выполнение задания создания моментального снимка отфильтрованных данных, в формате ЧЧММСС. *active_end_time_of_day* — **int**, значение по умолчанию NULL.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Определяет задание моментального снимка отфильтрованных данных в [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) системной таблицы.|  
|**dynamic_snapshot_jobname**|**sysname**|Имя задания моментального снимка фильтрованных данных.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Уникально идентифицирует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задание агента на распространителе.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_adddynamicsnapshot_job** используется в репликации слиянием для публикаций, использующих параметризованный фильтр.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-adddynamicsnapshot-jo_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_adddynamicsnapshot_job**.  
  
## <a name="see-also"></a>См. также:  
 [Создать моментальный снимок для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [хранимую процедуру sp_dropdynamicsnapshot_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md)   
 [sp_helpdynamicsnapshot_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md)  
  
  
