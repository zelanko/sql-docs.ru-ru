---
title: sp_post_msx_operation (Transact-SQL) | Документация Майкрософт
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
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1524f9e3f20a774d32c491bc264f2c6c63e7b18
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395805"
---
# <a name="sppostmsxoperation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вставляет операции (строки) в **sysdownloadlist** системной таблице на целевых серверах для скачивания и выполнения.  
  
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
 [  **@operation =**] **"***операции***"**  
 Тип операции для отправленной операции. *Операция*— **varchar(64)**, не имеет значения по умолчанию. Допустимость операций зависит *object_type*.  
  
|Тип объекта|Операция|  
|-----------------|---------------|  
|**JOB**|INSERT<br /><br /> UPDATE<br /><br /> DELETE<br /><br /> START<br /><br /> STOP|  
|**СЕРВЕР**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**РАСПИСАНИЕ**|INSERT<br /><br /> UPDATE<br /><br /> DELETE|  
  
 [  **@object_type =**] **"***объект***"**  
 Тип объекта, для которого отправляется операция. Допустимые типы: **задания**, **SERVER**, и **РАСПИСАНИЕ**. *Объект* — **varchar(64)**, значение по умолчанию **задания**.  
  
 [  **@job_id =**] *job_id*  
 Идентификационный номер задания, к которому применяется операция. *job_id* — **uniqueidentifier**, не имеет значения по умолчанию. **0x00** подразумевает все задания. Если *объект* — **SERVER**, затем *job_id*не является обязательным.  
  
 [ **@specific_target_server =**] **'***target_server***'**  
 Имя целевого сервера, к которому применяется заданная операция. Если *job_id* указан, но *target_server* не указан, то операции направляются на все серверы задания. *target_server* — **nvarchar(30)**, значение по умолчанию NULL.  
  
 [  **@value =**] *значение*  
 Интервал опроса (в секундах). Аргумент*value* имеет тип **int**и значение по умолчанию NULL. Укажите этот параметр только в том случае, если *операции* — **SET-POLL**.  
  
 [  **@schedule_uid=** ] *schedule_uid*  
 Уникальный идентификатор расписания, к которому применяется операция. *schedule_uid* — **uniqueidentifier**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_post_msx_operation** должна запускаться из **msdb** базы данных.  
  
 **sp_post_msx_operation** всегда может вызывать безопасно, так как он сначала определяет, если текущий сервер является многосерверных агента Microsoft SQL Server и если да, ли *объект*многосерверным заданием.  
  
 После операции, он отображается в **sysdownloadlist** таблицы. После создания и отправки задания все его дальнейшие изменения должны отправляться на целевые серверы (TSX). Для этого необходимо использовать список загрузки.  
  
 Для управления списком загрузки настоятельно рекомендуется использовать среду SQL Server Management Studio. Дополнительные сведения см. в разделе [Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md).  
  
## <a name="permissions"></a>Разрешения  
 Чтобы выполнить эту хранимую процедуру, пользователям необходимо предоставить **sysadmin** предопределенной роли сервера.  
  
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
  
  
