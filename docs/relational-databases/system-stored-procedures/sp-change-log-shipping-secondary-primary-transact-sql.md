---
title: sp_change_log_shipping_secondary_primary (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_primary
- sp_change_log_shipping_secondary_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_primary
ms.assetid: 5bcb4df7-6df3-4f2b-9207-b97b5addf2a6
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 499c95fc980bd6e8d996b14c47907b814cbb94aa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240004"
---
# <a name="spchangelogshippingsecondaryprimary-transact-sql"></a>sp_change_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Меняет настройки базы данных-получателя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_log_shipping_secondary_primary  
[ @primary_server = ] 'primary_server',  
[ @primary_database = ] 'primary_database',  
[, [ @backup_source_directory = ] 'backup_source_directory']  
[, [ @backup_destination_directory = ] 'backup_destination_directory']  
[, [ @file_retention_period = ] file_retention_period]  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@primary_server** =] '*primary_server*"  
 Имя первичного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов. *primary_server* — **sysname** и не может иметь значение NULL.  
  
 [ **@primary_database** =] '*primary_database*"  
 Имя базы данных на сервере-источнике. *primary_database* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@backup_source_directory** =] '*backup_source_directory*"  
 Каталог, в котором хранятся файлы резервной копии журнала транзакций с сервера-источника. *backup_source_directory* — **nvarchar(500)** и не может иметь значение NULL.  
  
 [ **@backup_destination_directory** =] '*backup_destination_directory*"  
 Каталог сервера-получателя, в который копируются файлы резервных копий. *backup_destination_directory* — **nvarchar(500)** и не может иметь значение NULL.  
  
 [ **@file_retention_period** =] '*file_retention_period*"  
 Отрезок времени в минутах, в течение которого сохраняются данные журнала. *history_retention_period* — **int**, значение по умолчанию NULL. Если ничего не указано, подразумевается значение 14420.  
  
 [ **@monitor_server_security_mode** =] '*monitor_server_security_mode*"  
 Режим безопасности, используемый для подключения к серверу мониторинга:  
  
 1 = проверка подлинности Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. *monitor_server_security_mode* — **бит** и не может иметь значение NULL.  
  
 [ **@monitor_server_login** =] '*monitor_server_login*"  
 Имя учетной записи, используемой для доступа к серверу мониторинга.  
  
 [ **@monitor_server_password** =] '*monitor_server_password*"  
 Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_change_log_shipping_secondary_primary** должна запускаться из **master** базы данных на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  Изменяет параметры **log_shipping_secondary** записывает при необходимости.  
  
2.  Если сервер мониторинга отличается от сервера-получателя, изменяет контрольную запись **log_shipping_monitor_secondary** мониторинга сервера, используя указанные аргументы при необходимости.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
