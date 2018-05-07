---
title: sp_dropdynamicsnapshot_job, хранимая процедура (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2f4166aa3cfed68aae16bdccd09a001ef55f3661
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет отфильтрованное задание моментального снимка данных для публикации с параметризованными фильтрами строк. Эта хранимая процедура выполняется на издателе в базе данных публикации. При удалении задания все связанные данные будут удалены из [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) системной таблицы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, из которой удаляется отфильтрованное задание моментального снимка данных. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@dynamic_snapshot_jobname**=] **"***dynamic_snapshot_jobname***"**  
 Имя удаляемого отфильтрованного задания моментального снимка данных. *dynamic_snapshot_jobname*имеет тип sysname, и если не указаны значения по умолчанию для любого задания имени будет связан с *dynamic_snapshot_jobid*.  
  
 [ **@dynamic_snapshot_jobid**=] **"***dynamic_snapshot_jobid***"**  
 Идентификатор созданного задания моментального снимка удаляемых данных. *dynamic_snapshot_jobid*— **uniqueidentifier**, по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Только *dynamic_snapshot_jobid*или *dynamic_snapshot_jobname* можно указать. Если значения не указаны ни для *dynamic_snapshot_jobid*или *dynamic_snapshot_jobname*, будут удалены все задания динамического моментального снимка для публикации.  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 *ignore_distributor* — **бит**, значение по умолчанию **0**. Этот аргумент может использоваться для удаления динамического задания моментального снимка, не выполняя задачи очистки на распространителе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_dropdynamicsnapshot** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
