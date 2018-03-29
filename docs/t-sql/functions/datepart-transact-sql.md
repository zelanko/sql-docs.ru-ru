---
title: DATEPART (Transact-SQL) | Документация Microsoft
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: ''
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a972e0646d68620b915fe441e35ebfb617d06859
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datepart-transact-sql"></a>DATEPART (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает целое число — указанную аргументом *datepart* часть заданной вторым аргументом даты (*date*).
  
Общие сведения обо всех типах данных и функциях даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATEPART ( datepart , date )  
```  
  
## <a name="arguments"></a>Аргументы  
*datepart*  
Часть аргумента *date* (значение даты или времени), для которого будет возвращено **целое число**. В следующей таблице перечислены все допустимые значения аргумента *datepart*. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
|*datepart*|Сокращения|  
|---|---|
|**year**|**yy**, **yyyy**|  
|**quarter**|**qq**, **q**|  
|**month**|**mm**, **m**|  
|**dayofyear**|**dy**, **y**|  
|**day**|**dd**, **d**|  
|**week**|**wk**, **ww**|  
|**weekday**|**dw**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss**, **s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
|**TZoffset**|**tz**|  
|**ISO_WEEK**|**isowk**, **isoww**|  
  
*date*  
Это выражение, которое разрешается к значениям **time**, **date**, **smalldatetime**, **datetime**, **datetime2** или **datetimeoffset**. *date* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двузначном обозначении года см. в статье [Настройка параметра конфигурации сервера two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
Каждое выражение *datepart* и его краткие формы возвращают одно и то же значение.
  
Возвращаемое значение зависит от языка среды, задаваемого инструкцией [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md), и от [параметра конфигурации сервера "язык по умолчанию"](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) для имени для входа. Если значение *date* для некоторых форматов является строковым литералом, то тип возвращаемого значения зависит от формата, заданного с помощью функции [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md). Инструкция SET DATEFORMAT не влияет на возвращаемое значение, если date — выражение столбца типа данных date или time.
  
Ниже представлена таблица соответствия аргументов функции *datepart* и значений, возвращенных выражением `SELECT DATEPART(datepart,'2007-10-30 12:15:32.1234567 +05:10')`. Тип данных аргумента *date* — **datetimeoffset(7)**. Масштаб значения, возвращаемого функцией **nanosecond***datepart*, составляет 9 (.123456700). При этом два последних значения всегда имеют значение 00.
  
|*datepart*|Возвращаемое значение|  
|---|---|
|**year, yyyy, yy**|2007|  
|**quarter, qq, q**|4|  
|**month, mm, m**|10|  
|**dayofyear, dy, y**|303|  
|**day, dd, d**|30|  
|**week, wk, ww**|45|  
|**weekday, dw**|1|  
|**hour, hh**|12|  
|**minute, n**|15|  
|**second, ss, s**|32|  
|**millisecond, ms**|123|  
|**microsecond, mcs**|123456|  
|**nanosecond, ns**|123456700|  
|**TZoffset, tz**|310|  
  
## <a name="week-and-weekday-datepart-arguments"></a>Аргументы функции datepart, содержащие информацию о номере недели и дня
Когда переменная *datepart* содержит значение **week** (**wk**, **ww**) или **weekday** (**dw**), то тип возвращаемого значения определяется установками функции [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
1 января любого года определяет начальное число для **week***datepart*, например DATEPART (**wk**, '1 января, *xxx*x') = 1, где *xxxx* — любой год.
  
Ниже представлена таблица возвращаемых значений параметров **week** и **weekday***datepart* даты 21.04.2007 с каждым аргументом функции SET DATEFIRST. 1 января 2007 г. — первый понедельник в году. 21 апреля 2007 г. — суббота. SET DATEFIRST 7, воскресенье задается по умолчанию для региональных настроек "Английский (США)".
  
|SET DATEFIRST<br /><br /> аргумент|week<br /><br /> возвращаемое значение|weekday<br /><br /> возвращаемое значение|  
|---|---|---|
|1|16|6|  
|2|17|5|  
|3|17|4|  
|4|17|3|  
|5|17|2|  
|6|17|1|  
|7|16|7|  
  
## <a name="year-month-and-day-datepart-arguments"></a>Аргументы year, month и day функции datepart  
Значения, возвращаемые в результате выполнения команд DATEPART (**year**, *date*), DATEPART (**month**, *date*) и DATEPART (**day**, *date*), совпадают с результатами выполнения функций [YEAR](../../t-sql/functions/year-transact-sql.md), [MONTH](../../t-sql/functions/month-transact-sql.md) и [DAY](../../t-sql/functions/day-transact-sql.md), соответственно.
  
## <a name="isoweek-datepart"></a>ISO_WEEK datepart  
Стандарт ISO 8601 включает в себя систему отсчета дней и недель ISO. Каждая неделя приписывается тому году, в котором находится ее четверг. Например, 1-я неделя 2004 г. (2004W01) считается с понедельника 29 декабря 2003 г. по воскресенье 4 января 2004 г. Наибольшее число недель в году может составлять 52 или 53. Этот стиль нумерации обычно используется в странах и регионах Европы, но редко в других странах.
  
Система отсчета недель в разных странах и регионах может не совпадать со стандартом ISO. Как показано в следующей таблице, существует как минимум шесть методов отсчета:
  
|Первый день недели|Содержание первой недели года|Двойное присвоение недель|Где применяется|  
|---|---|---|---|
|Воскресенье|1 января,<br /><br /> первая суббота,<br /><br /> 1–7 дней года|Да|США|  
|Понедельник|1 января,<br /><br /> первое воскресенье,<br /><br /> 1–7 дней года|Да|Большинство стран Европы, а также Соединенное Королевство|  
|Понедельник|4 января,<br /><br /> первый четверг<br /><br /> 4–7 дней года|Нет|ISO 8601, Норвегия и Швеция|  
|Понедельник|7 января,<br /><br /> первый понедельник,<br /><br /> 7 дней года|Нет||  
|Среда|1 января,<br /><br /> первый вторник,<br /><br /> 1–7 дней года|Да||  
|Суббота|1 января,<br /><br /> первая пятница,<br /><br /> 1–7 дней года|Да||  
  
## <a name="tzoffset"></a>TZoffset  
Значение переменной **TZoffset** (**tz**) возвращает количество минут (со знаком). В результате выполнения представленной ниже инструкции выдается значение временного смещения 310 минут.
  
```sql
SELECT DATEPART (TZoffset, '2007-05-10  00:00:01.1234567 +05:10');  
```  
Значение TZoffset выводится следующим образом:
- Для datetime2 и datetimeoffset TZoffset возвращает смещение времени в минутах, где смещение datetime2 всегда равно 0 минут.
- Для типов данных, которые могут быть неявно преобразованы в datetimeoffset или datetime2, за исключением других типов данных даты и времени, возвращает смещение времени в минутах.
- Параметры любых других типов приведут к ошибке.
  
  
## <a name="smalldatetime-date-argument"></a>Аргумент date с типом smalldatetime  
Когда *date* имеет тип данных [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), возвращается значение секунд 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-a-date-argument"></a>Для аргумента функции datepart, который отличен от аргумента date, возвращается значение по умолчанию  
Если в типе данных аргумента *date* не указана часть *datepart*, для этого *datepart* будет возвращаться значение по умолчанию, только если для *date* указан литерал.
  
Например, значение "год-месяц-день" по умолчанию для любого типа данных **date** равно 1900-01-01. Следующая инструкция содержит аргументы компонентов даты для *datepart*, аргумент времени для *date* и возвращает `1900, 1, 1, 1, 2`.
  
```sql
SELECT DATEPART(year, '12:10:30.123')  
    ,DATEPART(month, '12:10:30.123')  
    ,DATEPART(day, '12:10:30.123')  
    ,DATEPART(dayofyear, '12:10:30.123')  
    ,DATEPART(weekday, '12:10:30.123');  
```  
  
Если *date* указан как переменная или столбец таблицы и тип данных переменной или столбца не содержит указанной части *datepart*, возвращается ошибка 9810. Приведенный пример кода завершается ошибкой, потому что год даты не является допустимым для типа данных **time**, объявленного для переменной *@t*.
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATEPART(year, @t);  
```  
  
## <a name="fractional-seconds"></a>Доли секунд
Отображение долей секунд производится, как показано в следующих инструкциях:
  
```sql
SELECT DATEPART(millisecond, '00:00:01.1234567'); -- Returns 123  
SELECT DATEPART(microsecond, '00:00:01.1234567'); -- Returns 123456  
SELECT DATEPART(nanosecond,  '00:00:01.1234567'); -- Returns 123456700  
```  
  
## <a name="remarks"></a>Замечания  
Функция DATEPART может использоваться в предложениях WHERE, HAVING, GROUP BY и ORDER BY, а также при составлении списка выбора.
  
В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] функция DATEPART неявно приводит строковые литералы в качестве типа **datetime2**. Это означает, что DATEPART не поддерживает формат ГЧМ (год, число, месяц) при передаче даты в виде строки. Для использования формата ГЧМ (год, число, месяц) необходимо явно привести строку к типу **datetime** или **smalldatetime**.
  
## <a name="examples"></a>Примеры  
В ходе выполнения представленного ниже примера производится отображение значения базового года отсчета. Значение базового года используется при расчетах, связанных с датами. В следующем примере дата указана как число. Обратите внимание, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует 0 как 1 января 1900 г.
  
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
  
```
--------
20
```  
  
В следующем примере возвращается значение года даты `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (year,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
--------
1974
```  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
