---
title: sp_help_downloadlist (Transact-SQL) | Документы Microsoft
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
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e48423bc91413518abe3002a3c3d8da2cef330c2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpdownloadlist-transact-sql"></a>sp_help_downloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перечисляет все строки в **sysdownloadlist** системной таблицы для предоставленного задания или все строки, если задание не указано.  
  
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
 [  **@job_id=** ] *job_id*  
 Идентификационный номер задания, для которого возвращаются сведения. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name=** ] **"***job_name***"**  
 Имя задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@operation=** ] **"***операции***"**  
 Допустимая операция для указанного задания. *Операция* — **varchar(64)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**ДЕФЕКТ**|Серверная операция, запрашивающая целевой сервер для отключения от образца **SQLServerAgent** службы.|  
|**DELETE**|Операция задания, удаляющая все задание.|  
|**INSERT**|Операция задания, вставляющая все задание или обновляющая существующее задание. Эта операция включает все шаги и расписания задания, если возможно.|  
|**ПРИКРЕПИТЬ СНОВА**|Серверная операция, вызывающая повторную отсылку многосерверному домену целевым сервером его сведений о прикреплении, включая интервал опроса и часовой пояс. Целевой сервер также перезагружает **MSXOperator** сведения.|  
|**SET-POLL**|Серверная операция, устанавливающая интервал в секундах для опроса многосерверного домена целевыми серверами. Если указано, *значение* интерпретируется как требуемое значение интервала и может иметь значение от **10** для **28800**.|  
|**ЗАПУСК**|Операция задания, запрашивающая начало выполнения задания.|  
|**ОСТАНОВИТЬ**|Операция задания, запрашивающая прекращение выполнения задания.|  
|**ВО ВРЕМЯ СИНХРОНИЗАЦИИ**|Серверная операция, вызывающая синхронизацию системных часов целевого сервера с многосерверным доменом. Это дорогостоящая операция, поэтому ее не стоит выполнять регулярно.|  
|**UPDATE**|Операция задания, обновляющая только **sysjobs** сведения для задания, а не шаги задания или расписания. Автоматически вызывается **sp_update_job**.|  
  
 [  **@object_type=** ] **"***object_type***"**  
 Тип объекта для указанного задания. *object_type* — **varchar(64)**, значение по умолчанию NULL. *object_type* может быть JOB или SERVER. Дополнительные сведения о допустимых *object_type*значения, в разделе [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md).  
  
 [  **@object_name=** ] **"***object_name***"**  
 Имя объекта. *object_name* — **sysname**, значение по умолчанию NULL. Если *object_type* имеет значение JOB, *object_name*является именем задания. Если *object_type*является СЕРВЕРОМ, *object_name*— это имя сервера.  
  
 [ **@target_server=** ] **'***target_server***'**  
 Имя целевого сервера. *целевой_сервер* — **nvarchar(128)**, значение по умолчанию NULL.  
  
 [  **@has_error=** ] *has_error*  
 Будет ли задание подтверждать ошибки. *has_error* — **tinyint**, и значение по умолчанию NULL, которое указывает, нет ошибки будут подтверждаться. **1** указывает, что все ошибки будут подтверждаться.  
  
 [  **@status=** ] *состояния*  
 Состояние каждого задания. *состояние* — **tinyint**, значение по умолчанию NULL.  
  
 [  **@date_posted=** ] *date_posted*  
 Дата и время, для которых все записи, сделанные во время или после обозначенного времени и даты, должны быть включены в результирующий набор. *date_posted* — **datetime**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Уникальный целочисленный идентификационный номер инструкции.|  
|**source_server**|**nvarchar(30)**|Имя сервера, с которого поступила инструкция. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 это всегда имя компьютера главного сервера (MSX).|  
|**operation_code**|**nvarchar(4000)**|Код операции для инструкции.|  
|**object_name**|**sysname**|Объект, обрабатываемый инструкцией.|  
|**object_id**|**uniqueidentifier**|Идентификационный номер объекта, обрабатываемого инструкцией (**job_id** для объекта задания или 0x00 для серверного объекта) или значение данных, относящиеся к **operation_code**.|  
|**target_server**|**nvarchar(30)**|Целевой сервер, загружающий данную инструкцию.|  
|**error_message**|**nvarchar(1024)**|Сообщение об ошибке (при наличии) от целевого сервера, если в процессе обработки этой инструкции возникает проблема.<br /><br /> Примечание: Любое сообщение об ошибке блокирует дальнейшие загрузки целевого сервера.|  
|**date_posted**|**datetime**|Дата отправления инструкции в таблицу.|  
|**date_downloaded**|**datetime**|Дата загрузки инструкции целевым сервером.|  
|**status**|**tinyint**|Состояние задания:<br /><br /> **0** = еще не загружено<br /><br /> **1** = успешно загружено.|  
  
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
  
  
