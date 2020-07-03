---
title: sp_change_log_shipping_primary_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_primary_database
- sp_change_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_primary_database
ms.assetid: 8c9dce6b-d2a3-4ca7-a832-8f59a5adb214
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81a6a9fc318534df9f2ce9c2e89fb978fb15b260
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85873075"
---
# <a name="sp_change_log_shipping_primary_database-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет настройки базы данных-источника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_log_shipping_primary_database [ @database = ] 'database'  
[, [ @backup_directory = ] 'backup_directory']   
[, [ @backup_share = ] 'backup_share']   
[, [ @backup_retention_period = ] 'backup_retention_period']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] 'backup_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
[, [ @backup_compression = ] backup_compression_option ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] 'database'`Имя базы данных на сервере-источнике. Аргумент *primary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @backup_directory = ] 'backup_directory'`Путь к папке резервного копирования на сервере-источнике. *backup_directory* имеет тип **nvarchar (500)**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @backup_share = ] 'backup_share'`Сетевой путь к каталогу резервного копирования на сервере-источнике. *backup_share* имеет тип **nvarchar (500)**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @backup_retention_period = ] 'backup_retention_period'`Продолжительность времени в минутах, в течение которого файл резервной копии журнала сохраняется в каталоге резервного копирования на сервере-источнике. *backup_retention_period* имеет **тип int**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'`Режим безопасности, используемый для подключения к серверу мониторинга.  
  
 1 = проверка подлинности Windows.  
  
 0 = проверка подлинности SQL Server.  
  
 *monitor_server_security_mode* имеет **бит** и не может иметь значение null.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Имя пользователя учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @backup_threshold = ] 'backup_threshold'`Продолжительность времени (в минутах) после создания последней резервной копии до возникновения ошибки *threshold_alert* . *backup_threshold* имеет **тип int**и значение по умолчанию 60 минут.  
  
`[ @threshold_alert = ] 'threshold_alert'`Предупреждение, создаваемое при превышении порогового значения резервного копирования. *threshold_alert* имеет **тип int** и не может иметь значение null.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'`Указывает, возникает ли предупреждение при превышении *backup_threshold* .  
  
 1 = выдается.  
  
 0 = не выдается.  
  
 *threshold_alert_enabled* имеет **бит** и не может иметь значение null.  
  
`[ @history_retention_period = ] 'history_retention_period'`Продолжительность времени в минутах, в течение которого сохраняется журнал. *history_retention_period* имеет **тип int**. Если параметр не указан, используется значение 14420.  
  
`[ @backup_compression = ] backup_compression_option`Указывает, использует ли конфигурация доставки журналов [Сжатие резервных копий](../../relational-databases/backup-restore/backup-compression-sql-server.md). Этот параметр поддерживается только в [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (или более поздней версии).  
  
 0 = отключено. Не сжимать резервные копии журналов.  
  
 1 = включено. Всегда сжимать резервные копии журналов.  
  
 2 = использовать параметр [конфигурации сервера «Просмотр» или «Настройка сжатия резервных копий по умолчанию](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)». Это значение по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_change_log_shipping_primary_database** должны быть запущены из базы данных **master** на сервере источника. Эта хранимая процедура выполняет следующее:  
  
1.  При необходимости изменяет параметры в записи **log_shipping_primary_database** .  
  
2.  При необходимости изменяет локальную запись в **log_shipping_monitor_primary** на сервере источника, используя указанные аргументы.  
  
3.  Если сервер мониторинга отличается от сервера-источника, при необходимости изменения записываются в **log_shipping_monitor_primary** на сервере мониторинга с помощью предоставляемых аргументов.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование **sp_change_log_shipping_primary_database** для обновления параметров, связанных с базой данных источника [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
EXEC master.dbo.sp_change_log_shipping_primary_database   
 @database = N'AdventureWorks'   
, @backup_directory = N'c:\LogShipping'   
, @backup_share = N'\\tribeca\LogShipping'   
, @backup_retention_period = 1440   
, @backup_threshold = 60   
, @threshold_alert = 0   
, @threshold_alert_enabled = 1   
, @history_retention_period = 1440   
,@monitor_server_security_mode = 1  
,@backup_compression = 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [log_shipping_primary_databases (Transact-SQL)](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
