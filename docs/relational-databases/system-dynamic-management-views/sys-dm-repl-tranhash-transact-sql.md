---
title: sys.dm_repl_tranhash (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d10d4451071ac476b25fdfef00ab4a48d1c3f63
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736593"
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о транзакции, реплицируемой в публикации транзакций.  
  
|column_name|Тип данных|description|  
|------------------|----------------|-----------------|  
|**контейнеры**|**bigint**|Количество сегментов в хэш-таблице.|  
|**hashed_trans**|**bigint**|Количество зафиксированных транзакций, реплицированных в текущем пакете.|  
|**completed_trans**|**bigint**|Количество транзакций, выполненных до настоящего момента.|  
|**compensated_trans**|**bigint**|Количество транзакций, содержащих частичный откат.|  
|**first_begin_lsn**|**Nvarchar(64)**|Самый ранний начальный регистрационный номер транзакции в журнале (LSN) в текущем пакете.|  
|**last_commit_lsn**|**Nvarchar(64)**|Последняя фиксация номера LSN в текущем пакете.|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW DATABASE STATE в базе данных публикации для вызова **dm_repl_tranhash**.  
  
## <a name="remarks"></a>Примечания  
 Возвращаются сведения только по реплицируемым объектам базы данных, которые загружены в кэш статей репликации.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с репликацией &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
