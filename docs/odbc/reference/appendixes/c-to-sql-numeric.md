---
title: 'C в SQL: Числовые | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6dc440e27b362fef9c9794cf0005c6af0b435efc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019310"
---
# <a name="c-to-sql-numeric"></a>C в SQL: Numeric
Идентификаторы для числовых типов данных ODBC C следующие:  
  
 SQL_C_STINYINT  
  
 SQL_C_SLONG  
  
 SQL_C_UTINYINT  
  
 SQL_C_ULONG  
  
 SQL_C_TINYINT  
  
 SQL_C_LONG  
  
 SQL_C_SSHORT  
  
 SQL_C_FLOAT  
  
 SQL_C_USHORT  
  
 SQL_C_DOUBLE  
  
 SQL_C_SHORT  
  
 SQL_C_NUMERIC  
  
 SQL_C_SBIGINT  
  
 SQL_C_UBIGINT  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым можно преобразовать числовые данные C. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Число цифр или символов < = длина столбца в байтах<br /><br /> Число цифр или символов > длина столбца в байтах|Н/Д<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Число символов < = длина столбца символов<br /><br /> Число символов > длины столбца символов|Н/Д<br /><br /> 22001|  
|SQL_DECIMAL [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]|Данные преобразуются без усечения, или усекается цифр дробной части<br /><br /> Данные преобразуются с помощью усечение целой части|Н/Д<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Данные не выходят за диапазон типа данных, в который преобразуется значение<br /><br /> Данных находится вне диапазона типа данных, в который преобразуется значение|Н/Д<br /><br /> 22003|  
|SQL_BIT|Данные являются 0 или 1<br /><br /> Данные больше 0, меньше 2 и не равно 1<br /><br /> Данных меньше 0 или больше или равно 2|Н/Д<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR [a]<br /><br /> SQL_INTERVAL_MONTH [a]<br /><br /> SQL_INTERVAL_DAY [a]<br /><br /> SQL_INTERVAL_HOUR [a]<br /><br /> SQL_INTERVAL_MINUTE [a]<br /><br /> SQL_INTERVAL_SECOND [a]|Данные не усекаются.<br /><br /> Усечение данных.|Н/Д<br /><br /> 22015|  
  
 [a] Эти преобразования поддерживаются только для точных числовых типов данных (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC). Они не поддерживаются для приблизительных числовых типов данных (SQL_C_FLOAT или SQL_C_DOUBLE). Точные числовые типы данных C нельзя преобразовать тип SQL, точности которого интервала не состоит из одного поля интервала.  
  
 [b] для варианта «н/д» драйвер может при необходимости возвращают значение SQL_SUCCESS_WITH_INFO и 01S07 при отсутствии частичное усечение.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных из числовых типов данных C и предполагается, что размер буфера данных является размером числового типа данных C. Значение длины и индикатора, переданное в *StrLen_or_Ind* аргумента в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумента в **SQLBindParameter**. Буфер данных указывается с помощью *DataPtr* аргумента в **SQLPutData** и *ParameterValuePtr* аргумента в **SQLBindParameter**.
