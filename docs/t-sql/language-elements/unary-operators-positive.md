---
title: "+ (Унарный плюс) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- + (positive)
- +
- positive
dev_langs:
- TSQL
helpviewer_keywords:
- + (positive operator)
- positive operator (+)
- positive values [SQL Server]
ms.assetid: 0f31c5cc-3078-4f6a-9870-7eb1a98053fb
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a0e451cc1e4341d7e516733ab8d82efe09b1be7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="unary-operators---positive"></a>Унарные операторы — положительный результат
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение числового выражения (унарный оператор). Унарные операторы выполняют операцию только на одном выражении любого типа данных из категории числовых типов данных.   
  
|Оператор|Значение|  
|--------------|-------------|  
|[+ (положительное значение)](../../t-sql/language-elements/unary-operators-positive.md)|Числовое значение положительно.|  
|[- (отрицательное значение)](../../t-sql/language-elements/unary-operators-negative.md)|Числовое значение отрицательно.|  
|[~ (Побитовое не)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Возвращает поразрядное дополнение числа.|  
  
 Операторы + (знак «плюс») и - (знак «минус») можно использовать в любом выражении любого типа данных из категории числовых типов данных. Оператор ~ (побитовое НЕ) можно использовать только в выражениях любого типа данных из категории целочисленных типов данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
+ numeric_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) какой-либо один из данных типов в категории числовых типов данных, за исключением **datetime** и **smalldatetime** типов данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *numeric_expression*.  
  
## <a name="remarks"></a>Замечания  
 Хотя оператор унарного сложения может стоять перед любым числовым выражением, он не выполняет никаких действий со значением, полученным в результате вычисления выражения. В частности, оно не вернет положительное значение, если значение выражения отрицательно. Для получения положительного значения из отрицательного значения выражения, используйте [ABS](../../t-sql/functions/abs-transact-sql.md) функции.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-a-variable-to-a-positive-value"></a>A. Присваивание переменной положительного значения  
 В следующем примере производится присваивание переменной положительного значения.  
  
```  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = +123.45;  
SELECT @MyNumber;  
GO  
```  
  
 Результирующий набор:  
  
```  
-----------   
123.45            
  
(1 row(s) affected)  
```  
  
### <a name="b-using-the-unary-plus-operator-with-a-negative-value"></a>Б. Использование оператора «унарный плюс» с отрицательными значениями  
 Следующий пример показывает, как унарное сложение используется с отрицательными значениями и как с ними же используется функция ABS(). Функция ABS возвращает положительное значение выражения, а унарное сложение никак не влияет на него.  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = -5;  
SELECT +@Num1, ABS(@Num1);  
GO  
```  
  
 Результирующий набор:  
  
```  
----------- -----------  
-5          5  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [ABS &#40; Transact-SQL &#41;](../../t-sql/functions/abs-transact-sql.md)  
  
  

