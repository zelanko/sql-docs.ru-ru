---
title: sp_set_session_context (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4c7c68341338706c59c7ef966bf5abc6110c46e6
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51811875"
---
# <a name="spsetsessioncontext-transact-sql"></a>sp_set_session_context (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Задает пару ключ значение в контексте сеанса.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_set_session_context [ @key= ] N'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @key=] N'key "  
 Ключ, задаваемое типа **sysname**. Максимальный размер ключа составляет 128 байт.  
  
 [ @value=] 'value'  
 Значение для указанного ключа, типа **sql_variant**. При установке значения NULL освобождает память. Максимальный размер 8 000 байт.  
  
 [ @read_only= ] { 0 | 1 }  
 Флаг типа **бит**. Если значение равно 1, затем значение для указанного ключа невозможно еще раз на этом логическое соединение. Если 0 (по умолчанию), то значение может быть изменен.  
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может установить контекст сеанса своего сеанса.  
  
## <a name="remarks"></a>Примечания  
 Как и другие хранимые процедуры только литералы и переменные (не выражения или вызовы функций) могут передаваться как параметры.  
  
 Общий размер контекста сеанса ограничено до 1 МБ. Если задать значение, которое вызывает этот предел превышен, инструкция завершается неудачно. Вы можете отслеживать общее использование памяти в [sys.dm_os_memory_objects &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).  
  
 Можно отслеживать общее использование памяти, запросив [sys.dm_os_memory_cache_counters &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) следующим образом: `SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>Примеры  
 Приведенный ниже показано, как задать и затем вернуть ключ сеансы контекста с именем языка со значением на английском языке.  
  
```  
EXEC sys.sp_set_session_context @key = N'language', @value = 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 Следующий пример демонстрирует использование необязательный флаг только для чтения.  
  
```  
EXEC sys.sp_set_session_context @key = N'user_id', @value = 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [CURRENT_TRANSACTION_ID (Transact-SQL)](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT (Transact-SQL)](../../t-sql/functions/session-context-transact-sql.md)   
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO  (Transact-SQL)](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO (Transact-SQL)](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
