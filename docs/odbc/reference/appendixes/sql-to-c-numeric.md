---
title: 'SQL в C: Числовые | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], numeric
- numeric data type [ODBC], converting
- converting data from SQL to C types [ODBC], numeric
ms.assetid: 76f8b5d5-4bd0-4dcb-a90a-698340e0d36e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a23e60b161c09367cfb079cea1f7ca146b4ebee5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056849"
---
# <a name="sql-to-c-numeric"></a>SQL в C: Numeric

Ниже перечислены идентификаторы для числовых типов данных ODBC SQL.

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

Следующая таблица показывает ODBC C типы данных, к которым можно преобразовать числовые данные SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Длина байтов символьной < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) > = *BufferLength*|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина символьной < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) < *BufferLength*<br /><br /> Количество цифр в целом (в отличие от долей) > = *BufferLength*|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|Данные, преобразованные без усечения, [a]<br /><br /> Данные преобразуются с помощью усечения цифр дробной части [a]<br /><br /> Преобразование данных приведет к потере разрядов (в отличие от долей) []|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Н/Д<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|Данные не выходят за диапазон типа данных, в который преобразуется значение [a]<br /><br /> Данных находится вне диапазона типа данных, в который преобразуется значение [a]|Data<br /><br /> Не определено.|Размер типа данных C<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
|SQL_C_BIT|Данные являются 0 или 1, [a]<br /><br /> Данные больше 0, меньше 2 и не равно 1, [a]<br /><br /> Данных меньше 0 или больше или равно 2, [a]|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|1 [b]<br /><br /> 1 [b]<br /><br /> Не определено.|Н/Д<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Data<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH[c] SQL_C_INTERVAL_YEAR[c] SQL_C_INTERVAL_DAY[c] SQL_C_INTERVAL_HOUR[c] SQL_C_INTERVAL_MINUTE[c] SQL_C_INTERVAL_SECOND[c]|Данные не усекаются<br /><br /> Усечены с обозначением долей секунды<br /><br /> Целая часть числа усекаются|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|Целая часть числа усекаются|Не определено.|Не определено.|22015|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.  
  
 [c] это преобразование поддерживается только для точных числовых типов данных (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER и SQL_BIGINT). Не поддерживается для приблизительных числовых типов данных (SQL_REAL, SQL_FLOAT или SQL_DOUBLE).  

## <a name="sqlcnumeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC и SQLSetDescField

 [Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) необходим для выполнения ручной привязки со значениями SQL_C_NUMERIC. (Обратите внимание, что SQLSetDescField был добавлен в ODBC 3.0). Чтобы выполнить привязку вручную, сначала необходимо получить дескриптор.  

```cpp
if (fCType == SQL_C_NUMERIC) {   
   // special processing required for NUMERIC to get right scale & precision  
   // Modify the fields in the implicit application parameter descriptor  
   SQLHDESC hdesc=NULL;  
  
   // Use SQL_ATTR_APP_ROW_DESC for calls to SQLBindCol()  
   // Use SQL_ATTR_APP_PARAM_DESC for calls to SQLBindParameter()  
   //  
   // retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_ROW_DESC, &hdesc, 0, NULL);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &hdesc, 0, NULL);  
   if (!ODBC_CALL_SUCCESS(retcode)) {  
      printf ("\nSQLGetStmtAttr failed");  
      i = 1;  
      sqlstate[7] = '\0';  
      while (SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, sqlstate, &NativeError, wrkbuf, sizeof(wrkbuf), &len) != SQL_NO_DATA) {  
         printf("\niTestCase = %d Failed...Precision = %d, Scale = %d\nNativeError=%d, State=%s, \n  Message=%s",   
            iTestCase, Precision, Scale, NativeError, sqlstate, wrkbuf);  
         i++;  
      }  
      continue;  
   }  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_PRECISION, (SQLPOINTER)num.precision, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_SCALE, (SQLPOINTER)num.scale, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_DATA_PTR, (SQLPOINTER) &(num), sizeof(num));  
```
