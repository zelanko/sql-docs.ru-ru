---
title: "TIMEFROMPARTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: e7cb7497251a0a61cff9f71c07d3c5d9e9028d5d
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

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
  


