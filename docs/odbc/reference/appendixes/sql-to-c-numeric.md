---
description: 'Преобразование данных из SQL в C: числовые данные'
title: 'Из SQL в C: numeric | Документация Майкрософт'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d48706eddabc71f28c84fae5623a8c9e440d8506
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429566"
---
# <a name="sql-to-c-numeric"></a>Преобразование данных из SQL в C: числовые данные

Ниже приведены идентификаторы числовых типов данных ODBC SQL.

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы числовые данные SQL. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Идентификатор типа C|Тест|**таржетвалуептр*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Длина байта символов < *BufferLength*<br /><br /> Целое число (в отличие от дробной) цифр < *BufferLength*<br /><br /> Число целых знаков (в отличие от дробной) >= *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Символьная длина < *BufferLength*<br /><br /> Целое число (в отличие от дробной) цифр < *BufferLength*<br /><br /> Число целых знаков (в отличие от дробной) >= *BufferLength*|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|Данные, преобразованные без усечения [a]<br /><br /> Данные, преобразованные с усечением дробных разрядов [a]<br /><br /> Преобразование данных приведет к утере целых (в отличие от дробных) цифр [a]|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|Данные находятся в диапазоне типа данных, в который преобразуется число [a]<br /><br /> Данные выходят за пределы диапазона типа данных, в который преобразуется число [a]|Данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_BIT|Данные равны 0 или 1 [a]<br /><br /> Данные больше 0, меньше 2 и не равны 1 [a]<br /><br /> Данные меньше 0 или больше или равны 2 [a]|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|1 [b]<br /><br /> 1 [b]<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных в байтах <= *BufferLength*<br /><br /> Длина байта данных > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH [c] SQL_C_INTERVAL_YEAR [c] SQL_C_INTERVAL_DAY [c] SQL_C_INTERVAL_HOUR [c] SQL_C_INTERVAL_MINUTE [c] SQL_C_INTERVAL_SECOND [c]|Данные не усечены<br /><br /> Часть долей секунды усечена<br /><br /> Целая часть числа усечена|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|Целая часть числа усечена|Не определено|Не определено|22015|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **таржетвалуептр* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.  
  
 [c] это преобразование поддерживается только для точных числовых типов данных (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER и SQL_BIGINT). Он не поддерживается для приблизительных числовых типов данных (SQL_REAL, SQL_FLOAT или SQL_DOUBLE).  

## <a name="sql_c_numeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC и SQLSetDescField

 [Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) необходима для выполнения привязки вручную со значениями SQL_C_NUMERIC. (Обратите внимание, что SQLSetDescField был добавлен в ODBC 3,0.) Чтобы выполнить привязку вручную, необходимо сначала получить дескриптор дескриптора.  

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
