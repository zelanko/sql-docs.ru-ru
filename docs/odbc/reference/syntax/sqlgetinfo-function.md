---
title: Функция SQLGetInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInfo
helpviewer_keywords:
- SQLGetInfo function [ODBC]
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 514922fd085cfd2ba19eb5c07dd844db82d55202
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303346"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLGetInfo** возвращает общие сведения о драйвере и источнике данных, связанном с соединением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *коннектионхандле*  
 [Input] Дескриптор подключения  
  
 *инфотипе*  
 Входной Тип сведений.  
  
 *инфовалуептр*  
 Проверки Указатель на буфер, в который возвращаются сведения. В зависимости от запрошенного *инфотипе* , возвращаемые данные будут иметь одно из следующих значений: строку символов, завершающуюся нулем, значение склусмаллинт, битовую маску SQLUINTEGER, флаг SQLUINTEGER, двоичное значение SQLUINTEGER или значение SQLULEN.  
  
 Если аргумент *инфотипе* имеет значение SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT, аргумент *инфовалуептр* является входным и выходным. (Дополнительные сведения см. в описании SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT дескрипторах этой функции.)  
  
 Если *инфовалуептр* имеет значение null, *стрингленгсптр* будет возвращать общее число байтов (исключая символ завершения null для символьных данных), доступный для возврата в буфер, на который указывает *инфовалуептр*.  
  
 *BufferLength*  
 Входной \*Длина буфера *инфовалуептр* . Если значение в * \*инфовалуептр* не является символьной строкой или если *инфовалуептр* является пустым указателем, аргумент *BufferLength* игнорируется. Драйвер предполагает, что размер * \*инфовалуептр* — склусмаллинт или SQLUINTEGER на основе *инфотипе*. Если * \*инфовалуептр* является строкой Юникода (при вызове **склжетинфов**), аргумент *BufferLength* должен быть четным числом; в противном случае возвращается значение SQLSTATE HY090 (Недопустимая строка или длина буфера).  
  
 *стрингленгсптр*  
 Проверки Указатель на буфер, в котором возвращается общее число байтов (за исключением символа завершения null для символьных данных), доступных для возврата в **инфовалуептр*.  
  
 Для символьных данных, если число возвращаемых байт больше или равно *BufferLength*, информация в \* *инфовалуептр* усекается до *BufferLength* байт минус длина символа завершения, равного null, и заканчивается нулем драйвером.  
  
 Для всех других типов данных значение *BufferLength* игнорируется, и драйвер предполагает, что размер \* *инфовалуептр* равен склусмаллинт или SQLUINTEGER, в зависимости от *инфотипе*.  
  
## <a name="return-value"></a>Возвращаемое значение  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Если **SQLGetInfo** возвращает либо SQL_ERROR, либо SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_DBC и *маркером* *коннектионхандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLGetInfo** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, усеченные справа|Буфер \* *инфовалуептр* недостаточно велик для возврата всех запрошенных сведений. Поэтому данные были усечены. Длина запрошенной информации в неусеченной форме возвращается в **стрингленгсптр*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08003|Соединение не открыто|(DM) для типа сведений, запрашиваемых в *инфотипе* , требуется открытое соединение. Из типов данных, зарезервированных ODBC, только SQL_ODBC_VER могут возвращаться без открытого соединения.|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY024|Недопустимое значение атрибута|(DM) аргумент *инфотипе* был SQL_DRIVER_HSTMT, а значение, на которое указывает *инфовалуептр* , не является допустимым маркером инструкции.<br /><br /> (DM) аргумент *инфотипе* был SQL_DRIVER_HDESC, а значение, на которое указывает *инфовалуептр* , не является допустимым дескриптором дескриптора.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное для аргумента *BufferLength* , было меньше 0.<br /><br /> (DM) значение, указанное для *BufferLength* , было нечетным числом, а * \*инфовалуептр* — типом данных Юникода.|  
|HY096|Тип данных вне допустимого диапазона|Значение, указанное для аргумента *инфотипе* , недопустимо для версии ODBC, поддерживаемой драйвером.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательное поле не реализовано|Значение, указанное для аргумента *инфотипе* , было зависящим от драйвера значением, которое не поддерживается драйвером.|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, соответствующий *коннектионхандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Типы сведений, определенные в настоящее время, показаны Далее в этом разделе Ожидается, что для использования преимуществ различных источников данных будет определено больше. Диапазон типов данных зарезервирован ODBC. Разработчики драйверов должны зарезервировать значения для собственного использования драйвера из Open Group. **SQLGetInfo** не выполняет преобразование в Юникод или *преобразователь* (см. [приложение A. коды ошибок ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) *справочника по программированию ODBC*) для определяемого драйвером *инфотипес*. Дополнительные сведения см. в разделе [зависящие от драйвера типы данных, Типы дескрипторов, типы сведений, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Формат сведений, возвращаемых в \* *инфовалуептр* , зависит от запрашиваемого *инфотипе* . **SQLGetInfo** будет возвращать информацию в одном из пяти различных форматов:  
  
-   Строка символов, завершающаяся нулем  
  
-   Значение СКЛУСМАЛЛИНТ  
  
-   Битовая маска SQLUINTEGER  
  
-   Значение SQLUINTEGER  
  
-   Двоичное значение SQLUINTEGER  
  
 Формат каждого из следующих типов сведений указывается в описании типа. Приложение должно соответствующим образом привести значение, возвращаемое в **инфовалуептр* . Пример того, как приложение может извлечь данные из битовой маски SQLUINTEGER, см. в разделе «пример кода».  
  
 Драйвер должен возвращать значение для каждого типа данных, определенного в следующих таблицах. Если тип сведений не применяется к драйверу или источнику данных, драйвер возвращает одно из значений, перечисленных в следующей таблице.  
  
 Символьная строка ("Y" или "N")  
 "N"  
  
 Символьная строка (не "Y" или "N")  
 Пустая строка.  
  
 склусмаллинт  
 0  
  
 Битовая маска SQLUINTEGER или SQLUINTEGER двоичное значение  
 0L  
  
 Например, если источник данных не поддерживает процедуры, **SQLGetInfo** возвращает значения, перечисленные в следующей таблице, для значений *инфотипе* , связанных с процедурами.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Пустая строка.  
  
 **SQLGetInfo** ВОЗВРАЩАЕТ SQLSTATE HY096 (недопустимое значение аргумента) для значений *инфотипе* , которые находятся в диапазоне типов данных, зарезервированных для использования ODBC, но не определяются версией ODBC, поддерживаемой драйвером. Чтобы определить, к какой версии ODBC-драйвера соответствует, приложение вызывает **SQLGetInfo** с типом данных SQL_DRIVER_ODBC_VER. **SQLGetInfo** ВОЗВРАЩАЕТ значение SQLSTATE HYC00 (Необязательная функция не реализована) для значений *инфотипе* , которые находятся в диапазоне типов данных, зарезервированных для использования драйвером, но не поддерживаются драйвером.  
  
 Для всех вызовов **SQLGetInfo** требуется открытое соединение, за исключением случаев, когда *инфотипе* имеет значение SQL_ODBC_VER, возвращающее версию диспетчера драйверов.  
  
## <a name="information-types"></a>Типы сведений  
 В этом разделе перечислены типы сведений, поддерживаемые **SQLGetInfo**. Типы сведений группируются по категориям и сортируются в алфавитном порядке. Также перечислены типы сведений, добавленных или переименованных для ODBC 3 *. x* .  
  
## <a name="driver-information"></a>Сведения о драйвере  
 Следующие значения аргумента *инфотипе* возвращают сведения о драйвере ODBC, такие как число активных инструкций, имя источника данных и уровень соответствия стандартам интерфейса:  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_FILE_USAGE|  
|SQL_ASYNC_MODE|SQL_GETDATA_EXTENSIONS|  
|SQL_ASYNC_NOTIFICATION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_BATCH_ROW_COUNT|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_BATCH_SUPPORT|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_DATA_SOURCE_NAME|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_DRIVER_AWARE_POOLING_SUPPORTED|SQL_MAX_CONCURRENT_ACTIVITIES|  
|SQL_DRIVER_HDBC|SQL_MAX_DRIVER_CONNECTIONS|  
|SQL_DRIVER_HDESC|SQL_ODBC_INTERFACE_CONFORMANCE|  
|SQL_DRIVER_HENV|SQL_ODBC_STANDARD_CLI_CONFORMANCE|  
|SQL_DRIVER_HLIB|SQL_ODBC_VER|  
|SQL_DRIVER_HSTMT|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_DRIVER_NAME|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DRIVER_ODBC_VER|SQL_ROW_UPDATES|  
|SQL_DRIVER_VER|SQL_SEARCH_PATTERN_ESCAPE|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|SQL_SERVER_NAME|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_STATIC_CURSOR_ATTRIBUTES2|  
  
> [!NOTE]  
>  При реализации **SQLGetInfo**драйвер может повысить производительность, минимизируя количество попыток отправки или запроса информации с сервера.  
  
## <a name="dbms-product-information"></a>Сведения о продукте СУБД  
 Следующие значения аргумента *инфотипе* возвращают сведения о продукте СУБД, такие как имя и версия СУБД:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Сведения об источнике данных  
 Следующие значения аргумента *инфотипе* возвращают сведения об источнике данных, такие как характеристики курсора и возможности транзакций:  
  
|||  
|-|-|  
|SQL_ACCESSIBLE_PROCEDURES|SQL_MULT_RESULT_SETS|  
|SQL_ACCESSIBLE_TABLES|SQL_MULTIPLE_ACTIVE_TXN|  
|SQL_BOOKMARK_PERSISTENCE|SQL_NEED_LONG_DATA_LEN|  
|SQL_CATALOG_TERM|SQL_NULL_COLLATION|  
|SQL_COLLATION_SEQ|SQL_PROCEDURE_TERM|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_SCHEMA_TERM|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_SCROLL_OPTIONS|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_TABLE_TERM|  
|SQL_CURSOR_SENSITIVITY|SQL_TXN_CAPABLE|  
|SQL_DATA_SOURCE_READ_ONLY|SQL_TXN_ISOLATION_OPTION|  
|SQL_DEFAULT_TXN_ISOLATION|SQL_USER_NAME|  
|SQL_DESCRIBE_PARAMETER||  
  
## <a name="supported-sql"></a>Поддерживаемые SQL  
 Следующие значения аргумента *инфотипе* возвращают сведения о ИНСТРУКЦИЯх SQL, поддерживаемых источником данных. Синтаксис SQL каждого компонента, описываемого этими типами данных, является синтаксисом SQL-92. Эти типы сведений не полностью описывают грамматику SQL-92. Вместо этого они описывают эти части грамматики, для которых источники данных обычно предлагают различные уровни поддержки. В частности, рассматриваются большинство инструкций DDL в SQL-92.  
  
 Приложения должны определить общий уровень поддерживаемой грамматики из типа данных SQL_SQL_CONFORMANCE и использовать другие типы сведений для определения вариантов из указанного уровня соответствия стандартам.  
  
|||  
|-|-|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DROP_TABLE|  
|SQL_ALTER_DOMAIN|SQL_DROP_TRANSLATION|  
|SQL_ALTER_SCHEMA|SQL_DROP_VIEW|  
|SQL_ALTER_TABLE|SQL_EXPRESSIONS_IN_ORDERBY|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_GROUP_BY|  
|SQL_CATALOG_LOCATION|SQL_IDENTIFIER_CASE|  
|SQL_CATALOG_NAME|SQL_IDENTIFIER_QUOTE_CHAR|  
|SQL_CATALOG_NAME_SEPARATOR|SQL_INDEX_KEYWORDS|  
|SQL_CATALOG_USAGE|SQL_INSERT_STATEMENT|  
|SQL_COLUMN_ALIAS|SQL_INTEGRITY|  
|SQL_CORRELATION_NAME|SQL_KEYWORDS|  
|SQL_CREATE_ASSERTION|SQL_LIKE_ESCAPE_CLAUSE|  
|SQL_CREATE_CHARACTER_SET|SQL_NON_NULLABLE_COLUMNS|  
|SQL_CREATE_COLLATION|SQL_SQL_CONFORMANCE|  
|SQL_CREATE_DOMAIN|SQL_OJ_CAPABILITIES|  
|SQL_CREATE_SCHEMA|SQL_ORDER_BY_COLUMNS_IN_SELECT|  
|SQL_CREATE_TABLE|SQL_OUTER_JOINS|  
|SQL_CREATE_TRANSLATION|SQL_PROCEDURES|  
|SQL_DDL_INDEX|SQL_QUOTED_IDENTIFIER_CASE|  
|SQL_DROP_ASSERTION|SQL_SCHEMA_USAGE|  
|SQL_DROP_CHARACTER_SET|SQL_SPECIAL_CHARACTERS|  
|SQL_DROP_COLLATION|SQL_SUBQUERIES|  
|SQL_DROP_DOMAIN|SQL_UNION|  
|SQL_DROP_SCHEMA||  
  
## <a name="sql-limits"></a>Ограничения SQL  
 Следующие значения аргумента *инфотипе* возвращают сведения об ограничениях, применяемых к идентификаторам и предложениям в инструкциях SQL, например к максимальной длине идентификаторов и максимальному числу столбцов в списке выбора. Ограничения могут быть накладываются либо драйвером, либо источником данных.  
  
|||  
|-|-|  
|SQL_MAX_BINARY_LITERAL_LEN|SQL_MAX_IDENTIFIER_LEN|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAX_INDEX_SIZE|  
|SQL_MAX_CHAR_LITERAL_LEN|SQL_MAX_PROCEDURE_NAME_LEN|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAX_ROW_SIZE|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAX_ROW_SIZE_INCLUDES_LONG|  
|SQL_MAX_COLUMNS_IN_INDEX|SQL_MAX_SCHEMA_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAX_STATEMENT_LEN|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAX_TABLE_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAX_TABLES_IN_SELECT|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAX_USER_NAME_LEN|  
  
## <a name="scalar-function-information"></a>Сведения о скалярной функции  
 Следующие значения аргумента *инфотипе* возвращают сведения о скалярных функциях, поддерживаемых источником данных и драйвером. Дополнительные сведения о скалярных функциях см. в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Сведения о преобразовании  
 Следующие значения аргумента *инфотипе* возвращают список типов данных SQL, в которые источник данных может преобразовать указанный тип данных SQL с помощью скалярной функции **Convert** :  
  
|||  
|-|-|  
|SQL_CONVERT_BIGINT|SQL_CONVERT_LONGVARBINARY|  
|SQL_CONVERT_BINARY|SQL_CONVERT_LONGVARCHAR|  
|SQL_CONVERT_BIT|SQL_CONVERT_NUMERIC|  
|SQL_CONVERT_CHAR|SQL_CONVERT_REAL|  
|SQL_CONVERT_DATE|SQL_CONVERT_SMALLINT|  
|SQL_CONVERT_DECIMAL|SQL_CONVERT_TIME|  
|SQL_CONVERT_DOUBLE|SQL_CONVERT_TIMESTAMP|  
|SQL_CONVERT_FLOAT|SQL_CONVERT_TINYINT|  
|SQL_CONVERT_INTEGER|SQL_CONVERT_VARBINARY|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_CONVERT_VARCHAR|  
|SQL_CONVERT_INTERVAL_DAY_TIME||  
  
## <a name="information-types-added-for-odbc-3x"></a>Типы сведений, добавленные для ODBC 3. x  
 Для ODBC 3 *. x*были добавлены следующие значения аргумента *инфотипе* :  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_DRIVER_AWARE_POOLING_SUPPORTED|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DRIVER_HDESC|  
|SQL_ALTER_DOMAIN|SQL_DROP_ASSERTION|  
|SQL_ALTER_SCHEMA|SQL_DROP_CHARACTER_SET|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_DROP_COLLATION|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_DROP_DOMAIN|  
|SQL_ASYNC_MODE|SQL_DROP_SCHEMA|  
|SQL_ASYNC_NOTIFICATION|SQL_DROP_TABLE|  
|SQL_BATCH_ROW_COUNT|SQL_DROP_TRANSLATION|  
|SQL_BATCH_SUPPORT|SQL_DROP_VIEW|  
|SQL_CATALOG_NAME|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|  
|SQL_COLLATION_SEQ|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|  
|SQL_CONVERT_INTERVAL_DAY_TIME|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_ASSERTION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_CREATE_CHARACTER_SET|SQL_INSERT_STATEMENT|  
|SQL_CREATE_COLLATION|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_CREATE_DOMAIN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_SCHEMA|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_CREATE_TABLE|SQL_MAX_IDENTIFIER_LEN|  
|SQL_CREATE_TRANSLATION|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_CURSOR_SENSITIVITY|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DDL_INDEX|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_DESCRIBE_PARAMETER|SQL_STATIC_CURSOR_ATTRIBUTES2|  
|SQL_DM_VER|SQL_XOPEN_CLI_YEAR|  
  
## <a name="information-types-renamed-for-odbc-3x"></a>Типы сведений, переименованные для ODBC 3. x  
 Следующие значения аргумента *инфотипе* были переименованы для ODBC 3 *. x*.  
  
 SQL_ACTIVE_CONNECTIONS  
 SQL_MAX_DRIVER_CONNECTIONS  
  
 SQL_ACTIVE_STATEMENTS  
 SQL_MAX_CONCURRENT_ACTIVITIES  
  
 SQL_MAX_OWNER_NAME_LEN  
 SQL_MAX_SCHEMA_NAME_LEN  
  
 SQL_MAX_QUALIFIER_NAME_LEN  
 SQL_MAX_CATALOG_NAME_LEN  
  
 SQL_ODBC_SQL_OPT_IEF  
 SQL_INTEGRITY  
  
 SQL_OWNER_TERM  
 SQL_SCHEMA_TERM  
  
 SQL_OWNER_USAGE  
 SQL_SCHEMA_USAGE  
  
 SQL_QUALIFIER_LOCATION  
 SQL_CATALOG_LOCATION  
  
 SQL_QUALIFIER_NAME_SEPARATOR  
 SQL_CATALOG_NAME_SEPARATOR  
  
 SQL_QUALIFIER_TERM  
 SQL_CATALOG_TERM  
  
 SQL_QUALIFIER_USAGE  
 SQL_CATALOG_USAGE  
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Нерекомендуемые типы сведений в ODBC 3. x  
 Следующие значения аргумента *инфотипе* являются устаревшими в ODBC 3 *. x*. Драйверы ODBC 3 *. x* должны продолжать поддерживать эти типы данных для обеспечения обратной совместимости с приложениями ODBC 2 *. x* . (Дополнительные сведения об этих типах см. в разделе [Поддержка SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md) в приложении G: рекомендации по драйверу для обеспечения обратной совместимости.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Описания типов сведений  
 В следующей таблице перечислены все типы данных, версия ODBC, в которой они были введены, и описание.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1,0)  
 Строка символов: "Y", если пользователь может выполнить все процедуры, возвращенные **SQLProcedures**; "N", если могут быть возвращены процедуры, которые пользователь не может выполнить.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1,0)  
 Строка символов: "Y", если пользователь гарантированно **выбирает** права доступа ко всем таблицам, возвращаемым функцией **SQLTables**; "N", если могут возвращаться таблицы, к которым пользователь не может получить доступ.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных сред, которое может поддерживать драйвер. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3,0)  
 SQLUINTEGER битовая маска, поддерживающая агрегатные функции:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_ALTER_DOMAIN (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **ALTER Domain** , как определено в SQL-92, поддерживаемое источником данных. Драйвер SQL-92, совместимый с полным уровнем, всегда возвращает все битовые маски. Возвращаемое значение "0" означает, что инструкция **ALTER Domain** не поддерживается.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = Добавление ограничения домена поддерживается (полный уровень)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter Domain> \<set предложение default домена> поддерживается (полный уровень)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<предложение определения имени ограничения> поддерживается для ограничения домена именования (промежуточный уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<предложение удаления ограничения домена поддерживается> (полный уровень)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter Domain> \<предложение DROP домена по умолчанию> поддерживается (полный уровень)  
  
 Следующие биты задают поддерживаемые \<атрибуты ограничения> если \<поддерживается добавление ограничения домена> (установлен бит SQL_AD_ADD_DOMAIN_CONSTRAINT):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)  
  
 SQL_ALTER_TABLE (ODBC 2,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **ALTER TABLE** , поддерживаемой источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<предложение "добавить столбец>" поддерживается с помощью средства для указания параметров сортировки столбцов (полный уровень) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<предложение "добавить столбец>" поддерживается с помощью средства, определяющего значения по умолчанию для столбцов (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<поддерживается> добавления столбцов (уровень передачи FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_CONSTRAINT = \<предложение "добавить столбец>" поддерживается с помощью средства для указания ограничений столбца (уровень "TRANSITIONAL" FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<поддерживается предложение добавления> ограничения таблицы (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<определение имени ограничения> поддерживается для именования столбцов и ограничений таблицы (промежуточный уровень) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<DROP COLUMN> Cascade поддерживается (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<alter Column> \<предложение DROP column по умолчанию> поддерживается (промежуточный уровень) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<DROP COLUMN> restrict поддерживается (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<DROP COLUMN> restrict поддерживается (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<alter Column> \<задать предложение default столбца> поддерживается (промежуточный уровень) (ODBC 3,0)  
  
 Следующие биты задают атрибуты ограничения \<поддержки> при условии, что ограничения столбца или таблицы поддерживаются (бит SQL_AT_ADD_CONSTRAINT установлен):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (полный уровень) (ODBC 3,0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3,8)  
 Значение SQLUINTEGER, указывающее, может ли драйвер асинхронно выполнять функции в обработчике соединения.  
  
 SQL_ASYNC_DBC_CAPABLE = драйвер может выполнять функции подключения асинхронно.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = драйвер не может выполнять функции подключения асинхронно.  
  
 SQL_ASYNC_MODE (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее уровень асинхронной поддержки в драйвере:  
  
 SQL_AM_CONNECTION = асинхронное выполнение на уровне соединения поддерживается. Все дескрипторы инструкций, связанные с данным дескриптором соединения, находятся в асинхронном режиме или работают в синхронном режиме. Маркер инструкции в соединении не может находиться в асинхронном режиме, в то время как другой обработчик на том же соединении работает в синхронном режиме и наоборот.  
  
 SQL_AM_STATEMENT = асинхронное выполнение уровня инструкции поддерживается. Некоторые дескрипторы инструкций, связанные с дескриптором соединения, могут находиться в асинхронном режиме, в то время как другие дескрипторы инструкций в одном соединении находятся в синхронном режиме.  
  
 SQL_AM_NONE = асинхронный режим не поддерживается.  
  
 SQL_ASYNC_NOTIFICATION  
 Значение SQLUINTEGER, указывающее, поддерживает ли драйвер Асинхронное уведомление:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** Драйвер поддерживает асинхронное уведомление о выполнении.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** Уведомление о асинхронном выполнении не поддерживается драйвером.  
  
 Существуют две категории асинхронных операций ODBC: асинхронные операции на уровне соединения и асинхронные операции на уровне инструкций.  Если драйвер возвращает SQL_ASYNC_NOTIFICATION_CAPABLE, он должен поддерживать уведомление для всех интерфейсов API, которые он может выполнять асинхронно.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет поведение драйвера в отношении доступности количества строк. Вместе с типом данных используются следующие битовые маски:  
  
 SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE сведено в один. Если этот бит не установлен, для каждой инструкции доступны счетчики строк.  
  
 SQL_BRC_PROCEDURES = количество строк, если таковые имеются, доступны при выполнении пакета в хранимой процедуре. Если счетчики строк доступны, они могут быть сведены или доступны по отдельности в зависимости от SQL_BRC_ROLLED_UP бита.  
  
 SQL_BRC_EXPLICIT = количество строк, если таковые имеются, доступны при непосредственном выполнении пакета путем вызова **SQLExecute** или **SQLExecDirect**. Если счетчики строк доступны, они могут быть сведены или доступны по отдельности в зависимости от SQL_BRC_ROLLED_UP бита.  
  
 SQL_BATCH_SUPPORT (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет поддержку пакетов в драйвере. Для определения поддерживаемого уровня используются следующие битовые маски.  
  
 SQL_BS_SELECT_EXPLICIT = драйвер поддерживает явные пакеты, в которых могут создаваться инструкции результирующего набора.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = драйвер поддерживает явные пакеты, которые могут формировать инструкции по количеству строк.  
  
 SQL_BS_SELECT_PROC = драйвер поддерживает явные процедуры, в которых могут создаваться инструкции результирующего набора.  
  
 SQL_BS_ROW_COUNT_PROC = драйвер поддерживает явные процедуры, которые могут формировать инструкции по количеству строк.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2,0)  
 Битовая маска SQLUINTEGER, в которой перечисляются операции, с помощью которых сохраняются закладки.  
  
 Следующие битовые маски используются вместе с флагом для определения сохраняемых параметров.  
  
 SQL_BP_CLOSE = закладки допустимы после того, как приложение вызывает **SQLFreeStmt** с параметром SQL_CLOSE или **SQLCloseCursor** , чтобы закрыть курсор, связанный с инструкцией.  
  
 SQL_BP_DELETE = закладка для строки допустима после удаления этой строки.  
  
 SQL_BP_DROP = закладки допустимы после того, как приложение вызовет **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_STMT для удаления инструкции.  
  
 SQL_BP_TRANSACTION = закладки допустимы после фиксации или отката транзакции приложением.  
  
 SQL_BP_UPDATE = закладка для строки допустима после обновления любого столбца в этой строке, включая ключевые столбцы.  
  
 SQL_BP_OTHER_HSTMT = Закладка, связанная с одной инструкцией, может использоваться с другой инструкцией. Если не указано SQL_BP_CLOSE или SQL_BP_DROP, курсор в первой инструкции должен быть открыт.  
  
 SQL_CATALOG_LOCATION (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее расположение каталога в полном имени таблицы:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Например, драйвер xbase возвращает SQL_CL_START, так как имя каталога (каталога) находится в начале имени таблицы, как в \ЕМПДАТА\ЕМП. Присоединен. Драйвер сервера ORACLE возвращает SQL_CL_END, так как каталог находится в конце имени таблицы, как в ADMIN.EMP@EMPDATA.  
  
 Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать SQL_CL_START. Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_LOCATION ODBC 2,0 *инфотипе* .  
  
 SQL_CATALOG_NAME (ODBC 3,0)  
 Строка символов: "Y", если сервер поддерживает имена каталогов, или "N", если нет.  
  
 Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать значение "Y".  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1,0)  
 Символьная строка. символ или символы, которые источник данных определяет как разделитель между именем каталога и элементом с полным именем, который следует за ним или предшествует ему.  
  
 Если каталоги не поддерживаются источником данных, возвращается пустая строка. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME. Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать ".".  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_NAME_SEPARATOR ODBC 2,0 *инфотипе* .  
  
 SQL_CATALOG_TERM (ODBC 1,0)  
 Символьная строка с именем поставщика источника данных для каталога; Например, "Database" или "Directory". Эта строка может быть в верхнем, нижнем или смешанном регистре.  
  
 Если каталоги не поддерживаются источником данных, возвращается пустая строка. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME. Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать "Catalog".  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_TERM ODBC 2,0 *инфотипе* .  
  
 SQL_CATALOG_USAGE (ODBC 2,0)  
 Битовая маска SQLUINTEGER, которая перечисляет инструкции, в которых можно использовать каталоги.  
  
 Чтобы определить, где можно использовать каталоги, используются следующие битовые маски:  
  
 SQL_CU_DML_STATEMENTS = каталоги поддерживаются во всех инструкциях языка обработки данных: **SELECT**, **INSERT**, **Update**, **Delete**и, если поддерживается, **SELECT для Update** и позиционированных инструкций UPDATE и DELETE.  
  
 SQL_CU_PROCEDURE_INVOCATION = каталоги поддерживаются в операторе вызова процедуры ODBC.  
  
 SQL_CU_TABLE_DEFINITION = каталоги поддерживаются во всех инструкциях определения таблицы: **CREATE TABLE**, **Создание представления**, **изменение таблицы**, **Удаление таблицы**и **представление Drop**.  
  
 SQL_CU_INDEX_DEFINITION = каталоги поддерживаются во всех инструкциях определения индекса: **Создание индекса** и **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = каталоги поддерживаются во всех инструкциях определения прав: **Grant** и **REVOKE**.  
  
 Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME. Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать битовую маску со всеми этими наборами битов.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_USAGE ODBC 2,0 *инфотипе* .  
  
 SQL_COLLATION_SEQ (ODBC 3,0)  
 Имя последовательности параметров сортировки. Это символьная строка, указывающая имя параметров сортировки по умолчанию для набора символов по умолчанию для данного сервера (например, "ISO 8859-1" или EBCDIC). Если это неизвестно, будет возвращена пустая строка. Драйвер, соотносящийся к полному уровню SQL-92, всегда возвращает непустую строку.  
  
 SQL_COLUMN_ALIAS (ODBC 2,0)  
 Символьная строка: "Y", если источник данных поддерживает псевдонимы столбцов; в противном случае — "N".  
  
 Псевдоним столбца — это альтернативное имя, которое можно указать для столбца в списке выбора с помощью предложения AS. Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает значение "Y".  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, как источник данных обрабатывает объединение столбцов символьного типа данных со значением NULL со столбцами типа данных, не являющимися значениями NULL:  
  
 SQL_CB_NULL = result имеет значение NULL.  
  
 SQL_CB_NON_NULL = Result объединяет столбец или столбцы, не имеющие значений NULL.  
  
 Драйвер, поддерживающий уровень ввода SQL-92, всегда будет возвращать SQL_CB_NULL.  
  
 SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR SQL_CONVERT_CHAR SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT (ODBC 1,0)  
 Битовая маска SQLUINTEGER. Битовая маска указывает, какие преобразования поддерживаются источником данных с помощью скалярной функции **Convert** для данных типа, указанного в *инфотипе*. Если битовая маска равна нулю, источник данных не поддерживает преобразования из данных именованного типа, включая преобразование в тот же тип данных.  
  
 Например, чтобы определить, поддерживает ли источник данных преобразование SQL_INTEGER данных в SQL_BIGINT тип данных, приложение вызывает **SQLGetInfo** с *инфотипе* SQL_CONVERT_INTEGER. Приложение выполняет операцию **и** с возвращенной битовой маской и SQL_CVT_BIGINT. Если полученное значение не равно нулю, преобразование поддерживается.  
  
 Для определения поддерживаемых преобразований используются следующие битовые маски.  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1,0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1,0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 1.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY SQL_CVT_LONGVARCHAR (ODBC 1,0) SQL_CVT_NUMERIC CVT_REAL ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) SQL_CVT_TIME (ODBC 1.0) SQL_CVT_TIMESTAMP (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1,0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1,0)  
 Битовая маска SQLUINTEGER, которая перечисляет скалярные функции преобразования, поддерживаемые драйвером и связанным источником данных.  
  
 Для определения поддерживаемых функций преобразования используется следующая битовая маска:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, поддерживаются ли имена корреляции таблиц:  
  
 SQL_CN_NONE = корреляционные имена не поддерживаются.  
  
 SQL_CN_DIFFERENT = имена корреляции поддерживаются, но должны отличаться от имен таблиц, которые они представляют.  
  
 SQL_CN_ANY = имена корреляции поддерживаются и могут быть любым допустимым именем, определенным пользователем.  
  
 Драйвер, поддерживающий уровень ввода SQL-92, всегда будет возвращать SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE assertion** , как определено в SQL-92, поддерживается источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Следующие биты задают атрибут Supported Constraint, если возможность указывать атрибуты ограничения явно поддерживается (см. SQL_ALTER_TABLE и SQL_CREATE_TABLE типы сведений):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые. Возвращаемое значение "0" означает, что инструкция **CREATE assertion** не поддерживается.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE character set** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые. Возвращаемое значение "0" означает, что инструкция **CREATE character set** не поддерживается.  
  
 SQL_CREATE_COLLATION (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE collation** , как определено в SQL-92, поддерживается источником данных.  
  
 Для определения поддерживаемых предложений используется следующая битовая маска:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается. Возвращаемое значение "0" означает, что инструкция **CREATE collation** не поддерживается.  
  
 SQL_CREATE_DOMAIN (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE Domain** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_CDO_CREATE_DOMAIN = поддерживается инструкция CREATE DOMAIN (промежуточный уровень).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<определение имени ограничения> поддерживается для именования ограничений домена (промежуточный уровень).  
  
 Следующие биты определяют возможность создания ограничений столбца: SQL_CDO_DEFAULT = указание ограничений домена поддерживается (промежуточный уровень) SQL_CDO_CONSTRAINT = указание значений по умолчанию домена поддерживается (промежуточный уровень) SQL_CDO_COLLATION = указание поддержки параметров сортировки домена (полный уровень)  
  
 Следующие биты задают поддерживаемые атрибуты ограничения, если указано, что ограничения домена поддерживаются (SQL_CDO_DEFAULT установлен):  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) SQL_CDO_CONSTRAINT_DEFERRABLE (полный уровень) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (полный уровень)  
  
 Возвращаемое значение "0" означает, что инструкция **CREATE Domain** не поддерживается.  
  
 SQL_CREATE_SCHEMA (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE SCHEMA** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Драйвер, совместимый с промежуточным уровнем SQL-92, всегда будет возвращать параметры SQL_CS_CREATE_SCHEMA и SQL_CS_AUTHORIZATION, как поддерживается. Они также должны поддерживаться на уровне ввода SQL-92, но не обязательно как инструкции SQL. Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_CREATE_TABLE (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в операторе **CREATE TABLE** , как определено в SQL-92, поддерживается источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_CT_CREATE_TABLE = поддерживается инструкция CREATE TABLE. (Уровень записи)  
  
 SQL_CT_TABLE_CONSTRAINT = поддерживается указание ограничений таблицы (уровень FIPS)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = предложение \<Name CONSTRAINT Definition> поддерживается для именования столбцов и ограничений таблицы (промежуточный уровень)  
  
 Следующие биты указывают возможность создания временных таблиц:  
  
 SQL_CT_COMMIT_PRESERVE = удаленные строки сохраняются при фиксации. (Полный уровень) SQL_CT_COMMIT_DELETE = удаленные строки удаляются при фиксации. (Полный уровень) SQL_CT_GLOBAL_TEMPORARY = можно создавать глобальные временные таблицы. (Полный уровень) SQL_CT_LOCAL_TEMPORARY = можно создавать локальные временные таблицы. (Полный уровень)  
  
 Следующие биты определяют возможность создания ограничений столбцов.  
  
 SQL_CT_COLUMN_CONSTRAINT = не поддерживается указание ограничений столбца (уровень FIPS) SQL_CT_COLUMN_DEFAULT = указание значений по умолчанию для столбцов поддерживается (уровень перехода FIPS) SQL_CT_COLUMN_COLLATION = задание параметров сортировки столбцов поддерживается (полный уровень)  
  
 Следующие биты задают поддерживаемые атрибуты ограничения, если указано ограничение столбца или таблицы.  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) SQL_CT_CONSTRAINT_DEFERRABLE (полный уровень) SQL_CT_CONSTRAINT_NON_DEFERRABLE (полный уровень)  
  
 SQL_CREATE_TRANSLATION (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE Translation** , как определено в SQL-92, поддерживается источником данных.  
  
 Для определения поддерживаемых предложений используется следующая битовая маска:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать эти параметры, как и поддерживается. Возвращаемое значение "0" означает, что инструкция **CREATE Translation** не поддерживается.  
  
 SQL_CREATE_VIEW (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Create View** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Возвращаемое значение "0" означает, что инструкция **Create View** не поддерживается.  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать параметры SQL_CV_CREATE_VIEW и SQL_CV_CHECK_OPTION, как поддерживается.  
  
 Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, как операция **фиксации** влияет на курсоры и подготовленные инструкции в источнике данных (поведение источника данных при фиксации транзакции).  
  
 Значение этого атрибута будет отражать текущее состояние следующего параметра: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = закрывающие курсоры и удалять подготовленные инструкции. Чтобы снова использовать курсор, приложение должно повторно подготовиться и повторно выполнить инструкцию.  
  
 SQL_CB_CLOSE = закрывающие курсоры. Для подготовленных инструкций приложение может вызвать **SQLExecute** для инструкции без повторного вызова **SQLPrepare** . Значение по умолчанию для драйвера SQL ODBC — SQL_CB_CLOSE. Это означает, что при фиксации транзакции драйвер ODBC SQL будет закрывать ваши курсоры.  
  
 SQL_CB_PRESERVE = сохранять курсоры в той же позиции, что и до операции **фиксации** . Приложение может продолжить выборку данных, или же можно закрыть курсор и повторно выполнить инструкцию без его повторной подготовки.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, как операция **отката** влияет на курсоры и подготовленные инструкции в источнике данных:  
  
 SQL_CB_DELETE = закрывающие курсоры и удалять подготовленные инструкции. Чтобы снова использовать курсор, приложение должно повторно подготовиться и повторно выполнить инструкцию.  
  
 SQL_CB_CLOSE = закрывающие курсоры. Для подготовленных инструкций приложение может вызвать **SQLExecute** для инструкции без повторного вызова **SQLPrepare** .  
  
 SQL_CB_PRESERVE = сохранять курсоры в той же позиции, что и перед операцией **отката** . Приложение может продолжить выборку данных или закрыть курсор и повторно выполнить инструкцию без повторной подготовки.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее на поддержку чувствительности курсора:  
  
 SQL_INSENSITIVE = все курсоры на маркере инструкции показывают результирующий набор, не отражая изменения, внесенные в него любым другим курсором в рамках той же транзакции.  
  
 SQL_UNSPECIFIED = не указано, отображаются ли курсоры в маркере инструкции изменения, внесенные в результирующий набор другим курсором в той же транзакции. Курсоры в маркере инструкции могут сделать видимыми ничего, некоторые или все подобные изменения.  
  
 SQL_SENSITIVE = курсоры чувствительны к изменениям, внесенным другими курсорами в рамках той же транзакции.  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать параметр SQL_UNSPECIFIED, как поддерживается.  
  
 Драйвер, совместимый с SQL-92, всегда будет возвращать параметр SQL_INSENSITIVE, как поддерживается.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1,0)  
 Строка символов с именем источника данных, которое было использовано во время соединения. Если приложение называется **SQLConnect**, это значение аргумента *сздсн* . Если приложение называется **SQLDriverConnect** или **SQLBrowseConnect**, это значение является ЗНАЧЕНИЕМ ключевого слова DSN в строке подключения, передаваемой драйверу. Если строка подключения не содержит ключевого слова **DSN** (например, если оно содержит ключевое слово **Driver** ), это пустая строка.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1,0)  
 Строка символов. "Y", если для источника данных задан режим "только для чтения", в противном случае — "N".  
  
 Эта характеристика относится только к самому источнику данных. Он не является характеристикой драйвера, обеспечивающего доступ к источнику данных. Драйвер, доступный для чтения и записи, можно использовать с источником данных, который доступен только для чтения. Если драйвер доступен только для чтения, все его источники данных должны быть доступны только для чтения и должны возвращать SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME (ODBC 1,0)  
 Строка символов с именем текущей базы данных, если источник данных определяет именованный объект с именем "Database".  
  
> [!NOTE]
>  В ODBC 3 *. x*значение, возвращаемое для этого *инфотипе* , также может возвращаться путем вызова **SQLGetConnectAttr** с аргументом *атрибута* SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет литералы datetime SQL-92, поддерживаемые источником данных. Обратите внимание, что это литералы datetime, перечисленные в спецификации SQL-92, и они отделены от литеральных предложений литерала DateTime, определенных ODBC. Дополнительные сведения о предложениях escape-выражений ODBC DateTime см. в статье [литералы даты, времени и отметок времени](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Драйвер, поддерживающий переход на уровне FIPS, всегда возвращает значение "1" в битовой маске для битов, указанных в следующем списке. Значение "0" означает, что литералы datetime в SQL-92 не поддерживаются.  
  
 Для определения поддерживаемых литералов используются следующие битовые маски:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1,0)  
 Строка символов с именем продукта СУБД, к которому обращается драйвер.  
  
 SQL_DBMS_VER (ODBC 1,0)  
 Символьная строка, указывающая версию продукта СУБД, к которой обращается драйвер. Версия имеет вид # #. # #. # # # #, где первые две цифры являются основной версией, следующие две цифры — дополнительный номер версии, а последние четыре цифры — версия выпуска. Драйвер должен визуализировать версию продукта СУБД в этой форме, но также может добавлять версию СУБД, относящуюся к продукту. Например, "04.01.0000 Rdb 4,1".  
  
 SQL_DDL_INDEX (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее поддержку создания и удаления индексов:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1,0)  
 Значение SQLUINTEGER, указывающее уровень изоляции транзакции по умолчанию, поддерживаемый драйвером или источником данных, или нуль, если источник данных не поддерживает транзакции. Для определения уровней изоляции транзакции используются следующие термины.  
  
 **"Грязное" чтение** Транзакция 1 изменяет строку. Транзакция 2 считывает измененную строку до того, как транзакция 1 фиксирует изменение. Если транзакция 1 откатывает изменение, то транзакция 2 будет считать строку, которая, как никогда, не существовала.  
  
 **Неповторяемое чтение** Транзакция 1 считывает строку. Транзакция 2 обновляет или удаляет эту строку и фиксирует это изменение. Если транзакция 1 пытается повторно прочитать строку, она получит другие значения строки или обнаружит, что строка была удалена.  
  
 **Фантомный** Транзакция 1 считывает набор строк, удовлетворяющих некоторым условиям поиска. Транзакция 2 создает одну или несколько строк (с помощью вставок или обновлений), соответствующих условиям поиска. Если транзакция 1 выполняет инструкцию, которая считывает строки, она получает другой набор строк.  
  
 Если источник данных поддерживает транзакции, драйвер возвращает одну из следующих битовых масок:  
  
 SQL_TXN_READ_UNCOMMITTED = "грязные" операции чтения, неповторяемые операции чтения и фантомы.  
  
 SQL_TXN_READ_COMMITTED = "грязные" операции чтения невозможны. Возможны неповторяемые операции чтения и фантомы.  
  
 SQL_TXN_REPEATABLE_READ = "грязное" чтение и неповторяемые операции чтения невозможны. Фантомы возможны.  
  
 SQL_TXN_SERIALIZABLE = транзакции сериализуемыми. Сериализуемые транзакции не допускают "грязных" операций чтения, неповторяемых операций чтения или фантомов.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3,0)  
 Символьная строка: "Y", если можно описать параметры; "N", если нет.  
  
 Драйвер SQL-92 с полным соответствием, как правило, возвращает значение "Y", поскольку оно будет поддерживать оператор **описания входных данных** . Поскольку в этом случае не указывается базовая поддержка SQL, то описанные параметры могут не поддерживаться даже в драйвере SQL-92 с полным уровнем соответствия.  
  
 SQL_DM_VER (ODBC 3,0)  
 Символьная строка с версией диспетчера драйверов. Версия имеет вид # #. # #. # # # #. # # # #, где:  
  
 Первый набор из двух цифр — это основной номер версии ODBC, заданный константой SQL_SPEC_MAJOR.  
  
 Второй набор из двух цифр — это незначительная версия ODBC, заданная константой SQL_SPEC_MINOR.  
  
 Третьим набором из четырех цифр является номер основной сборки диспетчера драйверов.  
  
 Последний набор из четырех цифр — номер вспомогательной сборки диспетчера драйверов.  
  
 Версия диспетчера драйверов Windows 7 — 03,80. Версия диспетчера драйверов для Windows 8 — 03,81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3,8)  
 Значение SQLUINTEGER, указывающее, поддерживает ли драйвер пулы с учетом драйверов. (Дополнительные сведения см. в статье [Организация пулов соединений с учетом драйверов](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE указывает, что драйвер может поддерживать механизм пулов с поддержкой драйверов.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE указывает, что драйвер не поддерживает механизм пулов с поддержкой драйверов.  
  
 Драйверу не требуется реализовывать SQL_DRIVER_AWARE_POOLING_SUPPORTED, а диспетчер драйверов не будет учитывать возвращаемое значение драйвера.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1,0)  
 Значение SQLULEN, обработчик среды или маркер подключения драйвера, определяемый аргументом *инфотипе*.  
  
 Эти типы информации реализуются только диспетчером драйверов.  
  
 SQL_DRIVER_HDESC (ODBC 3,0)  
 Значение SQLULEN, дескриптор дескриптора драйвера, определяемый дескриптором дескриптора диспетчера драйверов, который должен передаваться в качестве входных данных в \* *инфовалуептр* из приложения. В этом случае *инфовалуептр* является как входным, так и выходным аргументом. Дескриптор входного дескриптора, \*переданный в *инфовалуептр* , должен быть либо явно, либо неявно выделен в *коннектионхандле*.  
  
 Приложение должно создать копию дескриптора дескриптора диспетчера драйверов перед вызовом **SQLGetInfo** с этим типом данных, чтобы убедиться в том, что дескриптор не перезаписывается на выходе.  
  
 Этот тип информации реализуется только диспетчером драйверов.  
  
 SQL_DRIVER_HLIB (ODBC 2,0)  
 Значение SQLULEN, *хинст* из библиотеки загрузки, возвращенное диспетчеру драйверов при загрузке библиотеки DLL драйвера в операционной системе Microsoft Windows или ее эквиваленте в другой операционной системе. Этот маркер допустим только для маркера соединения, указанного в вызове **SQLGetInfo**.  
  
 Этот тип информации реализуется только диспетчером драйверов.  
  
 SQL_DRIVER_HSTMT (ODBC 1,0)  
 Значение SQLULEN, обработчик инструкций драйвера, определяемый обработчиком драйвера диспетчера драйверов, который должен передаваться в качестве входных \*данных в *инфовалуептр* из приложения. В этом случае *инфовалуептр* является входным и выходным аргументом. Входной маркер инструкции, переданный \*в *инфовалуептр* , должен быть выделен в аргументе *коннектионхандле*.  
  
 Приложение должно создать копию обработчика операторов диспетчера драйверов перед вызовом **SQLGetInfo** с этим типом данных, чтобы гарантировать, что этот маркер не перезаписывается на выходе.  
  
 Этот тип информации реализуется только диспетчером драйверов.  
  
 SQL_DRIVER_NAME (ODBC 1,0)  
 Символьная строка с именем файла драйвера, используемого для доступа к источнику данных.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2,0)  
 Символьная строка с версией ODBC, поддерживаемой драйвером. Версия имеет вид # #. # #, где первые две цифры — основной номер версии, а следующие две цифры — дополнительный номер версии. SQL_SPEC_MAJOR и SQL_SPEC_MINOR определяют основной и дополнительный номера версии. Для версии ODBC, описанной в этом руководстве, указаны 3 и 0, а драйвер должен вернуть значение "03,00".  
  
 Диспетчер драйверов ODBC не изменит возвращаемое значение SQLGetInfo (SQL_DRIVER_ODBC_VER) для обеспечения обратной совместимости существующих приложений. Драйвер указывает, какое значение будет возвращено. Однако драйвер, поддерживающий расширение типа данных C, должен возвращать 3,8 (или более поздней версии), когда приложение вызывает **SQLSetEnvAttr** для установки SQL_ATTR_ODBC_VERSION в 3,8. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1,0)  
 Символьная строка с версией драйвера и при необходимости описание драйвера. Как минимум, версия имеет форму # #. # #. # # # #, где первые две цифры — основной номер версии, две следующие цифры — дополнительный номер версии, а последние четыре цифры — версия выпуска.  
  
 SQL_DROP_ASSERTION (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Assert** , как определено в SQL-92, поддерживается источником данных.  
  
 Для определения поддерживаемых предложений используется следующая битовая маска:  
  
 SQL_DA_DROP_ASSERTION  
  
 Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop character set** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используется следующая битовая маска:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.  
  
 SQL_DROP_COLLATION (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop collation** , как определено в SQL-92, поддерживается источником данных.  
  
 Для определения поддерживаемых предложений используется следующая битовая маска:  
  
 SQL_DC_DROP_COLLATION  
  
 Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.  
  
 SQL_DROP_DOMAIN (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Domain** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Драйвер, совместимый с промежуточным уровнем SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_DROP_SCHEMA (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Schema** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Драйвер, совместимый с промежуточным уровнем SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_DROP_TABLE (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **DROP TABLE** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.  
  
 SQL_DROP_TRANSLATION (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Translation** , как определено в SQL-92, поддерживается источником данных.  
  
 Для определения поддерживаемых предложений используется следующая битовая маска:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.  
  
 SQL_DROP_VIEW (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **DROP VIEW** , как определено в SQL-92, поддерживаемое источником данных.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты динамического курсора, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA1_NEXT = аргумент *фетчориентатион* SQL_FETCH_NEXT поддерживается при вызове **SQLFetchScroll** , если курсор является динамическим курсором.  
  
 SQL_CA1_ABSOLUTE = *фетчориентатион* аргументы SQL_FETCH_FIRST, SQL_FETCH_LAST и SQL_FETCH_ABSOLUTE поддерживаются при вызове **SQLFetchScroll** , если курсор является динамическим курсором. (Набор строк, который будет извлекаться, не зависит от текущей позиции курсора.)  
  
 SQL_CA1_RELATIVE = *фетчориентатион* аргументы SQL_FETCH_PRIOR и SQL_FETCH_RELATIVE поддерживаются при вызове **SQLFetchScroll** , если курсор является динамическим курсором. (Набор строк, который будет извлекаться, зависит от текущей позиции курсора. Обратите внимание, что это отделено от SQL_FETCH_NEXT поскольку в однонаправленном курсоре поддерживается только SQL_FETCH_NEXT.)  
  
 SQL_CA1_BOOKMARK = аргумент *фетчориентатион* SQL_FETCH_BOOKMARK поддерживается при вызове **SQLFetchScroll** , если курсор является динамическим курсором.  
  
 SQL_CA1_LOCK_EXCLUSIVE = аргумент *LockType* SQL_LOCK_EXCLUSIVE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_LOCK_NO_CHANGE = аргумент *LockType* SQL_LOCK_NO_CHANGE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_LOCK_UNLOCK = аргумент *LockType* SQL_LOCK_UNLOCK поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_POS_POSITION = аргумент *операции* SQL_POSITION поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_POS_UPDATE = аргумент *операции* SQL_UPDATE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_POS_DELETE = аргумент *операции* SQL_DELETE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_POS_REFRESH = аргумент *операции* SQL_REFRESH поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.  
  
 SQL_CA1_POSITIONED_UPDATE = обновление, в котором поддерживается текущая инструкция SQL, если курсор является динамическим курсором. (Серверный драйвер начального уровня SQL-92 всегда будет возвращать этот параметр, как поддерживается).  
  
 SQL_CA1_POSITIONED_DELETE = удаление, где текущая инструкция SQL поддерживается, если курсор является динамическим курсором. (Серверный драйвер начального уровня SQL-92 всегда будет возвращать этот параметр, как поддерживается).  
  
 SQL_CA1_SELECT_FOR_UPDATE = инструкция SELECT для инструкции UPDATE SQL поддерживается, если курсор является динамическим курсором. (Серверный драйвер начального уровня SQL-92 всегда будет возвращать этот параметр, как поддерживается).  
  
 SQL_CA1_BULK_ADD = аргумент *операции* SQL_ADD поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = аргумент *операции* SQL_UPDATE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = аргумент *операции* SQL_DELETE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = аргумент *операции* SQL_FETCH_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.  
  
 Драйвер, поддерживающий промежуточный уровень SQL-92, обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE, так как поддерживаются прокручиваемые курсоры посредством внедренной инструкции SQL FETCH. Так как это не определяет непосредственно базовую поддержку SQL, возможно, прокручиваемые курсоры не поддерживаются даже для драйвера, соответствующего промежуточному уровню SQL-92.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты динамического курсора, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = динамический курсор только для чтения, в котором обновления не разрешены, поддерживаются. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_READ_ONLY для динамического курсора).  
  
 SQL_CA2_LOCK_CONCURRENCY = динамический курсор, который использует самый низкий уровень блокировки, достаточный для того, чтобы гарантировать, что строка может быть обновлена. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_LOCK для динамического курсора.) Эти блокировки должны соответствовать уровню изоляции транзакций, заданному атрибутом подключения SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = динамический курсор, использующий управление оптимистичным параллелизмом, Сравнение версий строк поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_ROWVER для динамического курсора.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = динамический курсор, использующий управление оптимистичным параллелизмом, сравнение значений поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_VALUES для динамического курсора.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = добавленные строки видимы динамическому курсору; курсор может перейти к этим строкам. (Когда эти строки добавляются в курсор, зависит от драйвера.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = удаленные строки больше не доступны динамическому курсору и не оставляют "отверстие" в результирующем наборе; После прокрутки динамического курсора из удаленной строки она не может вернуться к этой строке.  
  
 SQL_CA2_SENSITIVITY_UPDATES = обновления строк видимы для динамического курсора; Если динамический курсор прокручивается из и возвращается к обновленной строке, то возвращаемые курсором данные являются обновленными, а не исходными данными.  
  
 SQL_CA2_MAX_ROWS_SELECT = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **SELECT** , если курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_INSERT = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **INSERT** , если курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_DELETE = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **Delete** , если курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_UPDATE = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **Update** , если курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_CATALOG = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на результирующие наборы **каталога** , когда курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **SELECT**, **INSERT**, **Delete**и **Update** , а также на результирующие наборы **каталога** , если курсор является динамическим курсором.  
  
 SQL_CA2_CRC_EXACT = точное число строк доступно в поле диагностики SQL_DIAG_CURSOR_ROW_COUNT, если курсор является динамическим курсором.  
  
 SQL_CA2_CRC_APPROXIMATE = приблизительное число строк доступно в поле диагностики SQL_DIAG_CURSOR_ROW_COUNT, если курсор является динамическим курсором.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = драйвер не гарантирует, что смоделированные позиционированные инструкции UPDATE или DELETE повлияют только на одну строку, если курсор является динамическим курсором; Это гарантируется за пределом приложения. (Если инструкция затрагивает более одной строки, **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операций курсора].) Чтобы задать это поведение, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_SIMULATE_CURSOR, для которого задано значение SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = драйвер пытается гарантировать, что смоделированные позиционированные обновления или инструкции DELETE будут влиять только на одну строку, если курсор является динамическим курсором. Драйвер всегда выполняет такие инструкции, даже если они могут повлиять на более чем одну строку, например при отсутствии уникального ключа. (Если инструкция затрагивает более одной строки, **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операций курсора].) Чтобы задать это поведение, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_SIMULATE_CURSOR, для которого задано значение SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE = драйвер гарантирует, что смоделированные позиционированные инструкции UPDATE или DELETE повлияют только на одну строку, если курсор является динамическим курсором. Если драйвер не может гарантировать это для данной инструкции, **SQLExecDirect** или **SQLPREPARE** возвращают SQLSTATE 01001 (конфликт операций курсора). Чтобы задать это поведение, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_SIMULATE_CURSOR, для которого задано значение SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1,0)  
 Символьная строка: "Y", если источник данных поддерживает выражения в списке **ORDER BY** ; "N", если нет.  
  
 SQL_FILE_USAGE (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, как одноуровневый драйвер непосредственно обрабатывает файлы в источнике данных:  
  
 SQL_FILE_NOT_SUPPORTED = драйвер не является одноуровневое. Например, драйвер ORACLE — это двухуровневый драйвер.  
  
 SQL_FILE_TABLE = одноуровневый драйвер рассматривает файлы в источнике данных как таблицы. Например, драйвер xbase обрабатывает каждый файл xbase как таблицу.  
  
 SQL_FILE_CATALOG = одноуровневый драйвер рассматривает файлы в источнике данных как каталог. Например, драйвер Microsoft Access обрабатывает каждый файл Microsoft Access как полную базу данных.  
  
 Приложение может использовать его для определения того, как пользователи будут выбирать данные. Например, xbase пользователи часто считают данные хранимыми в файлах, тогда как пользователи ORACLE и Microsoft Access обычно считают данные хранимыми в таблицах.  
  
 Когда пользователь выбирает источник данных xbase, приложение может отобразить диалоговое окно Открыть общий **файл** Windows. Когда пользователь выбирает источник данных Microsoft Access или ORACLE, приложение может отобразить диалоговое окно Выбор пользовательской **таблицы** .  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты однопроходного курсора, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и в описаниях замените "однонаправленный курсор" на "динамический курсор").  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты однопроходного курсора, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и в описаниях замените "однонаправленный курсор" на "динамический курсор").  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2,0)  
 Битовая маска SQLUINTEGER, перечисление расширений в **SQLGetData**.  
  
 Следующие битовые маски используются вместе с флагом, чтобы определить, какие общие расширения драйвер поддерживает для **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** можно вызывать для любого несвязанного столбца, включая те, которые предшествуют последнему привязанному столбцу. Обратите внимание, что столбцы должны вызываться в порядке возрастания номера столбца, если также не возвращается SQL_GD_ANY_ORDER.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** можно вызывать для несвязанных столбцов в любом порядке. Обратите внимание, что **SQLGetData** может вызываться только для столбцов после последнего связанного столбца, если не возвращается значение SQL_GD_ANY_COLUMN.  
  
 SQL_GD_BLOCK = **SQLGetData** можно вызывать для непривязанного столбца в любой строке блока (где размер набора строк больше 1) данных после позиционирования в эту строку с помощью функции **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** можно вызывать для связанных столбцов в дополнение к несвязанным столбцам. Драйвер не может вернуть это значение, если он также не возвращает SQL_GD_ANY_COLUMN.  
  
 Для возврата значений выходных параметров можно вызвать SQL_GD_OUTPUT_PARAMS = **SQLGetData** . Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** требуется для возврата данных только из несвязанных столбцов, которые происходят после последнего связанного столбца, вызываются в порядке возрастания номера столбца и не находятся в строке блока строк.  
  
 Если драйвер поддерживает закладки (с фиксированной длиной или переменной длиной), он должен поддерживать вызов **SQLGetData** для столбца 0. Эта поддержка необходима независимо от того, что возвращает драйвер для вызова **SQLGetInfo** с помощью SQL_GETDATA_EXTENSIONS *инфотипе*.  
  
 SQL_GROUP_BY (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее связь между столбцами в предложении **Group By** и неагрегированными столбцами в списке выбора:  
  
 SQL_GB_COLLATE = предложение **COLLATE** можно указать в конце каждого столбца группирования. (ODBC 3,0)  
  
 SQL_GB_NOT_SUPPORTED = предложения **Group By** не поддерживаются. (ODBC 2,0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = предложение **Group By** должно содержать все неагрегированные столбцы в списке выбора. Он не может содержать другие столбцы. Например, **выберите отдел, Макс (оклад) из группы сотрудников по Отделу**. (ODBC 2,0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = предложение **Group By** должно содержать все неагрегированные столбцы в списке выбора. Он может содержать столбцы, которых нет в списке выбора. Например, **выберите отдел, Макс (зарплата) из группы сотрудников по Отделу, возраст**. (ODBC 2,0)  
  
 SQL_GB_NO_RELATION = столбцы в предложении **Group By** и список выбора не связаны. Значение несгруппированных неагрегированных столбцов в списке выбора зависит от источника данных. Например, **выберите отдел, ОКЛАД из группы сотрудников по Отделу, возраст**. (ODBC 2,0)  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать параметр SQL_GB_GROUP_BY_EQUALS_SELECT, как поддерживается. Драйвер, совместимый с SQL-92, всегда будет возвращать параметр SQL_GB_COLLATE, как поддерживается. Если ни один из параметров не поддерживается, то предложение **Group By** не поддерживается источником данных.  
  
 SQL_IDENTIFIER_CASE (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ следующим образом:  
  
 SQL_IC_UPPER = идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в верхнем регистре.  
  
 SQL_IC_LOWER = идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в нижнем регистре.  
  
 SQL_IC_SENSITIVE = идентификаторы в SQL учитывают регистр и хранятся в системном каталоге в смешанном регистре.  
  
 SQL_IC_MIXED = идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в смешанном регистре.  
  
 Поскольку идентификаторы в SQL-92 никогда не учитывают регистр, драйвер, который строго соответствует SQL-92 (любой уровень), никогда не будет возвращать параметр SQL_IC_SENSITIVE, как поддерживается.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1,0)  
 Символьная строка, используемая в качестве начального и конечного разделителей (разделенных кавычками) идентификаторов в инструкциях SQL. (Идентификаторы, переданные в качестве аргументов в функции ODBC, не обязательно должны быть заключены в кавычки.) Если источник данных не поддерживает заключенные в кавычки идентификаторы, то возвращается пустое значение.  
  
 Эту символьную строку можно также использовать для заключения в кавычки аргументов функции каталога, если атрибут Connection SQL_ATTR_METADATA_ID имеет значение SQL_TRUE.  
  
 Поскольку символ кавычки идентификатора в SQL-92 представляет собой двойную кавычку ("), драйвер, который строго соответствует SQL-92, всегда будет возвращать символ двойной кавычки.  
  
 SQL_INDEX_KEYWORDS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет ключевые слова в инструкции CREATE INDEX, поддерживаемые драйвером.  
  
 SQL_IK_NONE = ни одно из ключевых слов не поддерживается.  
  
 Поддерживается ключевое слово SQL_IK_ASC = ASC.  
  
 SQL_IK_DESC = ключевое слово DESC поддерживается.  
  
 SQL_IK_ALL = все ключевые слова поддерживаются.  
  
 Чтобы узнать, поддерживается ли инструкция CREATE INDEX, приложение вызывает **SQLGetInfo** с типом данных SQL_DLL_INDEX.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет представления в INFORMATION_SCHEMA, поддерживаемые драйвером. Представления в, а также содержимое INFORMATION_SCHEMA являются определенными в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения поддерживаемых представлений используются следующие битовые маски:  
  
 SQL_ISV_ASSERTIONS = определяет утверждения каталога, принадлежащие данному пользователю. (Полный уровень)  
  
 SQL_ISV_CHARACTER_SETS = определяет наборы символов каталога, к которым может получить доступ указанный пользователь. (Промежуточный уровень)  
  
 SQL_ISV_CHECK_CONSTRAINTS = определяет ПРОВЕРОЧные ограничения, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_COLLATIONS = определяет параметры сортировки символов для каталога, к которому может получить доступ данный пользователь. (Полный уровень)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = определяет столбцы для каталога, зависящие от доменов, определенных в каталоге и принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_COLUMN_PRIVILEGES = определяет привилегии для столбцов постоянных таблиц, доступных или предоставленных данным пользователем. (Уровень переходов FIPS)  
  
 SQL_ISV_COLUMNS = определяет столбцы постоянных таблиц, к которым может получить доступ данный пользователь. (Уровень переходов FIPS)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE — аналогично CONSTRAINT_TABLE_USAGE View, столбцы определяются для различных ограничений, принадлежащих данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = определяет таблицы, используемые ограничениями (ссылочные, уникальные и проверочные), и принадлежат заданному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = определяет ограничения домена (для доменов в каталоге), к которым может получить доступ указанный пользователь. (Промежуточный уровень)  
  
 SQL_ISV_DOMAINS = определяет домены, определенные в каталоге, к которому может получить доступ пользователь. (Промежуточный уровень)  
  
 SQL_ISV_KEY_COLUMN_USAGE = определяет столбцы, определенные в каталоге и ограниченные ключами данного пользователя. (Промежуточный уровень)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = определяет ссылочные ограничения, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_SCHEMATA = определяет схемы, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_SQL_LANGUAGES = определяет уровни соответствия SQL, параметры и диалекты, поддерживаемые реализацией SQL. (Промежуточный уровень)  
  
 SQL_ISV_TABLE_CONSTRAINTS = определяет ограничения таблицы, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_TABLE_PRIVILEGES = определяет привилегии для постоянных таблиц, доступных или предоставленных данным пользователем. (Уровень переходов FIPS)  
  
 SQL_ISV_TABLES = определяет постоянные таблицы, определенные в каталоге, к которым может получить доступ данный пользователь. (Уровень переходов FIPS)  
  
 SQL_ISV_TRANSLATIONS = определяет переводы символов для каталога, к которому может получить доступ данный пользователь. (Полный уровень)  
  
 SQL_ISV_USAGE_PRIVILEGES = определяет привилегии на использование объектов каталога, доступных или принадлежащих данному пользователю. (Уровень переходов FIPS)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = определяет столбцы, от которых зависят представления каталога, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_VIEW_TABLE_USAGE = определяет таблицы, от которых зависят представления каталога, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_VIEWS = определяет просмотренные таблицы, определенные в этом каталоге, к которым может получить доступ данный пользователь. (Уровень переходов FIPS)  
  
 SQL_INSERT_STATEMENT (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая указывает на поддержку инструкций **INSERT** :  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_INTEGRITY (ODBC 1,0)  
 Строка символов: "Y", если источник данных поддерживает функцию улучшения целостности; "N", если нет.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_ODBC_SQL_OPT_IEF ODBC 2,0 *инфотипе* .  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты курсора KEYSET, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и подставьте курсор, управляемый набором ключей, для динамического курсора в описаниях).  
  
 Драйвер, поддерживающий промежуточный уровень SQL-92, обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE, так как они поддерживаются, так как драйвер поддерживает прокручиваемые курсоры с помощью внедренной инструкции SQL FETCH. Так как это не определяет непосредственно базовую поддержку SQL, возможно, прокручиваемые курсоры не поддерживаются даже для драйвера, соответствующего промежуточному уровню SQL-92.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты курсора KEYSET, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и подставьте курсор, управляемый набором ключей, для динамического курсора в описаниях).  
  
 SQL_KEYWORDS (ODBC 2,0)  
 Символьная строка, содержащая разделенный запятыми список всех ключевых слов, зависящих от источника данных. Этот список не содержит ключевые слова, относящиеся к ODBC или ключевым словам, используемым как источником данных, так и ODBC. Этот список представляет все зарезервированные ключевые слова; приложения, поддерживающие взаимодействие, не должны использовать эти слова в именах объектов.  
  
 Список ключевых слов ODBC см. в разделе [зарезервированные ключевые слова](../../../odbc/reference/appendixes/reserved-keywords.md) в [приложении C: грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Значение **#define** SQL_ODBC_KEYWORDS содержит список ключевых слов ODBC с разделителями-запятыми.  
  
 Приложение В. Грамматика SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2,0)  
 Символьная строка: "Y", если источник данных поддерживает escape-символ для символа процента (%) и символ подчеркивания (_) в предикате **Like** , а драйвер поддерживает синтаксис ODBC для определения escape-символа предиката **Like** ; В противном случае — значение "N".  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее максимальное количество активных параллельных операторов в асинхронном режиме, которые драйвер может поддерживать для данного соединения. Если нет какого-либо конкретного ограничения или неизвестного ограничения, это значение равно нулю.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2,0)  
 Значение SQLUINTEGER, указывающее максимальную длину (число шестнадцатеричных символов, исключая префикс литерала и суффикс, возвращаемый **SQLGetTypeInfo**) двоичного литерала в инструкции SQL. Например, двоичный литерал 0xFFAA имеет длину 4. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени каталога в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 Драйвер полного соответствия FIPS будет возвращать не менее 128.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_MAX_QUALIFIER_NAME_LEN ODBC 2,0 *инфотипе* .  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2,0)  
 Значение SQLUINTEGER, указывающее максимальную длину (число символов, за исключением префикса литерала и суффикса, возвращаемого **SQLGetTypeInfo**) символьного литерала в инструкции SQL. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени столбца в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество столбцов, разрешенное в предложении **Group By** . Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 6. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 15.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимально допустимое количество столбцов в индексе. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное число столбцов, разрешенное в предложении **ORDER BY** . Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 6. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 15.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное число столбцов, допустимое в списке выбора. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает по крайней мере 100. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимально допустимое количество столбцов в таблице. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает по крайней мере 100. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных инструкций, которые драйвер может поддерживать для соединения. Инструкция определена как активная, если она имеет ожидающие результаты, а термин «Results» означает строки из операции **выбора** или строки, на которые повлияла операция **вставки**, **обновления**или **удаления** (например, число строк), или если она находится в NEED_DATA состоянии. Это значение может отражать ограничение, налагаемое либо драйвером, либо источником данных. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_ACTIVE_STATEMENTS ODBC 2,0 *инфотипе* .  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени курсора в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных соединений, которые драйвер может поддерживать для среды. Это значение может отражать ограничение, налагаемое либо драйвером, либо источником данных. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_ACTIVE_CONNECTIONS ODBC 2,0 *инфотипе* .  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3,0)  
 Объект СКЛУСМАЛЛИНТ, указывающий максимальный размер в символах, поддерживаемый источником данных для определяемых пользователем имен.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2,0)  
 Значение SQLUINTEGER, указывающее максимальное число байтов, разрешенное в Объединенных полях индекса. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени процедуры в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 SQL_MAX_ROW_SIZE (ODBC 2,0)  
 Значение SQLUINTEGER, указывающее максимальную длину одной строки в таблице. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает по крайней мере 2 000. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 8 000.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3,0)  
 Строка символов: "Y", если максимальный размер строки, возвращаемый для типа сведений SQL_MAX_ROW_SIZE, содержит длину всех SQL_LONGVARCHAR и SQL_LONGVARBINARY столбцов в строке; В противном случае — значение "N".  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени схемы в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_MAX_OWNER_NAME_LEN ODBC 2,0 *инфотипе* .  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2,0)  
 Значение SQLUINTEGER, указывающее максимальную длину (число символов, включая пробел) инструкции SQL. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени таблицы в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество таблиц, допустимых в предложении **from** инструкции **SELECT** . Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 15. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 50.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени пользователя в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.  
  
 SQL_MULT_RESULT_SETS (ODBC 1,0)  
 Символьная строка: "Y", если источник данных поддерживает несколько результирующих наборов, "N", если нет.  
  
 Дополнительные сведения о нескольких результирующих наборах см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1,0)  
 Строка символов: "Y", если драйвер поддерживает несколько активных транзакций одновременно, "N", если в любой момент времени может быть активна только одна транзакция.  
  
 Сведения, возвращаемые для этого типа данных, не применяются в случае распределенных транзакций.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2,0)  
 Символьная строка: "Y", если источнику данных требуется длина длинного значения данных (тип данных SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных, зависящий от источника данных), прежде чем это значение будет отправлено в источник данных, "N", если нет. Дополнительные сведения см. в разделе [функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) и [Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, поддерживает ли источник данных не значение NULL в столбцах:  
  
 SQL_NNC_NULL = все столбцы должны допускать значение null.  
  
 SQL_NNC_NON_NULL = столбцы не могут допускать значения NULL. (Источник данных поддерживает ограничение столбца **NOT NULL** в инструкциях **CREATE TABLE** .)  
  
 Драйвер, поддерживающий уровень ввода SQL-92, возвращает SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее, где в результирующем наборе сортируются значения NULL:  
  
 SQL_NC_END = NULL сортируются в конце результирующего набора независимо от ключевых слов ASC и DESC.  
  
 SQL_NC_HIGH = NULL сортируются по верхнему краю результирующего набора в зависимости от ключевых слов ASC или DESC.  
  
 SQL_NC_LOW = NULL сортируются в нижней части результирующего набора в зависимости от ключевых слов ASC или DESC.  
  
 SQL_NC_START = NULL сортируются в начале результирующего набора независимо от ключевых слов ASC и DESC.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1,0)  
 Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.  
  
 Битовая маска SQLUINTEGER, которая перечисляет скалярные числовые функции, поддерживаемые драйвером и связанным источником данных.  
  
 Для определения поддерживаемых числовых функций используются следующие битовые маски.  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 1.0) SQL_FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 2.0) SQL_FN_NUM_LOG10 NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 2,0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее уровень интерфейса ODBC 3 *. x* , который соответствует драйверу.  
  
 SQL_OIC_CORE: минимальный уровень, которым должны соответствовать все драйверы ODBC. Этот уровень включает основные элементы интерфейса, такие как функции подключения, функции для подготовки и исполнения инструкции SQL, основные функции метаданных результирующего набора, базовые функции каталога и т. д.  
  
 SQL_OIC_LEVEL1: уровень, включая основные функции уровня соответствия стандартам, а также прокручиваемые курсоры, закладки, позиционированные обновления и удаления и т. д.  
  
 SQL_OIC_LEVEL2: уровень, включающий функции уровня соответствия стандартам уровня 1, а также расширенные функции, такие как конфиденциальные курсоры; обновление, удаление и обновление по закладкам; Поддержка хранимых процедур; функции каталога для первичных и внешних ключей; Поддержка нескольких каталогов; и т. д.  
  
 Дополнительные сведения см. в разделе [уровни соответствия интерфейсов](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER (ODBC 1,0)  
 Символьная строка с версией ODBC, которая соответствует диспетчеру драйверов. Версия имеет вид # #. # #. 0000, где первые две цифры — основной номер версии, а следующие две цифры — дополнительный номер версии. Это реализовано только в диспетчере драйверов.  
  
 SQL_OJ_CAPABILITIES (ODBC 2,01)  
 Битовая маска SQLUINTEGER, которая перечисляет типы внешних соединений, поддерживаемые драйвером и источником данных. Для определения поддерживаемых типов используются следующие битовые маски:  
  
 SQL_OJ_LEFT = левые внешние объединения поддерживаются.  
  
 SQL_OJ_RIGHT — поддерживаются правая внешние объединения.  
  
 SQL_OJ_FULL = поддерживаются полные внешние объединения.  
  
 SQL_OJ_NESTED = поддерживаются вложенные внешние объединения.  
  
 SQL_OJ_NOT_ORDERED = имена столбцов в предложении ON внешнего объединения не обязательно должны находиться в том же порядке, что и соответствующие имена таблиц в предложении **внешнего объединения** .  
  
 SQL_OJ_INNER = внутренняя таблица (правая таблица в левом внешнем соединении или Левая таблица в правом внешнем соединении) также может использоваться во внутреннем соединении. Это не относится к полным внешним объединениям, у которых нет внутренней таблицы.  
  
 SQL_OJ_ALL_COMPARISON_OPS = оператор сравнения в предложении ON может быть любым из операторов сравнения ODBC. Если этот бит не задан, в внешних объединениях может использоваться только оператор сравнения Equals (=).  
  
 Если ни один из этих параметров не возвращается как поддерживаемый, предложение внешнего объединения не поддерживается.  
  
 Сведения о поддержке операторов реляционного объединения в инструкции SELECT, как определено в SQL-92, см. в разделе SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2,0)  
 Строка символов: "Y", если столбцы в предложении **ORDER BY** должны находиться в списке выбора; в противном случае — "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3,0)  
 SQLUINTEGER перечисление свойств драйвера, касающихся доступности количества строк в параметризованном выполнении. Имеет следующие значения:  
  
 SQL_PARC_BATCH = количество отдельных строк доступно для каждого набора параметров. Это концептуально эквивалентно драйверу, создающему пакет инструкций SQL, по одному для каждого набора параметров в массиве. Расширенные сведения об ошибке можно получить с помощью поля дескриптор SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH = доступно только одно количество строк, то есть общее число строк, полученное в результате выполнения инструкции для всего массива параметров. Это концептуально эквивалентно обработке инструкции вместе с полным массивом параметров как одной атомарной единицей. Ошибки обрабатываются так же, как если бы выполнялась одна инструкция.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3,0)  
 SQLUINTEGER перечисление свойств драйвера, касающихся доступности результирующих наборов в параметризованном выполнении. Имеет следующие значения:  
  
 SQL_PAS_BATCH = для каждого набора параметров доступен один результирующий набор. Это концептуально эквивалентно драйверу, создающему пакет инструкций SQL, по одному для каждого набора параметров в массиве.  
  
 SQL_PAS_NO_BATCH = доступен только один результирующий набор, который представляет собой совокупный результат, полученный в результате выполнения инструкции для полного массива параметров. Это концептуально эквивалентно обработке инструкции вместе с полным массивом параметров как одной атомарной единицей.  
  
 SQL_PAS_NO_SELECT = драйвер не позволяет выполнять инструкцию создания результирующего набора с массивом параметров.  
  
 SQL_PROCEDURE_TERM (ODBC 1,0)  
 Символьная строка с именем поставщика источника данных для процедуры; Например, "процедура базы данных", "хранимая процедура", "процедура", "пакет" или "хранимый запрос".  
  
 SQL_PROCEDURES (ODBC 1,0)  
 Символьная строка: "Y", если источник данных поддерживает процедуры, а драйвер поддерживает синтаксис вызова процедур ODBC. В противном случае — значение "N".  
  
 SQL_POS_OPERATIONS (ODBC 2,0)  
 Битовая маска SQLINTEGER, перечисление операций поддержки в **SQLSetPos**.  
  
 Следующие битовые маски используются вместе с флагом для определения поддерживаемых параметров.  
  
 SQL_POS_POSITION (ODBC 2,0) SQL_POS_REFRESH (ODBC 2,0) SQL_POS_UPDATE (ODBC 2,0) SQL_POS_DELETE (ODBC 2,0) SQL_POS_ADD (ODBC 2,0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2,0)  
 Значение СКЛУСМАЛЛИНТ следующим образом:  
  
 SQL_IC_UPPER = заключенные в кавычки идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в верхнем регистре.  
  
 SQL_IC_LOWER = заключенные в кавычки идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в нижнем регистре.  
  
 SQL_IC_SENSITIVE = заключенные в кавычки идентификаторы в SQL учитывают регистр и хранятся в системном каталоге в смешанном регистре. (В базе данных, совместимой с SQL-92, заключенные в кавычки идентификаторы всегда чувствительны к регистру.)  
  
 SQL_IC_MIXED = заключенные в кавычки идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в смешанном регистре.  
  
 Драйвер, поддерживающий уровень ввода SQL-92, всегда будет возвращать SQL_IC_SENSITIVE.  
  
 SQL_ROW_UPDATES (ODBC 1,0)  
 Символьная строка: "Y", если курсор, управляемый набором ключей или смешанный, поддерживает версии строк или значения для всех выбранных строк и, следовательно, может обнаруживать любые обновления, внесенные в строку любым пользователем со времени последней выборки строки. (Это относится только к обновлениям, а не к операциям удаления или вставки.) Драйвер может вернуть SQL_ROW_UPDATED флаг к массиву состояния строки при вызове **SQLFetchScroll** . В противном случае — "N".  
  
 SQL_SCHEMA_TERM (ODBC 1,0)  
 Символьная строка с именем поставщика источника данных для схемы; Например, "владелец", "идентификатор авторизации" или "схема".  
  
 Символьная строка может быть возвращена в верхнем, нижнем или смешанном регистрах.  
  
 Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает "Schema".  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_OWNER_TERM ODBC 2,0 *инфотипе* .  
  
 SQL_SCHEMA_USAGE (ODBC 2,0)  
 Битовая маска SQLUINTEGER, которая перечисляет инструкции, в которых можно использовать схемы:  
  
 SQL_SU_DML_STATEMENTS = схемы поддерживаются во всех инструкциях языка обработки данных: **SELECT**, **INSERT**, **Update**, **Delete**и, если поддерживается, **SELECT для Update** и позиционированных инструкций UPDATE и DELETE.  
  
 SQL_SU_PROCEDURE_INVOCATION = схемы поддерживаются в операторе вызова процедуры ODBC.  
  
 SQL_SU_TABLE_DEFINITION = схемы поддерживаются во всех инструкциях определения таблицы: **CREATE TABLE**, **Create View**, **ALTER TABLE**, **DROP TABLE**и **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = схемы поддерживаются во всех инструкциях определения индекса: **Создание индекса** и **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = схемы поддерживаются во всех инструкциях определения привилегий: **Grant** и **REVOKE**.  
  
 Драйвер на уровне ввода SQL-92 всегда будет возвращать параметры SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION и SQL_SU_PRIVILEGE_DEFINITION, как поддерживается.  
  
 Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_OWNER_USAGE ODBC 2,0 *инфотипе* .  
  
 SQL_SCROLL_OPTIONS (ODBC 1,0)  
 Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.  
  
 Битовая маска SQLUINTEGER, которая перечисляет параметры прокрутки, поддерживаемые для прокручиваемых курсоров.  
  
 Для определения поддерживаемых параметров используются следующие битовые маски.  
  
 SQL_SO_FORWARD_ONLY = курсор прокручивается вперед. (ODBC 1,0)  
  
 SQL_SO_STATIC = данные в результирующем наборе являются статическими. (ODBC 2,0)  
  
 SQL_SO_KEYSET_DRIVEN = драйвер сохраняет и использует ключи для каждой строки в результирующем наборе. (ODBC 1,0)  
  
 SQL_SO_DYNAMIC = драйвер сохраняет ключи для каждой строки в наборе строк (размер набора ключей совпадает с размером наборов строк). (ODBC 1,0)  
  
 SQL_SO_MIXED = драйвер сохраняет ключи для каждой строки набора ключей, а размер набора ключей больше размера набора строк. Курсор, управляемый набором ключей, находится внутри набора ключей и является динамическим за пределами набора ключей. (ODBC 1,0)  
  
 Дополнительные сведения о прокручиваемых курсорах см. в разделе [прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1,0)  
 Символьная строка, указывающая, что драйвер поддерживает в качестве escape-символа, позволяющего использовать символы подчеркивания шаблона (_) и знак процента (%) в качестве допустимых символов в шаблонах поиска. Этот escape-символ применяется только к тем аргументам функции каталога, которые поддерживают строки поиска. Если эта строка пуста, драйвер не поддерживает escape-символ шаблона поиска.  
  
 Так как этот тип информации не указывает на общую поддержку escape-символа в предикате **Like** , SQL-92 не включает требования для этой символьной строки.  
  
 Эта *инфотипеа* ограничена функциями каталога. Описание использования escape-символа в строках шаблона поиска см. в разделе [аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME (ODBC 1,0)  
 Символьная строка с фактическим именем сервера, относящимся к источнику данных; полезно, когда имя источника данных используется во время **SQLConnect**, **SQLDriverConnect**и **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2,0)  
 Символьная строка, содержащая все специальные символы (т. е. все символы, за исключением от a до z, от A до Z, от 0 до 9 и символа подчеркивания), которые можно использовать в имени идентификатора, например имя таблицы, имя столбца или имя индекса, в источнике данных. Например, "# $ ^". Если идентификатор содержит один или несколько из этих символов, идентификатор должен быть идентификатором с разделителями.  
  
 SQL_SQL_CONFORMANCE (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее уровень поддержки SQL-92, поддерживаемый драйвером.  
  
 SQL_SC_SQL92_ENTRY — соответствует уровню ввода SQL-92.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = уровень соответствия FIPS 127-2.  
  
 SQL_SC_SQL92_FULL = полный уровень соответствует SQL-92.  
  
 SQL_SC_ SQL92_INTERMEDIATE = SQL-92, соответствующий промежуточному уровню.  
  
 SQL_SQL92_DATETIME_FUNCTIONS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет скалярные функции DateTime, поддерживаемые драйвером, и соответствующий источник данных, как определено в SQL-92.  
  
 Для определения поддерживаемых функций datetime используются следующие битовые маски:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет правила, поддерживаемые внешним ключом в инструкции **Delete** , как определено в SQL-92.  
  
 Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет правила, поддерживаемые для внешнего ключа в инструкции **Update** , как определено в SQL-92.  
  
 Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_SQL92_GRANT (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет предложения, поддерживаемые в инструкции **Grant** , как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:  
  
 SQL_SG_DELETE_TABLE (начального уровня) SQL_SG_INSERT_COLUMN (промежуточный уровень) SQL_SG_INSERT_TABLE SQL_SG_REFERENCES_TABLE (уровень записи) SQL_SG_REFERENCES_COLUMN (начального уровня) SQL_SG_SELECT_TABLE (начального уровня) SQL_SG_UPDATE_COLUMN (уровень записи) SQL_SG_UPDATE_TABLE (уровень записи) SQL_SG_USAGE_ON_DOMAIN (уровень перехода FIPS) SQL_SG_USAGE_ON_CHARACTER_SET SQL_SG_USAGE_ON_COLLATION (уровень перехода FIPS уровень) SQL_SG_WITH_GRANT_OPTION (уровень записи)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление скалярных функций числовых значений, поддерживаемых драйвером и связанным источником данных, как определено в SQL-92.  
  
 Для определения поддерживаемых числовых функций используются следующие битовые маски.  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет предикаты, поддерживаемые в инструкции **SELECT** , как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.  
  
 SQL_SP_BETWEEN (начального уровня) SQL_SP_COMPARISON (начального уровня) SQL_SP_EXISTS SQL_SP_IN (начального уровня) SQL_SP_ISNOTNULL (начального уровня) SQL_SP_ISNULL (уровень записи) SQL_SP_LIKE (полный уровень) SQL_SP_MATCH_FULL (полный уровень) SQL_SP_MATCH_PARTIAL (полный уровень) (SQL_SP_MATCH_UNIQUE_FULL) SQL_SP_MATCH_UNIQUE_PARTIAL (уровень "на уровень") (уровень "Entry" () SQL_SP_OVERLAPS (на уровне записи)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет операторы реляционного объединения, поддерживаемые в инструкции **SELECT** , как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (промежуточный уровень) SQL_SRJO_CROSS_JOIN (полный уровень) SQL_SRJO_FULL_OUTER_JOIN SQL_SRJO_EXCEPT_JOIN (промежуточный уровень) SQL_SRJO_INNER_JOIN (промежуточный уровень FIPS) SQL_SRJO_INTERSECT_JOIN SQL_SRJO_LEFT_OUTER_JOIN (промежуточный уровень FIPS) SQL_SRJO_NATURAL_JOIN (уровень перехода FIPS) SQL_SRJO_RIGHT_OUTER_JOIN SQL_SRJO_UNION_JOIN (полный уровень)  
  
 SQL_SRJO_INNER_JOIN указывает поддержку для синтаксиса **внутреннего объединения** , а не для возможности внутреннего объединения. Поддержка синтаксиса **внутреннего объединения** — это переход на стандарт FIPS, тогда как поддержка внутреннего объединения является **записью**.  
  
 SQL_SQL92_REVOKE (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет предложения, поддерживаемые в инструкции **REVOKE** , как определено в SQL-92, поддерживаемом источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:  
  
 SQL_SR_CASCADE (уровень переходов FIPS) SQL_SR_DELETE_TABLE (уровень ввода) SQL_SR_GRANT_OPTION_FOR (промежуточный уровень) SQL_SR_INSERT_COLUMN (промежуточный уровень) SQL_SR_INSERT_TABLE (уровень записи) SQL_SR_REFERENCES_COLUMN (уровень записи) SQL_SR_REFERENCES_TABLE (уровень ввода FIPS) SQL_SR_RESTRICT (уровень записи) SQL_SR_SELECT_TABLE SQL_SR_UPDATE_COLUMN (уровень записи) SQL_SR_UPDATE_TABLE УСТАНОВИТЬ (уровень переходов FIPS) SQL_SR_USAGE_ON_COLLATION (уровень переходов FIPS) SQL_SR_USAGE_ON_TRANSLATION (уровень поддержки FIPS)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет выражения конструктора значений строк, поддерживаемые в инструкции **SELECT** , как определено в SQL-92. Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление строковых скалярных функций, поддерживаемых драйвером, и связанным источником данных, как определено в SQL-92.  
  
 Для определения поддерживаемых строковых функций используются следующие битовые маски:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет поддерживаемые выражения значений, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.  
  
 SQL_SVE_CASE (промежуточный уровень) SQL_SVE_CAST (уровень перехода FIPS) SQL_SVE_COALESCE SQL_SVE_NULLIF (промежуточный уровень)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет стандарт CLI или стандарты, которым соответствует драйвер. Для определения уровней, которые соответствует драйверу, используются следующие маски.  
  
 SQL_SCC_XOPEN_CLI_VERSION1: драйвер соответствует CLI открытой группы, версия 1.  
  
 SQL_SCC_ISO92_CLI. драйвер соответствует интерфейсу командной строки ISO 92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты статического курсора, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (в описаниях — "статический курсор" для динамического курсора).  
  
 Драйвер, поддерживающий промежуточный уровень SQL-92, обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE, так как они поддерживаются, так как драйвер поддерживает прокручиваемые курсоры с помощью внедренной инструкции SQL FETCH. Так как это не определяет непосредственно базовую поддержку SQL, возможно, прокручиваемые курсоры не поддерживаются даже для драйвера, соответствующего промежуточному уровню SQL-92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Битовая маска SQLUINTEGER, описывающая атрибуты статического курсора, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Для определения поддерживаемых атрибутов используются следующие битовые маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (в описаниях — "статический курсор" для динамического курсора).  
  
 SQL_STRING_FUNCTIONS (ODBC 1,0)  
 Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.  
  
 Битовая маска SQLUINTEGER, перечисление скалярных строковых функций, поддерживаемых драйвером и связанным источником данных.  
  
 Для определения поддерживаемых строковых функций используются следующие битовые маски:  
  
 SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 1.0) SQL_FN_STR_INSERT (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT SQL_FN_STR_LENGTH (ODBC 1,0) SQL_FN_STR_LOCATE (ODBC 1,0) SQL_FN_STR_OCTET_LENGTH (ODBC 3,0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 1.0) SQL_FN_STR_REPEAT (ODBC 1,0) SQL_FN_STR_SUBSTRING  
  
 Если приложение может вызвать скалярную функцию " **Открыть** " с аргументами *string_exp1*, *string_exp2*и *Start* , драйвер возвращает SQL_FN_STR_LOCATE битовую маску. Если приложение может вызвать скалярную функцию «нахождение» только с аргументами *string_exp1* и *string_exp2* , драйвер возвращает SQL_FN_STR_LOCATE_2 битовую маску. Драйверы, полностью поддерживающие скалярную функцию " **разместить** ", возвращают обе битовые маски.  
  
 (Дополнительные сведения см. в разделе [функции строк](../../../odbc/reference/appendixes/string-functions.md) в приложении E "скалярные функции".)  
  
 SQL_SUBQUERIES (ODBC 2,0)  
 Битовая маска SQLUINTEGER, перечисление предикатов, которые поддерживают вложенные запросы:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Битовая маска SQL_SQ_CORRELATED_SUBQUERIES указывает, что все предикаты, поддерживающие вложенные запросы, поддерживают коррелированные вложенные запросы.  
  
 Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает битовую маску, в которой установлены все эти биты.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1,0)  
 Битовая маска SQLUINTEGER, перечисление скалярных системных функций, поддерживаемых драйвером и связанным источником данных.  
  
 Для определения поддерживаемых системных функций используются следующие битовые маски.  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1,0)  
 Символьная строка с именем поставщика источника данных для таблицы; Например, "Table" или "File".  
  
 Эта символьная строка может быть в верхнем, нижнем или смешанном регистре.  
  
 Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает "Table".  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2,0)  
 Битовая маска SQLUINTEGER, которая перечисляет интервалы времени, поддерживаемые драйвером, и соответствующий источник данных для скалярной функции ТИМЕСТАМПАДД.  
  
 Для определения поддерживаемых интервалов используются следующие битовые маски:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Драйвер, поддерживающий переход на уровне FIPS, всегда возвращает битовую маску, в которой установлены все эти биты.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2,0)  
 Битовая маска SQLUINTEGER, которая перечисляет интервалы времени, поддерживаемые драйвером, и соответствующий источник данных для скалярной функции ТИМЕСТАМПДИФФ.  
  
 Для определения поддерживаемых интервалов используются следующие битовые маски:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Драйвер, поддерживающий переход на уровне FIPS, всегда возвращает битовую маску, в которой установлены все эти биты.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1,0)  
 Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.  
  
 Битовая маска SQLUINTEGER, которая перечисляет скалярные функции даты и времени, поддерживаемые драйвером, и связанным источником данных.  
  
 Для определения поддерживаемых функций даты и времени используются следующие битовые маски:  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1,0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1,0) SQL_FN_TD_EXTRACT SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_SECOND (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 1.0) SQL_FN_TD_WEEK (ODBC 1,0)  
  
 SQL_TXN_CAPABLE (ODBC 1,0)  
 Примечание. Этот тип информации появился в ODBC 1,0; каждое возвращаемое значение помечено версией, в которой оно было введено.  
  
 Значение СКЛУСМАЛЛИНТ, описывающее поддержку транзакций в драйвере или источнике данных:  
  
 SQL_TC_NONE = транзакции не поддерживаются. (ODBC 1,0)  
  
 SQL_TC_DML = транзакции могут содержать только инструкции языка обработки данных DML (**Выбор**, **Вставка**, **Обновление**, **Удаление**). Инструкции языка описания данных DDL, обнаруженные в транзакции, приводят к ошибке. (ODBC 1,0)  
  
 SQL_TC_DDL_COMMIT = транзакции могут содержать только инструкции DML. Инструкции DDL (**CREATE TABLE**, **DROP INDEX**и т. д.), обнаруженные в транзакции, приводят к фиксации транзакции. (ODBC 2,0)  
  
 SQL_TC_DDL_IGNORE = транзакции могут содержать только инструкции DML. Инструкции DDL, обнаруженные в транзакции, игнорируются. (ODBC 2,0)  
  
 SQL_TC_ALL = транзакции могут содержать инструкции DDL и инструкции DML в любом порядке. (ODBC 1,0)  
  
 (Поскольку поддержка транзакций обязательна в SQL-92, встроенный драйвер SQL-92 [любой уровень] никогда не возвращает SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1,0)  
 Битовая маска SQLUINTEGER, которая перечисляет уровни изоляции транзакций, доступные из драйвера или источника данных.  
  
 Следующие битовые маски используются вместе с флагом для определения поддерживаемых параметров:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Описание этих уровней изоляции см. в описании SQL_DEFAULT_TXN_ISOLATION.  
  
 Чтобы задать уровень изоляции транзакции, приложение вызывает **SQLSetConnectAttr** , чтобы установить атрибут SQL_ATTR_TXN_ISOLATION. Дополнительные сведения см. в разделе [функция SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Драйвер на уровне ввода SQL-92 всегда будет возвращать SQL_TXN_SERIALIZABLE, как поддерживается. Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.  
  
 SQL_UNION (ODBC 2,0)  
 Битовая маска SQLUINTEGER, которая перечисляет поддержку предложения **Union** :  
  
 SQL_U_UNION = источник данных поддерживает предложение **Union** .  
  
 SQL_U_UNION_ALL = источник данных поддерживает ключевое слово **ALL** в предложении **Union** . (В данном случае**SQLGetInfo** возвращает как SQL_U_UNION, так SQL_U_UNION_ALL.)  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать оба этих параметра, как поддерживается.  
  
 SQL_USER_NAME (ODBC 1,0)  
 Символьная строка с именем, используемой в конкретной базе данных, которая может отличаться от имени для входа.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3,0)  
 Символьная строка, указывающая год публикации спецификации Open Group, с которой полностью согласуется версия диспетчера драйверов ODBC.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1,0)  
 Строка символов: "Y", если пользователь может выполнить все процедуры, возвращенные **SQLProcedures**; "N", если могут быть возвращены процедуры, которые пользователь не может выполнить.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1,0)  
 Строка символов: "Y", если пользователь гарантированно **выбирает** права доступа ко всем таблицам, возвращаемым функцией **SQLTables**; "N", если могут возвращаться таблицы, к которым пользователь не может получить доступ.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3,0)  
 Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных сред, которое может поддерживать драйвер. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3,0)  
 SQLUINTEGER битовая маска, поддерживающая агрегатные функции:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.  
  
 SQL_ALTER_DOMAIN (ODBC 3,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **ALTER Domain** , как определено в SQL-92, поддерживаемое источником данных. Драйвер SQL-92, совместимый с полным уровнем, всегда возвращает все битовые маски. Возвращаемое значение "0" означает, что инструкция **ALTER Domain** не поддерживается.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = Добавление ограничения домена поддерживается (полный уровень)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter Domain> \<set предложение default домена> поддерживается (полный уровень)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<предложение определения имени ограничения> поддерживается для ограничения домена именования (промежуточный уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<предложение удаления ограничения домена поддерживается> (полный уровень)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter Domain> \<предложение DROP домена по умолчанию> поддерживается (полный уровень)  
  
 Следующие биты задают поддерживаемые \<атрибуты ограничения> если \<поддерживается добавление ограничения домена> (установлен бит SQL_AD_ADD_DOMAIN_CONSTRAINT):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)  
  
 SQL_ALTER_TABLE (ODBC 2,0)  
 Битовая маска SQLUINTEGER, перечисление предложений в инструкции **ALTER TABLE** , поддерживаемой источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.  
  
 Для определения поддерживаемых предложений используются следующие битовые маски:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<предложение "добавить столбец>" поддерживается с помощью средства для указания параметров сортировки столбцов (полный уровень) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<предложение "добавить столбец>" поддерживается с помощью средства, определяющего значения по умолчанию для столбцов (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<поддерживается> добавления столбцов (уровень передачи FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_CONSTRAINT = \<предложение "добавить столбец>" поддерживается с помощью средства для указания ограничений столбца (уровень "TRANSITIONAL" FIPS) (ODBC 3,0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<поддерживается предложение добавления> ограничения таблицы (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<определение имени ограничения> поддерживается для именования столбцов и ограничений таблицы (промежуточный уровень) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<DROP COLUMN> Cascade поддерживается (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<alter Column> \<предложение DROP column по умолчанию> поддерживается (промежуточный уровень) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<DROP COLUMN> restrict поддерживается (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<DROP COLUMN> restrict поддерживается (уровень переходов FIPS) (ODBC 3,0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<alter Column> \<задать предложение default столбца> поддерживается (промежуточный уровень) (ODBC 3,0)  
  
 Следующие биты задают атрибуты ограничения \<поддержки> при условии, что ограничения столбца или таблицы поддерживаются (бит SQL_AT_ADD_CONSTRAINT установлен):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (полный уровень) (ODBC 3,0)  
  
 SQL_ASYNC_MODE (ODBC 3,0)  
 Значение SQLUINTEGER, указывающее уровень асинхронной поддержки в драйвере:  
  
 SQL_AM_CONNECTION = асинхронное выполнение на уровне соединения поддерживается. Все дескрипторы инструкций, связанные с данным дескриптором соединения, находятся в асинхронном режиме или работают в синхронном режиме. Маркер инструкции в соединении не может находиться в асинхронном режиме, в то время как другой обработчик на том же соединении работает в синхронном режиме и наоборот.  
  
 SQL_AM_STATEMENT = асинхронное выполнение уровня инструкции поддерживается. Некоторые дескрипторы инструкций, связанные с дескриптором соединения, могут находиться в асинхронном режиме, в то время как другие дескрипторы инструкций на одном соединении находятся в синхронном режиме.  
  
 SQL_AM_NONE = асинхронный режим не поддерживается.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3,0)  
 Битовая маска SQLUINTEGER, которая перечисляет поведение драйвера в отношении доступности количества строк. Вместе с типом данных используются следующие битовые маски:  
  
 SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE сведено в один. Если этот бит не установлен, для каждой инструкции доступны счетчики строк.  
  
 SQL_BRC_PROCEDURES = количество строк, если таковые имеются, доступны при выполнении пакета в хранимой процедуре. Если счетчики строк доступны, они могут быть сведены или доступны по отдельности в зависимости от SQL_BRC_ROLLED_UP бита.  
  
 SQL_BRC_EXPLICIT = количество строк, если таковые имеются, доступны при непосредственном выполнении пакета путем вызова **SQLExecute** или **SQLExecDirect**. Если счетчики строк доступны, они могут быть сведены или доступны по отдельности в зависимости от SQL_BRC_ROLLED_UP бита.  
  
## <a name="example"></a>Пример  
 **SQLGetInfo** возвращает списки поддерживаемых параметров в виде битовой маски SQLUINTEGER в **инфовалуептр*. Битовая маска для каждого параметра используется вместе с флагом, чтобы определить, поддерживается ли параметр.  
  
 Например, приложение может использовать следующий код, чтобы определить, поддерживается ли скалярная функция подстроки драйвером, связанным с соединением.  
  
 Еще один пример использования **SQLGetInfo**см. в разделе [Функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md).  
  
```cpp  
SQLUINTEGER fFuncs;  
  
SQLGetInfo(hdbc,   
           SQL_STRING_FUNCTIONS,  
           (SQLPOINTER)&fFuncs,  
           sizeof(fFuncs),  
           NULL);  
  
// SUBSTRING supported  
if (fFuncs & SQL_FN_STR_SUBSTRING)   
   ;   // do something  
  
// SUBSTRING not supported  
else  
   ;   // do something else  
```  
  
## <a name="related-functions"></a>Связанные функции  
 Возврат значения атрибута соединения  
 [Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Определение того, поддерживает ли драйвер функцию  
 [Функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Возврат значения атрибута инструкции  
 [Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Возврат сведений о типах данных источника данных  
 [Функция SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
