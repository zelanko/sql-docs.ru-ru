---
title: 'С SQL на C: интервалы лет-месяцев | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c7412226dd0674022da022b0a0a63e5bf2063cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065042"
---
# <a name="sql-to-c-year-month-intervals"></a>Преобразование данных из SQL в C: интервалы месяцев года

В качестве идентификаторов для типов данных ODBC SQL в месяц используется следующее:

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные SQL для интервала ежегодного месяца. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Идентификатор типа C|Тест|таржетвалуептр|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH [a]<br /><br /> SQL_C_INTERVAL_YEAR [a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH [a]|Часть конечных полей не усекается<br /><br /> Часть конечных полей усечена<br /><br /> Начальная точность целевого объекта недостаточно велика для хранения данных из источника|Данные<br /><br /> Усеченные данные<br /><br /> Не определено|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено|Недоступно<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b]<br /><br /> SQL_C_UTINYINT [b]<br /><br /> SQL_C_USHORT [b]<br /><br /> SQL_C_SHORT [b]<br /><br /> SQL_C_SLONG [b]<br /><br /> SQL_C_ULONG [b]<br /><br /> SQL_C_NUMERIC [b]<br /><br /> SQL_C_BIGINT [b]|Точность интервала была одним полем, и данные были преобразованы без усечения<br /><br /> Точность интервала была одиночным полем и усечена целиком<br /><br /> Точность интервала не является одним полем|Данные<br /><br /> Усеченные данные<br /><br /> Не определено|Размер типа данных C<br /><br /> Длина данных в байтах<br /><br /> Размер типа данных C|Недоступно<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Длина данных в байтах <= *BufferLength*<br /><br /> Длина байта данных > *BufferLength*|Данные<br /><br /> Не определено|Длина данных в байтах<br /><br /> Не определено|Недоступно<br /><br /> 22003|  
|SQL_C_CHAR|Длина байта символов < *BufferLength*<br /><br /> Целое число (в отличие от дробной) цифр < *BufferLength*<br /><br /> Число целых знаков (в отличие от дробной) >= *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Символьная длина < *BufferLength*<br /><br /> Целое число (в отличие от дробной) цифр < *BufferLength*<br /><br /> Число целых знаков (в отличие от дробной) >= *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено|Недоступно<br /><br /> 01004<br /><br /> 22003|  
  
 [a] тип SQL-месяца для интервала год может быть преобразован в любой тип времени года C.  
  
 [b] Если точность интервала является одним полем (один из лет или месяцев), то тип SQL Interval можно преобразовать в любой точный числовой (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC).  

## <a name="default-conversions"></a>Преобразования по умолчанию

По умолчанию тип SQL Interval преобразуется в соответствующий тип данных Interval в C. Затем приложение привязывает столбец или параметр (или задает поле SQL_DESC_DATA_PTR в соответствующей записи АРД) для указания на инициализированную структуру SQL_INTERVAL_STRUCT (или передает указатель на структуру SQL_ INTERVAL_STRUCT в качестве аргумента *таржетвалуептр* в вызове **SQLGetData**).
