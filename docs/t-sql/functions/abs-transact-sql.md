---
title: "ABS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
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
- ABS_TSQL
- ABS
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], positive
- values [SQL Server], absolute
- ABS function
- absolute positive value
ms.assetid: e2ea7a6d-3e2f-472c-afbc-437d3b835c03
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eed45893b664e79071d1b423f5d84977e11f5a24
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="abs-transact-sql"></a>ABS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Математическая функция, возвращающая абсолютное (положительное) значение указанного числового выражения. (`ABS` изменения отрицательные значения для положительных значений. `ABS`не влияет на ноль или положительные значения.)
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ABS ( numeric_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*numeric_expression*  
Выражение категории точного числового или приблизительного числового типа данных.
  
## <a name="return-types"></a>Типы возвращаемых значений  
Возвращает тот же тип, что и аргумент *numeric_expression*.
  
## <a name="examples"></a>Примеры  
В следующем примере показаны результаты применения функции `ABS` к трем различным числам.
  
```sql
SELECT ABS(-1.0), ABS(0.0), ABS(1.0);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---- ---- ----  
1.0  .0   1.0  
```  
  
Функция `ABS` может вызвать ошибку переполнения, если абсолютное значение числа больше наибольшего числа, которое может быть представлено указанным типом данных. Например, тип данных `int` может содержать только значения в пределах от `-2,147,483,648` до `2,147,483,647`. Расчет абсолютного значения для целого числа со знаком `-2,147,483,648` приводит к ошибке переполнения, поскольку его абсолютное значение превышает положительный диапазон для типа данных `int`.
  
```sql
DECLARE @i int;  
SET @i = -2147483648;  
SELECT ABS(@i);  
GO  
```  
  
Сообщение об ошибке:
  
«Сообщение 8115, уровень 16, состояние 2, строка 3».
  
«Арифметическое переполнение при преобразовании выражения к типу данных int».

  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[Встроенные функции (Transact-SQL)](../../t-sql/functions/functions.md)
  
  


