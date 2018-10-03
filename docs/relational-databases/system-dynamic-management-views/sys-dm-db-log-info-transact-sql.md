---
title: sys.dm_db_log_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f93bf921236676b40a9d6917af38ca3ca88ff5f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644112"
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Возвращает [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) сведения журнала транзакций. Обратите внимание, что все файлы журнала транзакций, объединяются в выходной таблице. Каждая строка в выходных данных представляет VLF в журнале транзакций и предоставляет сведения, относящиеся к этой VLF в журнале.

## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_log_info ( database_id )  
``` 

## <a name="arguments"></a>Аргументы  
 *database_id* | NULL | ПО УМОЛЧАНИЮ  
 Идентификатор базы данных. Аргумент *database_id* имеет тип **int**. Допустимыми входными значениями являются Идентификационный номер базы данных, значение NULL или значение по умолчанию. Значение по умолчанию — NULL. Значение NULL и значение по умолчанию — это эквивалент значения в контексте текущей базы данных.
 
 Укажите значение NULL для возврата сведений о виртуальных файлах Журнала текущей базы данных.

 Встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md) можно указать. При использовании `DB_ID` без указания имени базы данных, уровень совместимости текущей базы данных должен быть равен 90 или выше.  

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|
|file_id|**smallint**|Идентификатор файла журнала транзакций.|  
|vlf_begin_offset|**bigint** |Смещение расположения [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) от начала файла журнала транзакций.|
|vlf_size_mb |**float** |[виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) размер в МБ, округленное до 2 десятичных разряда.|     
|vlf_sequence_number|**bigint** |[виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) порядковый номер в созданного заказа. Используется для уникальной идентификации VLF в файле журнала.|
|vlf_active|**bit** |Указывает, является ли [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) уже используется или нет. <br />0 — виртуального файла Журнала не используется.<br />1 - VLF активна.|
|vlf_status|**int** |Состояние [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Возможные значения: <br />0 — VLF неактивна <br />1 - VLF инициализирован, но неиспользуемого <br /> 2 - VLF активна.|
|vlf_parity|**tinyint** |Четность [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Используется внутренним образом для определения конца журнала в VLF.|
|vlf_first_lsn|**nvarchar(48)** |[Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) первой записи журнала в [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar(48)** |[Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) записи журнала, созданные [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|

## <a name="remarks"></a>Примечания
`sys.dm_db_log_info` Заменяет функцию динамического управления `DBCC LOGINFO` инструкции.    
 
## <a name="permissions"></a>Разрешения  
Требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Определение баз данных в экземпляре SQL Server с большое количество виртуальных файлов журнала
Следующий запрос определяет баз данных с более чем 100 виртуальных файлов журнала в файлах журналов, которые могут повлиять на время запуска, восстановления и восстановления базы данных.

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-position-of-the-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>Б. Определить положение последнего `VLF` в журнале транзакций, прежде чем при сжатии файла журнала

Следующий запрос может использоваться для определения позиции последнем виртуальном файле Журнала active перед запуском shrinkfile на журнал транзакций, чтобы определить, если журнал транзакций можно сжать.

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

