---
title: "C в SQL: числовые | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2cbdbbd3da828d5a995dbd9bff9c6b95aed1420a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-numeric"></a>C в SQL: числовые
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
  
 В следующей таблице показаны ODBC SQL типы данных, к которым может быть преобразован числовых данных C. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Число цифр < = длина столбца в байтах<br /><br /> Число цифр > длина столбца в байтах|н/д<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Число символов < = длина столбца символов<br /><br /> Число символов > символов столбца|н/д<br /><br /> 22001|  
|SQL_DECIMAL [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]|Данные преобразуются без усечения, или с усечен цифр дробной части<br /><br /> Преобразование данных с усечение всего цифр|н/д<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Данных входит в диапазон типа данных, в который преобразуется значение<br /><br /> Данных находится вне диапазона типа данных, в который преобразуется значение|н/д<br /><br /> 22003|  
|SQL_BIT|Данные являются 0 или 1<br /><br /> Данные больше 0, меньше 2 и не равно 1<br /><br /> Данных меньше 0 или больше или равно 2|н/д<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR []<br /><br /> SQL_INTERVAL_MONTH []<br /><br /> SQL_INTERVAL_DAY []<br /><br /> SQL_INTERVAL_HOUR []<br /><br /> SQL_INTERVAL_MINUTE []<br /><br /> SQL_INTERVAL_SECOND []|Данные не усекаются.<br /><br /> Произошло усечение данных.|н/д<br /><br /> 22015|  
  
 [] Эти преобразования поддерживаются только для точных числовых типов данных (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG или SQL_C_NUMERIC). Они не поддерживаются для приблизительных числовых типов данных (SQL_C_FLOAT или SQL_C_DOUBLE). Точные числовые типы данных C невозможно преобразовать в пределах которого точности интервала не состоит из одного поля типа SQL.  
  
 [b] для варианта «н/д» драйвер может при необходимости вернуть SQL_SUCCESS_WITH_INFO и 01S07 при отсутствии частичное усечение.  
  
 Драйвер не учитывает значение длины/индикатора при преобразовании данных из числовых типов данных C и предполагается, что размер буфера данных размер числовой тип данных C. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.

