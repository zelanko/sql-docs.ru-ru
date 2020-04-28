---
title: 'С SQL на C: день — интервалы времени | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1318da5285ba2384dd23e4c235e698aa72c7658e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296474"
---
# <a name="sql-to-c-day-time-intervals"></a>Преобразование данных из SQL в C: интервалы времени дня

Ниже приведены идентификаторы для типов данных ODBC SQL для интервала времени.

- SQL_INTERVAL_DAY
- SQL_INTERVAL_DAY_TO_MINUTE
- SQL_INTERVAL_HOUR
- SQL_INTERVAL_DAY_TO_SECOND
- SQL_INTERVAL_MINUTE
- SQL_INTERVAL_HOUR_TO_MINUTE
- SQL_INTERVAL_SECOND
- SQL_INTERVAL_HOUR_TO_SECOND
- SQL_INTERVAL_DAY_TO_HOUR
- SQL_INTERVAL_MINUTE_TO_SECOND

В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные SQL в течение дня времени. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).

|Идентификатор типа C|Тест|**таржетвалуептр*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Все типы интервалов C-дневного времени|Часть конечных полей не усекается<br /><br /> Часть конечных полей усечена<br /><br /> Начальная точность целевого объекта недостаточно велика для хранения данных из источника|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных<br /><br /> Длина данных<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT [b] SQL_C_SHORT [b] SQL_C_SLONG [b] SQL_C_ULONG [b] SQL_C_NUMERIC [b] SQL_C_BIGINT [b]|Точность интервала была одним полем, и данные были преобразованы без усечения<br /><br /> Точность интервала была одиночным полем и усечена в дробной части<br /><br /> Точность интервала была одиночным полем и усечена целиком<br /><br /> Точность интервала не является одним полем|Данные<br /><br /> Усеченные данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных<br /><br /> Длина данных<br /><br /> Размер типа данных C|Недоступно<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Длина данных в байтах <= *BufferLength*<br /><br /> Длина байта данных > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_CHAR|Длина байта символов < *BufferLength*<br /><br /> Целое число (в отличие от дробной) цифр < *BufferLength*<br /><br /> Число целых знаков (в отличие от дробной) >= *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Символьная длина < *BufferLength*<br /><br /> Целое число (в отличие от дробной) цифр < *BufferLength*<br /><br /> Число целых знаков (в отличие от дробной) >= *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
  
 [a] тип SQL для интервала времени суток может быть преобразован в любой тип временного интервала C.  
  
 [b] Если точность интервала является одним полем (один день, час, МИНУТа или СЕКУНДа), то тип SQL Interval можно преобразовать в любой точный числовой (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  
  
По умолчанию тип SQL Interval преобразуется в соответствующий тип данных Interval в C. Затем приложение привязывает столбец или параметр (или задает поле SQL_DESC_DATA_PTR в соответствующей записи АРД) для указания на инициализированную структуру SQL_INTERVAL_STRUCT (или передает указатель на структуру SQL_ INTERVAL_STRUCT в качестве аргумента *таржетвалуептр* в вызове **SQLGetData**).  
  
В следующем примере показано, как передавать данные из столбца типа SQL_INTERVAL_DAY_TO_MINUTE в структуру SQL_INTERVAL_STRUCT таким образом, что она возвращается в качестве интервала DAY_TO_HOUR.  

```cpp
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```
