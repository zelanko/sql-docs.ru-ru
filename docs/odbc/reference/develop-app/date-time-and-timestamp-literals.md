---
title: Литералы отметки времени, даты и времени | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], literals
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a13356aae88f332132bc6e8f6d6578971d2be99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641022"
---
# <a name="date-time-and-timestamp-literals"></a>Литералы даты, времени и отметок времени
Escape-последовательность для литералов даты, времени и timestamp —  
  
 **{** _-тип_ **"** _значение_ **"}**  
  
 где *литерал типа* одно из значений, перечисленных в следующей таблице.  
  
|*тип литерала*|Значение|Форматирование из *значение*|  
|---------------------|-------------|-----------------------|  
|**d**|Дата|*гггг*-*мм*-*дд*|  
|**t**|Время *|*hh*:*мм*:*ss*[1]|  
|**служб терминалов**|Отметка времени|*гггг*-*мм*-*дд* *hh*:*мм*:*ss*[.*f...* ] [1]|  
  
 [1] количество цифр справа от десятичного разделителя в определенный интервал времени или метки времени, литерал, содержащий компонент секунд зависит точность секунды, а в поле дескриптора SQL_DESC_PRECISION. (Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Дополнительные сведения о дату, время и управляющие последовательности отметок времени, см. в разделе [дату, время и управляющие последовательности отметок времени](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) в приложение в: Грамматика SQL.  
  
 Например оба из следующих инструкций SQL обновить открытой датой заказа на продажу 1023 в таблице Orders. В первой инструкции используется синтаксис escape-последовательности. Вторая инструкция имеет собственный синтаксис Oracle Rdb для столбца даты и не поддерживает взаимодействие.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Escape-последовательность для даты, времени или метки времени литерал также может размещаться в символьной переменной, привязанного к даты, времени или значение параметра метки времени. Например следующий код использует параметр даты, привязан к переменной символ для обновления открытой датой заказа на продажу 1023 в таблице Orders:  
  
```  
SQLCHAR      OpenDate[56]; // The size of a date literal is 55.  
SQLINTEGER   OpenDateLenOrInd = SQL_NTS;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_TYPE_DATE, 0, 0,  
                  OpenDate, sizeof(OpenDate), &OpenDateLenOrInd);  
  
// Place the date in the OpenDate variable. In addition to the escape  
// sequence shown, it would also be possible to use either of the  
// strings "{d '1995-01-15'}" and "15-Jan-1995", although the latter  
// is data source-specific.  
strcpy_s( (char*) OpenDate, _countof(OpenDate), "{d '1995-01-15'}");  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Orders SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Тем не менее это обычно более эффективно, чтобы привязать параметр непосредственно на структуру:  
  
```  
SQL_DATE_STRUCT   OpenDate;  
SQLINTEGER        OpenDateInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &OpenDate, 0, &OpenDateLen);  
  
// Place the date in the dsOpenDate structure.  
OpenDate.year = 1995;  
OpenDate.month = 1;  
OpenDate.day = 15;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Employee SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности ODBC для даты, времени или метки времени литералы, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных даты, времени или метки времени, он также должен поддерживать соответствующие escape-последовательность.  
  
 Источники данных также может поддерживать литералами даты и времени, определенному в спецификации ANSI SQL-92, которые отличаются от escape-последовательности ODBC для даты, времени или метки времени литералы. Чтобы определить, поддерживает ли источник данных ANSI литералы, приложение вызывает **SQLGetInfo** с параметром SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности ODBC для литералов интервала, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных datetime интервал, он также должен поддерживать соответствующие escape-последовательность.  
  
 Источники данных также может поддерживать литералами даты и времени, определенному в спецификации ANSI SQL-92, которые отличаются от escape-последовательности ODBC для литералов даты и времени интервала. Чтобы определить, поддерживает ли источник данных ANSI литералы, приложение вызывает **SQLGetInfo** с параметром SQL_ANSI_SQL_DATETIME_LITERALS.
