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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 979bfe85e1e78b55718e1f12fdcfcc7583097bb4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292304"
---
# <a name="c-data-types"></a>Типы данных C
Типы данных ODBC C указывают тип данных буферов C, используемых для хранения данных в приложении.  
  
 Все драйверы должны поддерживать все типы данных C. Это необходимо, так как все драйверы должны поддерживать все типы C, для которых поддерживается преобразование типов SQL, а все драйверы поддерживают по крайней мере один символ SQL. Поскольку символьный тип SQL можно преобразовать в типы и из всех типов C, все драйверы должны поддерживать все типы C.  
  
 Тип данных C указывается в функциях **SQLBindCol** и **SQLGetData** с аргументом *TargetType* и в функции **SQLBindParameter** с аргументом *ValueType* . Его также можно указать с помощью вызова **SQLSetDescField** , чтобы задать поле SQL_DESC_CONCISE_TYPE АРД или APD, или путем вызова **SQLSetDescRec** с аргументом *типа* (и аргументом *подтипа* , если это необходимо), а аргументу *дескрипторхандле* задано значение Handle для АРД или APD.  
  
 В следующих таблицах перечислены допустимые идентификаторы типов данных C. В таблице также представлен тип данных ODBC C, соответствующий каждому идентификатору и определению этого типа данных.  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR-|wchar_t *|  
|SQL_C_SSHORT [j]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j]|склусмаллинт|короткое целочисленное число без знака|  
|SQL_C_SLONG [j]|SQLINTEGER|long int|  
|SQL_C_ULONG [j]|SQLUINTEGER|длинное целочисленное число без знака|  
|SQL_C_FLOAT|склреал|FLOAT|  
|SQL_C_DOUBLE|SQLDOUBLE, СКЛФЛОАТ|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT [j]|склсчар|signed char|  
|SQL_C_UTINYINT [j]|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|склубигинт|неподписанный _int64 [h]|  
|SQL_C_BINARY|SQLCHAR|unsigned char *|  
|SQL_C_BOOKMARK [i]|Закладка|long int без знака [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|  
|Все типы данных интервала C|SQL_INTERVAL_STRUCT|См. раздел [Структура интервалов C](../../../odbc/reference/appendixes/c-interval-structure.md) далее в этом приложении.|  
  
 **Идентификатор типа C** SQL_C_TYPE_DATE [C]  
  
 **Определение типа ODBC C** SQL_DATE_STRUCT  
  
 **Тип C**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_TYPE_TIME [C]  
  
 **Определение типа ODBC C** SQL_TIME_STRUCT  
  
 **Тип C**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_TYPE_TIMESTAMP [C]  
  
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
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **Идентификатор типа C** SQL_C_GUID  
  
 **Определение типа ODBC C** склгуид  
  
 **Тип C**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] значения полей год, месяц, день, час, минут и секунд в типах данных DateTime C должны соответствовать ограничениям григорианского календаря. (См. раздел [ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) далее в этом приложении.)  
  
 [b] значение поля "дробь" равно числу биллионсс секунды и диапазонам от 0 до 999 999 999 (1 меньше 1 000 000 000). Например, значение поля "дробь" для половины секунды равно 500 000 000, то есть доли секунды (одна миллисекунда) — 1 000 000, для миллионной части секунды (одна микросекунда) — 1 000, а для биллионс секунды (один наносекундных) — 1.  
  
 [c] в ODBC 2. *x*, типы данных даты, времени и отметок времени C SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP.  
  
 [d] приложения ODBC 3 *. x* должны использовать SQL_C_VARBOOKMARK, а не SQL_C_BOOKMARK. Когда приложение ODBC 3 *. x* работает с ODBC 2. драйвер *x* , диспетчер драйверов ODBC 3 *. x* будет сопоставлять SQL_C_VARBOOKMARK SQL_C_BOOKMARK.  
  
 [e] число хранится в поле *Val* структуры SQL_NUMERIC_STRUCT как масштабируемое целое число, в режиме с прямым порядком байтов (самый левый байт является наименьшим значащим байтом). Например, число 10,001 с основанием 10 и масштабом 4, масштабируется до целого числа 100010. Так как это 186AA в шестнадцатеричном формате, значение в SQL_NUMERIC_STRUCT будет равно "AA 86 01 00 00... 00 ", с числом байтов, определенным **#defineом**SQL_MAX_NUMERIC_LEN.  
  
 Дополнительные сведения о **SQL_NUMERIC_STRUCT**см. [в разделе Практическое руководство. Извлечение числовых данных с помощью SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] поля точности и масштаба SQL_C_NUMERIC типа данных ареусед для ввода из приложения и для вывода из драйвера в приложение. Когда драйвер записывает числовое значение в SQL_NUMERIC_STRUCT, оно будет использовать собственное значение по умолчанию, зависящее от драйвера, в качестве значения для поля *точность* , и будет использовать значения в поле SQL_DESC_SCALE дескриптора приложения (значение по умолчанию — 0) для поля *Scale* . Приложение может предоставлять собственные значения точности и масштаба, устанавливая поля SQL_DESC_PRECISION и SQL_DESC_SCALE дескриптора приложения.  
  
 [g] поле знака имеет значение 1, если оно положительное, 0 (если отрицательное).  
  
 [h] _int64 могут быть не предоставлены некоторыми компиляторами.  
  
 [i] _SQL_C_BOOKMARK не рекомендуется использовать в ODBC 3 *. x*.  
  
 [j] _SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC с помощью подписанных и неподписанных типов: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG, а SQL_C_STINYINT и SQL_C_UTINYINT. Драйвер ODBC 3 *. x* , который должен работать с ODBC 2. приложения *x* должны поддерживать SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT, поскольку при их вызове диспетчер драйверов передает их в драйвер.  
  
 [k] SQL_C_GUID можно преобразовать только в SQL_CHAR или SQL_WCHAR.  
  
 Этот раздел содержит следующий раздел.  
  
-   [64-разрядные целочисленные структуры](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>См. также:  
 [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
