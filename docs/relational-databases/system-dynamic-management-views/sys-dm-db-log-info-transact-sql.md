---
title: "sys.dm_db_log_info (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 661647715d2fcff3a4821250dfaa65e0fea07d6e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) сведения журнала транзакций. Обратите внимание, что все файлы журнала транзакций, объединяются в выходной таблице. Каждая строка в выходных данных представляет VLF в журнале транзакций и предоставляет сведения, относящиеся к этой виртуального файла Журнала в журнале.

## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>Аргументы  
 *database_id* | ЗНАЧЕНИЕ NULL | ПО УМОЛЧАНИЮ  
 Идентификатор базы данных. *database_id* — **int**. Допустимыми входными значениями являются идентификатор базы данных, NULL или по умолчанию. Значение по умолчанию — NULL. Значение NULL по умолчанию значения и эквивалентны в контексте текущей базы данных.
 
 Укажите значение NULL для возврата сведений о VLF текущей базы данных.

 Встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md) можно указать. При использовании `DB_ID` без указания имени базы данных, уровень совместимости текущей базы данных должен быть равен 90 или выше.  

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|
|file_id|**smallint**|Идентификатор файла журнала транзакций.|  
|vlf_begin_offset|**bigint** |Смещение расположения [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) от начала файла журнала транзакций.|
|vlf_size_mb |**float** |[виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) размер в МБ, округляется до 2 десятичных разряда.|     
|vlf_sequence_number|**bigint** |[виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) порядковый номер в созданного заказа. Используется для уникальной идентификации VLF в файле журнала.|
|vlf_active|**bit** |Указывает, является ли [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) уже используется или не. <br />0 — виртуального файла Журнала не используется.<br />1 — VLF активен.|
|vlf_status|**int** |Состояние [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Возможные значения: <br />0 — неактивные VLF <br />1 — VLF инициализирована, но неиспользуемого <br /> 2 - VLF активен.|
|vlf_parity|**tinyint** |Четность [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Используется внутренним образом для определения конца журнала в пределах виртуального файла Журнала.|
|vlf_first_lsn|**nvarchar(48)** |[Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) первой записи журнала в [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar(48)** |[Регистрационный номер транзакции в (журнале LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) записи журнала, созданные [виртуальный файл журнала (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|

## <a name="remarks"></a>Remarks
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

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>Б. Определение состояния последней `VLF` в журнале транзакций до при сжатии файла журнала

Следующий запрос может использоваться для определения состояния последнем виртуальном файле Журнала перед выполнением процедуры SHRINKFILE модуля на журнал транзакций, чтобы определить, если журнал транзакций можно сжать.

```sql
USE AdventureWorks2016
GO

SELECT TOP 1 DB_NAME(database_id) AS "Database Name", file_id, vlf_size_mb, vlf_sequence_number, vlf_active, vlf_status
FROM sys.dm_db_log_info(DEFAULT)
ORDER BY vlf_sequence_number DESC
```


## <a name="see-also"></a>См. также:  
[Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

