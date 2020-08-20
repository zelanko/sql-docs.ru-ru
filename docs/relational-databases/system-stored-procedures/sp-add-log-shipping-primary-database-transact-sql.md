---
description: sp_add_log_shipping_primary_database (Transact-SQL)
title: sp_add_log_shipping_primary_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_primary_database
- sp_add_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_primary_database
ms.assetid: 69531611-113f-46b5-81a6-7bf496d0353c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ed823f2b6564593388893db74866931bc1c0c93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464672"
---
# <a name="sp_add_log_shipping_primary_database-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Настраивает базу данных-источник для конфигурации доставки журналов, включая задания резервного копирования, запись локального монитора и запись удаленного монитора.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_log_shipping_primary_database [ @database = ] 'database',   
[ @backup_directory = ] 'backup_directory',   
[ @backup_share = ] 'backup_share',   
[ @backup_job_name = ] 'backup_job_name',   
[, [ @backup_retention_period = ] backup_retention_period]  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] backup_threshold ]   
[, [ @threshold_alert = ] threshold_alert ]   
[, [ @threshold_alert_enabled = ] threshold_alert_enabled ]   
[, [ @history_retention_period = ] history_retention_period ]  
[, [ @backup_job_id = ] backup_job_id OUTPUT ]  
[, [ @primary_id = ] primary_id OUTPUT]  
[, [ @backup_compression = ] backup_compression_option ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] 'database'` Имя базы данных-источника доставки журналов. *база данных* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @backup_directory = ] 'backup_directory'` Путь к папке резервного копирования на сервере-источнике. *backup_directory* имеет тип **nvarchar (500)**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @backup_share = ] 'backup_share'` Сетевой путь к каталогу резервного копирования на сервере-источнике. *backup_share* имеет тип **nvarchar (500)**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @backup_job_name = ] 'backup_job_name'` Имя задания агент SQL Server на сервере-источнике, который копирует резервную копию в папку резервного копирования. *backup_job_name* имеет тип **sysname** и не может иметь значение null.  
  
`[ @backup_retention_period = ] backup_retention_period` Продолжительность времени в минутах, в течение которого файл резервной копии журнала сохраняется в каталоге резервного копирования на сервере-источнике. *backup_retention_period* имеет **тип int**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @monitor_server = ] 'monitor_server'` Имя сервера мониторинга. Аргумент *Monitor_server* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @monitor_server_security_mode = ] monitor_server_security_mode` Режим безопасности, используемый для подключения к серверу мониторинга.  
  
 1 = проверка подлинности Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности. *monitor_server_security_mode* имеет **бит** и не может иметь значение null.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` Имя пользователя учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @backup_threshold = ] backup_threshold` Продолжительность времени (в минутах) после создания последней резервной копии до возникновения ошибки *threshold_alert* . *backup_threshold* имеет **тип int**и значение по умолчанию 60 минут.  
  
`[ @threshold_alert = ] threshold_alert` Предупреждение, создаваемое при превышении порогового значения резервного копирования. *threshold_alert* имеет **тип int**и значение по умолчанию 14 420.  
  
`[ @threshold_alert_enabled = ] threshold_alert_enabled` Указывает, будет ли создаваться предупреждение при превышении *backup_threshold* . Значение по умолчанию (0) указывает, что это предупреждение отключено и не будет активизироваться. *threshold_alert_enabled* имеет **бит**.  
  
`[ @history_retention_period = ] history_retention_period` Продолжительность времени в минутах, в течение которого будет храниться журнал. *history_retention_period* имеет **тип int**и значение по умолчанию NULL. Если ничего не указано, подразумевается значение 14420.  
  
`[ @backup_job_id = ] backup_job_id OUTPUT`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Идентификатор задания агента, связанного с заданием резервного копирования на сервере источника. *backup_job_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
`[ @primary_id = ] primary_id OUTPUT` Идентификатор базы данных источника для конфигурации доставки журналов. *primary_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
`[ @backup_compression = ] backup_compression_option` Указывает, использует ли конфигурация доставки журналов [Сжатие резервных копий](../../relational-databases/backup-restore/backup-compression-sql-server.md). Этот параметр поддерживается только в [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (или более поздней версии).  
  
 0 = отключено. Не сжимать резервные копии журналов.  
  
 1 = включено. Всегда сжимать резервные копии журналов.  
  
 2 = использовать параметр [конфигурации сервера «Просмотр» или «Настройка сжатия резервных копий по умолчанию](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)». Это значение по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_log_shipping_primary_database** должны быть запущены из базы данных **master** на сервере источника. Эта хранимая процедура выполняет следующие действия:  
  
1.  Создает первичный идентификатор и добавляет запись для базы данных-источника в таблицу **log_shipping_primary_databases** используя указанные аргументы.  
  
2.  создает задание резервного копирования для базы данных-источника, если она отключена;  
  
3.  Задает идентификатор задания резервного копирования в записи **log_shipping_primary_databases** в качестве идентификатора задания резервного копирования.  
  
4.  Добавляет запись локального монитора в таблицу **log_shipping_monitor_primary** на сервере-источнике, используя указанные аргументы.  
  
5.  Если сервер мониторинга отличается от сервера-источника, добавляет запись монитора в **log_shipping_monitor_primary** на сервере мониторинга, используя указанные аргументы.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] добавляется в качестве базы данных-источника в конфигурацию доставки журналов.  
  
```  
DECLARE @LS_BackupJobId AS uniqueidentifier ;  
DECLARE @LS_PrimaryId AS uniqueidentifier ;  
  
EXEC master.dbo.sp_add_log_shipping_primary_database   
@database = N'AdventureWorks'   
,@backup_directory = N'c:\lsbackup'   
,@backup_share = N'\\tribeca\lsbackup'   
,@backup_job_name = N'LSBackup_AdventureWorks'   
,@backup_retention_period = 1440  
,@monitor_server = N'rockaway'   
,@monitor_server_security_mode = 1   
,@backup_threshold = 60   
,@threshold_alert = 0   
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440   
,@backup_job_id = @LS_BackupJobId OUTPUT   
,@primary_id = @LS_PrimaryId OUTPUT   
,@overwrite = 1   
,@backup_compression = 0;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
