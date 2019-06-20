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
manager: craigg
ms.openlocfilehash: 136771c5bf691155b4547963fa2b6bd035f3f039
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62994233"
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
`[ @restore_delay = ] 'restore_delay'` Количество времени, в минутах, которое сервер-получатель ожидает перед восстановлением данного файла резервной копии. *restore_delay* — **int** и не может иметь значение NULL. Значение по умолчанию — 0.  
  
`[ @restore_all = ] 'restore_all'` Если задано значение 1, сервер-получатель восстанавливает все доступные резервные копии журналов, при выполнении задания восстановления. В противном случае восстанавливается один файл. *restore_all* — **бит** и не может иметь значение NULL.  
  
`[ @restore_mode = ] 'restore_mode'` Режим восстановления базы данных-получателя.  
  
 0 = восстановить журнал с аргументом NORECOVERY;  
  
 1 = восстановление журнала с аргументом STANDBY.  
  
 *восстановление* — **бит** и не может иметь значение NULL.  
  
`[ @disconnect_users = ] 'disconnect_users'` Если задано значение 1, пользователи не подключен к базе данных-получателе, при выполнении операции восстановления. По умолчанию равно 0. *disconnect_users* — **бит** и не может иметь значение NULL.  
  
`[ @block_size = ] 'block_size'` Размер в байтах, используемый в качестве размера блока для устройства резервного копирования. *block_size* — **int** со значением по умолчанию-1.  
  
`[ @buffer_count = ] 'buffer_count'` Общее число буферов, используемых при операции резервного копирования или восстановления. *buffer_count* — **int** со значением по умолчанию-1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` Размер в байтах максимального входного или выходного запроса, который выдает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на устройство резервного копирования. *max_transfersize* — **int** и может иметь значение NULL.  
  
`[ @restore_threshold = ] 'restore_threshold'` Количество минут, может пройти между операциями восстановления до формирования предупреждения. *restore_threshold* — **int** и не может иметь значение NULL.  
  
`[ @threshold_alert = ] 'threshold_alert'` Это предупреждение, создаваемое при истечении порогового срока восстановления. *threshold_alert* — **int**, значение по умолчанию 14 420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` Указывает, будет ли предупреждение возникает, когда *restore_threshold*превышено. 1 = включены; 0 = отключены. *threshold_alert_enabled* — **бит** и не может иметь значение NULL.  
  
`[ @history_retention_period = ] 'history_retention_period'` — Это продолжительность времени в минутах, в которых сохраняются данные журнала. *history_retention_period* — **int**. Если ничего не указано, используется значение 1440.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sp_change_log_shipping_secondary_database** должна запускаться из **master** базы данных на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  Изменяет параметры в **log_shipping_secondary_database** записывает при необходимости.  
  
2.  Изменяет запись локального монитора в **log_shipping_monitor_secondary** на сервере-получателе, используя указанные аргументы, при необходимости.  
  
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
 [О доставке журналов &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
