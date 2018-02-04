---
title: "sys.dm_tran_version_store (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_TSQL
- sys.dm_tran_version_store
- dm_tran_version_store
- dm_tran_version_store_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_version_store dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be8779d40624e9f88ee74ea85a1126c1b4b76ebf
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmtranversionstore-transact-sql"></a>sys.dm_tran_version_store (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает виртуальную таблицу, в которой отображаются все записи о версиях в хранилище версий. **sys.dm_tran_version_store** неэффективно, так как он запрашивает все хранилище версий и хранилище версий может быть очень большим.  
  
 Каждая запись версии хранится в виде двоичных данных вместе с некоторыми сведениями о состоянии и отслеживании. Как и в таблицах базы данных, записи в хранилище версий хранятся в страницах размером 8192 байта. Если размер записи превышает 8192 байта, она разбивается на две различные записи.  
  
 Так как запись версии хранится в двоичном виде, не возникает проблем с разными параметрами сортировки из разных баз данных. Используйте **sys.dm_tran_version_store** для поиска предыдущих версий строк в двоичном представлении, в котором они хранятся в хранилище версий.  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_tran_version_store  
```  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|Порядковый номер транзакции, формирующей версию записи.|  
|**version_sequence_num**|**bigint**|Порядковый номер версии записи. Значение является уникальным в рамках сформировавшей эту версию транзакции.|  
|**database_id**|**int**|Идентификатор базы данных версии записи.|  
|**rowset_id**|**bigint**|Идентификатор набора строк записи.|  
|**status**|**tinyint**|Указывает, была ли запись версии разбита на две записи. Если значение равно 0, запись хранится на одной странице. Если оно равно 1, запись разбивается на две записи, которые хранятся на двух различных страницах.|  
|**min_length_in_bytes**|**smallint**|Минимальная длина записи в байтах.|  
|**record_length_first_part_in_bytes**|**smallint**|Длина первой части записи версии в байтах.|  
|**record_image_first_part**|**varbinary(8000)**|Двоичный образ первой части записи версии.|  
|**record_length_second_part_in_bytes**|**smallint**|Длина второй части записи версии в байтах.|  
|**record_image_second_part**|**varbinary(8000)**|Двоичный образ второй части записи версии.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
 

  
## <a name="examples"></a>Примеры  
 Следующий пример использует тестовый сценарий, содержащий четыре параллельные транзакции, идентифицированные порядковыми номерами (XSN), который выполняется в базе данных с параметрами ALLOW_SNAPSHOT_ISOLATION и READ_COMMITTED_SNAPSHOT, установленными в значение ON. Следующие транзакции запущены:  
  
-   XSN-57 является операцией обновления с сериализуемой изоляцией.  
  
-   XSN-58 аналогична XSN-57.  
  
-   XSN-59 является операцией выбора с изоляцией моментального снимка.  
  
-   XSN-60 аналогична XSN-59.  
  
 Выполнен следующий запрос.  
  
```  
SELECT  
    transaction_sequence_num,  
    version_sequence_num,  
    database_id rowset_id,  
    status,  
    min_length_in_bytes,  
    record_length_first_part_in_bytes,  
    record_image_first_part,  
    record_length_second_part_in_bytes,  
    record_image_second_part  
  FROM sys.dm_tran_version_store;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_sequence_num version_sequence_num database_id  
------------------------ -------------------- -----------  
57                      1                    9             
57                      2                    9             
57                      3                    9             
58                      1                    9             
  
rowset_id            status min_length_in_bytes  
-------------------- ------ -------------------  
72057594038321152    0      12                   
72057594038321152    0      12                   
72057594038321152    0      12                   
72057594038386688    0      16                   
  
record_length_first_part_in_bytes  
---------------------------------  
29                                 
29                                 
29                                 
33                                 
  
record_image_first_part                                               
--------------------------------------------------------------------  
0x50000C0073000000010000000200FCB000000001000000270000000000          
0x50000C0073000000020000000200FCB000000001000100270000000000          
0x50000C0073000000030000000200FCB000000001000200270000000000          
0x500010000100000002000000030000000300F800000000000000002E0000000000  
  
record_length_second_part_in_bytes record_image_second_part  
---------------------------------- ------------------------  
0                                  NULL  
0                                  NULL  
0                                  NULL  
0                                  NULL  
```  
  
 Выход показывает, что транзакция XSN-57 создала три версии строк из одной таблицы, а XSN-58 — одну версию строки из другой таблицы.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
