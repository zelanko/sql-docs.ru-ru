---
title: "SESSION_CONTEXT (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/22/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SESSION_CONTEXT
- sys.SESSION_CONTEXT
- SESSION_CONTEXT_TSQL
- sys.SESSION_CONTEXT_TSQL
helpviewer_keywords:
- SESSION_CONTEXT function
ms.assetid: b6bdbc54-331a-43cc-ab3d-3872d6a12100
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23eea4b51009272ae06987ee2e9c1730750b3d6d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sessioncontext-transact-sql"></a>SESSION_CONTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает значение указанного ключа в контексте текущего сеанса. Значение задается с помощью [sp_set_session_context &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md) процедуры.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SESSION_CONTEXT(N'key')  
```  
  
## <a name="arguments"></a>Аргументы  
 'key'  
 Ключ извлекается значение (типа sysname).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **sql_variant**  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение, связанное с указанным ключом в контексте сеанса, или значение NULL, если значение не было задано для этого ключа.  
  
## <a name="permissions"></a>Permissions  
 Любой пользователь может считывать контекста сеанса для сеанса.  
  
## <a name="remarks"></a>Замечания  
 Поведение режима MARS в SESSION_CONTEXT аналогична CONTEXT_INFO. Если пакет MARS задает пару ключ значение, новое значение не возвращается в других пакетах режима MARS в том же соединении только после их запуска после завершения пакетом, устанавливающим новое значение. Если несколько пакетов MARS активны для подключения, значения невозможно задать в качестве «read_only.» Это предотвращает гонки и недетерминированные о нужное значение «по значению».  
  
## <a name="examples"></a>Примеры  
 Следующий простой пример задает значение контекста сеанса для ключа `user_id` 4, а затем использует **SESSION_CONTEXT** функции для получения значения.  
  
```  
EXEC sp_set_session_context 'user_id', 4;  
SELECT SESSION_CONTEXT(N'user_id');  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_set_session_context (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)   
 [CURRENT_TRANSACTION_ID &#40; Transact-SQL &#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  

