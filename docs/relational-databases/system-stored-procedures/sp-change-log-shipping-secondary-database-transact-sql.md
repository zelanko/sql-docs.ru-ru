---
title: sp_change_log_shipping_secondary_database (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_database
- sp_change_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_database
ms.assetid: 3ebcf2f1-980f-4543-a84b-fbaeea54eeac
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0edae5ffcd82e45c348cb382788e5ca6718419ce
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spchangelogshippingsecondarydatabase-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Меняет настройки базы данных-получателя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
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
 [ **@restore_delay =** ] '*restore_delay*'  
 Время ожидания (в минутах), по истечении которого сервер-получатель восстанавливает данный файл резервной копии. *restore_delay* — **int** и не может иметь значение NULL. Значение по умолчанию — 0.  
  
 [  **@restore_all =** ] "*restore_all*"  
 Если значение этого аргумента равно 1, сервер-получатель восстанавливает все доступные резервные копии журналов транзакций при выполнении задания восстановления. В противном случае восстанавливается один файл. *restore_all* — **бит** и не может иметь значение NULL.  
  
 [  **@restore_mode =** ] "*restore_mode*"  
 Режим восстановления базы данных-получателя.  
  
 0 = восстановить журнал с аргументом NORECOVERY;  
  
 1 = восстановление журнала с аргументом STANDBY.  
  
 *восстановление* — **бит** и не может иметь значение NULL.  
  
 [  **@disconnect_users =** ] "*disconnect_users*"  
 Если аргумент имеет значение 1, пользователи отключаются от базы данных-получателя при выполнении операции восстановления. По умолчанию равно 0. *disconnect_users* — **бит** и не может иметь значение NULL.  
  
 [  **@block_size =** ] "*block_size*"  
 Размер блока (в байтах) устройства резервного копирования. *block_size* — **int** со значением по умолчанию-1.  
  
 [  **@buffer_count =** ] "*buffer_count*"  
 Общее число буферов, используемых операцией создания резервной копии или восстановления. *buffer_count* — **int** со значением по умолчанию-1.  
  
 [  **@max_transfer_size =** ] "*max_transfer_size*"  
 Размер (в байтах) максимального входного или выходного запроса, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдает на устройство резервного копирования. *max_transfersize* — **int** и может иметь значение NULL.  
  
 [  **@restore_threshold =** ] "*restore_threshold*"  
 Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение. *restore_threshold* — **int** и не может иметь значение NULL.  
  
 [  **@threshold_alert =** ] "*threshold_alert*"  
 Предупреждение, создаваемое при истечении порогового срока восстановления. *threshold_alert* — **int**, значение по умолчанию 14 420.  
  
 [  **@threshold_alert_enabled =** ] "*threshold_alert_enabled*"  
 Указывает, будет ли предупреждение возникает, когда *restore_threshold*превышено. 1 = включены; 0 = отключены. *threshold_alert_enabled* — **бит** и не может иметь значение NULL.  
  
 [  **@history_retention_period =** ] "*history_retention_period*"  
 Отрезок времени в минутах, в течение которого сохраняются данные журнала. *history_retention_period* — **int**. Если значение не указано, будет использоваться значение 1440.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_change_log_shipping_secondary_database** должна запускаться из **master** базы данных на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  Изменяет параметры в **log_shipping_secondary_database** записывает при необходимости.  
  
2.  Изменяет запись локального монитора в **log_shipping_monitor_secondary** на сервере-получателе, используя указанные аргументы при необходимости.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 Этот пример иллюстрирует использование **sp_change_log_shipping_secondary_database** обновление параметров базы данных-получателя для базы данных **LogShipAdventureWorks**.  
  
```  
EXEC master.dbo.sp_change_log_shipping_secondary_database   
 @secondary_database =  'LogShipAdventureWorks'  
,  @restore_delay = 0  
,  @restore_all = 1  
,  @restore_mode = 0  
,  @disconnect_users = 0  
,  @threshold_alert = 14420  
,  @threshold_alert_enabled = 1  
,  @history_retention_period = 14420;  
```  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
