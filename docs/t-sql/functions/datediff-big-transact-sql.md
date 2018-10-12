---
title: DATEDIFF_BIG (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4516965f66256e21e5e68310f7668770e17cabb9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644852"
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Эта функция возвращает количество пересеченных границ (целое число со знаком), указанных в аргументе *datepart*, за период времени, указанный в аргументах *startdate* и *enddate*.
  
Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Аргументы  
*datepart*  
Часть аргументов *startdate* и *enddate*, которая задает тип пересекаемых границ. `DATEDIFF_BIG` не будет принимать эквивалентные переменные, определяемые пользователем. В приведенной ниже таблице перечислены все допустимые аргументы *datepart*.

> [!NOTE]
> `DATEDIFF_BIG` не принимает эквивалентные переменные, определяемые пользователем, для аргументов *datepart*.
  
|*datepart*|Сокращения|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**чч**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
Выражение, которое может быть разрешено в одно из следующих значений.

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

Для *date* `DATEDIFF_BIG` будет принимать столбец выражения, выражение, строковый литерал или определяемую пользователем переменную. Значение строкового литерала должно разрешаться в **datetime**. Во избежание неоднозначности используйте четырехзначную запись года. `DATEDIFF_BIG` вычитает *startdate* из *enddate*. Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двузначном обозначении года см. в статье [Настройка параметра конфигурации сервера two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
См. описание аргумента *startdate*.
  
## <a name="return-type"></a>Тип возвращаемых данных  

**bigint** со знаком  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает количество пересеченных границ (целое число со знаком), указанных в аргументе datepart, за период времени, указанный в аргументах startdate и enddate.
-   Каждый конкретный аргумент *datepart* и сокращения для этого аргумента *datepart* будут возвращать одно и то же значение.  
  
В качестве возвращаемого значения вне диапазона для **bigint** (от –9 223 372 036 854 775 808 до 9 223 372 036 854 775 807) `DATEDIFF_BIG` возвращает сообщение об ошибке. Для **миллисекунды** максимальная разница между *enddate* и *startdate* составляет 24 дня 20 часов 31 минута и 23 647 секунд. Для **секунды** максимальная разница составляет 68 лет.
  
Если обоим аргументам, *startdate* и *enddate*, присвоено только значение времени, а аргумент *datepart* не содержит значения времени *datepart*, то `DATEDIFF_BIG` возвращает значение 0.
  
При вычислении возвращаемого значения `DATEDIFF_BIG` не учитывает компонент смещения часовых поясов для аргументов *startdate* или *enddate*.
  
Так как значение типа **smalldatetime** имеет точность до минуты, то при использовании в аргументах *startdate* или *enddate* `DATEDIFF_BIG` всегда задает 0 в качестве возвращаемого значения [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) секунд и миллисекунд.
  
Если переменной типа данных date присвоено только значение времени, в качестве недостающей части даты `DATEDIFF_BIG` задает значение по умолчанию: 1900-01-01. Если переменной типа данных time или date присвоено только значение даты, в качестве недостающей части времени `DATEDIFF_BIG` задает значение по умолчанию: 00:00:00. Если в одном из аргументов *startdate* или *enddate* указано только время, а в другом только дата, в качестве недостающей информации `DATEDIFF_BIG` задает значения по умолчанию.
  
Если аргументы *startdate* и *enddate* имеют разные типы данных даты, но при этом один из них имеет больше частей времени или обладает более высокой точностью, `DATEDIFF_BIG` присваивает значения 0 недостающим частям другого аргумента.
  
## <a name="datepart-boundaries"></a>Границы, задаваемые аргументом datepart
Приведенные ниже инструкции имеют одинаковые значения аргументов *startdate* и *enddate*. Указанные даты являются соседними, а временная разница между ними составляет 0,0000001 секунды. Разница между аргументами *startdate* и *enddate* в каждой инструкции пересекает одну календарную или временную границу аргумента *datepart*. Каждое выражение возвращает значение 1. Если аргументы *startdate* и *enddate* имеют разные значения года, но одинаковые значения календарной недели, `DATEDIFF_BIG` вернет 0 для части **week** аргумента *datepart*.

```sql
SELECT DATEDIFF_BIG(year,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter,     '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month,       '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear,   '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day,         '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
Функция `DATEDIFF_BIG` может использоваться в предложениях SELECT, <list>WHERE, HAVING, GROUP BY и ORDER BY.
  
Функция `DATEDIFF_BIG` неявно приводит строковые литералы к типу **datetime2**. Это означает, что `DATEDIFF_BIG` не поддерживает формат ГЧМ (год, число, месяц) при передаче даты в виде строки. Для использования формата ГЧМ (год, число, месяц) необходимо явно привести строку к типу **datetime** или **smalldatetime**.
  
Указание SET DATEFIRST не влияет на `DATEDIFF_BIG`. `DATEDIFF_BIG` всегда считает воскресенье первым днем недели, чтобы обеспечить детерминизм работы функции.
  
## <a name="examples"></a>Примеры 
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Указание столбцов в качестве начальной и конечной даты  
В этом примере выражения различного типа используются в качестве аргументов для параметров *startdate* и *enddate*. В нем подсчитывается количество границ дней, пересекаемых между датами, указанными в двух столбцах таблицы.
  
```sql
CREATE TABLE dbo.Duration  
    (startDate datetime2, endDate datetime2);  
    
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT DATEDIFF_BIG(day, startDate, endDate) AS 'Duration'  
    FROM dbo.Duration;  
-- Returns: 1  
```  

Тесно связанные примеры см. в статье [DATEDIFF (Transact-SQL)](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF (Transact-SQL)](../../t-sql/functions/datediff-transact-sql.md)
  
  
