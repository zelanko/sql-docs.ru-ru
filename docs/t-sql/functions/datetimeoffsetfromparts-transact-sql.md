---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5549f258e758cc91a228d5fee707120b57963d46
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает значение **datetimeoffset** для указанных даты и времени с указанными смещением и точностью.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
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
  
*minute*  
Целочисленное выражение, задающее минуты.
  
*секунд*  
Целочисленное выражение, задающее секунды.
  
*fractions*  
Целочисленное выражение, задающее доли секунд.
  
*hour_offset*  
Целочисленное выражение, задающее часть смещения часового пояса в часах.
  
*minute_offset*  
Целочисленное выражение, задающее часть смещения часового пояса в минутах.
  
*precision*  
Целочисленное литеральное значение, определяющее точность возвращаемого значения **datetimeoffset**.
  
## <a name="return-types"></a>Типы возвращаемых данных
**datetimeoffset(** *precision* **)**
  
## <a name="remarks"></a>Remarks  
**DATETIMEOFFSETFROMPARTS** возвращает полностью инициализированный тип данных **datetimeoffset**. Аргументы смещения представляют смещение часового пояса. Если аргументы смещения пропущены, то предполагается, что смещение часового пояса равно 00:00, то есть отсутствует. Если аргументы смещения указаны, то должны присутствовать оба аргумента, причем оба должны быть или положительными, или отрицательными. Если аргумент *minute_offset* указан без *hour_offset*, возникает ошибка. Если другие аргументы недопустимы, также возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL. Однако если аргумент *precision* равен NULL, то возникает ошибка.
  
Аргумент *fractions* зависит от аргумента *precision*. Например, если значение *precision* равно 7, то каждая дробная часть представляет 100 наносекунд; если значение *precision* равно 3, то каждая дробная часть представляет миллисекунду. Если значение *precision* равно нулю, то значение *fractions* также должно быть равно нулю, иначе возникает ошибка.
  
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
В приведенном ниже примере показано использование параметров *fractions* и *precision*.
1.   Если параметр *fractions* имеет значение 5, а параметр *precision* — значение 1, то значение параметра *fractions* представляет 5/10 секунды.  
1.   Если параметр *fractions* имеет значение 50, а параметр *precision* — значение 2, то значение параметра *fractions* представляет 50/100 секунды.  
1.   Если параметр *fractions* имеет значение 500, а параметр *precision* — значение 3, то значение параметра *fractions* представляет 500/1000 секунды.  
  
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
  
## <a name="see-also"></a>См. также раздел
[datetimeoffset (Transact-SQL)](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[AT TIME ZONE (Transact-SQL)](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


