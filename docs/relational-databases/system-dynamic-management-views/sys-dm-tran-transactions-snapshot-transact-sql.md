---
title: "sys.dm_tran_transactions_snapshot (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_transactions_snapshot
- dm_tran_transactions_snapshot
- sys.dm_tran_transactions_snapshot_TSQL
- dm_tran_transactions_snapshot_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_transactions_snapshot dynamic management view
ms.assetid: 03f64883-07ad-4092-8be0-31973348c647
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab16132fd9b9bca0b0c2e0f12eedfbfe87fae530
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtrantransactionssnapshot-transact-sql"></a>sys.dm_tran_transactions_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает виртуальную таблицу для **sequence_number** транзакций, активных при каждой транзакции моментальных снимков запускается. Данные, возвращаемые этим представлением, могут помочь:  
  
-   найти номера активных в настоящее время транзакций моментальных снимков;  
  
-   определить изменения данных, пропущенные обычной транзакцией моментальных снимков. Для транзакции, активной при запуске транзакции моментальных снимков, все измененные этой транзакцией данные (даже после того, как она будет зафиксирована) будут пропущены транзакцией моментальных снимков.  
  
 Например, рассмотрим следующие выходные данные **sys.dm_tran_transactions_snapshot**:  
  
```  
transaction_sequence_num snapshot_id snapshot_sequence_num  
------------------------ ----------- ---------------------  
59                       0           57  
59                       0           58  
60                       0           57  
60                       0           58  
60                       0           59  
60                       3           57  
60                       3           58  
60                       3           59  
60                       3           60  
```  
  
 Столбец `transaction_sequence_num` содержит последовательные номера транзакции (XSN) текущих транзакций моментальных снимков. В выходных данных их два: `59` и `60`. Столбец `snapshot_sequence_num` содержит последовательные номера транзакций, активных при запуске каждой транзакции моментальных снимков.  
  
 Видно, что запуск транзакции моментальных снимков XSN-59 произошел, когда были активны транзакции XSN-57 и XSN-58. Если в транзакциях XSN-57 или XSN-58 выполняется изменение данных, транзакция XSN-59 пропустит эти изменения и будет использовать управление версиями строк для поддержки транзакционно согласованного представления базы данных.  
  
 Транзакция моментальных снимков XSN-60 пропустит изменения данных, сделанные в транзакциях XSN-57, XSN-58 и XSN 59.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dm_tran_transactions_snapshot  
```  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|Последовательный номер транзакции моментальных снимков.|  
|**snapshot_id**|**int**|Идентификатор моментального снимка для каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], вызванной в контексте чтения зафиксированных данных с помощью управления версиями строк. Этот идентификатор используется для формирования согласованного на уровне транзакций представления базы данных, поддерживающего выполнение каждого запроса в контексте управления версиями строк с чтением только зафиксированных данных.|  
|**snapshot_sequence_num**|**bigint**|Последовательный номер транзакции, которая была активна при запуске транзакции моментальных снимков.|  
  
## <a name="permissions"></a>Разрешения  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="remarks"></a>Замечания  
 При запуске транзакции моментальных снимков компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] регистрирует все активные транзакции. **sys.dm_tran_transactions_snapshot** передает эту информацию для всех в настоящее время активных транзакций моментальных снимков.  
  
 Каждая транзакция имеет последовательный номер, который назначается ей при запуске. Запуск транзакций начинается с вызова инструкции BEGIN TRANSACTION или BEGIN WORK. Однако последовательный номер транзакции назначается компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] при выполнении первой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], следующей за инструкцией BEGIN TRANSACTION или BEGIN WORK. Последовательные номера транзакций увеличиваются с единичным интервалом.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

