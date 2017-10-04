---
title: "Остаток от деления (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- modulo
- '% (Modulo)'
- MOD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: f93c662e-f405-486e-bf23-a2d03907b5bd
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b417bbca6135db2f4ca6279bb9aac75d9d6f328
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="modulo-transact-sql"></a>Остаток от деления (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает остаток от деления одного числа на другое.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Аргументы  
 *dividend*  
 Делимое числовое выражение. *делимое* должен быть допустимым [выражение](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных в категорий целых или денежных типов, или **числовое** тип данных.  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. *делитель* должен быть любое допустимое выражение любого из типов данных в категорий целых или денежных типов, или **числовое** тип данных.  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов.  
  
## <a name="remarks"></a>Замечания  
 Можно использовать модулю в списке выбора инструкции SELECT с любым сочетанием имен столбцов, числовых констант или любым допустимым выражением целых или денежных данных введите категории или **числовое** данных тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example"></a>A. Простой пример  
 В следующем примере выполняется деление числа 38 на 5. Это приводит к 7 как целой части результата и показано, как остаток от деления возвращается число 3.  
  
```  
SELECT 38 / 5 AS Integer, 38 % 5 AS Remainder ;  
  
```  
  
### <a name="b-example-using-columns-in-a-table"></a>Б. Пример с использованием столбцов в таблице  
 Следующий пример возвращает код продукта, цену единицы модуля продукта и остаток от деления цены каждого продукта, преобразовывает к целому значению, в количество заказанных продуктов.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(100)ProductID, UnitPrice, OrderQty,  
   CAST((UnitPrice) AS int) % OrderQty AS Modulo  
FROM Sales.SalesOrderDetail;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example"></a>C: простой пример  
 В следующем примере показано результаты для `%` оператора, если деления 3 на 2.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) 3%2 FROM dimEmployee;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
1         
```  
  
## <a name="see-also"></a>См. также:  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [Остаток от деления равно &#40; Transact-SQL &#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



