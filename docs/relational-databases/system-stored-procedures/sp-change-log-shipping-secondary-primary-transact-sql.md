---
title: sp_change_log_shipping_secondary_primary (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_primary
- sp_change_log_shipping_secondary_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_primary
ms.assetid: 5bcb4df7-6df3-4f2b-9207-b97b5addf2a6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 757d842dfe0521bd8195bf85e02a3ed0eee2b5b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68045802"
---
# <a name="sp_change_log_shipping_secondary_primary-transact-sql"></a>sp_change_log_shipping_secondary_primary (Transact-SQL)
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
`[ @primary_server = ] 'primary_server'`Имя основного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов. *primary_server* имеет тип **sysname** и не может иметь значение null.  
  
`[ @primary_database = ] 'primary_database'`Имя базы данных на сервере-источнике. Аргумент *primary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @backup_source_directory = ] 'backup_source_directory'`Каталог, в котором хранятся файлы резервных копий журналов транзакций с сервера источника. *backup_source_directory* имеет тип **nvarchar (500)** и не может иметь значение null.  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'`Каталог на сервере-получателе, куда копируются файлы резервных копий. *backup_destination_directory* имеет тип **nvarchar (500)** и не может иметь значение null.  
  
`[ @file_retention_period = ] 'file_retention_period'`Продолжительность времени в минутах, в течение которого будет храниться журнал. *history_retention_period* имеет **тип int**и значение по умолчанию NULL. Если ничего не указано, подразумевается значение 14420.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'`Режим безопасности, используемый для подключения к серверу мониторинга.  
  
 1 = проверка подлинности Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности. *monitor_server_security_mode* имеет **бит** и не может иметь значение null.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Имя пользователя учетной записи, используемой для доступа к серверу мониторинга.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Пароль учетной записи, используемой для доступа к серверу мониторинга.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_change_log_shipping_secondary_primary** должны запускаться из базы данных **master** на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  При необходимости изменяет параметры в записях **log_shipping_secondary** .  
  
2.  Если сервер мониторинга отличается от сервера-получателя, при необходимости изменяет запись монитора в **log_shipping_monitor_secondary** на сервере мониторинга, используя указанные аргументы.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
