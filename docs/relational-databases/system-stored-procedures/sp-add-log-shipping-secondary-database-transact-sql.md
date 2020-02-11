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
ms.openlocfilehash: e26fa9b22578d91636eb554c75a55f184869d529
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046212"
---
# <a name="sp_add_log_shipping_secondary_database-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
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
`[ @secondary_database = ] 'secondary_database'`Имя базы данных-получателя. Аргумент *secondary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @primary_server = ] 'primary_server'`Имя основного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов. *primary_server* имеет тип **sysname** и не может иметь значение null.  
  
`[ @primary_database = ] 'primary_database'`Имя базы данных на сервере-источнике. Аргумент *primary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @restore_delay = ] 'restore_delay'`Время в минутах, в течение которого сервер-получатель ждет перед восстановлением заданного файла резервной копии. *restore_delay* имеет **тип int** и не может иметь значение null. По умолчанию используется значение 0.  
  
`[ @restore_all = ] 'restore_all'`Если задано значение 1, сервер-получатель восстанавливает все доступные резервные копии журналов транзакций при выполнении задания восстановления. В противном случае он останавливается после восстановления одного файла. *restore_all* имеет **бит** и не может иметь значение null.  
  
`[ @restore_mode = ] 'restore_mode'`Режим восстановления для базы данных-получателя.  
  
 0 = восстановление журнала с аргументом NORECOVERY.  
  
 1 = восстановление журнала с аргументом STANDBY.  
  
 значение *RESTORE* **bit** и не может быть равно null.  
  
`[ @disconnect_users = ] 'disconnect_users'`Если задано значение 1, то при выполнении операции восстановления пользователи отключаются от базы данных-получателя. По умолчанию равно 0. *Отключение* пользователей имеет **бит** и не может иметь значение null.  
  
`[ @block_size = ] 'block_size'`Размер в байтах, используемый в качестве размера блока для устройства резервного копирования. *block_size* имеет **тип int** и значение по умолчанию-1.  
  
`[ @buffer_count = ] 'buffer_count'`Общее число буферов, используемых операцией резервного копирования или восстановления. *buffer_count* имеет **тип int** и значение по умолчанию-1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'`Размер (в байтах) максимального запроса ввода или вывода, выданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устройством резервного копирования. *max_transfersize* имеет **тип int** и может иметь значение null.  
  
`[ @restore_threshold = ] 'restore_threshold'`Количество минут между операциями восстановления до создания предупреждения. *restore_threshold* имеет **тип int** и не может иметь значение null.  
  
`[ @threshold_alert = ] 'threshold_alert'`Предупреждение, создаваемое при превышении порогового значения резервного копирования. *threshold_alert* имеет **тип int**и значение по умолчанию 14 420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'`Указывает, возникает ли предупреждение при превышении *backup_threshold* . При значении, равном единице (1), устанавливаемом по умолчанию, предупреждение будет инициировано. *threshold_alert_enabled* имеет **бит**.  
  
`[ @history_retention_period = ] 'history_retention_period'`Продолжительность времени в минутах, в течение которого сохраняется журнал. *history_retention_period* имеет **тип int**и значение по умолчанию NULL. Если ничего не указано, используется значение 14 420.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_log_shipping_secondary_database** должны запускаться из базы данных **master** на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  перед этой хранимой процедурой необходимо вызвать **sp_add_log_shipping_secondary_primary** , чтобы инициализировать основную информацию о базе данных доставки журналов на сервере-получателе.  
  
2.  Добавляет запись для базы данных-получателя в **log_shipping_secondary_databases** с помощью предоставляемых аргументов.  
  
3.  Добавляет запись локального монитора в **log_shipping_monitor_secondary** на сервере-получателе с помощью предоставляемых аргументов.  
  
4.  Если сервер мониторинга отличается от сервера-получателя, добавляет запись монитора в **log_shipping_monitor_secondary** на сервере мониторинга, используя указанные аргументы.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование хранимой процедуры **sp_add_log_shipping_secondary_database** для добавления базы данных **LogShipAdventureWorks** в качестве базы данных-получателя в конфигурации доставки журналов с базой [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] данных-источником, находящейся на сервере-источнике Трибека.  
  
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
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
