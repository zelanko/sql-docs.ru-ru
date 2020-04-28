---
title: sys. dm_db_log_info (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 7cb87d2d5677085edc8e6bd998f20c3c45013823
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68262081"
---
# <a name="sysdm_db_log_info-transact-sql"></a>sys. dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Возвращает сведения о [файле виртуального журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) журнала транзакций. Примечание. все файлы журнала транзакций объединяются в выходные данные таблицы. Каждая строка выходных данных представляет собой VLF в журнале транзакций и предоставляет сведения, относящиеся к этому VLF в журнале.

## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_log_info ( database_id )  
``` 

## <a name="arguments"></a>Аргументы  
 *database_id* | NULL | ПАРАМЕТРЫ  
 Идентификатор базы данных. *database_id* имеет **тип int**. Допустимыми входными значениями являются идентификатор базы данных, значение NULL или значение по умолчанию. Значение по умолчанию — NULL. Значения NULL и DEFAULT являются эквивалентными значениями в контексте текущей базы данных.
 
 Укажите значение NULL, чтобы вернуть сведения о VLF текущей базы данных.

 Может быть указана встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md). При использовании `DB_ID` без указания имени базы данных уровень совместимости текущей базы данных должен быть 90 или выше.  

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|
|file_id|**smallint**|Идентификатор файла журнала транзакций.|  
|vlf_begin_offset|**bigint** |Смещение расположения [виртуального файла журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) с начала файла журнала транзакций.|
|vlf_size_mb |**float** |размер [виртуального файла журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) в МБ, округленный до двух десятичных разрядов.|     
|vlf_sequence_number|**bigint** |порядковый номер [файла виртуального журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) в созданном порядке. Используется для уникальной идентификации VLF в файле журнала.|
|vlf_active|**bit** |Указывает, используется ли [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) . <br />0 — VLF не используется.<br />1 — VLF является активным.|
|vlf_status|**int** |Состояние [виртуального файла журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Возможные значения: <br />0 — VLF неактивен <br />1 — VLF инициализирован, но не используется <br /> 2 — VLF активно.|
|vlf_parity|**tinyint** |Четность [виртуального файла журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Используется внутренне для определения конца журнала в VLF.|
|vlf_first_lsn|**nvarchar (48)** |Регистрационный [номер транзакции в журнале (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) первой записи журнала в [виртуальном файле журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar (48)** |Регистрационный [номер транзакции в журнале (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) для записи журнала, создавшей [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_encryptor_thumbprint|**varbinary(20)**| **Относится к** [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] <br><br> Показывает отпечаток шифратора VLF, если VLF шифруется с помощью [прозрачное шифрование данных](../../relational-databases/security/encryption/transparent-data-encryption.md), в противном случае — null. |

## <a name="remarks"></a>Remarks
Функция `sys.dm_db_log_info` динамического управления заменяет `DBCC LOGINFO` инструкцию.    
 
## <a name="permissions"></a>Разрешения  
Требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Деусловие базы данных в экземпляре SQL Server с большим количеством VLF
Следующий запрос определяет базы данных с более чем 100 VLF в файлах журнала, что может повлиять на время запуска, восстановления и восстановления базы данных.

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-position-of-the-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>Б) Расположение последнего `VLF` в журнале транзакций до сжатия файла журнала

Следующий запрос можно использовать для определения расположения последнего активного VLF перед выполнением команды SHRINKFILE в журнале транзакций, чтобы определить, может ли журнал транзакций сжиматься.

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

## <a name="see-also"></a>См. также:  
[Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys. dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

