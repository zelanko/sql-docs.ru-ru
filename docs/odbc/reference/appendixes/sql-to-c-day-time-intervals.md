---
title: "SQL на C: интервалы времени день | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b7952543ea1a014555b1227336355a2d6c31563
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-to-c-day-time-intervals"></a>SQL, чтобы интервалы времени дня C:
Идентификаторы типов данных ODBC SQL интервал времени дня следующие:  
  
 SQL_INTERVAL_DAY  
  
 SQL_INTERVAL_DAY_TO_MINUTE  
  
 SQL_INTERVAL_HOUR  
  
 SQL_INTERVAL_DAY_TO_SECOND  
  
 SQL_INTERVAL_MINUTE  
  
 SQL_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_INTERVAL_SECOND  
  
 SQL_INTERVAL_HOUR_TO_SECOND  
  
 SQL_INTERVAL_DAY_TO_HOUR  
  
 SQL_INTERVAL_MINUTE_TO_SECOND  
  
 Следующая таблица показывает ODBC C типы данных, к которым может быть преобразован день интервала данных SQL. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Все типы интервала C времени дня|Часть поля не усекаются замыкающие<br /><br /> В конце поля часть усечена<br /><br /> Начальные точность целевого объекта недостаточно велик для хранения данных из источника|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных<br /><br /> Длина данных<br /><br /> Не определено.|н/д<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT [b] SQL_C_SHORT [b] SQL_C_SLONG [b] SQL_C_ULONG [b] SQL_C_NUMERIC [b] SQL_C_BIGINT [b]|Интервал точность была одним полем и преобразован без усечения данных<br /><br /> Точность интервал был одним полем и усечение долей<br /><br /> Интервал точность была отдельное поле и усеченное всего<br /><br /> Точность интервала не был одного поля|data<br /><br /> Усеченные данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Длина данных<br /><br /> Длина данных<br /><br /> Размер типа данных C|н/д<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Байтовая длина данных > *BufferLength*|data<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_CHAR|Длина байтов символьной < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) > = *BufferLength*|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
_C_WCHAR|Длина символьной < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) < *BufferLength*<br /><br /> Число цифр в целом (в отличие от доли) > = *BufferLength*|data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
  
 [] A дневное время интервалом типа SQL можно преобразовать в любой день интервала C тип.  
  
 [b] Если точности интервала одно поле (один из день, час, МИНУТУ или СЕКУНДУ), можно преобразовать интервал тип SQL для любой точное числовое значение (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  
  
 Преобразования по умолчанию интервала тип SQL — соответствующие типы данных C интервал. Затем приложение привязывает столбца или параметра (или задает поле SQL_DESC_DATA_PTR в соответствующей записи Отменить) для указания инициализированный SQL_INTERVAL_STRUCT структуры (или передает указатель в качестве структуруSQL_INTERVAL_STRUCT*TargetValuePtr* аргумента в вызове **SQLGetData**).  
  
 Ниже приведен пример перенос данных из столбца типа SQL_INTERVAL_DAY_TO_MINUTE в структуре SQL_INTERVAL_STRUCT таким образом, что он возвращается как DAY_TO_HOUR интервал.  
  
```  
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
