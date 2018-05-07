---
title: Даты, времени и отметок времени литералы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], literals
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c41d78b848009083abef2595d8628bb8fa1c0b0e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="date-time-and-timestamp-literals"></a>Даты, времени и отметок времени литералы
Escape-последовательность для литералов даты, времени и отметок времени  
  
 **{***-тип* **"** *значение* **"}**  
  
 где *литерал типа* одно из значений, перечисленных в следующей таблице.  
  
|*тип литерала*|Значение|Форматирование из *значение*|  
|---------------------|-------------|-----------------------|  
|**d**|Дата|*гггг*-*мм*-*дд*|  
|**t**|Время *|*hh*:*мм*:*ss*[1]|  
|**служб терминалов**|Отметка времени|*гггг*-*мм*-*дд* *hh*:*мм*:*ss*[.*f...*] [1]|  
  
 [1] количество цифр справа от десятичной запятой в течение интервала времени или timestamp, литерал, содержащий компонент секунд зависит точность секунды, как указано в поле SQL_DESC_PRECISION дескриптора. (Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Дополнительные сведения о дате, времени и управляющие последовательности отметок времени см. в разделе [даты, времени и управляющие последовательности отметок времени](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) в грамматику SQL приложение C:.  
  
 Например оба из следующих инструкций SQL обновить открытой датой заказа на продажу 1023 в таблице Orders. В первом операторе используется синтаксис escape-последовательности. Вторая инструкция использует собственный синтаксис Oracle Rdb для столбца даты и не поддерживает взаимодействие.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Escape-последовательность для даты, времени или отметка времени литерал также может быть помещен в символьной переменной, привязанный к даты, времени или параметр отметки времени. Например следующий код использует параметр даты, привязан к переменной символ для обновления открытой датой заказа на продажу 1023 в таблице Orders:  
  
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
  
 Тем не менее обычно более эффективен, чтобы привязать параметр непосредственно на структуру данных:  
  
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
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности ODBC для даты, времени или отметка времени литералы, приложение вызывает **SQLGetTypeInfo**. Источник данных поддерживает тип данных даты, времени или отметки времени, должен также поддерживать соответствующие escape-последовательность.  
  
 Источники данных также могут поддерживать литералами даты и времени, определенные в спецификации ANSI SQL-92, отличающихся от escape-последовательности ODBC для даты, времени или литералы отметки времени. Чтобы определить, поддерживает ли источник данных ANSI литералы, приложение вызывает **SQLGetInfo** с параметром SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности ODBC для литералов интервал, приложение вызывает **SQLGetTypeInfo**. Источник данных поддерживает тип интервала datetime, должно также поддерживать соответствующие escape-последовательность.  
  
 Источники данных также могут поддерживать литералами даты и времени, определенные в спецификации ANSI SQL-92, отличающихся от escape-последовательности ODBC для литералов даты и времени интервала. Чтобы определить, поддерживает ли источник данных ANSI литералы, приложение вызывает **SQLGetInfo** с параметром SQL_ANSI_SQL_DATETIME_LITERALS.
