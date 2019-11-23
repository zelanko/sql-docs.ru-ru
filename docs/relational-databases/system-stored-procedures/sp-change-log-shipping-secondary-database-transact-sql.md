---
title: sp_change_log_shipping_secondary_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_database
- sp_change_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_database
ms.assetid: 3ebcf2f1-980f-4543-a84b-fbaeea54eeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0bd62fe3462441d4eab9d3d89bce20cf1144131
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909556"
---
# <a name="sp_change_log_shipping_secondary_database-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
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
`[ @restore_delay = ] 'restore_delay'` время в минутах, в течение которого сервер-получатель ждет перед восстановлением заданного файла резервной копии. *restore_delay* имеет **тип int** и не может иметь значение null. Значение по умолчанию — 0.  
  
`[ @restore_all = ] 'restore_all'` Если задано значение 1, сервер-получатель восстанавливает все доступные резервные копии журналов транзакций при выполнении задания восстановления. В противном случае восстанавливается один файл. *restore_all* имеет **бит** и не может иметь значение null.  
  
`[ @restore_mode = ] 'restore_mode'` режим восстановления для базы данных-получателя.  
  
 0 = восстановить журнал с аргументом NORECOVERY;  
  
 1 = восстановление журнала с аргументом STANDBY.  
  
 значение *RESTORE* **bit** и не может быть равно null.  
  
`[ @disconnect_users = ] 'disconnect_users'` Если задано значение 1, пользователи отключаются от базы данных-получателя при выполнении операции восстановления. По умолчанию равно 0. *disconnect_users* имеет **бит** и не может иметь значение null.  
  
`[ @block_size = ] 'block_size'` размер (в байтах), используемый в качестве размера блока для устройства резервного копирования. *block_size* имеет **тип int** и значение по умолчанию-1.  
  
`[ @buffer_count = ] 'buffer_count'` общее количество буферов, используемых операцией резервного копирования или восстановления. *buffer_count* имеет **тип int** и значение по умолчанию-1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` размер (в байтах) максимального запроса ввода или вывода, выданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на устройство резервного копирования. *max_transfersize* имеет **тип int** и может иметь значение null.  
  
`[ @restore_threshold = ] 'restore_threshold'` число минут между операциями восстановления до создания предупреждения. *restore_threshold* имеет **тип int** и не может иметь значение null.  
  
`[ @threshold_alert = ] 'threshold_alert'` — это предупреждение, которое будет выводиться при превышении порогового значения восстановления. *threshold_alert* имеет **тип int**и значение по умолчанию 14420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` указывает, будет ли создаваться предупреждение при превышении *restore_threshold*. 1 = включены; 0 = отключены. *threshold_alert_enabled* имеет **бит** и не может иметь значение null.  
  
`[ @history_retention_period = ] 'history_retention_period'` — это период времени в минутах, в течение которого будет храниться журнал. *history_retention_period* имеет **тип int**. Если не указано, будет использоваться значение 1440.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Remarks  
 **sp_change_log_shipping_secondary_database** должны запускаться из базы данных **master** на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  При необходимости изменяет параметры в записях **log_shipping_secondary_database** .  
  
2.  При необходимости изменяет запись локального монитора в **log_shipping_monitor_secondary** на сервере-получателе, используя указанные аргументы.  

## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование **sp_change_log_shipping_secondary_database** для обновления параметров базы данных-получателя **LogShipAdventureWorks**.  
  
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
  
## <a name="see-also"></a>См. также статью  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
