---
title: 'СЗЛ в C: Дневные интервалы (ru) Документы Майкрософт'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296474"
---
# <a name="sql-to-c-day-time-intervals"></a>Преобразование данных из SQL в C: интервалы времени дня

Идентификаторы для типов данных дневного интервала ODBC S'L:

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

В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные дневного интервала S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.

|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Все типы интервалов C в дневное время|Трейлинговые поля часть не усечены<br /><br /> Трейлинговые поля часть усеченных<br /><br /> Ведущая точность мишени недостаточно велика для хранения данных из источника|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных<br /><br /> Длина данных<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT SQL_C_BIGINT SQL_C_NUMERIC SQL_C_ULONG SQL_C_SLONG SQL_C_UTINYINT SQL_C_USHORT SQL_C_SHORT|Интервал точность была одно поле и данные были преобразованы без усечения<br /><br /> Интервал точность была одним полем и усеченные дробные<br /><br /> Интервал точность была одним полем и усеченных целом<br /><br /> Интервал точность не было ни одного поля|Данные<br /><br /> Truncated данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных<br /><br /> Длина данных<br /><br /> Размер типа данных C|Недоступно<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_CHAR|Длина байта персонажа < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр >*BufferLength*|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина персонажа < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр >*BufferLength*|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
  
 Тип интервала дневного времени S'L может быть преобразован в любой тип интервала C дневного времени.  
  
 Если точность интервала представляет собой одно поле (одно из DAY, HOUR, MINUTE, или SECOND), то тип интервала S'L может быть преобразован в любой точный числовой (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  
  
Преобразование по умолчанию интервала типа S'L происходит в соответствующий тип данных интервала C. Затем приложение связывает столбец или параметр (или устанавливает поле SQL_DESC_DATA_PTR в соответствующей записи ARD), чтобы указать на инициализированную структуру SQL_INTERVAL_STRUCT (или передает указатель на SQL_ INTERVAL_STRUCT структуру в качестве аргумента *TargetValuePtr* в вызове к **S'LGetData).**  
  
В следующем примере показано, как передавать данные из столбца SQL_INTERVAL_DAY_TO_MINUTE в структуру SQL_INTERVAL_STRUCT таким образом, чтобы они возвращались в качестве DAY_TO_HOUR интервала.  

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
