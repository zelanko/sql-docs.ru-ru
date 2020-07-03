---
title: sp_help_log_shipping_primary_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_database_TSQL
- sp_help_log_shipping_primary_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_database
ms.assetid: e711b01c-ef29-4eb6-a016-0e647e337818
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5606c29eb4592f15eff641d969f6fcd28c89fa90
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891744"
---
# <a name="sp_help_log_shipping_primary_database-transact-sql"></a>sp_help_log_shipping_primary_database (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Получает параметры базы данных-источника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_log_shipping_primary_database  
[ @database = ] 'database' OR  
[ @primary_id = ] 'primary_id'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] 'database'`Имя базы данных-источника доставки журналов. *база данных* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
`[ @primary_id = ] 'primary_id'`Идентификатор базы данных источника для конфигурации доставки журналов. *primary_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**primary_id**|Идентификатор базы данных-источника в конфигурации доставки журналов.|  
|**primary_database**|Имя базы данных-источника в конфигурации доставки журналов.|  
|**каталог_резервной_копии**|Каталог, в котором хранятся файлы резервной копии журнала транзакций с сервера-источника.|  
|**backup_share**|Сетевой или UNC-путь к каталогу резервных копий.|  
|**backup_retention_period**|Время хранения файла резервной копии журнала в каталоге резервных копий (в минутах).|  
|**backup_compression**|Указывает, использует ли конфигурация доставки журналов [Сжатие резервных копий](../../relational-databases/backup-restore/backup-compression-sql-server.md).<br /><br /> **0** = отключено. Не сжимать резервные копии журналов.<br /><br /> **1** = включено. Всегда сжимать резервные копии журналов.<br /><br /> **2** = использовать параметр [конфигурации сервера «Просмотр» или «Настройка сжатия резервных копий по умолчанию](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)». Это значение по умолчанию.<br /><br /> Сжатие резервной копии поддерживается только в [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (или в более поздней версии). В других выпусках это значение всегда равно 2.|  
|**backup_job_id**|Идентификатор задания агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], связанный с заданием резервного копирования на сервере-источнике.|  
|**monitor_server**|Имя экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], используемого в качестве сервера мониторинга в конфигурации доставки журналов.|  
|**monitor_server_security_mode**|Режим безопасности, используемый для подключения к серверу мониторинга:<br /><br /> 1 = проверка подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.|  
|**backup_threshold**|Максимальное время ожидания (в минутах) между операциями резервного копирования перед созданием предупреждения.|  
|**threshold_alert**|Предупреждение, создаваемое при превышении порогового значения.|  
|**threshold_alert_enabled**|Определяет, включены ли пороговые предупреждения резервного копирования.<br /><br /> **1** = включено.<br /><br /> **0** = отключено.|  
|**last_backup_file**|Абсолютный путь последней резервной копии журнала транзакций.|  
|**last_backup_date**|Дата и время создания последней резервной копии журнала.|  
|**last_backup_date_utc**|Время и дата создания последней резервной копии журнала транзакций в базе данных-источнике, выраженные в формате UTC.|  
|**history_retention_period**|Промежуток времени в минутах, после которого записи истории доставки журнала данной базы данных-источника будут удалены.|  
  
## <a name="remarks"></a>Комментарии  
 **sp_help_log_shipping_primary_database** должны быть запущены из базы данных **master** на сервере источника.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование **sp_help_log_shipping_primary_database** для получения параметров базы данных источника [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
EXEC master.dbo.sp_help_log_shipping_primary_database @database=N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
