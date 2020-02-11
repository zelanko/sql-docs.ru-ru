---
title: Литералы даты, времени и отметок времени | Документация Майкрософт
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
ms.openlocfilehash: e6191995c9d1c488fc5af056248ba39dd3eb4607
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076984"
---
# <a name="date-time-and-timestamp-literals"></a>Литералы даты, времени и отметок времени
Escape-последовательность литералов даты, времени и отметок времени:  
  
 **{**  _-Type_ **'** _value_ **'}**  
  
 где *Literal-Type* — одно из значений, перечисленных в следующей таблице.  
  
|*тип литерала*|Значение|Формат *значения*|  
|---------------------|-------------|-----------------------|  
|**четырехмерного**|Дата|*гггг*-** мм-*дд*|  
|**t**|Таймаут|*чч*:*мм*:*СС*[1]|  
|**лицензии**|Timestamp|*гггг*-** мм-*дд* *чч*:*мм*:*СС*[.* f...*] одного|  
  
 [1] количество цифр справа от десятичного разделителя в литерале времени или интервала времени, содержащего компонент секунд, зависит от точности секунд, которая содержится в поле дескриптора SQL_DESC_PRECISION. (Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Дополнительные сведения о escape-последовательностям даты, времени и меток времени см. в разделе [Дата, время и escape-последовательности меток](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) времени в приложении C: грамматика SQL.  
  
 Например, обе следующие инструкции SQL обновляют дату открытия заказа на продажу 1023 в таблице Orders. В первом операторе используется синтаксис escape-последовательности. Вторая инструкция использует собственный синтаксис Oracle RDB для столбца DATE и не поддерживает взаимодействие.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Escape-последовательность для литерала даты, времени или timestamp также может быть помещена в символьную переменную, привязанную к параметру даты, времени или метки времени. Например, следующий код использует параметр даты, привязанный к символьной переменной, для обновления даты открытия заказа на продажу 1023 в таблице Orders:  
  
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
  
 Однако обычно более эффективно привязывать параметр непосредственно к структуре даты:  
  
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
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности ODBC для литералов даты, времени или меток времени, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных даты, времени или отметки времени, он также должен поддерживать соответствующую escape-последовательность.  
  
 Источники данных также могут поддерживать литералы datetime, определенные в спецификации ANSI SQL-92, которые отличаются от escape-последовательностей ODBC для литералов даты, времени или меток времени. Чтобы определить, поддерживает ли источник данных литералы ANSI, приложение вызывает **SQLGetInfo** с параметром SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности ODBC для литералов интервала, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных интервала datetime, он также должен поддерживать соответствующую escape-последовательность.  
  
 Источники данных также могут поддерживать литералы datetime, определенные в спецификации ANSI SQL-92, которые отличаются от escape-последовательностей ODBC для литералов интервалов DateTime. Чтобы определить, поддерживает ли источник данных литералы ANSI, приложение вызывает **SQLGetInfo** с параметром SQL_ANSI_SQL_DATETIME_LITERALS.
