---
description: DATETIME2FROMPARTS (Transact-SQL)
title: DATETIME2FROMPARTS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 568c6334506b3b8cc2d186d9d6ad6ee48fa773ac
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116803"
---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Эта функция возвращает значение **datetime2** для указанных аргументов даты и времени. Точность возвращаемого значения определяется аргументом precision.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

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
Целочисленное выражение, задающее дробное значение секунд.
  
*precision*  
Целочисленное выражение, которое определяет точность значения **datetime2**, возвращаемого функцией `DATETIME2FROMPARTS`.
  
## <a name="return-types"></a>Типы возвращаемых данных
**datetime2(** *precision* **)**
  
## <a name="remarks"></a>Комментарии  
Функция `DATETIME2FROMPARTS` возвращает полностью инициализированное значение типа **datetime2**. Функция `DATETIME2FROMPARTS` вызывает ошибку, если по крайней мере один обязательный аргумент имеет недопустимое значение. Функция `DATETIME2FROMPARTS` возвращает NULL, если по крайней мере один обязательный аргумент имеет значение NULL. Однако если аргумент *precision* имеет значение NULL, функция `DATETIME2FROMPARTS` вызывает ошибку.

Аргумент *fractions* зависит от аргумента *precision*. Например, если значение *precision* равно 7, то каждая дробная часть представляет 100 наносекунд; если значение *precision* равно 3, то каждая дробная часть представляет миллисекунду. Если значение *precision* равно нулю, то значение *fractions* также должно быть равно нулю. В противном случае функция `DATETIME2FROMPARTS` вызовет ошибку.
  
Эта функция поддерживает удаленное взаимодействие с серверами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и более поздних версий. Она не поддерживает удаленное взаимодействие с серверами версий ниже [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Примеры  
  
### <a name="a-an-example-without-fractions-of-a-second"></a>A. Пример без долей секунды  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>Б. Пример с долями секунд  
В этом примере показано использование параметров *fractions* и *precision*:
  
1.  Если параметр *fractions* имеет значение 5, а параметр *precision* — значение 1, то значение параметра *fractions* представляет 5/10 секунды.  
  
2.  Если параметр *fractions* имеет значение 50, а параметр *precision* — значение 2, то значение параметра *fractions* представляет 50/100 секунды.  
  
3.  Если параметр *fractions* имеет значение 500, а параметр *precision* — значение 3, то значение параметра *fractions* представляет 500/1000 секунды.  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
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
  
## <a name="see-also"></a>См. также
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  

