---
title: "sp_set_session_context (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a55ee31e1f4d9f5f98766550f60a16d3dd56843c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spsetsessioncontext-transact-sql"></a>sp_set_session_context (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Задает пару ключ значение в контексте сеанса.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_set_session_context [ @key= ] 'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @key=] 'key'  
 Ключ, задаваемое типа **sysname**. Максимальный размер ключа составляет 128 байт.  
  
 [ @value=] 'value'  
 Значение для указанного ключа, типа **sql_variant**. При установке значения NULL освобождает память. Максимальный размер 8 000 байт.  
  
 [ @read_only= ] { 0 | 1 }  
 Флаг типа **бит**. Если значение равно 1, затем значение для указанного ключа нельзя добавить снова на это логическое соединение. Если 0 (по умолчанию), то значение может быть изменен.  
  
## <a name="permissions"></a>Permissions  
 Любой пользователь может задать контекст сеанса для сеанса.  
  
## <a name="remarks"></a>Замечания  
 Как и другие хранимые процедуры только литералы и переменные (не выражения или вызовы функций) могут передаваться как параметры.  
  
 Общий размер контекста сеанса ограничена 256 КБ. Если установить значение, которое вызывает этот предел превышен, то инструкция завершается ошибкой. Можно отслеживать общее использование памяти в [sys.dm_os_memory_objects &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).  
  
 Общее использование памяти можно отслеживать с помощью запроса [sys.dm_os_memory_cache_counters &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) следующим образом:`SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>Примеры  
 Приведенный ниже показано, как задать и возвращать сеансы ключ контекста с именем языка со значением английского языка.  
  
```  
EXEC sp_set_session_context 'language', 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 В следующем примере показано использование необязательный флаг только для чтения.  
  
```  
EXEC sp_set_session_context 'user_id', 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [CURRENT_TRANSACTION_ID &#40; Transact-SQL &#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT (Transact-SQL)](../../t-sql/functions/session-context-transact-sql.md)   
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
