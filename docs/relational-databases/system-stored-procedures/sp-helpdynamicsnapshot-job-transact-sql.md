---
title: "sp_helpdynamicsnapshot_job (Transact-SQL) | Документы Microsoft"
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
- sp_helpdynamicsnapshot_TSQL
- sp_helpdynamicsnapshot_job_TSQL
- job_TSQL
- helpdynamicsnapshot
- job
- sp_helpdynamicsnapshot
- sp_helpdynamicsnapshot_job
- helpdynamicsnapshot_TSQL
helpviewer_keywords: sp_helpdynamicsnapshot_job
ms.assetid: d6dfdf26-f874-495f-a8a6-8780699646d7
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f9accc8ae7ffb64d82fa10c3b60a2f8fec44b8a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpdynamicsnapshotjob-transact-sql"></a>sp_helpdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о заданиях агента, которые формируют моментальные снимки фильтрованных данных. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdynamicsnapshot_job [ [ @publication = ] 'publication' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication =** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию  **%** , возвращающий сведения по всем заданиям моментального снимка отфильтрованных данных, соответствующих указанному *dynamic_ snapshot_jobid*и *dynamic_snapshot_jobname*для всех публикаций.  
  
 [  **@dynamic_snapshot_jobname =** ] **"***dynamic_snapshot_jobname***"**  
 Имя задания моментального снимка фильтрованных данных. *dynamic_snapshot_jobname*— **sysname**, по умолчанию  **%** ", возвращаются все динамические задания для публикации с указанным *dynamic_ snapshot_jobid*. Если имя задания было задано явно во время создания задания, оно будет в следующем формате:  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
 [  **@dynamic_snapshot_jobid =** ] **"***dynamic_snapshot_jobid***"**  
 Идентификатор задания моментального снимка фильтрованных данных. *dynamic_snapshot_jobid*— **uniqueidentifier**, по умолчанию NULL, возвращаются все задания моментального снимка, соответствующих указанному *dynamic_snapshot_jobname*.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Задание моментального снимка фильтрованных данных.|  
|**job_name**|**sysname**|Имя задания моментального снимка фильтрованных данных.|  
|**Аргумент job_id**|**uniqueidentifier**|Идентифицирует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задание агента на распространителе.|  
|**имя_входа_динамического_фильтра**|**sysname**|Значение, используемое для вычисления [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) функции в параметризованном фильтре строк, определенных для публикации.|  
|**dynamic_filter_hostname**|**sysname**|Значение, используемое для вычисления [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) функции в параметризованном фильтре строк, определенных для публикации.|  
|**размещение_динамического_моментального_снимка**|**nvarchar(255)**|Путь к папке, откуда считываются файлы моментального снимка, если используется параметризованный фильтр строк.|  
|**frequency_type**|**int**|Частота, с которой агент выполняется по расписанию, может иметь одно из следующих значений.<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное расписание<br /><br /> **64** = автозапуск;<br /><br /> **128** = повторять|  
|**frequency_interval**|**int**|День, когда агент выполняется, может иметь одно из следующих значений.<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **3** = Вторник<br /><br /> **4** = среда<br /><br /> **5** = четверг<br /><br /> **6** = Пятница<br /><br /> **7** = суббота<br /><br /> **8** = день<br /><br /> **9** = рабочие дни<br /><br /> **10** = выходные дни|  
|**frequency_subday_type**|**int**|— Тип, который определяет, как часто запускается агент, если *frequency_type* — **4** (ежедневно) и может принимать одно из следующих значений.<br /><br /> **1** = в указанное время<br /><br /> **2** = секунды<br /><br /> **4** = минуты<br /><br /> **8** = часы|  
|**frequency_subday_interval**|**int**|Число интервалов *frequency_subday_type* , которые проходят между запланированными выполнениями агента.|  
|**frequency_relative_interval**|**int**|Неделя, когда запускается агент в данном месяце при *frequency_type* — **32** (относительно ежемесячно), и может принимать одно из следующих значений.<br /><br /> **1** = первый<br /><br /> **2** = секунды<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = последний|  
|**frequency_recurrence_factor**|**int**|Число недель или месяцев между запланированными выполнениями агента.|  
|**active_start_date**|**int**|Дата, когда агент будет впервые выполнен, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда агент будет выполнен в последний раз, в формате ГГГГММДД.|  
|**active_start_time**|**int**|Время, когда агент будет впервые выполнен, в формате ЧЧММСС.|  
|**active_end_time**|**int**|Время, когда агент будет выполнен в последний раз, в формате ЧЧММСС.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpdynamicsnapshot_job** используется в репликации слиянием.  
  
 Если для всех аргументов используются значения по умолчанию, возвращаются сведения по всем заданиям моментального снимка секционных данных для всей базы данных публикации.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** фиксированной роли базы данных, а в списке доступа к публикации для публикации могут выполнять процедуру **sp_helpdynamicsnapshot_job**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
