---
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
ms.openlocfilehash: 5af11c14c7b0bf3b8e32d503c4b77e59623ce9ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140450"
---
# <a name="spaddlogshippingprimarydatabase-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
`[ @database = ] 'database'` — Имя журнала доставки базы данных-источника. *База данных* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
`[ @backup_directory = ] 'backup_directory'` — Это путь к папке резервного копирования на сервере-источнике. *backup_directory* — **nvarchar(500)** , не имеет значения по умолчанию и не может иметь значение NULL.  
  
`[ @backup_share = ] 'backup_share'` Является сетевой путь к каталогу резервного копирования на сервере-источнике. *backup_share* — **nvarchar(500)** , не имеет значения по умолчанию и не может иметь значение NULL.  
  
`[ @backup_job_name = ] 'backup_job_name'` — Имя задания агента SQL Server на сервере-источнике, создает резервную копию в папке резервного копирования. *backup_job_name* — **sysname** и не может иметь значение NULL.  
  
`[ @backup_retention_period = ] backup_retention_period` — Это период времени в минутах, чтобы сохранить файл резервной копии журнала в каталоге резервных копий на сервере-источнике. *backup_retention_period* — **int**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
`[ @monitor_server = ] 'monitor_server'` — Имя сервера мониторинга. *Monitor_server* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
`[ @monitor_server_security_mode = ] monitor_server_security_mode` Режим безопасности, используемый для подключения к серверу мониторинга.  
  
 1 = проверка подлинности Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *monitor_server_security_mode* — **бит** и не может иметь значение NULL.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` — Это имя пользователя учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` — Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @backup_threshold = ] backup_threshold` — Это продолжительность времени в минутах после последнего резервного копирования до *threshold_alert* возникает ошибка. *backup_threshold* — **int**, значение по умолчанию 60 минут.  
  
`[ @threshold_alert = ] threshold_alert` Это предупреждение, создаваемое при превышении порогового значения. *threshold_alert* — **int**, значение по умолчанию 14 420.  
  
`[ @threshold_alert_enabled = ] threshold_alert_enabled` Указывает, будет ли предупреждение возникает, когда *backup_threshold* превышено. Значение по умолчанию (0) указывает, что это предупреждение отключено и не будет активизироваться. *threshold_alert_enabled* — **бит**.  
  
`[ @history_retention_period = ] history_retention_period` — Это продолжительность времени в минутах, в которых сохраняются данные журнала. *history_retention_period* — **int**, значение по умолчанию NULL. Если ничего не указано, подразумевается значение 14420.  
  
`[ @backup_job_id = ] backup_job_id OUTPUT` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Идентификатор задания агента, связанный с заданием резервного копирования на сервере-источнике. *backup_job_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
`[ @primary_id = ] primary_id OUTPUT` Идентификатор базы данных-источника для конфигурации доставки журналов. *primary_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
`[ @backup_compression = ] backup_compression_option` Указывает, использует ли конфигурация доставки журналов [сжатие резервных копий](../../relational-databases/backup-restore/backup-compression-sql-server.md). Этот параметр поддерживается только в [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (или более поздней версии).  
  
 0 = отключено. Не сжимать резервные копии журналов.  
  
 1 = включено. Всегда сжимать резервные копии журналов.  
  
 2 = использовать значение параметра [Просмотр или настройка параметра сжатия резервных копий по умолчанию параметр конфигурации сервера](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Это значение по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_add_log_shipping_primary_database** должна запускаться из **master** базы данных на сервере-источнике. Эта хранимая процедура выполняет следующие действия:  
  
1.  Создает первичный идентификатор и добавляет запись для базы данных-источника в таблице **log_shipping_primary_databases** с указанными аргументами.  
  
2.  создает задание резервного копирования для базы данных-источника, если она отключена;  
  
3.  Задает идентификатор задания резервного копирования в **log_shipping_primary_databases** запись идентификатору задания резервного копирования.  
  
4.  Добавляет запись локального монитора в таблице **log_shipping_monitor_primary** на сервере-источнике, используя указанные аргументы.  
  
5.  Если сервер мониторинга отличается от сервера-источника, добавляет запись монитора в **log_shipping_monitor_primary** на мониторе сервере, используя предоставленные аргументы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
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
  
## <a name="see-also"></a>См. также  
 [О доставке журналов &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
