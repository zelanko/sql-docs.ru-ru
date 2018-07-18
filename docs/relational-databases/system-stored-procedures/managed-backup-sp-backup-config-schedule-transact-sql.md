---
title: managed_backup.sp_backup_config_schedule (Transact-SQL) | Документация Майкрософт
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
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8ebeca4b0a1c9079f8786303207bcbae4dfe74c3
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38035282"
---
# <a name="managedbackupspbackupconfigschedule-transact-sql"></a>managed_backup.sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Настраивает параметры автоматической или пользовательского расписания для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
    
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
  
##  <a name="Arguments"></a> Аргументы  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования на определенной базе данных. Если значение равно NULL или *, то этот управляемого резервного копирования применяется ко всем базам данных на сервере.  
  
 @scheduling_option  
 Планирование управляемой системы резервного копирования, укажите «System». Укажите «Custom» применительно к пользовательскому расписанию, определяется другие параметры.  
  
 @full_backup_freq_type  
 Тип частоты в управляемых операции резервного копирования, который можно установить значение «Daily» или «Еженедельно».  
  
 @days_of_week  
 Дни недели для резервных копий при @full_backup_freq_type задана еженедельная. Укажите имена полную строку как «Понедельник».  Можно также указать более одного имени один день, разделенные вертикальной линией. Например N'Monday | Среда | Пятница ".  
  
 @backup_begin_time  
 Время начала резервного копирования. Резервные копии не будут запущены за пределами периода времени, который определен с помощью сочетания @backup_begin_time и @backup_duration.  
  
 @backup_duration  
 Длительность окна время резервного копирования. Обратите внимание, что нет никакой гарантии, что резервные копии будут выполняться в период времени, определяемый @backup_begin_time и @backup_duration. Операции резервного копирования, которые запущены в этот период времени, но превышает длительность окна не будут отменены.  
  
 @log_backup_freq  
 Этот параметр определяет частоту резервного копирования журнала транзакций. Эти резервные копии создаются с регулярными интервалами, а не по расписанию, указанному для резервных копий базы данных. @log_backup_freq 0 — допустимым, то резервное копирование журнала не может быть в часах или минутах Отключение резервные копии журналов только подойдут и для баз данных с простой модели восстановления.  
  
> [!NOTE]  
>  При изменении модели восстановления с simple на full необходимо перенастроить log_backup_freq от 0 к ненулевое значение.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в **db_backupoperator** роли базы данных с помощью **ALTER ANY CREDENTIAL** разрешения, и **EXECUTE** разрешения на **sp_delete_ backuphistory** хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
