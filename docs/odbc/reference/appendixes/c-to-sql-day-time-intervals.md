---
title: 'C в SQL: день — интервалы времени | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3a4df236273b5afcaba78052ac236669bb133f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019375"
---
# <a name="c-to-sql-day-time-intervals"></a>Преобразование из C в SQL: интервалы времени дня
Идентификаторы для типов данных ODBC C в течение дня времени:  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы данные интервала C. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Длина байта столбца >= Длина байтового символа<br /><br /> Длина байта столбца < длина байтовой кодировки [a]<br /><br /> Значение данных не является допустимым литералом интервала|Недоступно<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Длина символа столбца >= символьная длина данных<br /><br /> Длина символов в столбцах < символьной длины данных [a]<br /><br /> Значение данных не является допустимым литералом интервала|Недоступно<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Преобразование интервала с одним полем не привело к усечению целых цифр<br /><br /> Преобразование привело к усечению целых цифр|Недоступно<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Значение данных было преобразовано без усечения каких бы то ни было полей<br /><br /> Одно или несколько полей значения данных были усечены во время преобразования|Недоступно<br /><br /> 22015|  
  
 [a] все типы данных интервала C могут быть преобразованы в символьный тип данных.  
  
 [b] Если поле типа в структуре интервала имеет значение, равное одному полю (SQL_DAY, SQL_HOUR, SQL_MINUTE или SQL_SECOND), то тип "интервал C" можно преобразовать в любой точный числовой (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT , SQL_DECIMAL или SQL_NUMERIC).  
  
 По умолчанию, преобразование типа Time C соответствует типу SQL соответствующего интервала дня.  
  
 Драйвер не учитывает значение длины или индикатора при преобразовании данных из типа данных Interval C и предполагает, что размер буфера данных равен размеру типа данных Interval C. Значение length/индикатора передается в аргументе *StrLen_Or_Ind* в **SQLPutData** и в буфере, указанном аргументом *StrLen_or_IndPtr* в **SQLBindParameter**. Буфер данных указывается с помощью аргумента *датаптр* в **SQLPutData** и аргумента *параметервалуептр* в **SQLBindParameter**.  
  
 В следующем примере показано, как отправить данные интервала C, хранящиеся в структуре SQL_INTERVAL_STRUCT, в столбец базы данных. Структура интервала содержит DAY_TO_SECOND интервал; Он будет храниться в столбце базы данных типа SQL_INTERVAL_DAY_TO_MINUTE.  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
