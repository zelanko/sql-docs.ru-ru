---
title: "ROUND (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROUND_TSQL
- ROUND
dev_langs: TSQL
helpviewer_keywords:
- rounding expressions
- ROUND function [Transact-SQL]
ms.assetid: 23921ed6-dd6a-4c9e-8c32-91c0d44fe4b7
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: e9cb05c7f0b00f93f2602e114de2b502b8be0213
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="round-transact-sql"></a>ROUND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает числовое значение, округленное до указанной длины или точности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ROUND ( numeric_expression , length [ ,function ] )  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ROUND (numeric_expression , length )  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) точных числовых или приблизительных числовых типа данных, за исключением **бит** тип данных.  
  
 *length*  
 Точность, до которой *numeric_expression* должно быть округлено. *Длина* должен быть выражением типа **tinyint**, **smallint**, или **int**. Когда *длина* является положительным числом *numeric_expression* округляется до числа десятичных разрядов, заданные *длина*. Когда *длина* является отрицательным числом, *numeric_expression* округляется слева от десятичной запятой, в соответствии с *длина*.  
  
 *function*  
 Тип выполняемой операции. *функция* должно быть **tinyint**, **smallint**, или **int**. Когда *функция* опущен или имеет значение 0 (по умолчанию), *numeric_expression* округляется. Если значение, отличное от указано значение 0, *numeric_expression* усекается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает следующие типы данных.  
  
|Результат выражения|Возвращаемый тип|  
|-----------------------|-----------------|  
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**ssNoversion**|**int**|  
|**bigint**|**bigint**|  
|**десятичное число** и **числовое** категории (p, s)|**Decimal (p, s)**|  
|**Money** и **smallmoney** категории|**money**|  
|**число с плавающей запятой** и **реальные** категории|**float**|  
  
## <a name="remarks"></a>Замечания  
 Функция ROUND всегда возвращает значение. Если *длина* является отрицательным или больше, чем количество цифр перед десятичной запятой, ROUND возвращает 0.  
  
|Пример|Результат|  
|-------------|------------|  
|ROUND (748,58, -4)|0|  
  
 ROUND возвращает округленное *numeric_expression*, независимо от типа данных, когда *длина* является отрицательным числом.  
  
|Примеры|Результат|  
|--------------|------------|  
|ROUND (748,58, -1)|750.00|  
|ROUND (748,58, -2)|700.00|  
|ROUND(748.58, -3)|В результате возникает арифметическое переполнение, так как для значения 748,58 по умолчанию используется тип decimal (5,2), который не позволяет вернуть значение 1000.|  
|Чтобы округлить результат до четырех цифр, измените тип данных на входе. Например:<br /><br /> `SELECT ROUND(CAST (748.58 AS decimal (6,2)),-3);`|1000.00|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-round-and-estimates"></a>A. Использование функции ROUND и приближений  
 Следующий пример показывает два выражения, которые демонстрируют, используя `ROUND`, что последний знак всегда является приближением.  
  
```  
SELECT ROUND(123.9994, 3), ROUND(123.9995, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -----------  
123.9990    124.0000      
```  
  
### <a name="b-using-round-and-rounding-approximations"></a>Б. Использование функции ROUND и округляющих аппроксимаций  
 В следующем примере показаны округление и аппроксимация.  
  
```  
SELECT ROUND(123.4545, 2), ROUND(123.45, -2);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ----------
123.45    100.00
```
  
### <a name="c-using-round-to-truncate"></a>В. Использование функции ROUND для усечения  
 В следующем примере используются две инструкции `SELECT` для демонстрации различия между округлением и усечением. Первая инструкция округляет результат. Вторая инструкция усекает результат.  
  
```  
SELECT ROUND(150.75, 0);  
GO  
SELECT ROUND(150.75, 0, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
151.00  
  
(1 row(s) affected)  
  
--------  
150.00  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-round-and-estimates"></a>Г. Использование функции ROUND и приближений  
 Следующий пример показывает два выражения, которые демонстрируют, используя `ROUND`, что последний знак всегда является приближением.  
  
```  
SELECT ROUND(123.994999, 3), ROUND(123.995444, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ---------
123.995000    123.995444
```
  
## <a name="see-also"></a>См. также:  
 [Функция CEILING &#40; Transact-SQL &#41;](../../t-sql/functions/ceiling-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Функция FLOOR &#40; Transact-SQL &#41;](../../t-sql/functions/floor-transact-sql.md)   
 [Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

