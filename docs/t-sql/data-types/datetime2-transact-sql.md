---
title: "datetime2 (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetime2
- datetime2_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- dates [SQL Server], data types
- date and time [SQL Server], datetime2
- data types [SQL Server], date and time
- datetime2 data type [SQL Server]
ms.assetid: 868017f3-214f-43ef-8536-cc1632a2288f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 70a3f27fc59fcc904679040029e47f312017dbe3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datetime2-transact-sql"></a>datetime2 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Определяет дату, включающую время суток в 24-часовом формате. **datetime2** может рассматриваться как расширение существующего **datetime** типа, имеющего более широкий диапазон дат, большую точность долей по умолчанию и необязательный определяемый пользователем точности.
  
## <a name="datetime2-description"></a>Описание типа данных datetime2
  
|Свойство|Значение|  
|--------------|-----------|  
|Синтаксис|**datetime2** [(*точность в долях секунды*)]|  
|Использование|ОБЪЯВИТЕ @MyDatetime2 **datetime2(7)**<br /><br /> CREATE TABLE Таблица1 (Столбец1 **datetime2(7)** )|  
|Формат строковых литералов по умолчанию<br /><br /> (используется для клиента нижнего уровня)|ГГГГ-ММ-ДД чч:мм:сс[.доли секунды]<br /><br /> Дополнительные сведения см. в подразделе «Обратная совместимость для клиентов низкого уровня» следующего раздела.|  
|Диапазон даты|От 0001-01-01 до 31.12.99<br /><br /> Январь 1,1 CE до 31 декабря 9999 года CE|  
|Диапазон времени|от 00:00:00 до 23:59:59.9999999|  
|Диапазон смещения часового пояса|Нет|  
|Диапазоны элементов|ГГГГ представляет собой четырехзначное число от 0001 до 9999, определяющее год.<br /><br /> ММ — двузначное число от 01 до 12, представляющее месяц указанного года.<br /><br /> Обозначение ДД состоит из двух цифр, представляющих день указанного месяца, и принимает значения от 01 до 31 в зависимости от месяца.<br /><br /> Обозначение «чч» состоит из двух цифр, представляющих час, и принимает значения от 00 до 23.<br /><br /> Обозначение «мм» состоит из двух цифр, представляющих минуту, и принимает значения от 00 до 59.<br /><br /> Обозначение «сс» состоит из двух цифр, представляющих секунду, и принимает значения от 00 до 59.<br /><br /> Обозначение n* может содержать от нуля до семи цифр, представляющих доли секунды, и принимает значения от 0 до 9999999. В Informatica, доли секунд будут усечены, если n > 3.|  
|Длина в символах|Минимальная — 19 позиций (ГГГГ-ММ-ДД чч:мм:сс), максимальная — 27 позиций ((ГГГГ-ММ-ДД чч:мм:сс.0000000)|  
|Точность, масштаб|От 0 до 7 цифр, с точностью 100 нс. Точность по умолчанию составляет 7 цифр.|  
|Объем памяти|6 байт для представления точности меньше 3 цифр, 7 байт — для точности в 3 и 4 цифры. Для представления любых других значений точности требуется 8 байт.|  
|Точность|100 наносекунд|  
|Значение по умолчанию|1900-01-01 00:00:00|  
|Календарь|Григорианский|  
|Определяемая пользователем точность в долях секунды|Да|  
|Учет и сохранение смещения часового пояса|Нет|  
|Учет перехода на летнее время|Нет|  
  
Метаданные типа данных, в разделе [sys.systypes &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md) или [TYPEPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/typeproperty-transact-sql.md). В некоторых типах данных дат и времени точность и масштаб разные. Чтобы получить точность и масштаб столбца, в разделе [COLUMNPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/columnproperty-transact-sql.md), [COL_LENGTH &#40; Transact-SQL &#41; ](../../t-sql/functions/col-length-transact-sql.md), или [sys.columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).
  
## <a name="supported-string-literal-formats-for-datetime2"></a>Поддерживаемые форматы строковых литералов для типа datetime2
В следующих таблицах перечислены поддерживаемые ISO 8601 и ODBC форматы строковых литералов для **datetime2**. Сведения о форматах алфавитном, числовых, без разделителей и времени для частей даты и времени **datetime2**, в разделе [даты &#40; Transact-SQL &#41; ](../../t-sql/data-types/date-transact-sql.md) и [времени &#40; Transact-SQL &#41; ](../../t-sql/data-types/time-transact-sql.md).
  
|ISO 8601|Описания|  
|---|---|
|ГГГГ-ММ-ДДТчч:мм:сс[.nnnnnnn]<br /><br /> ГГГГ-ММ-ДДТчч:мм:сс[.nnnnnnn]|На этот формат не влияют настройки локали сеанса инструкций SET LANGUAGE и SET DATEFORMAT. **T**, двоеточие (:) и точку (.), включаются в строковый литерал, например «2007-05-02T19:58:47.1234567 ".|  
  
|интерфейс ODBC|Description|  
|---|---|
|{ ts 'гггг-мм-дд чч:мм:сс[.доли секунды]' }|Зависит от API-интерфейса ODBC.<br /><br /> Можно указать от 0 до 7 знаков (100 наносекунд) справа от десятичной запятой, представляющих доли секунды.|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI и ISO 8601  
Соответствие ANSI и ISO 8601 [даты](../../t-sql/data-types/date-transact-sql.md) и [время](../../t-sql/data-types/time-transact-sql.md) применяются к **datetime2**.
  
##  <a name="backward-compatibility-for-down-level-clients"></a>Обратная совместимость для клиентов нижнего уровня  
Некоторые клиенты низкого уровня не поддерживают **время**, **даты**, **datetime2** и **datetimeoffset** типов данных. В следующей таблице показано сопоставление типов экземпляра более высокого уровня [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и клиентов низкого уровня.
  
|Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Формат строкового литерала по умолчанию, передаваемый клиенту низкого уровня|ODBC низкого уровня|OLEDB низкого уровня|JDBC низкого уровня|SQLCLIENT низкого уровня|  
| --- | --- | --- | --- | --- | --- |
|**time**|чч:мм:сс[.ннннннн]|SQL_WVARCHAR или SQL_VARCHAR|DBTYPE_WSTR или DBTYPE_STR|Java.sql.String|String или SqString|  
|**date**|ГГГГ-ММ-ДД|SQL_WVARCHAR или SQL_VARCHAR|DBTYPE_WSTR или DBTYPE_STR|Java.sql.String|String или SqString|  
|**datetime2**|ГГГГ-ММ-ДД чч:мм:сс[.ннннннн]|SQL_WVARCHAR или SQL_VARCHAR|DBTYPE_WSTR или DBTYPE_STR|Java.sql.String|String или SqString|  
|**datetimeoffset**|ГГГГ-мм-дд чч [.ннннннн] [+ &#124;-] чч: мм|SQL_WVARCHAR или SQL_VARCHAR|DBTYPE_WSTR или DBTYPE_STR|Java.sql.String|String или SqString|  
  
## <a name="converting-date-and-time-data"></a>Преобразование данных даты и времени
При преобразовании в типы данных даты и времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отвергает все значения, которые он не распознает как значения даты или времени. Сведения об использовании функций CAST и CONVERT с данными даты и времени см. в разделе [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
### <a name="converting-other-date-and-time-types-to-the-datetime2-data-type"></a>Преобразование других типов даты и времени в тип данных datetime2
В этом разделе описано, что происходит при преобразовании типов данных даты и времени **datetime2** тип данных.  
  
При преобразовании из **Дата**, год, месяц и день копируются.  Компонента времени устанавливается значение 00:00:00.0000000.  Следующий код демонстрирует результаты преобразования значения `date` в значение `datetime2`.  
  
```sql
DECLARE @date date = '12-21-16';
DECLARE @datetime2 datetime2 = @date;

SELECT @datetime2 AS '@datetime2', @date AS '@date';
  
--Result  
--@datetime2                  @date
----------------------------- ----------
--2016-12-21 00:00:00.0000000 2016-12-21
```  
  
При преобразовании из **time(n)**, компонент времени копируется и компонента даты устанавливается значение "1900-01-01". Следующий пример показывает результаты преобразования значения `time(7)` в значение `datetime2`.  
  
```sql
DECLARE @time time(7) = '12:10:16.1234567';
DECLARE @datetime2 datetime2 = @time;

SELECT @datetime2 AS '@datetime2', @time AS '@time';
  
--Result  
--@datetime2                  @time
----------------------------- ----------------
--1900-01-01 12:10:16.1234567 12:10:16.1234567
```  
  
При преобразовании из **smalldatetime**, копируются в часах и минутах. Секунды и доли секунд устанавливаются в значение 0. Следующий код демонстрирует результаты преобразования значения `smalldatetime` в значение `datetime2`.  
  
```sql
DECLARE @smalldatetime smalldatetime = '12-01-16 12:32';
DECLARE @datetime2 datetime2 = @smalldatetime;

SELECT @datetime2 AS '@datetime2', @smalldatetime AS '@smalldatetime'; 
  
--Result  
--@datetime2                  @smalldatetime
----------------------------- -----------------------
--2016-12-01 12:32:00.0000000 2016-12-01 12:32:00 
```  
  
При преобразовании из **datetimeoffset(n)**, копируются компоненты даты и времени. Часовой пояс усекается. Следующий пример показывает результаты преобразования значения `datetimeoffset(7)` в значение `datetime2`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(7) = '2016-10-23 12:45:37.1234567 +10:0';
DECLARE @datetime2 datetime2 = @datetimeoffset;

SELECT @datetime2 AS '@datetime2', @datetimeoffset AS '@datetimeoffset'; 
  
--Result  
--@datetime2                  @datetimeoffset
----------------------------- ----------------------------------
--2016-10-23 12:45:37.1234567 2016-10-23 12:45:37.1234567 +10:00
```  

При преобразовании из **datetime**, даты и времени копируются.  Точность в долях секунды расширяется до 7 цифр.  Следующий пример показывает результаты преобразования значения `datetime` в значение `datetime2`.

```sql
DECLARE @datetime datetime = '2016-10-23 12:45:37.333';
DECLARE @datetime2 datetime2 = @datetime;

SELECT @datetime2 AS '@datetime2', @datetime AS '@datetime';
   
--Result  
--@datetime2                  @datetime
------------------------- ---------------------------
--2016-10-23 12:45:37.3333333 2016-10-23 12:45:37.333
```  
  
### <a name="converting-string-literals-to-datetime2"></a>Преобразование строковых литералов в datetime2  
Преобразование строковых литералов в типы данных даты и времени разрешается, если все части строк записаны в допустимом формате. Иначе возникает ошибка времени выполнения. Явные или скрытые преобразования, в которых не задан стиль преобразования типов данных даты и времени в строковые литералы, будут проведены в формате по умолчанию для текущего сеанса. В следующей таблице показаны правила преобразования строковых литералов для **datetime2** тип данных.
  
|Строковый литерал входа|**datetime2(n)**|  
|---|---|
|ODBC DATE|Строковые литералы ODBC сопоставляются с **datetime** тип данных. Любая операция присваивания литералов ODBC DATETIME в **datetime2** типов приведет к неявное преобразование между **datetime** и этот тип в соответствии с правилами преобразования.|  
|ODBC TIME|См. предыдущее правило ODBC DATE.|  
|ODBC DATETIME|См. предыдущее правило ODBC DATE.|  
|только DATE|Компонент TIME по умолчанию имеет значение 00:00:00.|  
|только TIME|Компонент DATE по умолчанию имеет значение 1900-1-1.|  
|только TIMEZONE|Указаны значения по умолчанию.|  
|DATE + TIME|Простейший.|  
|DATE + TIMEZONE|Не допускается.|  
|TIME + TIMEZONE|Компонент DATE по умолчанию имеет значение 1900-1-1. Входное значение TIMEZONE не учитывается.|  
|DATE + TIME + TIMEZONE|Используется локальный компонент DATETIME.|  
  
## <a name="examples"></a>Примеры  
В следующем примере сравниваются результаты приведения строкового типа к каждому из **даты** и **время** тип данных.
  
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
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
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
  
  
