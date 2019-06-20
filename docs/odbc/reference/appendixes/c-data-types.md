---
title: Типы данных C | Документация Майкрософт
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f948b50fae0995e16024ac41d8dd891630d1dbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62447543"
---
# <a name="c-data-types"></a>Типы данных C
Типы данных ODBC C указывают тип данных C буферов, используемых для хранения данных в приложении.  
  
 Все драйверы должны поддерживать все типы данных C. Это необходимо, поскольку все драйверы должны поддерживать все типы C, к которым можно преобразовать типы SQL, которые они поддерживают, и все драйверы поддерживают по крайней мере один символ типа SQL. Поскольку тип символа SQL можно преобразовать в и из всех типов C, все драйверы должны поддерживать все типы C.  
  
 Тип данных C указывается в **SQLBindCol** и **SQLGetData** функции с *TargetType* аргумент и в **SQLBindParameter**функционировать с *ValueType* аргумент. Также можно задать путем вызова **SQLSetDescField** задать поле SQL_DESC_CONCISE_TYPE в APD или Отменить, или путем вызова **SQLSetDescRec** с *тип* аргумента (и *подтип* аргумента при необходимости) и *DescriptorHandle* аргумент значение дескриптора, Отменить или APD.  
  
 В следующей таблице перечислены идентификаторы допустимый тип для типов данных C. В таблице также перечислены тип данных ODBC C, соответствующий каждому идентификатору и определение этого типа данных.  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT [j]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j]|SQLUSMALLINT|unsigned short int|  
|SQL_C_SLONG [j]|SQLINTEGER|Long int|  
|SQL_C_ULONG [j]|SQLUINTEGER|unsigned long int|  
|SQL_C_FLOAT|SQLREAL|float|  
|SQL_C_DOUBLE|SQLDOUBLE, SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|char без знака|  
|SQL_C_STINYINT [j]|SQLSCHAR|char со знаком|  
|SQL_C_UTINYINT [j]|SQLCHAR|char без знака|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|SQLUBIGINT|без знака _int64 [h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK [i]|ЗАКЛАДКА|unsigned long int [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|Все типы данных C интервал|SQL_INTERVAL_STRUCT|См. в разделе [структура Interval C](../../../odbc/reference/appendixes/c-interval-structure.md) раздела ниже в этом приложении.|  
  
 **Идентификатор типа C** SQL_C_TYPE_DATE [c]  
  
 **Определение типа ODBC C** SQL_DATE_STRUCT  
  
 **Тип C**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_TYPE_TIME [c]  
  
 **Определение типа ODBC C** SQL_TIME_STRUCT  
  
 **Тип C**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_TYPE_TIMESTAMP [c]  
  
 **Определение типа ODBC C** SQL_TIMESTAMP_STRUCT  
  
 **Тип C**  
  
```  
struct tagTIMESTAMP_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;[b]   
} TIMESTAMP_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_NUMERIC  
  
 **Определение типа ODBC C** помощью SQL_NUMERIC_STRUCT  
  
 **Тип C**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **Идентификатор типа C** SQL_C_GUID  
  
 **Определение типа ODBC C** SQLGUID  
  
 **Тип C**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] значения года, месяца, дня, часа, минуты и второго полей в типы данных даты и времени C должны соответствовать ограничениям, григорианского календаря. (См. в разделе [ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) далее в этом приложении.)  
  
 [b число миллиардных долей секунды и лежит в диапазоне от 0 до 999,999,999 (1 не более 1 миллиарда) значение поле дробной части. Например, поле дробной части для полсекунды значение 500,000,000, для разделителя доли секунды (1 миллисекунда) составляет 1 000 000, для миллионного доли секунды (1 микросекунде) 1000, а также для миллиардную долю секунды (1 наносекунде)-1.  
  
 [c] в ODBC 2. *x*, типы данных date, time и timestamp C — SQL_C_DATE SQL_C_TIME и SQL_C_TIMESTAMP.  
  
 [d] ODBC 3 *.x* приложения должны использовать SQL_C_VARBOOKMARK, не SQL_C_BOOKMARK. Когда ODBC 3 *.x* приложение работает с ODBC 2. *x* драйвера ODBC 3 *.x* диспетчера драйверов сопоставляется SQL_C_BOOKMARK SQL_C_VARBOOKMARK.  
  
 [e] A номер хранится в *val* помощью SQL_NUMERIC_STRUCT структуры как масштабированное значение типа integer, в режиме прямым порядком байтов (крайнего левого байта, что младший байт). Например номер 10.001 основание 10, с масштабом 4, масштабируется до целого числа 100010. Так как это 186AA в шестнадцатеричном формате, то значение в помощью SQL_NUMERIC_STRUCT должно быть «AA 86 01 00 00... 00", с числом байтов, определяется SQL_MAX_NUMERIC_LEN **#define**.  
  
 Дополнительные сведения о **помощью SQL_NUMERIC_STRUCT**, см. в разделе [HOWTO: Получение числовых данных с помощью SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] точность и Масштаб поля данных SQL_C_NUMERIC введите areused для входных данных из приложения, а также для вывода от драйвера в приложение. При драйвер записывает числовое значение в помощью SQL_NUMERIC_STRUCT, свои собственные специфические для драйвера по умолчанию будет использоваться как значение для *точности* поля и он будет использовать значение в поле SQL_DESC_SCALE (дескриптор) приложения которое по умолчанию равно 0) для *масштабирования* поля. Приложение может предоставлять собственные значения для точности и масштаба, задав SQL_DESC_PRECISION и SQL_DESC_SCALE поля дескриптора приложения.  
  
 [g] поле входа-1, если оно положительное, 0, если оно отрицательное.  
  
 [h] _int64 не может быть передан в некоторых компиляторах.  
  
 [i] _SQL_C_BOOKMARK был объявлен устаревшим в ODBC 3 *.x*.  
  
 [j] _SQL_C_SHORT SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC типы со знаком и без знака: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG и SQL_C_STINYINT и SQL_C_UTINYINT. ODBC 3 *.x* драйвер, должны работать с ODBC 2. *x* приложения должны поддерживать SQL_C_SHORT SQL_C_LONG и SQL_C_TINYINT, так как при вызове, диспетчер драйверов передает их через драйвер.  
  
 [k] SQL_C_GUID можно преобразовать только к SQL_CHAR или SQL_WCHAR.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [64-разрядные целочисленные структуры](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>См. также  
 [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
