---
title: sp_add_log_shipping_secondary_primary (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_primary_TSQL
- sp_add_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_primary
ms.assetid: bfbbbee2-c255-4a59-a963-47d6e980a8e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 155f59426e8167d5d888f3890089dd4b2ea3bf7c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72909686"
---
# <a name="sp_add_log_shipping_secondary_primary-transact-sql"></a>sp_add_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает первичные данные, добавляет ссылки на локальные и удаленные мониторы, а также создает задания копирования и восстановления на сервере-получателе для указанной базы данных-источника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_log_shipping_secondary_primary  
 [ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[ @backup_source_directory = ] 'backup_source_directory' ,   
[ @backup_destination_directory = ] 'backup_destination_directory'  
[ @copy_job_name = ] 'copy_job_name'  
[ @restore_job_name = ] 'restore_job_name'  
[, [ @file_retention_period = ] 'file_retention_period']  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @copy_job_id = ] 'copy_job_id' OUTPUT ]  
[, [ @restore_job_id = ] 'restore_job_id' OUTPUT ]  
[, [ @secondary_id = ] 'secondary_id' OUTPUT]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @primary_server = ] 'primary_server'`Имя основного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов. *primary_server* имеет тип **sysname** и не может иметь значение null.  
  
`[ @primary_database = ] 'primary_database'`Имя базы данных на сервере-источнике. Аргумент *primary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @backup_source_directory = ] 'backup_source_directory'`Каталог, в котором хранятся файлы резервных копий журналов транзакций с сервера источника. *backup_source_directory* имеет тип **nvarchar (500)** и не может иметь значение null.  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'`Каталог на сервере-получателе, куда копируются файлы резервных копий. *backup_destination_directory* имеет тип **nvarchar (500)** и не может иметь значение null.  
  
`[ @copy_job_name = ] 'copy_job_name'`Имя, используемое для создаваемого задания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента для копирования резервных копий журналов транзакций на сервер-получатель. *copy_job_name* имеет тип **sysname** и не может иметь значение null.  
  
`[ @restore_job_name = ] 'restore_job_name'`Имя задания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента на сервере-получателе, которое восстанавливает резервные копии в базе данных-получателе. *restore_job_name* имеет тип **sysname** и не может иметь значение null.  
  
`[ @file_retention_period = ] 'file_retention_period'`Продолжительность времени в минутах, в течение которого файл резервной копии сохраняется на сервере-получателе по пути, указанному @backup_destination_directory параметром, перед удалением. *history_retention_period* имеет **тип int**и значение по умолчанию NULL. Если ничего не указано, подразумевается значение 14420.  
  
`[ @monitor_server = ] 'monitor_server'`Имя сервера мониторинга. Аргумент *Monitor_server* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'`Режим безопасности, используемый для подключения к серверу мониторинга.  
  
 1 = проверка подлинности Windows.  
  
 0 = проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *monitor_server_security_mode* имеет **бит** и не может иметь значение null.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Имя пользователя учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @copy_job_id = ] 'copy_job_id' OUTPUT`Идентификатор, связанный с заданием копирования на сервере-получателе. *copy_job_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
`[ @restore_job_id = ] 'restore_job_id' OUTPUT`Идентификатор, связанный с заданием восстановления на сервере-получателе. *restore_job_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
`[ @secondary_id = ] 'secondary_id' OUTPUT`Идентификатор сервера-получателя в конфигурации доставки журналов. *secondary_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_log_shipping_secondary_primary** должны запускаться из базы данных **master** на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  Формирует идентификатор получателя для указанного сервера-источника и базы данных-источника.  
  
2.  Выполняет следующее:  

    1.  Добавляет запись для вторичного идентификатора в **log_shipping_secondary** используя указанные аргументы.  
  
    2.  создает отключенное задание копирования для идентификатора получателя;  
  
    3.  Задает идентификатор задания копирования в записи **log_shipping_secondary** в качестве идентификатора задания копирования.  
  
    4.  создает отключенное задание восстановления для идентификатора получателя;  
  
    5.  Задайте идентификатор задания восстановления в записи **log_shipping_secondary** в качестве идентификатора задания восстановления.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование хранимой процедуры **sp_add_log_shipping_secondary_primary** для настройки сведений о базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -источнике на сервере-получателе.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_primary   
@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks'   
,@backup_source_directory = N'\\tribeca\LogShipping'   
,@backup_destination_directory = N''   
,@copy_job_name = N''   
,@restore_job_name = N''   
,@file_retention_period = 1440   
,@monitor_server = N'ROCKAWAY'   
,@monitor_server_security_mode = 1   
,@copy_job_id = @LS_Secondary__CopyJobId OUTPUT   
,@restore_job_id = @LS_Secondary__RestoreJobId OUTPUT   
,@secondary_id = @LS_Secondary__SecondaryId OUTPUT ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
