---
title: managed_backup. sp_backup_config_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/20/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7bb477901dee22c70bb47cd0eaf7da5eb163b7f
ms.sourcegitcommit: 87b932dc4b603a35a19f16e2c681b6a8d4df1fec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77507541"
---
# <a name="managed_backupsp_backup_config_schedule-transact-sql"></a>managed_backup. sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Настраивает автоматические или настраиваемые параметры планирования для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'
    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="Arguments"></a>Даваемых  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования в определенной базе данных. Если задано значение NULL или *, то эта управляемая резервная копия применяется ко всем базам данных на сервере.  
  
 @scheduling_option  
 Укажите "System" для планирования резервного копирования, контролируемого системой. Укажите "Custom" для настраиваемого расписания, определенного другим паратметерс.  
  
 @full_backup_freq_type  
 Тип частоты для управляемой операции резервного копирования, для которой можно задать значение "ежедневно" или "еженедельно".  
  
 @days_of_week  
 Дни недели для резервных копий, если @full_backup_freq_type задано значение еженедельно. Укажите полные имена строк, например "понедельник".  Можно также указать более одного названия дня, разделенных вертикальной чертой. Например, Н'мондай | Среда | Пятница ".  
  
 @backup_begin_time  
 Время начала периода резервного копирования. Резервные копии не будут запущены за пределами временного окна, которое определяется сочетанием @backup_begin_time и @backup_duration.  
  
 @backup_duration  
 Длительность периода резервного копирования. Обратите внимание на то, что резервные копии не будут завершены в течение временного @backup_begin_time окна @backup_duration, определенного в и. Операции резервного копирования, запущенные в этом временном окне, но превышающие длительность окна, не будут отменены.  
  
 @log_backup_freq  
 Это определяет частоту резервного копирования журналов транзакций. Эти резервные копии выполняются через регулярные интервалы, а не по расписанию, заданному для резервных копий базы данных. @log_backup_freqможет быть в минутах или часах и `0:00` является допустимым, что означает отсутствие резервных копий журнала. Отключение резервных копий журналов будет уместно только для баз данных с простой моделью восстановления.  
  
> [!NOTE]  
>  Если модель восстановления изменяется с Simple на Full, необходимо перенастроить log_backup_freq с `0:00` ненулевым значением.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных **db_backupoperator** , с разрешениями **ALTER ANY CREDENTIAL** и **EXECUTE** для хранимой процедуры **sp_delete_backuphistory** .  
  
## <a name="see-also"></a>См. также:  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup. sp_backup_config_advanced &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
