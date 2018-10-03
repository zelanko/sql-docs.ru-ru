---
title: sp_add_log_shipping_secondary_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 35bd51c2c2d1d9e3ed82cd06cd4a4524b9f7e422
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635912"
---
# <a name="spaddlogshippingsecondarydatabase-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает базы данных-получателей для доставки журналов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@secondary_database** =] '*secondary_database*"  
 Имя базы данных-получателя. *secondary_database* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@primary_server** =] '*primary_server*"  
 Имя первичного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов. *primary_server* — **sysname** и не может иметь значение NULL.  
  
 [ **@primary_database** =] '*primary_database*"  
 Имя базы данных на сервере-источнике. *primary_database* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@restore_delay** =] '*restore_delay*"  
 Время ожидания (в минутах), по истечении которого сервер-получатель восстанавливает данный файл резервной копии. *restore_delay* — **int** и не может иметь значение NULL. Значение по умолчанию — 0.  
  
 [ **@restore_all** =] '*restore_all*"  
 Если значение этого аргумента равно 1, сервер-получатель восстанавливает все доступные резервные копии журналов транзакций при выполнении задания восстановления. В противном случае он останавливается после восстановления одного файла. *restore_all* — **бит** и не может иметь значение NULL.  
  
 [ **@restore_mode** =] '*restore_mode*"  
 Режим восстановления базы данных-получателя.  
  
 0 = восстановление журнала с аргументом NORECOVERY.  
  
 1 = восстановление журнала с аргументом STANDBY.  
  
 *восстановление* — **бит** и не может иметь значение NULL.  
  
 [ **@disconnect_users** =] '*disconnect_users*"  
 Если значение этого аргумента равно 1, пользователи отключаются от базы данных-получателя при выполнении операции восстановления. По умолчанию равно 0. *Отключение* пользователей: **бит** и не может иметь значение NULL.  
  
 [ **@block_size** =] '*block_size*"  
 Размер блока (в байтах) устройства резервного копирования. *block_size* — **int** со значением по умолчанию-1.  
  
 [ **@buffer_count** =] '*buffer_count*"  
 Общее число буферов, используемых операцией создания резервной копии или восстановления. *buffer_count* — **int** со значением по умолчанию-1.  
  
 [ **@max_transfer_size** =] '*max_transfer_size*"  
 Размер (в байтах) максимального входного или выходного запроса, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдает на устройство резервного копирования. *max_transfersize* — **int** и может иметь значение NULL.  
  
 [ **@restore_threshold** =] '*restore_threshold*"  
 Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение. *restore_threshold* — **int** и не может иметь значение NULL.  
  
 [ **@threshold_alert** =] '*threshold_alert*"  
 Предупреждение, создаваемое при превышении порогового значения. *threshold_alert* — **int**, значение по умолчанию 14 420.  
  
 [ **@threshold_alert_enabled** =] '*threshold_alert_enabled*"  
 Указывает, нужно ли создавать оповещение при *backup_threshold* превышено. При значении, равном единице (1), устанавливаемом по умолчанию, предупреждение будет инициировано. *threshold_alert_enabled* — **бит**.  
  
 [ **@history_retention_period** =] '*history_retention_period*"  
 Длительность времени в минутах, в течение которого сохраняется журнал. *history_retention_period* — **int**, значение по умолчанию NULL. Если ничего не указано, используется значение 14 420.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_add_log_shipping_secondary_database** должна запускаться из **master** базы данных на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  **sp_add_log_shipping_secondary_primary** должен вызываться перед Эта хранимая процедура для инициализации источника сведения о базе данных на сервере-получателе доставки журнала.  
  
2.  Добавляет запись для базы данных-получателя в **log_shipping_secondary_databases** с указанными аргументами.  
  
3.  Добавляет запись локального монитора в **log_shipping_monitor_secondary** на сервере-получателе, используя указанные аргументы.  
  
4.  Если сервер мониторинга отличается от сервера-получателя, добавляет запись монитора в **log_shipping_monitor_secondary** на мониторе сервере, используя предоставленные аргументы.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 Этот пример иллюстрирует использование **sp_add_log_shipping_secondary_database** хранимую процедуру для добавления базы данных **LogShipAdventureWorks** как базу данных-получатель в конфигурацию доставки журналов с помощью базы данных-источника [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на сервере-источнике TRIBECA.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
