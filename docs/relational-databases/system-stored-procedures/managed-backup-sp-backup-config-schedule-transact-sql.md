---
title: "managed_backup.sp_backup_config_schedule (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs: TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6b681a47cb0a67b6c77649b18c05cd024cf3a67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="managedbackupspbackupconfigschedule-transact-sql"></a>managed_backup.sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Настройка автоматической или пользовательские параметры планирования для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования в определенной базе данных. Если значение равно NULL или *, то это управляемое резервное копирование относится ко всем базам данных на сервере.  
  
 @scheduling_option  
 Для планирования резервного копирования с контролем системы, укажите «Система». Укажите «Custom» в настраиваемом расписании определяется другие параметры.  
  
 @full_backup_freq_type  
 Тип частоты для управляемых операции резервного копирования, который можно присвоить значение «Ежедневно» или «Еженедельно».  
  
 @days_of_week  
 Дни недели для резервных копий при @full_backup_freq_type задана еженедельная. Укажите имена полную строку как «Понедельник».  Можно также указать более чем один день недели, разделенных запятыми. Например «Понедельник, среда, пятница».  
  
 @backup_begin_time  
 Время начала резервного копирования. Резервное копирование не будет запущен за пределами периода времени, которая определяется сочетанием @backup_begin_time и @backup_duration.  
  
 @backup_duration  
 Продолжительность периода времени создания резервной копии. Обратите внимание, что нет никакой гарантии, что резервное копирование будет завершено в период времени, определяемый @backup_begin_time и @backup_duration. Операции резервного копирования, которые запущены в этот период времени, но превышает длительность окна не будут отменены.  
  
 @log_backup_freq  
 Определяет частоту резервных копий журнала транзакций. Эти резервные копии происходит через регулярные интервалы, а не по расписанию, указанный для архивации базы данных. @log_backup_freq0 — допустимым, указывающая, резервное копирование журнала не может быть в часах и минутах Отключение резервные копии журналов только приемлемо для баз данных с простой модели восстановления.  
  
> [!NOTE]  
>  При изменении модели восстановления с простой на полную, необходимо перенастроить log_backup_freq от 0 к ненулевое значение.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуется членство в **db_backupoperator** роли базы данных с **ALTER ANY CREDENTIAL** разрешения, и **EXECUTE** разрешения на **sp_delete_ backuphistory** хранимой процедуры.  
  
## <a name="see-also"></a>См. также:  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
