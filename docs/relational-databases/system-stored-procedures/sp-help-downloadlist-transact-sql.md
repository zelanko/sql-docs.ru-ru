---
title: sp_help_downloadlist (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bc658776dddbf79362e3ab4c90ba052abb193e63
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901502"
---
# <a name="sp_help_downloadlist-transact-sql"></a>sp_help_downloadlist (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Перечисляет все строки в системной таблице **sysdownloadlist** для указанного задания или все строки, если задание не указано.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_downloadlist { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }   
     [ , [ @operation = ] 'operation' ]   
     [ , [ @object_type = ] 'object_type' ]   
     [ , [ @object_name = ] 'object_name' ]   
     [ , [ @target_server = ] 'target_server' ]   
     [ , [ @has_error = ] has_error ]   
     [ , [ @status = ] status ]   
     [ , [ @date_posted = ] date_posted ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания, для которого возвращаются сведения. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @operation = ] 'operation'`Допустимая операция для указанного задания. *Операция* имеет тип **varchar (64)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|**ОШИБК**|Серверная операция, которая запрашивает у целевого сервера исключение из службы Master **SQLServerAgent** .|  
|**DELETE**|Операция задания, удаляющая все задание.|  
|**INSERT**|Операция задания, вставляющая все задание или обновляющая существующее задание. Эта операция включает все шаги и расписания задания, если возможно.|  
|**RE-ENLIST**|Серверная операция, вызывающая повторную отсылку многосерверному домену целевым сервером его сведений о прикреплении, включая интервал опроса и часовой пояс. Целевой сервер также снова скачивает сведения о **MSXOperator** .|  
|**SET-POLL**|Серверная операция, устанавливающая интервал в секундах для опроса многосерверного домена целевыми серверами. Если указано, *значение* интерпретируется как требуемое значение интервала и может быть значением от **10** до **28 800**.|  
|**ЗАПУСТИТЬ**|Операция задания, запрашивающая начало выполнения задания.|  
|**ПОЗИЦИИ**|Операция задания, запрашивающая прекращение выполнения задания.|  
|**SYNC-TIME**|Серверная операция, вызывающая синхронизацию системных часов целевого сервера с многосерверным доменом. Это дорогостоящая операция, поэтому ее не стоит выполнять регулярно.|  
|**UPDATE**|Операция задания, которая обновляет только данные **sysjobs** для задания, а не шаги задания или расписания. Автоматически вызывается **sp_update_job**.|  
  
`[ @object_type = ] 'object_type'`Тип объекта для указанного задания. *object_type* имеет тип **varchar (64)** и значение по умолчанию NULL. *object_type* может быть либо заданием, либо сервером. Дополнительные сведения о допустимых значениях *object_type*см. в разделе [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md).  
  
`[ @object_name = ] 'object_name'`Имя объекта. Аргумент *object_name* имеет тип **sysname**и значение по умолчанию NULL. Если *object_type* является заданием, *object_name*является именем задания. Если *object_type*является сервером, *object_name*является именем сервера.  
  
`[ @target_server = ] 'target_server'`Имя целевого сервера. *target_server* имеет тип **nvarchar (128)** и значение по умолчанию NULL.  
  
`[ @has_error = ] has_error`Указывает, должно ли задание подтверждать ошибки. *has_error* имеет тип **tinyint**и значение по умолчанию NULL, которое указывает, что ошибки не должны быть подтверждены. **1** означает, что все ошибки должны быть подтверждены.  
  
`[ @status = ] status`Состояние задания. *состояние* имеет тип **tinyint**и значение по умолчанию NULL.  
  
`[ @date_posted = ] date_posted`Дата и время, для которых в результирующий набор должны быть включены все записи, созданные в или после указанной даты и времени. *date_posted* имеет тип **DateTime**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Уникальный целочисленный идентификационный номер инструкции.|  
|**source_server**|**nvarchar(30)**|Имя сервера, с которого поступила инструкция. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7,0 это всегда имя компьютера главного сервера (MSX).|  
|**operation_code**|**nvarchar(4000)**|Код операции для инструкции.|  
|**object_name**|**sysname**|Объект, обрабатываемый инструкцией.|  
|**object_id**|**uniqueidentifier**|Идентификационный номер объекта, затрагиваемого инструкцией (**job_id** для объекта задания или 0x00 для объекта сервера) или значение данных, относящееся к **operation_code**.|  
|**target_server**|**nvarchar(30)**|Целевой сервер, загружающий данную инструкцию.|  
|**error_message**|**nvarchar(1024)**|Сообщение об ошибке (при наличии) от целевого сервера, если в процессе обработки этой инструкции возникает проблема.<br /><br /> Примечание. любое сообщение об ошибке блокирует все дальнейшие загрузки на целевом сервере.|  
|**date_posted**|**datetime**|Дата отправления инструкции в таблицу.|  
|**date_downloaded**|**datetime**|Дата загрузки инструкции целевым сервером.|  
|**status**|**tinyint**|Состояние задания:<br /><br /> **0** = еще не скачан<br /><br /> **1** = успешно загружен.|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере перечисляются строки в таблице `sysdownloadlist` для задания `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_downloadlist  
    @job_name = N'NightlyBackups',  
    @operation = N'UPDATE',   
    @object_type = N'JOB',   
    @object_name = N'NightlyBackups',  
    @target_server = N'SEATTLE2',   
    @has_error = 1,   
    @status = NULL,   
    @date_posted = NULL ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
