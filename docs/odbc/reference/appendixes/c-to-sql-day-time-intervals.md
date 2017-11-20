---
title: "C в SQL: интервалы времени день | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61c271a9de10bbc43db116f576b0c34589f899f3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-day-time-intervals"></a>C в SQL: интервалы времени дня
Идентификаторы типов данных ODBC C интервал времени дня следующие:  
  
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
  
 Следующая таблица показывает ODBC SQL типы данных, к которым может быть преобразован данных C интервал. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR []<br /><br /> SQL_VARCHAR []<br /><br /> SQL_LONGVARCHAR []|Длина столбца в байтах > = байт символов<br /><br /> Длина в байтах столбца < символов длина byte []<br /><br /> Значение данных не допустимый интервал литерала|н/д<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR []<br /><br /> SQL_WVARCHAR []<br /><br /> SQL_WLONGVARCHAR []|Длина столбца символ > = длина символов в данных<br /><br /> Длина столбца символ < длина данных []<br /><br /> Значение данных не допустимый интервал литерала|н/д<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Преобразование интервала одному полю не привел к усечение всего цифр<br /><br /> Преобразование привело к усечению всей цифр|н/д<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Преобразовать значение данных было без усечения всех полей<br /><br /> Одно или несколько полей значений данных были усечены во время преобразования|н/д<br /><br /> 22015|  
  
 [] типы данных всех C интервал можно преобразовать в символьный тип данных.  
  
 [b] Если поле "тип" в структуре интервал таким образом, что интервал состоит из одного поля (SQL_DAY, SQL_HOUR, SQL_MINUTE или SQL_SECOND), тип C интервал могут преобразовываться в любой точное числовое значение (SQL_TINYINT SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT SQL_DECIMAL или SQL_NUMERIC).  
  
 Преобразование типа C интервал по умолчанию — в интервал времени дня в соответствующий тип SQL.  
  
 Драйвер не учитывает значение длины/индикатора при преобразовании данных из типа данных C интервал и предполагает, что размер буфера данных размер типа данных C интервал. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.  
  
 В следующем примере показано, как для отправки данных interval C, хранится в структуре SQL_INTERVAL_STRUCT в столбец базы данных. Структура интервала содержит интервал DAY_TO_SECOND; он будет храниться в столбце типа SQL_INTERVAL_DAY_TO_MINUTE базы данных.  
  
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

