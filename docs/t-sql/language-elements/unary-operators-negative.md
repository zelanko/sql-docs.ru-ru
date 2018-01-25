---
title: "- (Отрицательное значение) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: negative
dev_langs: TSQL
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
- negative values
ms.assetid: d6c14d14-d379-403b-82db-c197ad58c896
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c2d561099b6208ad0057489efd27942e48882df9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="unary-operators---negative"></a>Унарные операторы - отрицательный результат
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает отрицательное значение числового выражения (унарный оператор). Унарные операторы выполняют операцию только на одном выражении любого типа данных из категории числовых типов данных.   
  
|Оператор|Значение|  
|--------------|-------------|  
|[+ (положительное значение)](../../t-sql/language-elements/unary-operators-positive.md)|Числовое значение положительно.|  
|[- (отрицательное значение)](../../t-sql/language-elements/unary-operators-negative.md)|Числовое значение отрицательно.|  
|[~ (побитовое НЕ)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Возвращает поразрядное дополнение числа.|  
  
 Операторы + (знак «плюс») и - (знак «минус») можно использовать в любом выражении любого типа данных из категории числовых типов данных. Оператор ~ (побитовое НЕ) можно использовать только в выражениях любого типа данных из категории целочисленных типов данных. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
- numeric_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любым из типов данных категории числовых типов данных, за исключением даты и времени категории.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *numeric_expression*, за исключением того, что неподписанный **tinyint** выражение со знаком для **smallint** результат.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-a-variable-to-a-negative-value"></a>A. Присваивание переменной отрицательного значения  
 Следующий пример присваивает переменной отрицательное значение.  
  
```  
USE tempdb;  
GO  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = -123.45;  
SELECT @MyNumber AS NegativeValue;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
NegativeValue  
---------------------------------------  
-123.45  
  
(1 row(s) affected)  
  
```  
  
### <a name="b-changing-a-variable-to-a-negative-value"></a>Б. Изменение значения переменной на отрицательное  
 Следующий пример изменяет значение переменной на отрицательное значение.  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = 5;  
SELECT @Num1 AS VariableValue, -@Num1 AS NegativeValue;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
VariableValue NegativeValue  
------------- -------------  
5             -5  
  
(1 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-negative-of-a-positive-constant"></a>В. Возвращает отрицательное положительное константы  
 В следующем примере возвращается отрицательное положительное константы.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - 17 FROM DimEmployee;  
```  
  
 Возвращает  
  
```  
-17  
```  
  
### <a name="d-returning-the-positive-of-a-negative-constant"></a>Г. Возвращает положительное отрицательная константа  
 В следующем примере возвращается положительное отрицательная константа.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) – ( - 17) FROM DimEmployee;  
```  
  
 Возвращает  
  
```  
17  
```  
  
### <a name="e-returning-the-negative-of-a-column"></a>Д. Возвращение отрицательного значения столбца  
 В следующем примере возвращается отрицательное `BaseRate` значение для каждого сотрудника в `dimEmployee` таблицы.  
  
```  
USE ssawPDW;  
  
SELECT - BaseRate FROM DimEmployee;  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

