---
title: "sp_add_log_shipping_secondary_primary (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_primary_TSQL
- sp_add_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_primary
ms.assetid: bfbbbee2-c255-4a59-a963-47d6e980a8e2
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c83d0a0062f7f7affc19e91b929bb16831a8946d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spaddlogshippingsecondaryprimary-transact-sql"></a>sp_add_log_shipping_secondary_primary (Transact-SQL)
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
 [ **@primary_server** = ] '*primary_server*'  
 Имя первичного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов. *primary_server* — **sysname** и не может иметь значение NULL.  
  
 [  **@primary_database**  =] '*primary_database*"  
 Имя базы данных на сервере-источнике. *primary_database* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@backup_source_directory** = ] '*backup_source_directory*'  
 Каталог, в котором хранятся файлы резервной копии журнала транзакций с сервера-источника. *backup_source_directory* — **nvarchar(500)** и не может иметь значение NULL.  
  
 [ **@backup_destination_directory** = ] '*backup_destination_directory*'  
 Каталог сервера-получателя, в который копируются файлы резервных копий. *backup_destination_directory* — **nvarchar(500)** и не может иметь значение NULL.  
  
 [ **@copy_job_name** = ] '*copy_job_name*'  
 Имя создаваемого задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для копирования резервных копий журналов транзакций на сервер-получатель. *copy_job_name* — **sysname** и не может иметь значение NULL.  
  
 [ **@restore_job_name** = ] '*restore_job_name*'  
 Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента на сервере-получателе, которое восстанавливает резервные копии баз данных-получателей. *restore_job_name* — **sysname** и не может иметь значение NULL.  
  
 [ **@file_retention_period** = ] '*file_retention_period*'  
 Время в минутах, в которых файл резервной копии хранится на сервере-получателе в каталоге, указанном @backup_destination_directory параметров перед их удалением. *history_retention_period* — **int**, значение по умолчанию NULL. Если ничего не указано, подразумевается значение 14420.  
  
 [ **@monitor_server** = ] '*monitor_server*'  
 Имя сервера мониторинга. *Monitor_server* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 [ **@monitor_server_security_mode** = ] '*monitor_server_security_mode*'  
 Режим безопасности, используемый для подключения к серверу мониторинга:  
  
 1 = проверка подлинности Windows.  
  
 0 = проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *monitor_server_security_mode* — **бит** и не может иметь значение NULL.  
  
 [ **@monitor_server_login** = ] '*monitor_server_login*'  
 Имя учетной записи, используемой для доступа к серверу мониторинга.  
  
 [ **@monitor_server_password** = ] '*monitor_server_password*'  
 Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
 [ **@copy_job_id** = ] '*copy_job_id*' OUTPUT  
 Идентификатор, назначенный заданию копирования на сервере-получателе. *copy_job_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
 [ **@restore_job_id** = ] '*restore_job_id*' OUTPUT  
 Идентификатор, назначенный заданию восстановления на сервере-получателе. *restore_job_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
 [  **@secondary_id**  =] '*secondary_id*"выходные данные  
 Идентификатор сервера-получателя в конфигурации доставки журналов. *secondary_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Remarks  
 **sp_add_log_shipping_secondary_primary** должна запускаться из **master** базы данных на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  Формирует идентификатор получателя для указанного сервера-источника и базы данных-источника.  
  
2.  Выполняет следующее:  
  
    1.  Добавляет запись для идентификатора получателя в **log_shipping_secondary** с указанными аргументами.  
  
    2.  создает отключенное задание копирования для идентификатора получателя;  
  
    3.  Задает идентификатор задания копирования в **log_shipping_secondary** входа идентификатору задания копирования.  
  
    4.  создает отключенное задание восстановления для идентификатора получателя;  
  
    5.  Задать идентификатор задания восстановления в **log_shipping_secondary** входа идентификатору задания восстановления.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 Этот пример иллюстрирует использование **sp_add_log_shipping_secondary_primary** хранимую процедуру, чтобы настроить данные для базы данных-источника [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на сервере-получателе.  
  
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
  
## <a name="see-also"></a>См. также  
 [О доставке журналов &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
