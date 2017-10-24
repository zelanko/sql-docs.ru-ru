---
title: "@@ROWCOUNT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@ROWCOUNT_TSQL'
- '@@ROWCOUNT'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@ROWCOUNT function'
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 97a47998-81d9-4331-a244-9eb8b6fe4a56
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 411dc7eb628ddff52eb2f9426488e05860c9d279
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40rowcount-transact-sql"></a>& #x 40; & #x 40; Количество СТРОК (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает число строк, затронутых при выполнении последней инструкции. Если число строк превышает 2 миллиарда, используйте [ROWCOUNT_BIG](../../t-sql/functions/rowcount-big-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@ROWCOUNT  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]операторы, можно задать значение в @@ROWCOUNT одним из следующих способов:  
  
-   Значение@ROWCOUNT на число строк, задействованных или считанных. Строки могут быть отосланы или не отосланы клиенту.  
  
-   Сохранить@ROWCOUNT из предыдущего выполнения инструкции.  
  
-   Сброс@ROWCOUNT 0, но не возвращать значение клиенту.  
  
 Инструкции, которые создают простые назначения, всегда устанавливают @@ROWCOUNT значение 1. Строки не отправляются клиенту. Примерами таких инструкций являются: значение*local_variable*, RETURN, READTEXT и выберите без запроса инструкции, такие как SELECT GETDATE() или SELECT **"***общего текстового* **'**.  
  
 Инструкции, которые осуществляют присвоение в запросе или используют RETURN в наборе запроса @@ROWCOUNT значение, число строк, задействованных или считанных запросом, например: ВЫБЕРИТЕ*local_variable* = c1 FROM t1.  
  
 Набор инструкций языка DML обработки данных @@ROWCOUNT значение, количество строк, затронутых запросом и возвращают это значение клиенту. DML-инструкции могут не отправлять строки клиенту.  
  
 Инструкции DECLARE CURSOR и FETCH значение @@ROWCOUNT значение 1.  
  
 Инструкции EXECUTE сохраняют предыдущих @@ROWCOUNT.  
  
 Операторы, такие как использование, ЗАДАЙТЕ \<параметр >, DEALLOCATE CURSOR, CLOSE CURSOR, BEGIN TRANSACTION или COMMIT TRANSACTION присваивают параметру ROWCOUNT значение 0.  
  
 Скомпилированных в собственном коде хранимые процедуры сохраняют предыдущих @@ROWCOUNT. [!INCLUDE[tsql](../../includes/tsql-md.md)]инструкции в хранимых процедурах, скомпилированных в собственном коде, не устанавливайте@ROWCOUNT. Дополнительные сведения см. в разделе [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример выполняет инструкцию `UPDATE` и использует `@@ROWCOUNT` для определения того, были ли изменены строки.  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee   
SET JobTitle = N'Executive'  
WHERE NationalIDNumber = 123456789  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were updated';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SET ROWCOUNT &#40; Transact-SQL &#41;](../../t-sql/statements/set-rowcount-transact-sql.md)  
  
  

