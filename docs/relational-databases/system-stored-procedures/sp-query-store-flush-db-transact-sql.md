---
title: sp_query_store_flush_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_query_store_flush_db_TSQL
- sys.sp_query_store_flush_db_TSQL
- sp_query_store_flush_db
- sys.sp_query_store_flush_db
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_flush_db
- sp_query_store_flush_db
ms.assetid: 580c03ae-57fc-4562-a6bb-5ec89521e38c
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 96c4e7a366c1235fa1062e5d66c2d6be160a6d22
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68418888"
---
# <a name="spquerystoreflushdb-transact-sql"></a>sp_query_store_flush_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Очищает часть данных хранилища запросов в памяти на диск.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_query_store_flush_db [;]  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **ALTER** на базу данных.
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется сброс части данных хранилища запросов, хранящихся в памяти, на диск.  
  
```  
EXEC sp_query_store_flush_db;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_query_store_force_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_remove_plan &#40;TRANSCT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_reset_exec_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [Query Store Catalog Views (Transact-SQL) ](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  (Представления каталогов хранилища запросов (Transact-SQL))  
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
