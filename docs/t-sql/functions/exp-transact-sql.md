---
title: "EXP (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXP_TSQL
- EXP
dev_langs:
- TSQL
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 5a9b8c52-6fb6-4e33-8b02-a878785b2f51
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c50757291a8f1fc3d58d8a9a131c4a24aa79a008
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает значение экспоненты заданного **float** выражение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *float_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **float** или типа, который может быть неявно преобразован в **float**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **float**  
  
## <a name="remarks"></a>Замечания  
 Константа **e** (2,718281...) является основанием натуральных логарифмов.  
  
 Экспонента числа является константой **e** степени числа. Например, EXP(1,0) = e^1,0 = 2,71828182845905, а EXP(10) = e^10 = 22026,4657948067.  
  
 Экспонента натурального логарифма числа — это номер сам: EXP (ЖУРНАЛА (*n*)) =  *n* . Натуральный логарифм экспоненты числа также является числом сам: ЖУРНАЛА (EXP (*n*)) =  *n* .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-finding-the-exponent-of-a-number"></a>A. Вычисление экспонента числа  
 В ходе выполнения следующего примера объявляется переменная и возвращается ее экспонента (`10`) с текстовым описанием.  
  
```  
DECLARE @var float  
SET @var = 10  
SELECT 'The EXP of the variable is: ' + CONVERT(varchar,EXP(@var))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------------------------------  
The EXP of the variable is: 22026.5  
(1 row(s) affected)  
```  
  
### <a name="b-finding-exponentials-and-natural-logarithms"></a>Б. Нахождение экспонентов и натуральных логарифмов  
 Представленный ниже пример возвращает значение экспоненты, взятой от натурального логарифма `20`, а также значение натурального логарифма, взятого от экспоненты `20`. Так как указанные функции являются обратными друг для друга, то в обоих случаях возвращается значение `20`.  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------- ----------------------  
20                     20  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-finding-the-exponent-of-a-number"></a>В. Вычисление экспонента числа  
 В следующем примере возвращается значение экспоненты заданного значения (`10`).  
  
```  
SELECT EXP(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------  
22026.4657948067  
```  
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>Г. Нахождение экспоненциального значения и натуральных логарифмов  
 Представленный ниже пример возвращает значение экспоненты, взятой от натурального логарифма `20`, а также значение натурального логарифма, взятого от экспоненты `20`. Так как указанные функции являются обратными друг для друга, то в обоих случаях возвращается значение `20`.  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------- -----------------  
20                  20  
```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [ЖУРНАЛ &#40; Transact-SQL &#41;](../../t-sql/functions/log-transact-sql.md)   
 [LOG10 &#40; Transact-SQL &#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  


