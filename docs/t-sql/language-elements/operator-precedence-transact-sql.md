---
title: "Приоритет операторов (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], precedence
- operator precedence [Transact-SQL]
- order of operator execution [Transact-SQL]
- precedence [SQL Server], operators
ms.assetid: f04d2439-6fff-4e4c-801f-cc62faef510a
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: db0c7bd10a7d53f4de8fb5aedbe6f1cf3c9be42b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="operator-precedence-transact-sql"></a>Приоритет операторов (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Если сложное выражение содержит несколько операторов, порядок выполнения этих операторов определяется их приоритетом. Порядок исполнения может существенно повлиять на результирующее значение.  
  
 Уровни приоритета операторов показаны в следующей таблице. Оператор с более высоким уровнем выполняется прежде, чем оператор с более низким уровнем.  
  
|Level|Операторы|  
|-----------|---------------|  
|1|~ (побитовое НЕ)|  
|2|* (умножение), / (деление), % (остаток от деления)|  
|3|+ (Положительное), - (отрицательное), + (сложение), (+ объединение), - (вычитание), & (побитовое и), ^ (побитовое исключающее или), &#124; (Побитовый оператор или)|  
|4|=, >, \<, > =, < = <>,! =,! >,! < (операторы сравнения)|  
|5|NOT|  
|6|и|  
|7|ALL, ANY, BETWEEN, IN, LIKE, OR, SOME|  
|8|= (присваивание)|  
  
 Если два оператора в выражении имеют один и тот же уровень старшинства, они выполняются в порядке слева направо по мере их появления в выражении. Например, если выражение использует инструкцию `SET`, то оператор вычитания будет выполнен до оператора сложения.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 4 - 2 + 27;  
-- Evaluates to 2 + 27 which yields an expression result of 29.  
SELECT @MyNumber;  
```  
  
 Чтобы изменить приоритет операторов в выражении, следует использовать скобки. Вначале все выражение внутри скобок рассчитывается до получения одного значения, которое затем может быть использовано любым оператором за пределами скобок.  
  
 Например, если выражение использует инструкцию `SET`, то у оператора умножения более высокий приоритет, чем у оператора сложения. Поэтому он вычисляется первым, и результатом выражения будет `13`.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * 4 + 5;  
-- Evaluates to 8 + 5 which yields an expression result of 13.  
SELECT @MyNumber;  
```  
  
 В выражении с инструкцией `SET` скобки показывают, что сначала необходимо выполнить операцию сложения. Результатом выражения будет `18`.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + 5);  
-- Evaluates to 2 * 9 which yields an expression result of 18.  
SELECT @MyNumber;  
```  
  
 Если в выражении содержатся вложенные скобки, то сначала вычисляется результат наиболее глубоко вложенных скобок. В следующем примере показано использование вложенных скобок, в наиболее глубоко вложенных скобках записано выражение `5 - 3`. Результатом этого выражения будет `2`. После этого оператор сложения (`+`) добавляет к этому результату `4`. Это приводит к новому значению `6`. Наконец, `6` умножается на `2`, чтобы получить результат выражения `12`.  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + (5 - 3) );  
-- Evaluates to 2 * (4 + 2) which then evaluates to 2 * 6, and   
-- yields an expression result of 12.  
SELECT @MyNumber;  
```  
  
## <a name="see-also"></a>См. также:  
 [Логические операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  

