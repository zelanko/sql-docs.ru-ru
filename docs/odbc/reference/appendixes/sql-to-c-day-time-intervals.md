---
title: 'SQL в C: Интервалы времени дня | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee08f42a4ccd7eb51f45e1654f20e264f80c49d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270431"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL в C: Интервалы времени дня

Ниже перечислены идентификаторы для типов данных ODBC SQL интервал времени дня.

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

Следующая таблица показывает ODBC C типы данных, к которым могут преобразовываться интервал времени дня данных SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).

|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Все типы интервала C времени дня|В конце часть полей не усечены<br /><br /> В конце поля часть усечена<br /><br /> Точность целевого объекта недостаточно велик для хранения данных из источника|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных<br /><br /> Длина данных<br /><br /> Не определено.|н/д<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b] SQL_C_UTINYINT[b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG[b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]|Интервал точности был одним полем и данные преобразованы без усечения<br /><br /> Интервал точности был одним полем и усечен дробного<br /><br /> Интервал точности был один поле и усеченное совершенно<br /><br /> Точность интервала не был одним полем|Данные<br /><br /> Усеченные данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных<br /><br /> Длина данных<br /><br /> Размер типа данных C|н/д<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_CHAR|Длина байтов символьной < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) > = *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина символьной < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) > = *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
  
 [a] интервал времени дня объект тип SQL можно преобразовать в любой тип интервала времени дня C.  
  
 [b] Если точности интервала одно поле (один из день, час, минуты или секунды), интервал тип SQL можно преобразовать в любой точный числовой (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  
  
Преобразования по умолчанию интервала тип SQL — соответствующие типы данных C интервал. Затем приложение выполняет привязку столбца или параметра (или задает поле SQL_DESC_DATA_PTR в соответствующую запись Отменить) для на инициализированный SQL_INTERVAL_STRUCT структуру (или передает указатель на структуру SQL_ INTERVAL_STRUCT как *TargetValuePtr* аргумента в вызове **SQLGetData**).  
  
Следующий пример демонстрирует способ передачи данных из столбца типа SQL_INTERVAL_DAY_TO_MINUTE в структуру SQL_INTERVAL_STRUCT таким образом, он возвращается как интервал DAY_TO_HOUR.  

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
