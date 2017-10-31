---
title: "smalldatetime (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smalldatetime_TSQL
- smalldatetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- smalldatetime data type [SQL Server]
- dates [SQL Server], data types
- date and time [SQL Server], smalldatetime
- data types [SQL Server], date and time
ms.assetid: 68b74610-d54c-4c8e-b4b2-7e3747546ee0
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 07012d85a54292fa763a7b291d1b7318b6969ca4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="smalldatetime-transact-sql"></a>smalldatetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Определяет дату, сочетающуюся с временем дня. Время представлено в 24-часовом формате с секундами, всегда равными нулю (:00), без долей секунд.
  
> [!NOTE]  
>  Используйте **время**, **даты**, **datetime2** и **datetimeoffset** для новых проектов типы данных. Эти типы соответствуют стандарту языка SQL. Их проще переносить на другие платформы. **время**, **datetime2** и **datetimeoffset** поддерживают более высокую точность секунд. **DateTimeOffset** обеспечивает поддержку часовых поясов для глобально развернутых приложений.  
  
## <a name="smalldatetime-description"></a>Описание типа smalldatetime
  
|||  
|-|-|  
|Синтаксис|**smalldatetime**|  
|Использование|ОБЪЯВИТЕ @MySmalldatetime **smalldatetime**<br /><br /> Создание TABLE Таблица1 (Столбец1 **smalldatetime** )|  
|Форматы строковых литералов по умолчанию<br /><br /> (используется для клиента нижнего уровня)|Неприменимо|  
|Диапазон даты|От 01.01.1900 до 06.06.2079<br /><br /> 1 января 1900 года — 6 июня 2079 года|  
|Диапазон времени|От 00:00:00 до 23:59:59<br /><br /> 2007-05-09 23:59:59 округляется до<br /><br /> 2007-05-10 00:00:00|  
|Диапазоны элементов|ГГГГ — четырехзначное число от 1900 до 2079, представляющее год.<br /><br /> ММ обозначает 2 цифры, которые представляют месяц и принимают значения от 01 до 12.<br /><br /> Обозначение ДД состоит из двух цифр, представляющих день указанного месяца, и принимает значения от 01 до 31 в зависимости от месяца.<br /><br /> Обозначение чч состоит из двух цифр, представляющих час, и принимает значения от 00 до 23.<br /><br /> Обозначение мм состоит из двух цифр, представляющих минуту, и принимает значения от 00 до 59.<br /><br /> Обозначение сс состоит из двух цифр, представляющих секунду, и принимает значения от 00 до 59. Значения, меньшие или равные 29,998 секунд, округляются до минуты в меньшую сторону; значения, равные или большие 29,999, округляются до минуты в большую сторону.|  
|Длина в символах|Максимально 19 позиций|  
|Объем памяти|4 байта, фиксированный.|  
|Точность|Одна минута|  
|Значение по умолчанию|1900-01-01 00:00:00|  
|Календарь|Григорианский<br /><br /> (Не включает полный диапазон лет)|  
|Определяемая пользователем точность в долях секунды|Нет|  
|Учет и сохранение смещения часового пояса|Нет|  
|Учет перехода на летнее время|Нет|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Соответствие стандартам ANSI и ISO 8601  
**smalldatetime** несовместим ANSI и ISO 8601.
  
## <a name="converting-date-and-time-data"></a>Преобразование данных даты и времени
При преобразовании в типы данных даты и времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отвергает все значения, которые он не распознает как значения даты или времени. Сведения об использовании функций CAST и CONVERT с данными даты и времени см. в разделе [CAST и CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-smalldatetime-to-other-date-and-time-types"></a>Преобразование типа smalldatetime в другие типы даты и времени
В этом разделе описано, что происходит при **smalldatetime** тип данных преобразуется в другие типы данных даты и времени.
  
В случае преобразования **Дата**, год, месяц и день копируются. Следующий код демонстрирует результаты преобразования значения `smalldatetime` в значение `date`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @date date = @smalldatetime  
  
SELECT @smalldatetime AS '@smalldatetime', @date AS 'date';  
  
--Result  
--@smalldatetime          date  
------------------------- ----------  
--1955-12-13 12:43:00     1955-12-13  
--  
--(1 row(s) affected)  
```  
  
Если преобразование выполняется в **time(n)**, часов, минут и секунд копируются. Доли секунды устанавливаются в значение 0. Следующий код демонстрирует результаты преобразования значения `smalldatetime` в значение `time(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @time time(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @time AS 'time';  
  
--Result  
--@smalldatetime          time  
------------------------- -------------  
--1955-12-13 12:43:00     12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
Если преобразование выполняется в **datetime**, **smalldatetime** копировать значение **datetime** значение. Доли секунды устанавливаются в значение 0. Следующий код демонстрирует результаты преобразования значения `smalldatetime` в значение `datetime`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime AS 'datetime';  
  
--Result  
--@smalldatetime          datetime  
------------------------- -----------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.000  
--  
--(1 row(s) affected)  
```  
  
В случае преобразования **datetimeoffset(n)**, **smalldatetime** копировать значение **datetimeoffset(n)** значение. Для долей секунды устанавливается значение 0; для смещения часового пояса устанавливается значение +00:0. Следующий код демонстрирует результаты преобразования значения `smalldatetime` в значение `datetimeoffset(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetimeoffset datetimeoffset(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetimeoffset AS 'datetimeoffset(4)';  
  
--Result  
--@smalldatetime          datetimeoffset(4)  
------------------------- ------------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000 +00:0  
--  
--(1 row(s) affected)  
```  
  
Для преобразования **datetime2(n)**, **smalldatetime** копировать значение **datetime2(n)** значение. Доли секунды устанавливаются в значение 0. Следующий код демонстрирует результаты преобразования значения `smalldatetime` в значение `datetime2(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime2 datetime2(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime2 AS ' datetime2(4)';  
  
--Result  
--@smalldatetime           datetime2(4)  
------------------------- ------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-casting-string-literals-with-seconds-to-smalldatetime"></a>A. Приведение строковых литералов с секундами к типу smalldatetime  
В следующем примере сравнивается преобразование секунд в строковых литералах в тип данных `smalldatetime`.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29'     AS smalldatetime)  
    ,CAST('2007-05-08 12:35:30'     AS smalldatetime)  
    ,CAST('2007-05-08 12:59:59.998' AS smalldatetime);  
```  
  
|Ввод|Вывод|  
|---|---|
|2007-05-08 12:35:29|2007-05-08 12:35:00|  
|2007-05-08 12:35:30|2007-05-08 12:36:00|  
|2007-05-08 12:59:59.998|2007-05-08 13:00:00|  
  
### <a name="b-comparing-date-and-time-data-types"></a>Б. Сравнение типов данных даты и времени  
В следующем примере сравниваются результаты приведения строкового типа к каждому из типов данных date и time.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
|Тип данных|Вывод|  
|---|---|
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

