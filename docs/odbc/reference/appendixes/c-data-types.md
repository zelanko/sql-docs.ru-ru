---
title: Типы данных C | Документы Microsoft
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 288ca6cbd5553b963131d34b8e63640518f70ef4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912740"
---
# <a name="c-data-types"></a>Типы данных C
Типы данных ODBC C указывают тип данных C буферов, используемых для хранения данных в приложении.  
  
 Все драйверы должны поддерживать все типы данных C. Это необходимо, поскольку все драйверы должны поддерживать все типы C, к которым можно преобразовать типы SQL, которые они поддерживают, и все драйверы поддерживать по крайней мере один символ типа SQL. Так как тип символа SQL может быть преобразована в и из всех типов C, все драйверы должны поддерживать все типы C.  
  
 Тип данных C указывается в **SQLBindCol** и **SQLGetData** функции с *TargetType* аргумент и в **SQLBindParameter**функционировать с *ValueType* аргумент. Также можно указать путем вызова **SQLSetDescField** требуется установить в поле SQL_DESC_CONCISE_TYPE в APD или Отменить или путем вызова **SQLSetDescRec** с *тип* аргумента (и *подтип* аргумента при необходимости) и *DescriptorHandle* аргумент значение дескриптора, Отменить или APD.  
  
 В следующей таблице указаны идентификаторы допустимым типом для типов данных C. В таблице также перечислены типа данных ODBC C, соответствующего для каждого идентификатора и определение этого типа данных.  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT [j]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j]|SQLUSMALLINT|unsigned short int|  
|SQL_C_SLONG [j]|SQLINTEGER|длинное целочисленное|  
|SQL_C_ULONG [j]|SQLUINTEGER|unsigned long int|  
|SQL_C_FLOAT|SQLREAL|float|  
|SQL_C_DOUBLE|SQLDOUBLE SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|char без знака|  
|SQL_C_STINYINT [j]|SQLSCHAR|char со знаком|  
|SQL_C_UTINYINT [j]|SQLCHAR|char без знака|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|SQLUBIGINT|без знака _int64 [h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK [i]|ЗАКЛАДКА|unsigned long int [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|Все типы данных C интервал|SQL_INTERVAL_STRUCT|В разделе [C интервал структуры](../../../odbc/reference/appendixes/c-interval-structure.md) подраздел, далее в этом приложении.|  
  
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
  
 **Определение типа ODBC C** SQL_NUMERIC_STRUCT  
  
 **Тип C**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
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
  
 [] значения год, месяц, день, час, минуту и второго поля в типы данных даты и времени C должны соответствовать ограничениям по григорианскому календарю. (См. [ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) далее в этом приложении.)  
  
 [b число миллиардных долей секунды и лежит в диапазоне от 0 до 999 999 999 (1 не более 1 миллиарда) равен поле дробной части. Например, значение поля долей для вторую половину — 500,000,000 для разделителя доли секунды (до одной миллисекунды) — 1 000 000 для миллионная доля секунды (1 микросекунде), 1 000, а также для миллиардной секунды (1 наносекунде)-1.  
  
 [c] в ODBC 2. *x*, типы данных даты, времени и отметок времени C: SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP.  
  
 [d] ODBC 3 *.x* приложения должны использовать SQL_C_VARBOOKMARK не SQL_C_BOOKMARK. Когда ODBC 3 *.x* приложение работает с ODBC 2. *x* драйвера ODBC 3 *.x* диспетчера драйверов сопоставит SQL_C_VARBOOKMARK SQL_C_BOOKMARK.  
  
 число [e] значение, хранящееся в *val* структуры SQL_NUMERIC_STRUCT масштабированный целого числа, в режиме прямым порядком следования байтов (крайнего левого байта выполняется младший байт). Например число 10.001 основание 10, с масштабом 4, масштабируется до целого числа 100010. Поскольку это 186AA в шестнадцатеричном формате, значение в SQL_NUMERIC_STRUCT бы «AA 86 01 00 00... 00", с количеством байт, определяется SQL_MAX_NUMERIC_LEN **#define**.  
  
 Дополнительные сведения о **SQL_NUMERIC_STRUCT**, в разделе [HOWTO: получение числовые данные с SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] точность и Масштаб поля данных SQL_C_NUMERIC введите areused для входных данных из приложения, а также для вывода от драйвера в приложение. Когда драйвер записывает в SQL_NUMERIC_STRUCT числовое значение, в нем используется собственный драйвера по умолчанию как значение для *точности* поле и он будет использовать значение в поле SQL_DESC_SCALE (дескриптор приложения который по умолчанию 0) для *шкалы* поля. Приложение может обеспечивать собственные значения для точности и масштаба, задав SQL_DESC_PRECISION и SQL_DESC_SCALE поля дескриптора приложения.  
  
 [g] поле входа имеет значение 1, если оно положительное, 0, если оно отрицательное.  
  
 [h] _int64 не может быть передан в некоторых компиляторах.  
  
 [i] _SQL_C_BOOKMARK рекомендуется к использованию в ODBC 3 *.x*.  
  
 [j] _SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC знаковых и беззнаковых типов: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG и SQL_C_STINYINT и SQL_C_UTINYINT. ODBC 3 *.x* драйвер, который должен работать с ODBC 2. *x* приложения должны поддерживать SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT, так как при их вызове диспетчера драйверов передает их с помощью драйвера.  
  
 [k] SQL_C_GUID можно преобразовать только для SQL_CHAR или SQL_WCHAR.  
  
 Этот раздел содержит следующий раздел.  
  
-   [64-разрядные целочисленные структуры](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>См. также  
 [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
