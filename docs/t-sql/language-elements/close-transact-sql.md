---
title: "ЗАКРЫТЬ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE_TSQL
- CLOSE
dev_langs:
- TSQL
helpviewer_keywords:
- closing cursors
- cursors [SQL Server], closing
- CLOSE statement
ms.assetid: 21546874-97e3-4b93-970f-87c27f6b78c7
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7315b45fa3b13b96fa01c7833ed1370f72e4bab8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="close-transact-sql"></a>CLOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Закрывает открытый курсор, высвобождая текущий результирующий набор и снимая блокировки курсоров для строк, на которых установлен курсор. Инструкция CLOSE оставляет структуры данных доступными для повторного открытия, но выборки и позиционированные обновления не разрешаются до повторного открытия курсора. Инструкция CLOSE должна выдаваться применительно к открытому курсору; CLOSE не применима к только что объявленным или уже закрытым курсорам.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>Аргументы  
 GLOBAL  
 Указывает, что *cursor_name* ссылается на глобальный курсор.  
  
 *cursor_name*  
 Имя открытого курсора. Если существует как глобальный, так и локальный курсор с *cursor_name* , имя *cursor_name* ссылается на глобальный курсор при GLOBAL указанного; в противном случае — *cursor_name* ссылается на локальный курсор.  
  
 *cursor_variable_name*  
 Имя переменной курсора, связанной с открытым курсором.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано правильное размещение инструкции `CLOSE` в процессе на основе курсора.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT EmployeeID, Title FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Курсоры](../../relational-databases/cursors.md)   
 [Курсоры (Transact-SQL)](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCATE &#40; Transact-SQL &#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [FETCH &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [ОТКРЫТЬ &#40; Transact-SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  

