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
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: "4"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: b7250943f4e92d60888a75d9e577388f3cc6b1ed
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает `VLF` сведения журналов транзакций. (Все файлы журнала объединяются в выходной таблице). Каждая строка в выходных данных представляет `VLF` в журнале транзакций и предоставляет сведения, относящиеся к этой виртуального файла Журнала в журнале.

## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>Аргументы  
 *database_id* | ЗНАЧЕНИЕ NULL | ПО УМОЛЧАНИЮ  
 Идентификатор базы данных. *database_id* — **int**. Допустимыми входными значениями являются идентификатор базы данных, NULL или по умолчанию. Значение по умолчанию — NULL. Значение NULL по умолчанию значения и эквивалентны в контексте текущей базы данных.
 
 Укажите NULL, чтобы возвратить `VLF` сведения текущей базы данных.

 Встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md) можно указать. Если функция DB_ID используется без указания имени базы данных, то уровень совместимости текущей базы данных должен быть равен 90 или выше.  

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных.|
|file_id|**smallint**|Идентификатор файла журнала транзакций.|  
|vlf_begin_offset|**bigint** |Смещение расположения `VLF` от начала файла журнала транзакций.|
|vlf_size_mb |**float** |`VLF`размер в МБ, округляется до 2 десятичных разряда.|     
|vlf_sequence_number|**bigint** |`VLF`Порядковый номер в созданного заказа. Используется для однозначной идентификации `VLFs` в файле журнала.|
|vlf_active|**bit** |Указывает, является ли использование виртуального файла Журнала или нет. <br />0 — виртуального файла журнала не используется.<br />1 - `VLF` активен.|
|vlf_status|**int** |Состояние `VLF`. Возможные значения: <br />0 — `VLF` неактивна <br />1 — vlf инициализирована, но неиспользуемого <br /> 2 - `VLF` активен.|
|vlf_parity|**tinyint** |Четность `VLF`. Используется внутренним образом для определения конца журнала в `VLF`.|
|vlf_first_lsn|**nvarchar(48)** |Номер LSN первой записи журнала в `VLF`.|
|vlf_create_lsn|**nvarchar(48)** |Номер LSN журнала запись, с которой создан `VLF`.|

## <a name="remarks"></a>Замечания
 `sys.dm_db_log_info` Заменяет функцию динамического управления `DBCC LOGINFO` инструкции. 
 
## <a name="permissions"></a>Permissions  
 Требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Определение баз данных в экземпляре SQL Server с большое количество`VLFs`
Следующий запрос определяет базы данных с более чем 100 `VLFs` в файлах журналов, которое может повлиять на время запуска, восстановления и восстановления базы данных.

```sql
SELECT name,count(l.database_id) as 'vlf_count' from sys.databases s
cross apply sys.dm_db_log_info(s.database_id) l
group by name
having count(l.database_id)> 100
```

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>Б. Определение состояния последней `VLF` в журнале транзакций до при сжатии файла журнала

Следующий запрос может использоваться для определения состояния последней `VLF` перед выполнением процедуры SHRINKFILE модуля на журнал транзакций, чтобы определить, если журнал транзакций можно сжать.

```sql
USE <database name>
GO

SELECT top 1 DB_NAME(database_id) as "Database Name",file_id,vlf_size_mb,vlf_sequence_number, vlf_active, vlf_status
from sys.dm_db_log_info(DEFAULT)
order by vlf_sequence_number desc
```


## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_log_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)    
  



