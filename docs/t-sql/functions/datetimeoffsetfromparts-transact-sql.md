---
title: "DATETIMEOFFSETFROMPARTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
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
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs: TSQL
helpviewer_keywords: DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1c8a5f8bea3bf6ca97e0f7b4a35f8f78315716df
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает **datetimeoffset** значение для указанной даты и времени и с указанным смещением и точностью.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
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
  
*минуты*  
Целочисленное выражение, задающее минуты.
  
*секунд*  
Целочисленное выражение, задающее секунды.
  
*доли секунды*  
Целочисленное выражение, задающее доли секунд.
  
*hour_offset*  
Целочисленное выражение, задающее часть смещения часового пояса в часах.
  
*minute_offset*  
Целочисленное выражение, задающее часть смещения часового пояса в минутах.
  
*precision*  
Целочисленный литерал, указывающее точность **datetimeoffset** возвращаемого значения.
  
## <a name="return-types"></a>Возвращаемые типы
**DateTimeOffset (** *точности* **)**
  
## <a name="remarks"></a>Замечания  
**DATETIMEOFFSETFROMPARTS** возвращает полностью инициализированное **datetimeoffset** тип данных. Аргументы смещения представляют смещение часового пояса. Если аргументы смещения пропущены, то предполагается, что смещение часового пояса равно 00:00, то есть отсутствует. Если аргументы смещения указаны, то должны присутствовать оба аргумента, причем оба должны быть или положительными, или отрицательными. Если *minute_offset* указан без *hour_offset*, возникает ошибка. Если другие аргументы недопустимы, также возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL. Однако если *точности* аргумент имеет значение null, то возникает ошибка.
  
*Дроби* зависит от аргумента *точности* аргумент. Например если *точности* равна 7, то каждая дробная часть представляет 100 наносекунд; Если *точности* — 3, то каждая дробная часть представляет миллисекунду. Если значение *точности* равно нулю, то значение *дроби* также должно быть равно нулю; в противном случае возникает ошибка.
  
Для серверов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и выше данная функция может быть удаленной. Данная функция не может быть удаленной для серверов с версией ниже [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Простой пример без долей секунд  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>Б. Пример с долями секунд  
В следующем примере показано использование *дроби* и *точности* параметры:
1.   Когда *дроби* имеет значение 5 и *точности* имеет значение 1, то значение *дробей* представляет 5/10 секунды.  
1.   При *дроби* имеет значение 50 и *точности* имеет значение 2, то значение *дроби* представляет 50 и 100 доли секунды.  
1.   Когда *дроби* имеет значение 500 и *точности* имеет значение 3, то значение *дроби* представляет 500/1000 секунды.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[datetimeoffset (Transact-SQL)](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[В ЧАСОВОМ ПОЯСЕ &#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


