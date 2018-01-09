---
title: "sys.dm_db_log_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_log_stats_TSQL
- sys.dm_db_log_stats
- sys.dm_db_log_stats_TSQL
- dm_db_log_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_stats dynamic management function
ms.assetid: 
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa7b169b3ff6887616346a8324854ab10aceab07
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sysdmdblogstats-transact-sql"></a>sys.dm_db_log_stats (Transact-SQL)   
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает сводные атрибутов на уровне и сведения в файлы журнала транзакций базы данных. Эти сведения можно используйте для наблюдения и диагностики работоспособности журнала транзакций.   
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 sys.dm_db_log_stats ( database_id )
```  
  
## <a name="arguments"></a>Аргументы  

*database_id* | ЗНАЧЕНИЕ NULL | **По умолчанию**

Идентификатор базы данных. Параметр `database_id` равен `int`. Допустимыми входными значениями являются идентификатор базы данных, `NULL`, или `DEFAULT`. Значение по умолчанию — `NULL`. `NULL`и `DEFAULT` эквивалент значения в контексте текущей базы данных.  
Встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md) можно указать. При использовании `DB_ID` без указания имени базы данных, уровень совместимости текущей базы данных должен быть равен 90 или выше.

  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|database_id    |**int**    |Идентификатор базы данных |  
|recovery_model |**nvarchar(60)**   |   Модель восстановления базы данных. Возможные значения. <br /> SIMPLE<br /> BULK_LOGGED <br /> ПОЛНОЕ |  
|log_min_lsn    |**nvarchar(24)**   |   Текущее начало [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) в журнале транзакций.|  
|log_end_lsn    |**nvarchar(24)**   |   [Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) последней записи журнала в журнале транзакций.|  
|current_vlf_sequence_number    |**bigint** |   Текущий [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) порядковый номер во время выполнения.|  
|current_vlf_size_mb    |**float**  |   Текущий [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) размер в МБ.|   
|total_vlf_count    |**bigint** |   Общее число [виртуальных файлов журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) в журнале транзакций. |  
|total_log_size_mb  |**float**  |   Полном размере журнала транзакций в МБ. |  
|active_vlf_count   |**bigint** |   Общее число активных [виртуальных файлов журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) в журнале транзакций.|  
|active_log_size_mb |**float**  |   Размер журнала общее активной транзакции в МБ.|  
|log_truncation_holdup_reason   |**nvarchar(60)**   |   Причина задержки усечения журнала. Значение совпадает с `log_reuse_wait_desc` столбец `sys.databases`.  (Более подробные объяснения этих значений см. в разделе [резервная копия журнала транзакций](../../relational-databases/logs/the-transaction-log-sql-server.md)). <br />Возможные значения. <br />NOTHING;<br />CHECKPOINT<br />LOG_BACKUP<br />ACTIVE_BACKUP_OR_RESTORE<br />ACTIVE_TRANSACTION<br />DATABASE_MIRRORING<br />REPLICATION<br />DATABASE_SNAPSHOT_CREATION<br />LOG_SCAN<br />AVAILABILITY_REPLICA<br />OLDEST_PAGE<br />XTP_CHECKPOINT<br />ДРУГИЕ ВРЕМЕННОЙ |  
|log_backup_time    |**datetime**   |   Транзакции журналов время последнего резервного копирования.|   
|log_backup_lsn |**nvarchar(24)**   |   Последней резервной копии журнала транзакций [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|   
|log_since_last_log_backup_mb   |**float**  |   Размер журнала в МБ с момента последней резервной копии журнала транзакций [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_checkpoint_lsn |**nvarchar(24)**   |   Последней контрольной точки [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_since_last_checkpoint_mb   |**float**  |   Размер журнала в МБ с момента последней контрольной точки [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_recovery_lsn   |**nvarchar(24)**   |   Восстановление [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) базы данных. Если `log_recovery_lsn` происходит до номера LSN, контрольной точки `log_recovery_lsn` является самой старой активной транзакции номер LSN, в противном случае `log_recovery_lsn` является номер LSN контрольной точки.|  
|log_recovery_size_mb   |**float**  |   Размер журнала в МБ с момента восстановления журнала [регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|recovery_vlf_count |**bigint** |   Общее число [виртуальных файлов журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) должен быть восстановлен, если произошла отработка отказа или перезапуска сервера. |  


## <a name="permissions"></a>Разрешения  
Требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="examples"></a>Примеры  

### <a name="a-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-high-number-of-vlfs"></a>A. Определение баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр с большим количеством VLF   
Следующий запрос возвращает базы данных с более чем 100 VLF в файлах журнала. Большое число VLF может влиять на время запуска, восстановления и восстановления базы данных.

```sql  
SELECT name AS 'Database Name', total_vlf_count AS 'VLF count' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id) 
WHERE total_vlf_count  > 100;
```   

### <a name="b-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-transaction-log-backups-older-than-4-hours"></a>Б. Определение баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр с более ранней, чем 4 часов резервные копии журналов транзакций   
Следующий запрос определяет последний раз резервного копирования журнала для баз данных в экземпляре.

```sql  
SELECT name AS 'Database Name', log_backup_time AS 'last log backup time' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id); 
```

## <a name="see-also"></a>См. также:  
[Динамические административные представления и функции (Transact-SQL)](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
  
