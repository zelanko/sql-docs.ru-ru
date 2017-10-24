---
title: "Данных даты и времени типы и функции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server]
- date and time [SQL Server], all data types and functions
- date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 83e378a2-6e89-4c80-bc4f-644958d9e0a9
caps.latest.revision: 79
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 60272ce672c0a32738b0084ea86f8907ec7fc0a5
ms.openlocfilehash: 7ce3baac7ec87ff3cad771234ab1196fb0a3855e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="date-and-time-data-types-and-functions-transact-sql"></a>Типы данных и функции даты и времени (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

В следующих разделах представлен обзор всех типов данных и функций даты и времени [!INCLUDE[tsql](../../includes/tsql-md.md)].
-   [Типы даты и времени данных](#DateandTimeDataTypes)  
-   [Функции даты и времени](#DateandTimeFunctions)  
    -   [Функция, которая Get системной даты и времени значения](#GetSystemDateandTimeValues)  
    -   [Функции, получающие даты и времени частей](#GetDateandTimeParts)  
    -   [Функции, получающие значения даты и времени из их компонентов](#fromParts)  
    -   [Функции, получающие даты и времени различие](#GetDateandTimeDifference)  
    -   [Функций, которые изменяют даты и значения времени](#ModifyDateandTimeValues)  
    -   [Функции, устанавливающие или получающие формат сеанса](#SetorGetSessionFormatFunctions)  
    -   [Функции, проверяющие даты и значения времени](#ValidateDateandTimeValues)  
-   [Дата и время — см. также](#DateandTimeRelatedTopics)  
  
##  <a name="DateandTimeDataTypes"></a>Типы данных даты и времени
[!INCLUDE[tsql](../../includes/tsql-md.md)] Типов данных даты и времени, перечислены в следующей таблице:
  
|Тип данных|Формат|Диапазон|Точность|Объем памяти (в байтах)|Определяемая пользователем точность в долях секунды|Смещение часового пояса|  
|---|---|---|---|---|---|---|
|[time](../../t-sql/data-types/time-transact-sql.md)|чч:мм:сс[.ннннннн]|От 00:00:00.0000000 до 23:59:59.9999999|100 наносекунд|от 3 до 5|Да|Нет|  
|[date](../../t-sql/data-types/date-transact-sql.md)|ГГГГ-ММ-ДД|От 0001-01-01 до 31.12.99|1 день|3|Нет|Нет|  
|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|ГГГГ-ММ-ДД чч:мм:сс|От 01.01.1900 до 06.06.2079|1 минута|4|Нет|Нет|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|ГГГГ-ММ-ДД чч:мм:сс[.ннн]|От 01.01.1753 до 31.12.9999|0,00333 секунды|8|Нет|Нет|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|ГГГГ-ММ-ДД чч:мм:сс[.ннннннн]|От 0001-01-01 00:00:00.0000000 до 9999-12-31 23:59:59.9999999|100 наносекунд|От 6 до 8|Да|Нет|  
|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|ГГГГ-мм-дд чч [.ннннннн] [+ &#124;-] чч: мм|От 0001-01-01 00:00:00.0000000 до 9999-12-31 23:59:59.9999999 (время в формате UTC)|100 наносекунд|От 8 до 10|Да|Да|  
  
> [!NOTE]  
>  [!INCLUDE[tsql](../../includes/tsql-md.md)] [Rowversion](../../t-sql/data-types/rowversion-transact-sql.md) тип данных не является типом данных даты или времени. **Отметка времени** является устаревшим синонимом **rowversion**.  
  
##  <a name="DateandTimeFunctions"></a>Функции даты и времени  
Функции даты и времени [!INCLUDE[tsql](../../includes/tsql-md.md)] перечислены в следующих таблицах. Дополнительные сведения о детерминизме см. в разделе [функций](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
###  <a name="GetSystemDateandTimeValues"></a>Функции, получающие значения даты и времени системы 
Все значения системной даты и времени наследуется от операционной системы компьютера, на котором работает экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
#### <a name="higher-precision-system-date-and-time-functions"></a>Высокоточные функции системной даты и времени  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Получает значения даты и времени с помощью GetSystemTimeAsFileTime() Windows API. Точность зависит от физического оборудования и версии Windows, в которой запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Точность возвращаемых значений этого API-интерфейса задана равной 100 нс. Точность может быть определена с помощью GetSystemTimeAdjustment() Windows API.
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[SYSDATETIME](../../t-sql/functions/sysdatetime-transact-sql.md)|SYSDATETIME ()|Возвращает **datetime2(7)** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Смещение часового пояса не включается.|**datetime2(7)**|Недетерминированная|  
|[SYSDATETIMEOFFSET](../../t-sql/functions/sysdatetimeoffset-transact-sql.md)|SYSDATETIMEOFFSET ( )|Возвращает **datetimeoffset(7)** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Смещение часового пояса включается.|**DateTimeOffset(7)**|Недетерминированная|  
|[SYSUTCDATETIME](../../t-sql/functions/sysutcdatetime-transact-sql.md)|SYSUTCDATETIME ( )|Возвращает **datetime2(7)** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Дата и время возвращаются в формате UTC (время по Гринвичу).|**datetime2(7)**|Недетерминированная|  
  
#### <a name="lower-precision--system-date-and-time-functions"></a>Функции даты и времени меньшей точности системы
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[CURRENT_TIMESTAMP](../../t-sql/functions/current-timestamp-transact-sql.md)|CURRENT_TIMESTAMP|Возвращает **datetime** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Смещение часового пояса не включается.|**datetime**|Недетерминированная|  
|[ФУНКЦИЯ GETDATE](../../t-sql/functions/getdate-transact-sql.md)|GETDATE ( )|Возвращает **datetime** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Смещение часового пояса не включается.|**datetime**|Недетерминированная|  
|[GETUTCDATE](../../t-sql/functions/getutcdate-transact-sql.md)|GETUTCDATE ( )|Возвращает **datetime** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Дата и время возвращаются в формате UTC (время по Гринвичу).|**datetime**|Недетерминированная|  
  
###  <a name="GetDateandTimeParts"></a>Функции, получающие компоненты даты и времени
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|--------------|------------|------------------|----------------------|-----------------|  
|[ФУНКЦИЯ DATENAME](../../t-sql/functions/datename-transact-sql.md)|Функция DATENAME ( *datepart* , *даты* )|Возвращает символьную строку, представляющий указанный *datepart* указанной даты.|**nvarchar**|Недетерминированная|  
|[DATEPART](../../t-sql/functions/datepart-transact-sql.md)|DATEPART ( *datepart* , *даты* )|Возвращает целое число, представляющее указанную *datepart* указанного *даты*.|**int**|Недетерминированная|  
|[ДЕНЬ](../../t-sql/functions/day-transact-sql.md)|ДЕНЬ ( *даты* )|Возвращает целое число, представляющее день указанной *даты*.|**int**|Детерминированное|  
|[МЕСЯЦ](../../t-sql/functions/month-transact-sql.md)|МЕСЯЦ ( *даты* )|Возвращает целое число, представляющее месяц указанной даты *даты*.|**int**|Детерминированное|  
|[ГОД](../../t-sql/functions/year-transact-sql.md)|ГОД ( *даты* )|Возвращает целое число, представляющее год указанной даты *даты*.|**int**|Детерминированное|  
  
###  <a name="fromParts"></a>Функции, получающие значения даты и времени из их компонентов
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[DATEFROMPARTS](../../t-sql/functions/datefromparts-transact-sql.md)|DATEFROMPARTS ( *года*, *месяц*, *день* )|Возвращает **даты** значение для заданного года, месяца и дня.|**date**|Детерминированное|  
|[DATETIME2FROMPARTS](../../t-sql/functions/datetime2fromparts-transact-sql.md)|DATETIME2FROMPARTS ( *года*, *месяц*, *день*, *час*, *минуту*, *секунд* , *дроби*, *точности*)|Возвращает **datetime2** значение для указанной даты и времени и с указанной точностью.|**datetime2 (** *точности* **)**|Детерминированное|  
|[DATETIMEFROMPARTS](../../t-sql/functions/datetimefromparts-transact-sql.md)|DATETIMEFROMPARTS ( *года*, *месяц*, *день*, *час*, *минуту*, *секунд* , *миллисекунд*)|Возвращает **datetime** значение для указанной даты и времени.|**datetime**|Детерминированное|  
|[DATETIMEOFFSETFROMPARTS](../../t-sql/functions/datetimeoffsetfromparts-transact-sql.md)|DATETIMEOFFSETFROMPARTS ( *года*, *месяц*, *день*, *час*, *минуту*,  *секунд*, *дроби*, *hour_offset*, *minute_offset*, *точности*)|Возвращает **datetimeoffset** значение для указанной даты и времени и с указанным смещением и точностью.|**DateTime (** *точности* **)**|Детерминированное|  
|[SMALLDATETIMEFROMPARTS](../../t-sql/functions/smalldatetimefromparts-transact-sql.md)|SMALLDATETIMEFROMPARTS ( *года*, *месяц*, *день*, *час*, *минуту* )|Возвращает **smalldatetime** значение для указанной даты и времени.|**smalldatetime**|Детерминированное|  
|[TIMEFROMPARTS](../../t-sql/functions/timefromparts-transact-sql.md)|TIMEFROMPARTS ( *час*, *минуту*, *секунд*, *дроби*, *точности* )|Возвращает **время** значение в течение определенного времени и с указанной точностью.|**время (** *точности* **)**|Детерминированное|  
  
###  <a name="GetDateandTimeDifference"></a>Функции, получающие разность даты и времени
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[ФУНКЦИЯ DATEDIFF](../../t-sql/functions/datediff-transact-sql.md)|DATEDIFF ( *datepart* , *startdate* , *enddate* )|Возвращает количество даты или времени *datepart* границы, пересекаемых между двумя указанными датами.|**int**|Детерминированное|  
|[DATEDIFF_BIG](../../t-sql/functions/datediff-big-transact-sql.md)|DATEDIFF_BIG ( *datepart* , *startdate* , *enddate* )|Возвращает количество даты или времени *datepart* границы, пересекаемых между двумя указанными датами.|**bigint**|Детерминированное|  
  
###  <a name="ModifyDateandTimeValues"></a>Функции, которые изменяют значения даты и времени
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[ФУНКЦИЯ DATEADD](../../t-sql/functions/dateadd-transact-sql.md)|Функция DATEADD (*datepart* , *номер* , *даты* )|Возвращает новый **datetime** значения путем добавления интервала к указанной *datepart* указанного *даты*.|Тип данных *даты* аргумент|Детерминированное|  
|[EOMONTH](../../t-sql/functions/eomonth-transact-sql.md)|EOMONTH ( *start_date* [, *month_to_add* ])|Возвращает последний день месяца, содержащего указанную дату, с необязательным смещением.|Тип возвращаемого значения — это тип *start_date* или **даты**.|Детерминированное|  
|[SWITCHOFFSET](../../t-sql/functions/switchoffset-transact-sql.md)|КОММУТАТОР*СМЕЩЕНИЕ* (*DATETIMEOFFSET* , *time_zone*)|КОММУТАТОР*СМЕЩЕНИЕ* изменяет смещение часового пояса для значения DATETIMEOFFSET и сохраняет значение UTC.|**DateTimeOffset** с точностью в долях *DATETIMEOFFSET*|Детерминированное|  
|[TODATETIMEOFFSET](../../t-sql/functions/todatetimeoffset-transact-sql.md)|TODATETIMEOFFSET (*выражение* , *time_zone*)|TODATETIMEOFFSET преобразует значение типа datetime2 в значение типа datetimeoffset. Значение datetime2 преобразуется в местное время для указанного time_zone.|**DateTimeOffset** с точностью в долях *datetime* аргумент|Детерминированное|  
  
###  <a name="SetorGetSessionFormatFunctions"></a>Функции, получить или задать формат сеанса
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md)|@@DATEFIRST|Возвращает текущее значение параметра SET DATEFIRST для сеанса.|**tinyint**|Недетерминированная|  
|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)|SET DATEFIRST { *номер* &#124;  **@**  *number_var* }|Устанавливает первый день недели в виде числа от 1 до 7.|Неприменимо|Неприменимо|  
|[SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|SET DATEFORMAT { *формат* &#124;  **@**  *format_var* }|Задает порядок составляющих даты (месяц/день/год) для ввода **datetime** или **smalldatetime** данных.|Неприменимо|Неприменимо|  
|[@@LANGUAGE](../../t-sql/functions/language-transact-sql.md)|@@LANGUAGE|Возвращает название используемого в данный момент языка. @@LANGUAGE не является функцией даты или времени. Однако на данные, выводимые функциями даты, могут повлиять настройки языка.|Неприменимо|Неприменимо|  
|[УСТАНОВИТЬ ЯЗЫК](../../t-sql/statements/set-language-transact-sql.md)|SET LANGUAGE {[N] **"***язык***"** &#124;  **@**  *language_var* }|Устанавливает языковую среду сеанса и системных сообщений. SET LANGUAGE не является функцией даты или времени. Однако на данные, выводимые функциями даты, влияет параметр языка.|Неприменимо|Неприменимо|  
|[sp_helplanguage](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)|**sp_helplanguage** [[  **@language =** ] **"***язык***"** ]|Возвращает сведения о формате даты всех поддерживаемых языков. **sp_helplanguage** не является дата или время хранимой процедуры. Однако на данные, выводимые функциями даты, влияет параметр языка.|Неприменимо|Неприменимо|  
  
###  <a name="ValidateDateandTimeValues"></a>Функции, проверяющие значения даты и времени
  
|Функция|Синтаксис|Возвращаемое значение|Тип возвращаемых данных|Детерминизм|  
|---|---|---|---|---|
|[ФУНКЦИЯ ISDATE](../../t-sql/functions/isdate-transact-sql.md)|Функция ISDATE ( *выражение* )|Определяет, является ли **datetime** или **smalldatetime** входное выражение является допустимым значением даты или времени.|**int**|Функция ISDATE детерминирована, только если используется совместно с функцией CONVERT и если заданный параметр стиля CONVERT не равен 0, 100, 9 или 109.|  
  
##  <a name="DateandTimeRelatedTopics"></a>Дата и время см. также 
  
|Раздел|Description|  
|-----------|-----------------|  
|[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)|Предоставляет сведения о преобразовании значений даты и времени в строковые литералы и обратно, а также в другие форматы даты и времени.|  
|[Написание инструкций Transact-SQL, адаптированных к международному использованию](../../relational-databases/collations/write-international-transact-sql-statements.md)|Содержит рекомендации для обеспечения переносимости баз данных и приложений баз данных, использующих [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции с одного языка на другой или поддержку нескольких языков.|  
|[Скалярные функции ODBC &#40; Transact-SQL &#41;](../../t-sql/functions/odbc-scalar-functions-transact-sql.md)|Предоставляет сведения о скалярных функций ODBC, которые могут использоваться в [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции. Сюда входят функции даты и времени ODBC.|  
|[В ЧАСОВОМ ПОЯСЕ &#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)|Обеспечивает преобразование часового пояса.|  
  
## <a name="see-also"></a>См. также:
[Функции](../../t-sql/functions/functions.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  

