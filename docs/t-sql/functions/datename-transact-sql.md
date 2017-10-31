---
title: "Функция DATENAME (Transact-SQL) | Документы Microsoft"
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
- DATENAME_TSQL
- DATENAME
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATENAME function [SQL Server
- functions [SQL Server], time
- functions [SQL Server], date and time
- dateparts [SQL Server], datename
- date and time [SQL Server], DATENAME
- comparing dates times [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 11855b56-c554-495d-aad4-ba446990153b
caps.latest.revision: 59
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d41bbf5a83f0dee8518ece6f074181b8412bad8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="datename-transact-sql"></a>DATENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает символьную строку, представляющий указанный *datepart* указанного *даты*
  
Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATENAME ( datepart , date )  
```  
  
## <a name="arguments"></a>Аргументы  
*часть_даты*  
— Это часть *даты* для возврата. В следующей таблице перечислены все допустимые *datepart* аргументы. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
|*часть_даты*|Сокращения|  
|---|---|
|**год**|**yy, yyyy**|  
|**квартал**|**б, q**|  
|**месяц**|**mm, m**|  
|**день года**|**dy, y**|  
|**день**|**дд, d**|  
|**Неделя**|**нед ww**|  
|**день недели**|**DW, w**|  
|**час**|**чч**|  
|**минуты**|**mi, n**|  
|**второй**|**ss, s**|  
|**миллисекунды**|**MS**|  
|**микросекунды**|**MCS**|  
|**наносекундных**|**NS**|  
|**TZoffset**|**TZ**|  
|**ISO_WEEK**|**ISOWK ISOWW**|  
  
*date*  
Выражение, которое разрешается к **время**, **даты**, **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение. *Дата* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о разделе двумя цифрами, [Настройка two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Тип возвращаемых данных  
**nvarchar**
  
## <a name="return-value"></a>Возвращаемое значение  
  
-   Каждый *datepart* и его краткие формы возвращают одинаковое значение.  
  
Возвращаемое значение зависит от языка среды, задаваемого с помощью [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) и [Настройка параметра конфигурации сервера язык по умолчанию](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) входа. Возвращаемое значение зависит [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) Если *даты* строка является литералом некоторого формата. Инструкция SET DATEFORMAT не влияет на возвращаемое значение, если дата представляется выражением столбца типа данных даты или времени.
  
Когда *даты* параметр имеет **даты** аргумента типа данных, возвращаемое значение зависит от настроек, заданных с помощью [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
## <a name="tzoffset-datepart-argument"></a>Аргумент TZoffset функции datepart  
Если *datepart* аргумент **TZoffset** (**tz**) и *даты* содержит без смещения часового пояса, возвращается значение 0.
  
## <a name="smalldatetime-date-argument"></a>Аргумент даты типа smalldatetime  
Когда *даты* — [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), секунд возвращается значение 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-the-date-argument"></a>Возвращается значение по умолчанию для аргумента функции datepart, который отличен от даты  
Если тип данных *даты* аргумента не указанный *datepart*, значение по умолчанию для этого *datepart* будет возвращаться только в том случае, если указан литерал для *даты*.
  
Например, по умолчанию год месяц день для любого **даты** 1900-01-01 имеет тип данных. Следующая инструкция содержит аргументы компонентов даты для *datepart*, аргумент времени для *даты*и возвращает `1900, January, 1, 1, Monday`.
  
```sql
SELECT DATENAME(year, '12:10:30.123')  
    ,DATENAME(month, '12:10:30.123')  
    ,DATENAME(day, '12:10:30.123')  
    ,DATENAME(dayofyear, '12:10:30.123')  
    ,DATENAME(weekday, '12:10:30.123');  
```  
  
Если *даты* указано как переменная или столбец таблицы и данные, тип для переменной или столбце у указанного *datepart*, возвращается ошибка 9810. Следующий пример кода заканчивается ошибкой из-за год даты не является допустимым для **время** тип данных, объявленного для переменной  *@t* .
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATENAME(year, @t);  
```  
  
## <a name="remarks"></a>Замечания  
Функция DATENAME может использоваться в предложениях WHERE, HAVING, GROUP BY и ORDER BY, а также при составлении списка выбора.
  
В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], функция DATENAME неявно приводит строковые литералы в качестве **datetime2** типа. Это означает, что DATENAME не поддерживает формат ГЧМ (год, число, месяц) при передаче даты в виде строки. Необходимо явно привести строку к **datetime** или **smalldatetime** тип, используемый формат ГДМ.
  
## <a name="examples"></a>Примеры  
В следующем примере производится отображение частей указанной даты.
  
`SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');`
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*часть_даты*|Возвращаемое значение|  
|---|---|
|**год, гггг, гг**|2007 г.|  
|**Квартал "," б "," q**|4|  
|**месяц, mm, m**|Октябрь|  
|**DayOfYear dy, y**|303|  
|**день "," dd "," d**|30|  
|**Неделя, нед, ww**|44|  
|**день недели, хранилища данных**|Вторник|  
|**час, hh**|12|  
|**минуты, n**|15|  
|**Во-вторых, ss, s**|32|  
|**миллисекунды, мс**|123|  
|**микросекунды mcs**|123456|  
|**наносекундных ns**|123456700|  
|**TZoffset tz**|310|  
|**ISOWW ISO_WEEK ISOWK,**|44|  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

В следующем примере производится отображение частей указанной даты.
  
```sql
SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*часть_даты*|Возвращаемое значение|  
|---|---|
|**год, гггг, гг**|2007 г.|  
|**Квартал "," б "," q**|4|  
|**месяц, mm, m**|Октябрь|  
|**DayOfYear dy, y**|303|  
|**день "," dd "," d**|30|  
|**Неделя, нед, ww**|44|  
|**день недели, хранилища данных**|Вторник|  
|**час, hh**|12|  
|**минуты, n**|15|  
|**Во-вторых, ss, s**|32|  
|**миллисекунды, мс**|123|  
|**микросекунды mcs**|123456|  
|**наносекундных ns**|123456700|  
|**TZoffset tz**|310|  
|**ISOWW ISO_WEEK ISOWK,**|44|  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


