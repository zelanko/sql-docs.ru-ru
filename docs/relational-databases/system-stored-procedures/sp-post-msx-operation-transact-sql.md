---
title: sp_post_msx_operation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2d9cc791a0bcd01b2af64ce61771d7460eda4b21
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831018"
---
# <a name="sp_post_msx_operation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вставляет операции (строки) в системную таблицу **sysdownloadlist** для загрузки и выполнения целевых серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_post_msx_operation  
     [ @operation = ] 'operation'  
     [ , [ @object_type = ] 'object' ]   
     { , [ @job_id = ] job_id }   
     [ , [ @specific_target_server = ] 'target_server' ]   
     [ , [ @value = ] value ]  
     [ , [ @schedule_uid = ] schedule_uid ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @operation = ] 'operation'`Тип операции для опубликованной операции. *Операция*имеет тип **varchar (64)** и не имеет значения по умолчанию. Допустимые операции зависят от *object_type*.  
  
|Тип объекта|Операция|  
|-----------------|---------------|  
|**ДОЛЖНО**|INSERT<br /><br /> UPDATE<br /><br /> DELETE<br /><br /> START<br /><br /> STOP|  
|**СЕРВЕРОМ**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**Расписание**|INSERT<br /><br /> UPDATE<br /><br /> DELETE|  
  
`[ @object_type = ] 'object'`Тип объекта, для которого необходимо опубликовать операцию. Допустимые типы: **Job**, **Server**и **Schedule**. *объект* имеет тип **varchar (64)** и значение по умолчанию **Job**.  
  
`[ @job_id = ] job_id`Идентификационный номер задания, к которому применяется операция. *job_id* имеет тип **uniqueidentifier**и не имеет значения по умолчанию. **0x00** означает все задания. Если *объект* является **сервером**, *job_id*не требуется.  
  
`[ @specific_target_server = ] 'target_server'`Имя целевого сервера, к которому применяется указанная операция. Если указан параметр *job_id* , но *target_server* не указаны, операции публикуются для всех серверов заданий задания. *target_server* имеет тип **nvarchar (30)** и значение по умолчанию NULL.  
  
`[ @value = ] value`Интервал опроса в секундах. Аргумент*value* имеет тип **int**и значение по умолчанию NULL. Этот параметр следует указывать только в том случае, если для параметра *Operation* задано **значение poll**.  
  
`[ @schedule_uid = ] schedule_uid`Уникальный идентификатор расписания, к которому применяется операция. *schedule_uid* имеет тип **uniqueidentifier**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_post_msx_operation** должны запускаться из базы данных **msdb** .  
  
 **sp_post_msx_operation** всегда можно вызвать безопасно, так как он сначала определяет, является ли текущий сервер агентом многосерверного Microsoft SQL Server и, если да *, это*многосерверное задание.  
  
 После публикации операции она появляется в таблице **sysdownloadlist** . После создания и отправки задания все его дальнейшие изменения должны отправляться на целевые серверы (TSX). Для этого необходимо использовать список загрузки.  
  
 Для управления списком загрузки настоятельно рекомендуется использовать среду SQL Server Management Studio. Дополнительные сведения см. в разделе [Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователям должна быть предоставлена предопределенная роль сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
