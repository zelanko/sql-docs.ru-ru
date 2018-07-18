---
title: sys.dm_db_log_info (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: 4
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e2b99ce1a417c31b4ca81eb9f538acda0edfc517
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34464660"
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Возвращает [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) сведения журнала транзакций. Обратите внимание, что все файлы журнала транзакций, объединяются в выходной таблице. Каждая строка в выходных данных представляет VLF в журнале транзакций и предоставляет сведения, относящиеся к этой виртуального файла Журнала в журнале.

## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_log_info ( database_id )  
``` 

## <a name="arguments"></a>Аргументы  
 *database_id* | ЗНАЧЕНИЕ NULL | ПО УМОЛЧАНИЮ  
 Идентификатор базы данных. Аргумент *database_id* имеет тип **int**. Допустимыми входными значениями являются идентификатор базы данных, NULL или по умолчанию. Значение по умолчанию — NULL. Значение NULL по умолчанию значения и эквивалентны в контексте текущей базы данных.
 
 Укажите значение NULL для возврата сведений о VLF текущей базы данных.

 Встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md) можно указать. При использовании `DB_ID` без указания имени базы данных, уровень совместимости текущей базы данных должен быть равен 90 или выше.  

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|
|file_id|**smallint**|Идентификатор файла журнала транзакций.|  
|vlf_begin_offset|**bigint** |Смещение расположения [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) от начала файла журнала транзакций.|
|vlf_size_mb |**float** |[виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) размер в МБ, округляется до 2 десятичных разряда.|     
|vlf_sequence_number|**bigint** |[виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) порядковый номер в созданного заказа. Используется для уникальной идентификации VLF в файле журнала.|
|vlf_active|**бит** |Указывает, является ли [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) уже используется или не. <br />0 — виртуального файла Журнала не используется.<br />1 — VLF активен.|
|vlf_status|**int** |Состояние [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Возможные значения: <br />0 — неактивные VLF <br />1 — VLF инициализирована, но неиспользуемого <br /> 2 - VLF активен.|
|vlf_parity|**tinyint** |Четность [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Используется внутренним образом для определения конца журнала в пределах виртуального файла Журнала.|
|vlf_first_lsn|**nvarchar(48)** |[Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) первой записи журнала в [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar(48)** |[Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) записи журнала, созданные [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|

## <a name="remarks"></a>Примечания
`sys.dm_db_log_info` Заменяет функцию динамического управления `DBCC LOGINFO` инструкции.    
 
## <a name="permissions"></a>Разрешения  
Требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Определение баз данных в экземпляре SQL Server с большим количеством VLF
Следующий запрос определяет базы данных с более чем 100 VLF в файлы журналов, которые могут повлиять на время запуска, восстановления и восстановления базы данных.

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-position-of-the-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>Б. Определение позиции последней `VLF` в журнале транзакций до при сжатии файла журнала

Следующий запрос используется для определения позиции из последнего активного виртуального файла Журнала перед выполнением процедуры SHRINKFILE модуля на журнал транзакций, чтобы определить, если журнал транзакций можно сжать.

```sql
USE AdventureWorks2016
GO

;WITH cte_vlf AS (
SELECT ROW_NUMBER() OVER(ORDER BY vlf_begin_offset) AS vlfid, DB_NAME(database_id) AS [Database Name], vlf_sequence_number, vlf_active, vlf_begin_offset, vlf_size_mb
    FROM sys.dm_db_log_info(DEFAULT)),
cte_vlf_cnt AS (SELECT [Database Name], COUNT(vlf_sequence_number) AS vlf_count,
    (SELECT COUNT(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 0) AS vlf_count_inactive,
    (SELECT COUNT(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS vlf_count_active,
    (SELECT MIN(vlfid) FROM cte_vlf WHERE vlf_active = 1) AS ordinal_min_vlf_active,
    (SELECT MIN(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS min_vlf_active,
    (SELECT MAX(vlfid) FROM cte_vlf WHERE vlf_active = 1) AS ordinal_max_vlf_active,
    (SELECT MAX(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS max_vlf_active
    FROM cte_vlf
    GROUP BY [Database Name])
SELECT [Database Name], vlf_count, min_vlf_active, ordinal_min_vlf_active, max_vlf_active, ordinal_max_vlf_active,
((ordinal_min_vlf_active-1)*100.00/vlf_count) AS free_log_pct_before_active_log,
((ordinal_max_vlf_active-(ordinal_min_vlf_active-1))*100.00/vlf_count) AS active_log_pct,
((vlf_count-ordinal_max_vlf_active)*100.00/vlf_count) AS free_log_pct_after_active_log
FROM cte_vlf_cnt
GO
```

## <a name="see-also"></a>См. также  
[Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

