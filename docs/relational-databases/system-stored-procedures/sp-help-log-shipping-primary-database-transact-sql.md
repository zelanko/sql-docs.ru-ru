---
title: sp_help_log_shipping_primary_database (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_database_TSQL
- sp_help_log_shipping_primary_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_database
ms.assetid: e711b01c-ef29-4eb6-a016-0e647e337818
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56f3955c179e73d30172f0ed2126a600b1c1771a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sphelplogshippingprimarydatabase-transact-sql"></a>sp_help_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Получает параметры базы данных-источника.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_log_shipping_primary_database  
[ @database = ] 'database' OR  
[ @primary_id = ] 'primary_id'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@database =** ] "*базы данных*"  
 Имя базы данных-источника для доставки журналов. *База данных* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 [  **@primary_id =** ] "*primary_id*"  
 Идентификатор базы данных-источника в конфигурации доставки журналов. *primary_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
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
|**backup_compression**|Указывает, использует ли конфигурация доставки журналов [сжатие резервных копий](../../relational-databases/backup-restore/backup-compression-sql-server.md).<br /><br /> **0** = отключено. Не сжимать резервные копии журналов.<br /><br /> **1** = включен. Всегда сжимать резервные копии журналов.<br /><br /> **2** = использовать значение параметра [Просмотр или настройка параметра конфигурации сервера по умолчанию сжатие резервных копий](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Это значение по умолчанию.<br /><br /> Сжатие резервной копии поддерживается только в [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (или в более поздней версии). В других выпусках это значение всегда равно 2.|  
|**backup_job_id**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Идентификатор задания агента, связанный с заданием резервного копирования на сервере-источнике.|  
|**monitor_server**|Имя экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], используемого в качестве сервера мониторинга в конфигурации доставки журналов.|  
|**monitor_server_security_mode**|Режим безопасности, используемый для подключения к серверу мониторинга:<br /><br /> 1 = проверка подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.|  
|**backup_threshold**|Максимальное время ожидания (в минутах) между операциями резервного копирования перед созданием предупреждения.|  
|**threshold_alert**|Предупреждение, создаваемое при превышении порогового значения.|  
|**threshold_alert_enabled**|Определяет, включены ли пороговые предупреждения резервного копирования.<br /><br /> **1** = включен.<br /><br /> **0** = отключено.|  
|**last_backup_file**|Абсолютный путь последней резервной копии журнала транзакций.|  
|**last_backup_date**|Дата и время создания последней резервной копии журнала.|  
|**last_backup_date_utc**|Время и дата создания последней резервной копии журнала транзакций в базе данных-источнике, выраженные в формате UTC.|  
|**history_retention_period**|Промежуток времени в минутах, после которого записи истории доставки журнала данной базы данных-источника будут удалены.|  
  
## <a name="remarks"></a>Замечания  
 **sp_help_log_shipping_primary_database** должна запускаться из **master** базы данных на сервере-источнике.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 Этот пример иллюстрирует использование **sp_help_log_shipping_primary_database** для получения параметров базы данных-источника для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC master.dbo.sp_help_log_shipping_primary_database @database=N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
