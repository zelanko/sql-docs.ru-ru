---
title: 'СЗЛ в C: Число (ч. 4) Документы Майкрософт'
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
ms.openlocfilehash: 36b24da4023a96b686742416b83bb5790e129278
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296414"
---
# <a name="sql-to-c-numeric"></a>Преобразование данных из SQL в C: числовые данные

Идентификаторы для численных типов данных ODBC S'L:

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

В следующей таблице показаны типы данных ODBC C, в которые могут быть преобразованы численные данные S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  

|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Длина байта персонажа < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр >*BufferLength*|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина персонажа < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр < *BufferLength*<br /><br /> Количество целых (в отличие от дробных) цифр >*BufferLength*|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|Данные, преобразуются без усечения<br /><br /> Данные, преобразуются с усеиванием дробных цифр<br /><br /> Преобразование данных приведет к потере целых (в отличие от дробных) цифр.|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|Данные находятся в пределах типа данных, к которому преобразуется число.<br /><br /> Данные не входят в диапазон типа данных, в который преобразуется число.|Данные<br /><br /> Не определено.|Размер типа данных C<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_BIT|Данные 0 или 1 'a)<br /><br /> Данные больше, чем 0, меньше, чем 2, и не равны<br /><br /> Данные меньше, чем 0 или больше, чем или равны 2|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|1 b<br /><br /> 1 b<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_SECOND SQL_C_INTERVAL_MINUTE SQL_C_INTERVAL_HOUR SQL_C_INTERVAL_DAY SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR|Данные не усечены<br /><br /> Фракционные секунды часть усечена<br /><br /> Вся часть числа усеченных|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|Вся часть числа усеченных|Не определено.|Не определено.|22015|  
  
 Значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер*TargetValuePtr* — это размер типа данных C.  
  
 Это размер соответствующего типа данных C.  
  
 Это преобразование поддерживается только для точных типов численных данных (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER и SQL_BIGINT). Он не поддерживается для приблизительных типов численных данных (SQL_REAL, SQL_FLOAT или SQL_DOUBLE).  

## <a name="sql_c_numeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC и S'LSetDescField

 [Функция S'LSetDescfield](../../../odbc/reference/syntax/sqlsetdescfield-function.md) необходима для выполнения ручного переплета с SQL_C_NUMERIC значениями. (Обратите внимание, что S'LSetDescField был добавлен в ODBC 3.0.) Для выполнения ручной привязки необходимо сначала получить ручку дескриптора.  

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
