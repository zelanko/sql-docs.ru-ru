---
title: "DATEPART (Transact-SQL) | Документы Microsoft"
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
- DATEPART_TSQL
- DATEPART
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], DATEPART
- dateparts [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
- dateparts [SQL Server], datepart
- comparing dates times [SQL Server]
- DATEPART function [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 15f1a5bc-4c0c-4c48-848d-8ec03473e6c1
caps.latest.revision: 57
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 05547f2dd50d7f130438d6a07b6952b8c29ec816
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="datepart-transact-sql"></a>DATEPART (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает целое число, представляющее указанную *datepart* указанного *даты*.
  
Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATEPART ( datepart , date )  
```  
  
## <a name="arguments"></a>Аргументы  
*часть_даты*  
— Это часть *даты* (значение даты или времени) для которого **целое** будут возвращены. В следующей таблице перечислены все допустимые *datepart* аргументы. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
|*часть_даты*|Сокращения|  
|---|---|
|**год**|**гг**, **гггг**|  
|**квартал**|**б**, **q**|  
|**месяц**|**мм**, **m**|  
|**день года**|**dy**, **y**|  
|**день**|**дд**, **d**|  
|**Неделя**|**нед**, **ww**|  
|**день недели**|**хранилища данных**|  
|**час**|**чч**|  
|**минуты**|**mi, n**|  
|**второй**|**SS**, **s**|  
|**миллисекунды**|**MS**|  
|**микросекунды**|**MCS**|  
|**наносекундных**|**NS**|  
|**TZoffset**|**TZ**|  
|**ISO_WEEK**|**isowk**, **isoww**|  
  
*date*  
Выражение, которое разрешается к **время**, **даты**, **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение. *Дата* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двух цифр года см. в разделе [Настройка two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
Каждый *datepart* и его краткие формы возвращают одинаковое значение.
  
Возвращаемое значение зависит от языка среды, задаваемого с помощью [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) и [Настройка параметра конфигурации сервера язык по умолчанию](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) входа. Если *даты* представляет собой строку литерала для некоторых форматов, возвращаемое значение зависит от формата, заданного с помощью [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md). Инструкция SET DATEFORMAT не влияет на возвращаемое значение, если дата представляется выражением столбца типа данных даты или времени.
  
В следующей таблице перечислены все *datepart* аргументы с соответствующими возвращаемые значения для инструкции `SELECT DATEPART(datepart,'2007-10-30 12:15:32.1234567 +05:10')`. Тип данных *даты* аргумент **datetimeoffset(7)**. **Наносекундных***datepart* возвращают значение имеет масштаб 9 (. 123456700) и две последние позиции всегда 00.
  
|*часть_даты*|Возвращаемое значение|  
|---|---|
|**год, гггг, гг**|2007 г.|  
|**Квартал "," б "," q**|4|  
|**месяц, mm, m**|10|  
|**DayOfYear dy, y**|303|  
|**день "," dd "," d**|30|  
|**Неделя, нед, ww**|45|  
|**день недели, хранилища данных**|1|  
|**час, hh**|12|  
|**минуты, n**|15|  
|**Во-вторых, ss, s**|32|  
|**миллисекунды, мс**|123|  
|**микросекунды mcs**|123456|  
|**наносекундных ns**|123456700|  
|**TZoffset tz**|310|  
  
## <a name="week-and-weekday-datepart-arguments"></a>Аргументы функции datepart недели и дня
Когда *datepart* — **недели** (**нед**, **ww**) или **дня недели** (**dw**), возвращаемое значение зависит от значения, которое устанавливается с помощью [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
1 января любого года определяет начальное число для **недели***datepart*, например: DATEPART (**нед**, "1 января *xxx*x') = 1, где *xxxx* любой год.
  
В следующей таблице перечислены возвращаемое значение для **недели** и **дня недели***datepart* для ' 2007-04-21' для каждого аргумента функции SET DATEFIRST. 1 января 2007 г. — первый понедельник в году. 21 апреля 2007 г. — суббота. SET DATEFIRST 7, воскресенье задается по умолчанию для региональных настроек «Английский (США)» Английский язык.
  
|SET DATEFIRST<br /><br /> аргумент|week<br /><br /> возвращаемое|weekday<br /><br /> возвращаемое|  
|---|---|---|
|1|16|6|  
|2|17|5|  
|3|17|4|  
|4|17|3|  
|5|17|2|  
|6|17|1|  
|7|16|7|  
  
## <a name="year-month-and-day-datepart-arguments"></a>Аргументы функции datepart, отображающие год, месяц и день даты  
Значения, которые были возвращены DATEPART (**года**, *даты*), DATEPART (**месяц**, *даты*) и DATEPART (**день** , *даты*) имеют такие же, как возвращаемые функциями [года](../../t-sql/functions/year-transact-sql.md), [месяц](../../t-sql/functions/month-transact-sql.md), и [день](../../t-sql/functions/day-transact-sql.md), f соответственно.
  
## <a name="isoweek-datepart"></a>ISO_WEEK datepart  
Стандарт ISO 8601 включает в себя систему отсчета дней и недель ISO. Каждая неделя приписывается тому году, в котором находится ее четверг. Например, 1-я неделя 2004 г. (2004W01) считается с понедельника 29 декабря 2003 г. по воскресенье 4 января 2004 г. Наибольшее число недель в году может составлять 52 или 53. Этот стиль нумерации обычно используется в странах и регионах Европы, но редко в других странах.
  
Система отсчета недель в разных странах и регионах может не совпадать со стандартом ISO. Как показано в следующей таблице, существует как минимум шесть методов отсчета:
  
|Первый день недели|Содержание первой недели года|Двойное присвоение недель|Применяется в:|  
|---|---|---|---|
|Воскресенье|1 января,<br /><br /> Первая суббота,<br /><br /> 1–7 дней года|Да|United States|  
|Понедельник|1 января,<br /><br /> Первое воскресенье,<br /><br /> 1–7 дней года|Да|Большинство стран Европы, а также Великобритания|  
|Понедельник|4 января<br /><br /> Первый четверг<br /><br /> 4 — 7 дней года|Нет|ISO 8601, Норвегия и Швеция|  
|Понедельник|7 января<br /><br /> Первый понедельник<br /><br /> 7 дней года|Нет||  
|Среда|1 января,<br /><br /> Первый вторник,<br /><br /> 1–7 дней года|Да||  
|Суббота|1 января,<br /><br /> Первая пятница,<br /><br /> 1–7 дней года|Да||  
  
## <a name="tzoffset"></a>TZoffset  
**TZoffset** (**tz**) возвращается как число минут (со знаком). В результате выполнения представленной ниже инструкции выдается значение временного смещения 310 минут.
  
```sql
SELECT DATEPART (TZoffset, '2007-05-10  00:00:01.1234567 +05:10');  
```  
Значение TZoffset отображается следующим образом:
- Для datetime2 и datetimeoffset TZoffset Возвращает смещение времени в минутах, где смещение datetime2 всегда равно 0 минут.
- Для типов данных, которые могут быть неявно преобразованы datetimeoffset или datetime2, за исключением других типов данных даты и времени Возвращает смещение времени в минутах.
- Параметры всех типов приведет к ошибке.
  
  
## <a name="smalldatetime-date-argument"></a>Аргумент даты типа smalldatetime  
Когда *даты* — [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), секунд возвращается значение 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-a-date-argument"></a>Возвращается значение по умолчанию для аргумента функции datepart, который отличен от даты  
Если тип данных *даты* аргумента не указанный *datepart*, значение по умолчанию для этого *datepart* будет возвращаться только в том случае, если указан литерал для *даты*.
  
Например, по умолчанию год месяц день для любого **даты** 1900-01-01 имеет тип данных. Следующая инструкция содержит аргументы компонентов даты для *datepart*, аргумент времени для *даты*и возвращает `1900, 1, 1, 1, 2`.
  
```sql
SELECT DATEPART(year, '12:10:30.123')  
    ,DATEPART(month, '12:10:30.123')  
    ,DATEPART(day, '12:10:30.123')  
    ,DATEPART(dayofyear, '12:10:30.123')  
    ,DATEPART(weekday, '12:10:30.123');  
```  
  
Если *даты* указано как переменная или столбец таблицы и данные, тип для переменной или столбце у указанного *datepart*, возвращается ошибка 9810. Следующий пример кода заканчивается ошибкой из-за год даты не является допустимым для **время** тип данных, объявленного для переменной  *@t* .
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATEPART(year, @t);  
```  
  
## <a name="fractional-seconds"></a>Доли секунды
Отображение долей секунд производится, как показано в следующих инструкциях:
  
```sql
SELECT DATEPART(millisecond, '00:00:01.1234567'); -- Returns 123  
SELECT DATEPART(microsecond, '00:00:01.1234567'); -- Returns 123456  
SELECT DATEPART(nanosecond,  '00:00:01.1234567'); -- Returns 123456700  
```  
  
## <a name="remarks"></a>Замечания  
Функция DATEPART может использоваться в предложениях WHERE, HAVING, GROUP BY и ORDER BY, а также при составлении списка выбора.
  
В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], функция DATEPART неявно приводит строковые литералы в качестве **datetime2** типа. Это означает, что DATEPART не поддерживает формат ГЧМ (год, число, месяц) при передаче даты в виде строки. Необходимо явно привести строку к **datetime** или **smalldatetime** тип, используемый формат ГДМ.
  
## <a name="examples"></a>Примеры  
В ходе выполнения представленного ниже примера производится отображение значения базового года отсчета. Значение базового года используется при расчетах, связанных с датами. В следующем примере дата указана как число. Обратите внимание на то, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует 0 как 1 января 1900 г.
  
```sql
SELECT DATEPART(year, 0), DATEPART(month, 0), DATEPART(day, 0);  
-- Returns: 1900    1    1 */  
```  
  
В следующем примере возвращается значение дня даты `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (day,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`--------`
  
 `20`  
  
Следующий пример возвращает компонент года даты `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (year,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`--------`
  
 `1974`  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

