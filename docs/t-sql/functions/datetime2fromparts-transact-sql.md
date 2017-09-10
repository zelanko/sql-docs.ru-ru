---
title: "DATETIME2FROMPARTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4ad800c684bcf69a52828969ca816a135901280
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает **datetime2** значение для указанной даты и времени и с указанной точностью.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Аргументы  
*год*  
Целочисленное выражение, задающее год.
  
*месяц*  
Целочисленное выражение, задающее месяц.
  
*день*  
Целочисленное выражение, задающее день.
  
 *час*  
Целочисленное выражение, задающее часы.
  
*минуты* целочисленное выражение, задающее минуты.
  
*секунд*  
Целочисленное выражение, задающее секунды.
  
*доли секунды*  
Целочисленное выражение, задающее доли секунд.
  
*precision*  
Целочисленный литерал, указывающее точность **datetime2** возвращаемого значения.
  
## <a name="return-types"></a>Возвращаемые типы
**datetime2 (** *точности* **)**
  
## <a name="remarks"></a>Замечания  
**DATETIME2FROMPARTS** возвращает полностью инициализированное **datetime2** значение. Если аргументы являются недопустимыми, то возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL. Однако если *точности* аргумент имеет значение null, то возникает ошибка.
  
*Дроби* зависит от аргумента *точности* аргумент. Например если *точности* равна 7, то каждая дробная часть представляет 100 наносекунд; Если *точности* — 3, то каждая дробная часть представляет миллисекунду. Если значение *точности* равно нулю, то значение *дроби* также должно быть равно нулю; в противном случае возникает ошибка.
  
Для серверов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и выше данная функция может быть удаленной. Данная функция не может быть удаленной для серверов с версией ниже [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Простой пример без долей секунд  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>Б. Пример с долями секунд  
В следующем примере показано использование *дроби* и *точности* параметры:
  
1.  Когда *дроби* имеет значение 5 и *точности* имеет значение 1, то значение *дробей* представляет 5/10 секунды.  
  
2.  При *дроби* имеет значение 50 и *точности* имеет значение 2, то значение *дроби* представляет 50 и 100 доли секунды.  
  
3.  Когда *дроби* имеет значение 500 и *точности* имеет значение 3, то значение *дроби* представляет 500/1000 секунды.  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example-without-fractions-of-a-second"></a>В. Простой пример без долей секунд  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="d-example-with-fractions-of-a-second"></a>Г. Пример с долями секунд  
В следующем примере показано использование *дроби* и *точности* параметры:
1.  Когда *дроби* имеет значение 5 и *точности* имеет значение 1, то значение *дробей* представляет 5/10 секунды.  
1.   При *дроби* имеет значение 50 и *точности* имеет значение 2, то значение *дроби* представляет 50 и 100 доли секунды.  
1.   Когда *дроби* имеет значение 500 и *точности* имеет значение 3, то значение *дроби* представляет 500/1000 секунды.  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  


