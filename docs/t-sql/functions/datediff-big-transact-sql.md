---
title: "DATEDIFF_BIG (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEDIFF_BIG
- DATEDIFF_BIG_TSQL
helpviewer_keywords:
- DATEDIFF_BIG function [SQL Server]
- dates [SQL Server]. functions
- date and time [SQL Server], DATEDIFF_BIG
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 19ac1693-3cfa-400d-bf83-20a9cb46599a
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 08f27953aac5fa36f1b38e243d8465f57458dafe
ms.contentlocale: ru-ru
ms.lasthandoff: 10/12/2017

---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Возвращает число (длинное целое число со знаком) указанного *datepart* пересекаемых границ между указанным *startdate* и *enddate*.
  
Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Аргументы  
*часть_даты*  
— Это часть *startdate* и *enddate* , указывающий тип пересекаемых границ. В следующей таблице перечислены все допустимые *datepart* аргументы. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
|*часть_даты*|Сокращения|  
|---|---|
|**год**|**yy, yyyy**|  
|**квартал**|**б, q**|  
|**месяц**|**mm, m**|  
|**день года**|**dy, y**|  
|**день**|**дд, d**|  
|**Неделя**|**нед ww**|  
|**час**|**чч**|  
|**минуты**|**mi, n**|  
|**второй**|**ss, s**|  
|**миллисекунды**|**MS**|  
|**микросекунды**|**MCS**|  
|**наносекундных**|**NS**|  
  
*startdate*  
Выражение, которое разрешается к **время**, **даты**, **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение. *Дата* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом. *StartDate* вычитается из *enddate*.  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двух цифр года см. в разделе [Настройка two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*Дата окончания*  
В разделе *startdate*.
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Подпись   
        **bigint**  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает число (со знаком bigint) заданных границ, пересеченных между указанной startdate и enddate.
-   Каждый *datepart* и его краткие формы возвращают одинаковое значение.  
  
Если возвращаемое значение вне допустимого диапазона для **bigint** (-9223372036854775808 до 9223372036854775807), возвращается сообщение об ошибке. Для **миллисекунды**, Максимальная разница между *startdate* и *enddate* — 24 дня, 20 часов, 31 минута и 23,647 секунд. Для **второй**, Максимальная разница составляет 68 лет.
  
Если *startdate* и *enddate* оба назначаются только значение времени и *datepart* времени *datepart*, возвращается значение 0.
  
Компонент смещения часового пояса *startdate* или *endate* не используется в вычислении возвращаемого значения.
  
Поскольку [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) имеет точность до минуты, когда **smalldatetime** значение используется для *startdate* или *enddate*, секунд и миллисекунды всегда равны 0, в возвращаемом значении.
  
Если только значение времени будет назначен переменной типа данных date, отсутствует часть даты значение по умолчанию: 1900-01-01. Значение типа date присвоено переменной типа данных даты и времени, если только недостающей части времени значение по умолчанию: 00:00:00. Если параметр *startdate* или *enddate* имеют только время, а другие — только часть даты, времени отсутствует и частей даты устанавливаются значения по умолчанию.
  
Если *startdate* и *enddate* имеют разные типы данных даты и один имеет больше частей времени или другого точность в долях секунды, значениям недостающих частей другого устанавливаются в значение 0.
  
## <a name="datepart-boundaries"></a>границы DatePart
Следующие операторы с одинаковым *startdate* и тот же *endate*. Указанные даты являются соседними, а временная разница между ними составляет 0,0000001 секунды. Разница между *startdate* и *endate* в каждой инструкции пересекает одну календарную или временную границу его *datepart*. Каждое выражение возвращает значение 1. Если в этом примере указаны различные года и оба *startdate* и *endate* находятся в пределах одной календарной недели, возвращаемое значение для **недели** будет равно 0.

```sql
SELECT DATEDIFF_BIG(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Замечания  
DATEDIFF_BIG можно использовать в списке выбора, предложениях WHERE, HAVING, GROUP BY и ORDER BY.
  
DATEDIFF_BIG неявно приводит строковые литералы в качестве **datetime2** типа. Это означает, что DATEDIFF_BIG не поддерживает формат ГДМ при передаче даты в виде строки. Необходимо явно привести строку к **datetime** или **smalldatetime** тип, используемый формат ГДМ.
  
Указание SET DATEFIRST не оказывает влияния на DATEDIFF_BIG. DATEDIFF_BIG всегда использует воскресенье первым днем недели, чтобы убедиться, что функция является детерминированной.
  
## <a name="examples"></a>Примеры  
В следующих примерах выражения различного типа используются как аргументы для *startdate* и *enddate* параметров.
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Указание столбцов в качестве начальной и конечной даты  
В следующем примере подсчитывается количество границ дней, пересекаемых между двумя датами, указанных в столбцах таблицы.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF_BIG(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
Многие Дополнительные примеры см. в разделе тесно связанных примеры в [DATEDIFF &#40; Transact-SQL &#41; ](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Функция DATEDIFF &#40; Transact-SQL &#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  

