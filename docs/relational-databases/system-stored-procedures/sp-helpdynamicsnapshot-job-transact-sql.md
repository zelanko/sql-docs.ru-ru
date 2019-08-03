---
title: sp_helpdynamicsnapshot_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdynamicsnapshot_TSQL
- sp_helpdynamicsnapshot_job_TSQL
- job_TSQL
- helpdynamicsnapshot
- job
- sp_helpdynamicsnapshot
- sp_helpdynamicsnapshot_job
- helpdynamicsnapshot_TSQL
helpviewer_keywords:
- sp_helpdynamicsnapshot_job
ms.assetid: d6dfdf26-f874-495f-a8a6-8780699646d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55d7ad0dfd941102cfeb6661e65980f980fa8b2d
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770978"
---
# <a name="sphelpdynamicsnapshotjob-transact-sql"></a>sp_helpdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает сведения о заданиях агента, которые формируют моментальные снимки фильтрованных данных. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdynamicsnapshot_job [ [ @publication = ] 'publication' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет **%** тип **sysname**и значение по умолчанию, которое возвращает сведения обо всех заданиях моментальных снимков отфильтрованных данных, соответствующих указанным *dynamic_snapshot_jobid*и *dynamic_snapshot_jobname*для всех материалы.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Имя задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobname*имеет тип **sysname**и значение по **%** умолчанию ", которое возвращает все динамические задания для публикации с указанным *dynamic_snapshot_jobid*. Если имя задания было задано явно во время создания задания, оно будет в следующем формате:  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Идентификатор для задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobid*имеет тип **uniqueidentifier**и значение по умолчанию NULL, которое возвращает все задания моментального снимка, соответствующие заданному *dynamic_snapshot_jobname*.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Задание моментального снимка фильтрованных данных.|  
|**job_name**|**sysname**|Имя задания моментального снимка фильтрованных данных.|  
|**job_id**|**uniqueidentifier**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Идентифицируетзадание[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента на распространителе.|  
|**dynamic_filter_login**|**sysname**|Значение, используемое для вычисления функции [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) в параметризованном фильтре строк, определенном для публикации.|  
|**dynamic_filter_hostname**|**sysname**|Значение, используемое для вычисления функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) в параметризованном фильтре строк, определенном для публикации.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Путь к папке, откуда считываются файлы моментального снимка, если используется параметризованный фильтр строк.|  
|**frequency_type**|**int**|Частота, с которой агент выполняется по расписанию, может иметь одно из следующих значений.<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное относительное<br /><br /> **64** = Автозапуск<br /><br /> **128** = повторяющаяся|  
|**frequency_interval**|**int**|День, когда агент выполняется, может иметь одно из следующих значений.<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **3** = вторник<br /><br /> **4** = среда<br /><br /> **5** = четверг<br /><br /> **6** = Пятница<br /><br /> **7** = Суббота<br /><br /> **8** = день<br /><br /> **9** = рабочие дни<br /><br /> **10** = выходные дни|  
|**frequency_subday_type**|**int**|Тип, определяющий частоту запуска агента, когда аргумент *frequency_type* равен **4** (ежедневно), и может принимать одно из следующих значений.<br /><br /> **1** = в указанное время<br /><br /> **2** = секунды<br /><br /> **4** = минуты<br /><br /> **8** = часы|  
|**frequency_subday_interval**|**int**|Количество интервалов *frequency_subday_type* , которые происходят между запланированным выполнением агента.|  
|**frequency_relative_interval**|**int**|Неделя, в которую агент работает в заданном месяце, когда аргумент *frequency_type* равен **32** (ежемесячное относительное) и может принимать одно из следующих значений.<br /><br /> **1** = сначала<br /><br /> **2** = секунда<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = Последняя|  
|**frequency_recurrence_factor**|**int**|Число недель или месяцев между запланированными выполнениями агента.|  
|**active_start_date**|**int**|Дата, когда агент будет впервые выполнен, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда агент будет выполнен в последний раз, в формате ГГГГММДД.|  
|**active_start_time**|**int**|Время, когда агент будет впервые выполнен, в формате ЧЧММСС.|  
|**active_end_time**|**int**|Время, когда агент будет выполнен в последний раз, в формате ЧЧММСС.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpdynamicsnapshot_job** используется в репликации слиянием.  
  
 Если для всех аргументов используются значения по умолчанию, возвращаются сведения по всем заданиям моментального снимка секционных данных для всей базы данных публикации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** и списка доступа к публикации для публикации могут выполнять **sp_helpdynamicsnapshot_job**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
