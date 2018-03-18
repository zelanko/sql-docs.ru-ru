---
title: "DATEDIFF_BIG (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6c8228f0db3e37fe3bf6425d60fd4f9067e92220
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Возвращает количество пересеченных границ (целое число со знаком), указанных в аргументе *datepart*, за период времени, указанный в аргументах *startdate* и *enddate*.
  
Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Аргументы  
*datepart*  
Часть аргументов *startdate* и *enddate*, которая задает тип пересекаемых границ. В приведенной ниже таблице перечислены все допустимые аргументы *datepart*. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
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
Выражение, которое можно привести к значению типа **time**, **date**, **smalldatetime**, **datetime**, **datetime2** или **datetimeoffset**. Аргумент *date* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом. *startdate* вычитается из *enddate*.  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двузначном обозначении года см. в статье [Настройка параметра конфигурации сервера two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
См. описание аргумента *startdate*.
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Со знаком   
        **bigint**  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает количество пересеченных границ (целое число со знаком), указанных в аргументе datepart, за период времени, заданный аргументами startdate и enddate.
-   Каждое выражение *datepart* и его краткие формы возвращают одно и то же значение.  
  
Если возвращенное значение выходит за границы диапазона типа **bigint** (от –9 223 372 036 854 775 808 до +9 223 372 036 854 775 807), возвращается ошибка. Для единицы измерения **millisecond** максимальная разница между значениями *startdate* и *enddate* составляет 24 дня, 20 часов, 31 минуту и 23,647 секунды. Для единицы измерения **second** максимальная разница составляет 68 лет.
  
Если обоим аргументам *startdate* и *enddate* присвоено только значение времени, а аргумент *datepart* не содержит значения времени *datepart*, то возвращается значение 0.
  
При вычислении возвращаемого значения смещение часовых поясов для аргументов *startdate* или *endate* не учитывается.
  
Так как значение типа [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) имеет точность до минуты, то при использовании в аргументах *startdate* и *enddate* значения типа **smalldatetime** секунды и миллисекунды всегда равны 0.
  
Если переменной типа данных date присвоено только значение времени, в качестве недостающей части даты используется значение по умолчанию: 1900-01-01. Если переменой типа данных time или date присвоено только значение даты, в качестве недостающей части времени используется значение по умолчанию: 00:00:00. Если в одном из аргументов *startdate* или *enddate* указано только время, а в другом только дата, в качестве недостающей информации используются значения по умолчанию.
  
Если аргументы *startdate* и *enddate* имеют разные типы данных даты, но при этом один из них имеет больше частей времени или обладает более высокой точностью, значениям недостающих частей другого аргумента присваиваются значения 0.
  
## <a name="datepart-boundaries"></a>Границы, задаваемые аргументом datepart
Приведенные ниже инструкции имеют одинаковые значения аргументов *startdate* и *endate*. Указанные даты являются соседними, а временная разница между ними составляет 0,0000001 секунды. Разница между аргументами *startdate* и *endate* в каждой инструкции пересекает одну календарную или временную границу аргумента *datepart*. Каждое выражение возвращает значение 1. Если в этом примере в аргументах *startdate* и *endate* указаны различные года и при этом указанные границы находятся в пределах одной календарной недели, то для значения **week** будет возвращено значение 0.

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
  
## <a name="remarks"></a>Remarks  
Функция DATEDIFF_BIG может использоваться в предложениях WHERE, HAVING, GROUP BY и ORDER BY, а также при составлении списка выбора.
  
Функция DATEDIFF_BIG неявно приводит строковые литералы к типу **datetime2**. Это означает, что при передаче даты в виде строки DATEDIFF_BIG не поддерживает формат ГЧМ (год, число, месяц). Для использования формата ГЧМ (год, число, месяц) необходимо явно привести строку к типу **datetime** или **smalldatetime**.
  
Указание SET DATEFIRST не влияет на DATEDIFF_BIG. DATEDIFF_BIG всегда считает воскресенье первым днем недели, чтобы обеспечить детерминированность функции.
  
## <a name="examples"></a>Примеры  
В приведенных ниже примерах выражения различного типа используются в качестве аргументов для параметров *startdate* и *enddate*.
  
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
  
Множество тесно связанных примеров можно найти в статье [DATEDIFF (Transact-SQL)](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF (Transact-SQL)](../../t-sql/functions/datediff-transact-sql.md)
  
  
