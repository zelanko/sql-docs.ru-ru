---
title: sp_help_log_shipping_monitor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_TSQL
- sp_help_log_shipping_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor
ms.assetid: a4e96c45-6dcd-471a-a494-b5c619459855
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2b8fc2ac96821427aaf0ef2550fb6624a923d7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68000930"
---
# <a name="sp_help_log_shipping_monitor-transact-sql"></a>sp_help_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор, содержащий сведения о состоянии и другие данные о зарегистрированных базах данных-источниках и базах данных-получателях на сервере-источнике, сервере-получателе или сервере мониторинга.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_log_shipping_monitor  
```  
  
## <a name="arguments"></a>Аргументы  
 Нет.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**состояние**|**bit**|Общее состояние агентов базы данных доставки журналов:<br /><br /> **0** = работоспособное состояние и сбои без агента.<br /><br /> **1** = в противном случае.|  
|**is_primary**|**bit**|Указывает, относится ли эта строка к базе данных-источнику:<br /><br /> **1** = строка предназначена для базы данных-источника.<br /><br /> **0** = строка предназначена для базы данных-получателя.|  
|**сервером**|**имеет sysname**|Имя сервера-источника или получателя, где находится эта база данных.|  
|**database_name**|**имеет sysname**|Имя базы данных.|  
|**time_since_last_backup**|**int**|Время (в минутах), прошедшее с момента создания последней резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_backup_file**|**nvarchar (500)**|Имя последнего файла успешно созданной резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**backup_threshold**|**int**|Длительность времени в минутах после выполнения последнего резервного копирования перед возникновением ошибки threshold_alert. **backup_threshold** имеет **тип int**и значение по умолчанию **60 минут**.<br /><br /> NULL = данные недоступны или нерелевантны.<br /><br /> Это значение можно изменить с помощью [sp_add_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md).|  
|**is_backup_alert_enabled**|**bit**|Указывает, будет ли создаваться предупреждение при превышении **backup_threshold** . Значение по умолчанию (**1**) означает, что предупреждение будет создано.<br /><br /> NULL = данные недоступны или нерелевантны.<br /><br /> Это значение можно изменить с помощью [sp_add_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md).|  
|**time_since_last_copy**|**int**|Время (в минутах), прошедшее с момента копирования последней резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_copied_file**|**nvarchar (500)**|Имя последнего успешно скопированного файла резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**time_since_last_restore**|**int**|Время (в минутах), прошедшее с момента восстановления последней резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_restored_file**|**nvarchar (500).**|Имя последнего успешно восстановленного файла резервной копии журнала.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**last_restored_latency**|**int**|Временной интервал (в минутах) от создания последней резервной копии до восстановления из резервной копии.<br /><br /> NULL = данные недоступны или нерелевантны.|  
|**restore_threshold**|**int**|Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение. **restore_threshold** не может иметь значение null.|  
|**is_restore_alert_enabled**|**bit**|Указывает, возникает ли предупреждение при превышении **restore_threshold** . Значение по умолчанию (**1**) означает, что создается предупреждение.<br /><br /> NULL = данные недоступны или нерелевантны.<br /><br /> Чтобы задать пороговое значение восстановления, используйте [sp_add_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md).|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_log_shipping_monitor** должны быть запущены из базы данных **master** на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
