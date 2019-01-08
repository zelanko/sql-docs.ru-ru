---
title: MSrepl_backup_lsns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b35c095b2c00b4293062086b9a79f92b1fb4e77b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52757916"
---
# <a name="msreplbackuplsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_backup_lsns** таблица содержит номера транзакций в журнале (LSN) для поддержки параметр «sync with backup» базы данных распространителя. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**valid_xact_id**|**varbinary(16)**|Идентификатор транзакции должен быть отправлен на сервер издателя для журналирования точки усечения. Используется, только если база данных распространителя находится в режиме «синхронизации с резервной копией». Содержит идентификатор последней реплицируемой транзакции в базе данных распространителя, для которой была сделана резервная копия. Будет отправлен издателю, чтобы отметить точку усечения журнала, выполненную модулем считывания журнала.|  
|**valid_xact_seqno**|**varbinary(16)**|Регистрационный номер транзакции, который должен быть отправлен на сервер издателя, чтобы отметить точку усечения журнала. Используется, только если база данных распространителя находится в режиме «синхронизации с резервной копией». Это последовательный номер в журнале для последней реплицируемой транзакции в базе данных распространителя, для которой была сделана резервная копия. Будет отправлен издателю, чтобы отметить точку усечения журнала, выполненную модулем считывания журнала.|  
|**next_xact_id**|**varbinary(16)**|Временный последовательный номер транзакции в журнале, используемый операциями восстановления.|  
|**nextx_xact_seqno**|**varbinary(16)**|Временный последовательный номер транзакции в журнале, используемый операциями восстановления.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
