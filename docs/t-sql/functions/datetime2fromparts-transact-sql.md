---
title: "DATETIME2FROMPARTS (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/29/2017
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
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ce109671228e82bc0f02e9920b2ef98c9bbcdb83
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает значение **datetime2**, соответствующее указанной дате и времени с заданной точностью.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Аргументы  
*year*  
Целочисленное выражение, задающее год.
  
*month*  
Целочисленное выражение, задающее месяц.
  
*day*  
Целочисленное выражение, задающее день.
  
 *hour*  
Целочисленное выражение, задающее часы.
  
*minute* Целочисленное выражение, задающее минуты.
  
*секунд*  
Целочисленное выражение, задающее секунды.
  
*fractions*  
Целочисленное выражение, задающее доли секунд.
  
*precision*  
Целочисленное литеральное значение, определяющее точность возвращаемого значения **datetime2**.
  
## <a name="return-types"></a>Типы возвращаемых данных
**datetime2(** *precision* **)**
  
## <a name="remarks"></a>Remarks  
**DATETIME2FROMPARTS** возвращает полностью инициализированное значение **datetime2**. Если аргументы являются недопустимыми, то возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL. Однако если аргумент *precision* равен NULL, то возникает ошибка.
  
Аргумент *fractions* зависит от аргумента *precision*. Например, если значение *precision* равно 7, то каждая дробная часть представляет 100 наносекунд; если значение *precision* равно 3, то каждая дробная часть представляет миллисекунду. Если значение *precision* равно нулю, то значение *fractions* также должно быть равно нулю, иначе возникает ошибка.
  
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
В приведенном ниже примере показано использование параметров *fractions* и *precision*.
  
1.  Если параметр *fractions* имеет значение 5, а параметр *precision* — значение 1, то значение параметра *fractions* представляет 5/10 секунды.  
  
2.  Если параметр *fractions* имеет значение 50, а параметр *precision* — значение 2, то значение параметра *fractions* представляет 50/100 секунды.  
  
3.  Если параметр *fractions* имеет значение 500, а параметр *precision* — значение 3, то значение параметра *fractions* представляет 500/1000 секунды.  
  
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
  
## <a name="see-also"></a>См. также раздел
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  

