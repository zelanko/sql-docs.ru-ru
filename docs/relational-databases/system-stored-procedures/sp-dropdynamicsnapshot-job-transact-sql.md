---
title: sp_dropdynamicsnapshot_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 224de422a7f43b7e2c3ff1dc090eeb3b55c752b1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85860163"
---
# <a name="sp_dropdynamicsnapshot_job-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет отфильтрованное задание моментального снимка данных для публикации с параметризованными фильтрами строк. Эта хранимая процедура выполняется на издателе в базе данных публикации. При удалении задания все связанные данные удаляются из системной таблицы [мсдинамикснапшотжобс](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, из которой удаляется задание моментального снимка отфильтрованных данных. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Имя удаляемого задания моментального снимка отфильтрованных данных. Аргумент *dynamic_snapshot_jobname*имеет тип sysname, и, если он не указан по умолчанию для любого имени задания, связанного с *dynamic_snapshot_jobid*.  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Идентификатор удаляемого задания моментального снимка отфильтрованных данных. *dynamic_snapshot_jobid*имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  Можно указать только *dynamic_snapshot_jobid*или *dynamic_snapshot_jobname* . Если значения не указаны ни для *dynamic_snapshot_jobid*, ни для *dynamic_snapshot_jobname*, все задания динамического моментального снимка для публикации удаляются.  
  
`[ @ignore_distributor = ] ignore_distributor`*ignore_distributor* имеет **бит**и значение по умолчанию **0**. Этот аргумент может использоваться для удаления динамического задания моментального снимка, не выполняя задачи очистки на распространителе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_dropdynamicsnapshot** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>См. также  
 [sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
