---
title: "sp_xtp_flush_temporal_history | Документы Microsoft"
ms.custom: 
ms.date: 02/21/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server (starting with 2016 CTP3)
f1_keywords:
- sp_xtp_flush_temporal_history
- sp_xtp_flush_temporal_history_TSQL
- sys.sp_xtp_flush_temporal_history
- sys.sp_xtp_flush_temporal_history_TSQL
helpviewer_keywords: sp_xtp_flush_temporal_history
ms.assetid: 322e3170-93f8-468a-a123-104ce7bd7fad
caps.latest.revision: "7"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 75a2394e72a0990a9f5108af6b77feb1fb3c44d6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="temporal-table---spxtpflushtemporalhistory"></a>Временная таблица - sp_xtp_flush_temporal_history
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Вызывается задача очистки данных, чтобы переместить все зафиксированные строки из промежуточной таблицы в памяти в таблицу журнала на диске.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_xtp_flush_temporal_history @schema_name, @object_name  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *@schema_name*  
 Имя схемы для текущей или темпоральной таблицей.  
  
 *@object_name*  
 Имя текущей или темпоральной таблицей.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Требуются права db_owner.  
  
## <a name="see-also"></a>См. также:  
 [Вопросы производительности оптимизированных для памяти темпоральных таблиц с системным управлением версиями](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)  
  
  
