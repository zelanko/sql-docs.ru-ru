---
title: sp_adddynamicsnapshot_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddynamicsnapshot_job
- sp_adddynamicsnapshot_job_TSQL
helpviewer_keywords:
- sp_adddynamicsnapshot_job
ms.assetid: ef50ccf6-e360-4e4b-91b9-6706b8fabefa
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 48f94f7fcf823a9ed9acc519e393369e44b45302
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771345"
---
# <a name="spadddynamicsnapshotjob-transact-sql"></a>Хранимая процедура sp_adddynamicsnapshot_job (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Создает задание агента, которое формирует моментальный снимок отфильтрованных данных для публикации с параметризированными фильтрами строк. Эта хранимая процедура выполняется на издателе в базе данных публикации. Эта хранимая процедура используется администратором, чтобы вручную создавать задания моментальных снимков отфильтрованных данных для подписчиков.  
  
> [!NOTE]  
>  Чтобы создать задание моментального снимка отфильтрованных данных, необходимо существование стандартного задания моментальных снимков для публикации.  
  
 Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
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
`[ @publication = ] 'publication'`Имя публикации, в которую добавляется задание моментального снимка отфильтрованных данных. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @suser_sname = ] 'suser_sname'`Значение, используемое при создании моментального снимка отфильтрованных данных для подписки, которая фильтруется по значению функции [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике. *SUSER_SNAME* имеет тип **sysname**и не имеет значения по умолчанию. значение *SUSER_SNAME* должно быть равно null, если эта функция не используется для динамической фильтрации публикации.  
  
`[ @host_name = ] 'host_name'`Значение, используемое при создании моментального снимка отфильтрованных данных для подписки, которая фильтруется по значению функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на подписчике. *HOST_NAME* имеет тип **sysname**и не имеет значения по умолчанию. *HOST_NAME* должен иметь значение null, если эта функция не используется для динамической фильтрации публикации.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Имя созданного задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobname* имеет тип **sysname**, значение по умолчанию NULL и является необязательным выходным параметром. Если указано, *dynamic_snapshot_jobname* должен разрешаться в уникальное задание на распространителе. Если аргумент не указан, имя задания будет автоматически сформировано и возвращено в результирующем наборе, причем имя создается следующим образом:  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
> [!NOTE]  
>  При формировании имени для задания динамического моментального снимка можно усекать имя стандартного задания моментальных снимков.  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Идентификатор созданного задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobid* имеет тип **uniqueidentifier**, значение по умолчанию NULL и является необязательным выходным параметром.  
  
`[ @frequency_type = ] frequency_type`Частота, с которой следует запланировать задание моментального снимка отфильтрованных данных. Аргумент *frequency_type* имеет **тип int**и может принимать одно из следующих значений.  
  
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
  
`[ @frequency_interval = ] frequency_interval`Период (измеряется в днях) при выполнении задания моментального снимка отфильтрованных данных. *frequency_interval* имеет **тип int**, значение по умолчанию 1 и зависит от значения *frequency_type*.  
  
|Значение *frequency_type*|Воздействие на *frequency_interval*|  
|--------------------------------|-------------------------------------|  
|**1**|*frequency_interval* не используется.|  
|**4** (по умолчанию)|Каждые *frequency_interval* дней и по умолчанию ежедневно.|  
|**8**|*frequency_interval* является одним или несколькими следующими (в сочетании с [ &#124; &#40;логическим оператором OR&#41; &#40;логического оператора Transact&#41; -SQL](../../t-sql/language-elements/bitwise-or-transact-sql.md) ):<br /><br /> **1** = воскресенье &#124; **2** = понедельник &#124; **4** = вторник &#124; **8** = среда &#124; **16** = четверг &#124; **32** = Пятница &#124; **64** = Суббота|  
|**16**|В *frequency_interval* день месяца.|  
|**32**|*frequency_interval* является одним из следующих:<br /><br /> **1** = воскресенье &#124; **2** = понедельник &#124; **3** = вторник &#124; **4** = среда &#124; **5** = четверг &#124; **6** = Пятница &#124; **7** = Суббота &#124; **8** = день &#124; **9** = день &#124; недели **10** = выходной день|  
|**64**|*frequency_interval* не используется.|  
|**128**|*frequency_interval* не используется.|  
  
`[ @frequency_subday = ] frequency_subday`Указывает единицы измерения для *frequency_subday_interval*. *frequency_subday* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**2**|Вторая|  
|**4** (по умолчанию)|Минута|  
|**8**|Час|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Число *frequency_subday* периодов между выполнением задания. *frequency_subday_interval* имеет **тип int**и значение по умолчанию 5.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`— Это вхождение задания моментального снимка отфильтрованных данных в каждый месяц. Этот параметр используется, если аргумент *frequency_type* имеет значение **32** (ежемесячное относительное). *frequency_relative_interval* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Коэффициент повторения, используемый в *frequency_type*. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию 0.  
  
`[ @active_start_date = ] active_start_date`Дата первого запланированного задания моментального снимка отфильтрованных данных в формате ГГГГММДД. *active_start_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_date = ] active_end_date`Дата окончания запланированного задания моментального снимка отфильтрованных данных в формате ГГГГММДД. *active_end_date* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Время суток, на которое запланировано первое выполнение задания моментального снимка отфильтрованных данных, в формате ЧЧММСС. *active_start_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Время суток, когда запланировано выполнение задания моментальных снимков отфильтрованных данных в формате ЧЧММСС. *active_end_time_of_day* имеет **тип int**и значение по умолчанию NULL.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Определяет задание моментального снимка отфильтрованных данных в системной таблице [мсдинамикснапшотжобс](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) .|  
|**dynamic_snapshot_jobname**|**sysname**|Имя задания моментального снимка фильтрованных данных.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Уникально идентифицирует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задание агента на распространителе.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_adddynamicsnapshot_job** используется в репликации слиянием для публикаций, использующих параметризованный фильтр.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-adddynamicsnapshot-jo_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_adddynamicsnapshot_job**.  
  
## <a name="see-also"></a>См. также  
 [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [sp_dropdynamicsnapshot_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md)   
 [sp_helpdynamicsnapshot_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md)  
  
  
