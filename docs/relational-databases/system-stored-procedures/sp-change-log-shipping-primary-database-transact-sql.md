---
title: "sp_change_log_shipping_primary_database (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_primary_database
- sp_change_log_shipping_primary_database_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_change_log_shipping_primary_database
ms.assetid: 8c9dce6b-d2a3-4ca7-a832-8f59a5adb214
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5f587550af49059f1ff72b167265862c8598ae93
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spchangelogshippingprimarydatabase-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет настройки базы данных-источника.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
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
 [  **@database =** ] "*базы данных*"  
 Имя базы данных на сервере-источнике. *primary_database* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@backup_directory =** ] "*backup_directory*"  
 Путь к папке резервного копирования на сервере-источнике. *backup_directory* — **nvarchar(500)**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 [  **@backup_share =** ] "*backup_share*"  
 Сетевой путь к каталогу резервного копирования на сервере-источнике. *backup_share* — **nvarchar(500)**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 [  **@backup_retention_period =** ] "*backup_retention_period*"  
 Время в минутах, в течение которого файл резервной копии журнала хранится в каталоге резервных копий на сервере-источнике. *backup_retention_period* — **int**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 [  **@monitor_server_security_mode =** ] "*monitor_server_security_mode*"  
 Режим безопасности, используемый для подключения к серверу мониторинга:  
  
 1 = проверка подлинности Windows.  
  
 0 = проверка подлинности SQL Server.  
  
 *monitor_server_security_mode* — **бит** и не может иметь значение NULL.  
  
 [  **@monitor_server_login =** ] "*monitor_server_login*"  
 Имя учетной записи, используемой для доступа к серверу мониторинга.  
  
 [  **@monitor_server_password =** ] "*monitor_server_password*"  
 Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
 [  **@backup_threshold =** ] "*backup_threshold*"  
 — Это период времени в минутах после последнего резервного копирования до *threshold_alert* возникает ошибка. *backup_threshold* — **int**, значение по умолчанию 60 минут.  
  
 [  **@threshold_alert =** ] "*threshold_alert*"  
 Предупреждение, создаваемое при превышении порогового значения. *threshold_alert* — **int** и не может иметь значение NULL.  
  
 [  **@threshold_alert_enabled =** ] "*threshold_alert_enabled*"  
 Указывает, формируется ли предупреждение при *backup_threshold* превышено.  
  
 1 = выдается.  
  
 0 = не выдается.  
  
 *threshold_alert_enabled* — **бит** и не может иметь значение NULL.  
  
 [  **@history_retention_period =** ] "*history_retention_period*"  
 Длительность времени в минутах, в течение которого сохраняется журнал. *history_retention_period* — **int**. Если ничего не указано, используется значение 14 420.  
  
 [  **@backup_compression** =] *backup_compression_option*  
 Указывает, использует ли конфигурации доставки журналов [сжатие резервных копий](../../relational-databases/backup-restore/backup-compression-sql-server.md). Этот параметр поддерживается только в [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (или более поздней версии).  
  
 0 = отключено. Не сжимать резервные копии журналов.  
  
 1 = включено. Всегда сжимать резервные копии журналов.  
  
 2 = использовать значение параметра [Просмотр или настройка параметра конфигурации сервера по умолчанию сжатие резервных копий](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Это значение по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_change_log_shipping_primary_database** должна запускаться из **master** базы данных на сервере-источнике. Эта хранимая процедура выполняет следующее:  
  
1.  Изменяет параметры в **log_shipping_primary_database** записи, при необходимости.  
  
2.  Изменяет локальную запись в **log_shipping_monitor_primary** на основном сервере, используя указанные аргументы при необходимости.  
  
3.  Если сервер мониторинга отличается от сервера-источника, изменяет запись в **log_shipping_monitor_primary** мониторинга сервера, используя указанные аргументы при необходимости.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование **sp_change_log_shipping_primary_database** для обновления параметров, связанных с базой данных-источником [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
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
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [log_shipping_primary_databases &#40; Transact-SQL &#41;](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
