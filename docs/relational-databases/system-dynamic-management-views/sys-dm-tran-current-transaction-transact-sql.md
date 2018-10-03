---
title: sys.dm_tran_current_transaction (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_current_transaction
- sys.dm_tran_current_transaction_TSQL
- dm_tran_current_transaction_TSQL
- dm_tran_current_transaction
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_current_transaction dynamic management view
ms.assetid: 75d5697d-b390-4963-99b8-fa0b4244a40c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 532bc1fb5f0ad31c56cd6b47dd3b0d98f5138fda
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640432"
---
# <a name="sysdmtrancurrenttransaction-transact-sql"></a>sys.dm_tran_current_transaction (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку, которая отображает сведения о состоянии транзакции в текущей сессии.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_current_transaction**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_tran_current_transaction  
```  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**transaction_id**|**bigint**|Идентификатор транзакции текущего моментального снимка.|  
|**transaction_sequence_num**|**bigint**|Порядковый номер транзакции, формирующей версию записи.|  
|**transaction_is_snapshot**|**bit**|Состояние изоляции моментального снимка. Значение 1, если транзакция запускается с изоляцией моментального снимка. В противном случае — значение 0.|  
|**first_snapshot_sequence_num**|**bigint**|Наименьший порядковый номер транзакции, которая была активна при получении моментального снимка. При выполнении транзакции моментального снимка она формирует моментальный снимок активных в этот момент транзакций. Для транзакций, не связанных с моментальными снимками, в этом столбце отображается 0.|  
|**last_transaction_sequence_num**|**bigint**|Глобальный последовательный номер. Последний последовательный номер транзакции, созданный системой.|  
|**first_useful_sequence_num**|**bigint**|Глобальный последовательный номер. Самый старый последовательный номер транзакции, версии строк которой должны сохраняться в хранилище версий. Версии строк, созданных предыдущими транзакциями, можно удалить.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="examples"></a>Примеры  
 Следующий пример использует тестовый сценарий, содержащий четыре параллельные транзакции, идентифицированные порядковыми номерами (XSN), который выполняется в базе данных с параметрами ALLOW_SNAPSHOT_ISOLATION и READ_COMMITTED_SNAPSHOT, установленными в значение ON. Следующие транзакции запущены:  
  
-   XSN-57 является операцией обновления с сериализуемой изоляцией.  
  
-   XSN-58 аналогична XSN-57.  
  
-   XSN-59 является операцией выбора с изоляцией моментального снимка.  
  
-   XSN-60 аналогична XSN-59.  
  
 Следующий запрос выполняется в области каждой транзакции.  
  
```  
SELECT   
    transaction_id  
   ,transaction_sequence_num  
   ,transaction_is_snapshot  
   ,first_snapshot_sequence_num  
   ,last_transaction_sequence_num  
   ,first_useful_sequence_num  
  FROM sys.dm_tran_current_transaction;  
```  
  
 Результат для XSN-59.  
  
```  
transaction_id       transaction_sequence_num transaction_is_snapshot  
-------------------- ------------------------ -----------------------  
9387                 59                       1                         
  
first_snapshot_sequence_num last_transaction_sequence_num  
--------------------------- -----------------------------  
57                               61                        
  
first_useful_sequence_num  
-------------------------  
57  
```  
  
 Выход показывает, что XSN-59 — транзакция моментального снимка, использовавшая XSN-57 как первую активную транзакцию на момент запуска XSN-59. Это означает, что транзакция XSN-59 считывает данные, зафиксированные транзакциями с порядковыми номерами ниже чем у XSN-57.  
  
 Результат для XSN-57.  
  
```  
transaction_id       transaction_sequence_num transaction_is_snapshot  
-------------------- ------------------------ -----------------------  
9295                 57                       0  
  
first_snapshot_sequence_num last_transaction_sequence_num  
--------------------------- -----------------------------  
NULL                        61  
  
first_useful_sequence_num  
-------------------------  
57  
```  
  
 Так как транзакция XSN-57 не связана с моментальными снимками, значение `first_snapshot_sequence_num` равно `NULL`.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


