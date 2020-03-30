---
title: CLOSE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 63234f9f337bd6427c4c5ed33c146e2ed3a714c9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67950329"
---
# <a name="close-transact-sql"></a>CLOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Закрывает открытый курсор, высвобождая текущий результирующий набор и снимая блокировки курсоров для строк, на которых установлен курсор. Инструкция `CLOSE` оставляет структуры данных доступными для повторного открытия, но выборки и позиционированные обновления не разрешаются до повторного открытия курсора. Инструкция CLOSE должна выдаваться применительно к открытому курсору; `CLOSE` не применима к только что объявленным или уже закрытым курсорам.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>Аргументы  
 GLOBAL  
 Указывает, что аргумент *cursor_name* ссылается на глобальный курсор.  
  
 *cursor_name*  
 Имя открытого курсора. Когда имеются как глобальный, так и локальный курсор с именем *cursor_name*, то *cursor_name* указывает на глобальный курсор, если задано GLOBAL. В противном случае *cursor_name* указывает на локальный курсор.  
  
 *cursor_variable_name*  
 Имя переменной курсора, связанной с открытым курсором.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано правильное размещение инструкции `CLOSE` в процессе на основе курсора.  
  
```sql  
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
 [DEALLOCATE (Transact-SQL)](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [FETCH (Transact-SQL)](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN (Transact-SQL)](../../t-sql/language-elements/open-transact-sql.md)  
  
  
