---
title: "SET CONTEXT_INFO (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_CONTEXT_INFO_TSQL
- SET CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- context information [SQL Server]
- CONTEXT_INFO option
- SET CONTEXT_INFO statement
ms.assetid: a0b7b9f3-dbda-4350-a274-bd9ecd5c0a74
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f74a45830a295467552c8fdc9f4781260339d9a6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-contextinfo-transact-sql"></a>SET CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Связывает до 128 байт бинарных данных с текущим сеансом или соединением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET CONTEXT_INFO { binary_str | @binary_var }  
```  
  
## <a name="arguments"></a>Аргументы  
 *binary_str*  
 — **Двоичных** константой или константа, которая неявно преобразуется в **двоичных**, связываемый с текущим сеансом или соединением.  
  
 **@***binary_var*  
 — **Varbinary** или **двоичных** переменной, удерживающие значение контекста для связи с текущим сеансом или соединением.  
  
## <a name="remarks"></a>Замечания  
 Предпочтительным способом для получения контекстных данных по текущему сеансу является использование функции CONTEXT_INFO. Сведения о контексте сеанса также сохраняются в **context_info** столбцов в следующих системных представлений:  
  
-   **sys.dm_exec_requests**  
  
-   **sys.dm_exec_sessions**  
  
-   **sys.sysprocesses**  
  
 SET CONTEXT_INFO не может быть задан в определенной пользователем функции. Нельзя применить значение NULL к SET CONTEXT_INFO, так как представления, хранящие значения, не допускают значения NULL.  
  
 SET CONTEXT_INFO не принимает другие выражения, нежели имена констант и переменных. Чтобы задать сведения о контексте результатом вызова функции, необходимо сначала назначить результат вызова функции в **двоичных** или **varbinary** переменной.  
  
 Если SET CONTEXT_INFO вызывается в сохраненной процедуре или триггере, то в отличие от других инструкций SET, для контекстных данных установится новое значение, сохраненное после завершения хранимой процедуры или триггера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-context-information-by-using-a-constant"></a>A. Задание контекстных данных с помощью константы  
 Следующий пример демонстрирует использование `SET CONTEXT_INFO` с заданием значения и отображением результатов. Заметьте, что запросы `sys.dm_exec_sessions` требуют разрешений на SELECT и VIEW SERVER STATE везде, где бы не использовалась функция CONTEXT_INFO.  
  
```  
SET CONTEXT_INFO 0x01010101;  
GO  
SELECT context_info   
FROM sys.dm_exec_sessions  
WHERE session_id = @@SPID;  
GO  
```  
  
### <a name="b-setting-context-information-by-using-a-function"></a>Б. Задание контекстных данных с помощью функции  
 В следующем примере показано задание контекстного значения, где значение от функции необходимо поместить в, используя вывод функции **двоичных** переменной.  
  
```  
DECLARE @BinVar varbinary(128);  
SET @BinVar = CAST(REPLICATE( 0x20, 128 ) AS varbinary(128) );  
SET CONTEXT_INFO @BinVar;  
  
SELECT CONTEXT_INFO() AS MyContextInfo;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)  
  
  

