---
title: MSrepl_transactions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_transactions_TSQL
- MSrepl_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_transactions system table
ms.assetid: d325288d-47ae-4488-8799-122f7ab43459
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 44ace7a4b203f3d34b7f9e8ee89dc916afab51e8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52775456"
---
# <a name="msrepltransactions-transact-sql"></a>MSrepl_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_transactions** таблица содержит по одной строке для каждой реплицируемой транзакции. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**xact_id**|**varbinary(16)**|Идентификатор транзакции.|  
|**xact_seqno**|**varbinary(16)**|Порядковый номер транзакции.|  
|**entry_time**|**datetime**|Время входа транзакции в базу данных распространителя.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
