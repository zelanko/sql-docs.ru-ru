---
title: C Типы данных Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292304"
---
# <a name="c-data-types"></a>Типы данных C
Типы данных ODBC C указывают тип буферов C данных, используемых для хранения данных в приложении.  
  
 Все драйверы должны поддерживать все типы данных C. Это необходимо, потому что все драйверы должны поддерживать все типы C, к которым могут быть преобразованы поддерживаемые ими типы S'L, и все драйверы поддерживают по крайней мере один тип типа S'L. Поскольку тип персонажа S'L может быть преобразован в и из всех типов C, все драйверы должны поддерживать все типы C.  
  
 Тип данных C указан в функциях **S'LBindCol** и **S'LGetData** с аргументом *TargetType* и в функции **S'LBindParameter** с аргументом *ValueType.* Она также может быть указана, позвонив в **S'LSetDesccField,** чтобы установить SQL_DESC_CONCISE_TYPE поле ARD или APD, или позвонив в **аргумент** *типа* (и аргумент *SubType,* если это необходимо) и аргумент *DescriptorHandle,* установленный на ручку ARD или APD.  
  
 В следующих таблицах перечислены действительные идентификаторы типов для типов данных C. В таблице также перечислен тип данных ODBC C, соответствующий каждому идентификатору, и определение этого типа данных.  
  
|Идентификатор типа C|Тип ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|СЗЛЧАР|unsigned char *|  
|SQL_C_WCHAR|СЗЛВЧАР|wchar_t *|  
|SQL_C_SSHORT|SQLSMALLINT|short int|  
|SQL_C_USHORT|СЛЮМЛМИНТ|короткое целочисленное число без знака|  
|SQL_C_SLONG|SQLINTEGER|long int|  
|SQL_C_ULONG|SQLUINTEGER|длинное целочисленное число без знака|  
|SQL_C_FLOAT|СЗЛРЕАЛ|FLOAT|  
|SQL_C_DOUBLE|СЗЛАДА, СЗЛЛОВ|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT|SQLSCHAR|signed char|  
|SQL_C_UTINYINT|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64|  
|SQL_C_UBIGINT|СЗЛУБИГИНТ|неподписанный _int64|  
|SQL_C_BINARY|СЗЛЧАР|unsigned char *|  
|SQL_C_BOOKMARK|Закладка|неподписанный длинный int'd|  
|SQL_C_VARBOOKMARK|СЗЛЧАР|unsigned char *|  
|Все типы интервальных данных C|SQL_INTERVAL_STRUCT|Смотрите раздел [C Interval Structure,](../../../odbc/reference/appendixes/c-interval-structure.md) позже в этом приложении.|  
  
 **Идентификатор типа C** SQL_C_TYPE_DATE  
  
 **Тип ODBC C** SQL_DATE_STRUCT  
  
 **Тип C**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_TYPE_TIME  
  
 **Тип ODBC C** SQL_TIME_STRUCT  
  
 **Тип C**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **Идентификатор типа C** SQL_C_TYPE_TIMESTAMP  
  
 **Тип ODBC C** SQL_TIMESTAMP_STRUCT  
  
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
  
 **Тип ODBC C** SQL_NUMERIC_STRUCT  
  
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
  
 **Тип ODBC C** СЗЛГУИД  
  
 **Тип C**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 Значения года, месяца, дня, часа, минуты и вторых полей в типах данных дата c должны соответствовать ограничениям григорианского календаря. [(См. Ограничения григорианского календаря](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) позже в этом приложении.)  
  
 Значение фракционного поля составляет количество миллиардных долей секунды и колеблется от 0 до 999 999 999 (1 меньше 1 миллиарда). Например, значение фракционного поля за полсекунды составляет 500 000 000, за тысячную долю секунды (одна миллисекунда) - 1 000 000, за миллионную долю секунды (одна микросекунда) - 1000, а для миллиардной доли секунды (одна наносекунда) - 1.  
  
 В ODBC 2. *x,* дата C, время и типы данных метки SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP.  
  
 Приложения ODBC 3 *.x* должны использовать SQL_C_VARBOOKMARK, а не SQL_C_BOOKMARK. Когда приложение ODBC 3 *.x* работает с ODBC 2. *x* драйвер, менеджер драйвера ODBC 3 *.x* нанес карту SQL_C_VARBOOKMARK SQL_C_BOOKMARK.  
  
 Номер хранится в *валь-поле* SQL_NUMERIC_STRUCT структуры в виде масштабирования целых, в маленьком эндианском режиме (левый байт является наименее значимым байтом). Например, число 10.001 base 10, с шкалой 4, масштабируется до целых 100010. Потому что это 186AA в гексадецимальном формате, значение в SQL_NUMERIC_STRUCT будет "AA 86 01 00 00 00 ... 00", с числом байтов, определяемых SQL_MAX_NUMERIC_LEN **#define**.  
  
 Для получения дополнительной информации о **SQL_NUMERIC_STRUCT**с [SQL_NUMERIC_STRUCTм.](retrieve-numeric-data-sql-numeric-struct-kb222831.md)  
  
 Поля точности и масштаба типа SQL_C_NUMERIC данных используются для ввода данных из приложения и для вывода от драйвера к приложению. Когда драйвер записывает числовое значение в SQL_NUMERIC_STRUCT, он будет использовать свой собственный драйвер-специфический по умолчанию в качестве значения для *поля точности,* и он будет использовать значение в SQL_DESC_SCALE поле дескриптора приложения (который по умолчанию до 0) для поля *масштаба.* Приложение может предоставить свои собственные значения точности и масштаба, установив SQL_DESC_PRECISION и SQL_DESC_SCALE полях дескриптора приложения.  
  
 Поле знака 1 если положительно, 0 если отрицательно.  
  
 _int64 могут не поставляться некоторыми компиляторами.  
  
 _SQL_C_BOOKMARK был обезвлечен в ODBC 3 *.x*.  
  
 _SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC подписанными и неподписанными типами: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG, а также SQL_C_STINYINT и SQL_C_UTINYINT. Водитель ODBC 3 *.x,* который должен работать с ODBC 2. *приложения x* должны поддерживать SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT, потому что, когда они вызываются, менеджер драйвера передает их водителю.  
  
 SQL_C_GUID может быть преобразован только в SQL_CHAR или SQL_WCHAR.  
  
 Этот раздел содержит следующую тему.  
  
-   [64-разрядные целочисленные структуры](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>См. также:  
 [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
