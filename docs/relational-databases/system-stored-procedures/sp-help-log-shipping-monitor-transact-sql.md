---
title: sp_help_log_shipping_monitor (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_help_log_shipping_monitor_TSQL
- sp_help_log_shipping_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor
ms.assetid: a4e96c45-6dcd-471a-a494-b5c619459855
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b8a1029c6423c90fc131ce2a5326ec69781308f6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelplogshippingmonitor-transact-sql"></a>sp_help_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор, содержащий сведения о состоянии и другие данные о зарегистрированных базах данных-источниках и базах данных-получателях на сервере-источнике, сервере-получателе или сервере мониторинга.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_log_shipping_monitor  
```  
  
## <a name="arguments"></a>Аргументы  
 Отсутствуют.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**status**|**бит**|Общее состояние агентов базы данных доставки журналов:<br /><br /> **0** = работоспособен и агента нет ошибок.<br /><br /> **1** = другое.|  
|**is_primary**|**бит**|Указывает, относится ли эта строка к базе данных-источнику:<br /><br /> **1** = строка относится к базе данных-источнике.<br /><br /> **0** = строка относится к базы данных-получателя.|  
|**server**|**sysname**|Имя сервера-источника или получателя, где находится эта база данных.|  
|**database_name**|**sysname**|Имя базы данных.|  
|**time_since_last_backup**|**int**|Время (в минутах), прошедшее с момента создания последней резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_backup_file**|**nvarchar(500)**|Имя последнего файла успешно созданной резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**backup_threshold**|**int**|Длительность времени в минутах после выполнения последнего резервного копирования перед возникновением ошибки threshold_alert. **backup_threshold** — **int**, значение по умолчанию **60 минут**.<br /><br /> NULL = данные недоступны или нерелевантны.<br /><br /> Это значение можно изменить с помощью [sp_add_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md).|  
|**is_backup_alert_enabled**|**бит**|Указывает, будет ли предупреждение возникает, когда **backup_threshold** превышено. Значение одного (**1**), устанавливаемом по умолчанию, предупреждение будет инициировано.<br /><br /> NULL = данные недоступны или нерелевантны.<br /><br /> Это значение можно изменить с помощью [sp_add_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md).|  
|**time_since_last_copy**|**int**|Время (в минутах), прошедшее с момента копирования последней резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_copied_file**|**nvarchar(500)**|Имя последнего успешно скопированного файла резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**time_since_last_restore**|**int**|Время (в минутах), прошедшее с момента восстановления последней резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_restored_file**|**nvarchar(500).**|Имя последнего успешно восстановленного файла резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_restored_latency**|**int**|Временной интервал (в минутах) от создания последней резервной копии до восстановления из резервной копии.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**restore_threshold**|**int**|Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение. **restore_threshold** не может иметь значение NULL.|  
|**is_restore_alert_enabled**|**бит**|Указывает, формируется ли предупреждение при **restore_threshold** превышено. Значение одного (**1**), устанавливаемом по умолчанию, предупреждение будет инициировано.<br /><br /> NULL = данные недоступны или нерелевантны.<br /><br /> Чтобы установить порог восстановления, используйте [sp_add_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md).|  
  
## <a name="remarks"></a>Замечания  
 **sp_help_log_shipping_monitor** должна запускаться из **master** базы данных на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
