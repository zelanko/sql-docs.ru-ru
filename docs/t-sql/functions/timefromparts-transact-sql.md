---
title: "TIMEFROMPARTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 43e6b8f2d234e0b2dd11299c56f1c6b9d0e06518
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Возвращает **время** значение в течение определенного времени и с указанной точностью.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Аргументы  
 *час*  
 Целочисленное выражение, задающее часы.  
  
 *минуты*  
 Целочисленное выражение, задающее минуты.  
  
 *секунд*  
 Целочисленное выражение, задающее секунды.  
  
 *доли секунды*  
 Целочисленное выражение, задающее доли секунд.  
  
 *precision*  
 Целочисленный литерал, указывающее точность **время** возвращаемого значения.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **время (** *точности* **)**  
  
## <a name="remarks"></a>Замечания  
 TIMEROMPARTS возвращает полностью инициализированное значение времени. Если аргументы недопустимы, то возникает ошибка. Если любой из параметров имеет значение NULL, возвращается NULL. Однако если *точности* аргумент имеет значение null, то возникает ошибка.  
  
 *Дроби* зависит от аргумента *точности* аргумент. Например если *точности* равна 7, то каждая дробная часть представляет 100 наносекунд; Если *точности* — 3, то каждая дробная часть представляет миллисекунду. Если значение *точности* равно нулю, то значение *дроби* также должно быть равно нулю; в противном случае возникает ошибка.  
  
 Данная функция может быть удаленной для серверов [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий. Она не может быть удаленной для серверов с версией ниже [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Простой пример без долей секунд  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>Б. Пример с долями секунд  
 В следующем примере показано использование *дроби* и *точности* параметры:  
  
1.  Когда *дроби* имеет значение 5 и *точности* имеет значение 1, то значение *дробей* представляет 5/10 секунды.  
  
2.  При *дроби* имеет значение 50 и *точности* имеет значение 2, то значение *дроби* представляет 50 и 100 доли секунды.  
  
3.  Когда *дроби* имеет значение 500 и *точности* имеет значение 3, то значение *дроби* представляет 500/1000 секунды.  
  
```tsql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example-without-fractions-of-a-second"></a>В. Простой пример без долей секунд  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="d-example-with-fractions-of-a-second"></a>Г. Пример с долями секунд  
 В следующем примере показано использование *дроби* и *точности* параметры:  
  
1.  Когда *дроби* имеет значение 5 и *точности* имеет значение 1, то значение *дробей* представляет 5/10 секунды.  
  
2.  При *дроби* имеет значение 50 и *точности* имеет значение 2, то значение *дроби* представляет 50 и 100 доли секунды.  
  
3.  Когда *дроби* имеет значение 500 и *точности* имеет значение 3, то значение *дроби* представляет 500/1000 секунды.  
  
```tsql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  
  


