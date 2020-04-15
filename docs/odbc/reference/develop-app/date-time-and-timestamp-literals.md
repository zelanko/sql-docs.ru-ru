---
title: Дата, время и хронология Литературы Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d899938be4689daab50a773f189219a797794006
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288300"
---
# <a name="date-time-and-timestamp-literals"></a>Литералы даты, времени и отметок времени
Последовательность побега для даты, времени и отметки времени буквальные  
  
 **значение**_типа_ _value_ **'типа'»** **'**    
  
 где *буквальный тип* является одним из значений, перечисленных в следующей таблице.  
  
|*буквальный тип*|Значение|Формат *стоимости*|  
|---------------------|-------------|-----------------------|  
|**D**|Дата|*yyyy*-*мм*-*dd*|  
|**T**|Время»|*hh*:*мм*:*ss*|  
|**Ts**|Отметка времени|*yyyy*-*мм*-*dd* *hh*:*мм*:*ss*.* f...* [1]|  
  
 Количество цифр справа от десятичной точки в интервале времени или временной метки, содержащего секундный компонент, зависит от секундной точности, как это содержится в поле SQL_DESC_PRECISION дескриптора. (Для получения более подробной информации, [см.](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Для получения более подробной информации о дате, времени и последовательности побега меток времени [см.](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md)  
  
 Например, обе следующие заявления s'L обновляют открытую дату заказа на продажу 1023 в таблице заказов. В первом заявлении используется синтаксис последовательности побега. Второе утверждение использует родной синтаксис Oracle Rdb для столбца DATE и не совместимо.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Последовательность побега для даты, времени или отметки времени буквальная также может быть помещена в переменную символа, связанную с параметром даты, времени или отметки времени. Например, в следующем коде используется параметр даты, привязанный к переменной символа, для обновления даты открытия заказа 1023 в таблице заказов:  
  
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
  
 Однако, как правило, более эффективно связывать параметр непосредственно со структурой даты:  
  
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
  
 Чтобы определить, поддерживает ли драйвер последовательности побега ODBC для даты, времени или отметки времени в буквальном смысле, приложение вызывает **S'LGetTypeInfo.** Если источник данных поддерживает дату, время или тип метки времени, он также должен поддерживать соответствующую последовательность побега.  
  
 Источники данных могут также поддерживать буквальные данные по дате, определенные в спецификации ANSI S'L-92, которые отличаются от последовательностей побега ODBC для даты, времени или буквалов времени. Чтобы определить, поддерживает ли источник данных буквальные данные ANSI, приложение вызывает **s'LGetInfo** с опцией SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Чтобы определить, поддерживает ли драйвер последовательности побега ODBC для интервалов в буквальном смысле, приложение вызывает **S'LGetTypeInfo**. Если источник данных поддерживает тип интервала времени даты, он также должен поддерживать соответствующую последовательность побега.  
  
 Источники данных могут также поддерживать буквальные данные по дате, определенные в спецификации ANSI S'L-92, которые отличаются от последовательностей побега ODBC для буквальных интервалов времени даты. Чтобы определить, поддерживает ли источник данных буквальные данные ANSI, приложение вызывает **s'LGetInfo** с опцией SQL_ANSI_SQL_DATETIME_LITERALS.
