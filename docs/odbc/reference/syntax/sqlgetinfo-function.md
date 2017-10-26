---
title: "SQLGetInfo, функция | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 48
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 57ba22ee8645f1d3548be91adc9aafb4fc016c79
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetinfo-function"></a>SQLGetInfo, функция
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetInfo** возвращает общие сведения об источнике драйвера и данные, связанные с подключением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConnectionHandle*  
 [Вход] Дескриптор соединения.  
  
 *Свойство*  
 [Вход] Тип данных.  
  
 *InfoValuePtr*  
 [Выход] Указатель на буфер, в котором для возвращения сведений. В зависимости от *свойство* запрошено, данные, возвращаемые будет иметь одно из следующих: строку символом null, значение SQLUSMALLINT, SQLUINTEGER битовую маску, с флагом SQLUINTEGER, двоичное значение SQLUINTEGER, или Значение SQLULEN.  
  
 Если *свойство* аргумент является SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT, *InfoValuePtr* как входной и выходной аргумент. (Дескрипторы SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT позже в этом описании функции для получения дополнительной информации см.)  
  
 Если *InfoValuePtr* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее количество байтов (за исключением знака конечное значение null для символьных данных) для возврата в буфере, на который указывает *InfoValuePtr*.  
  
 *BufferLength*  
 [Вход] Длина \* *InfoValuePtr* буфера. Если значение в * \*InfoValuePtr* не является символьной строкой или если *InfoValuePtr* является пустым указателем, *BufferLength* аргумент учитывается. Драйвер предполагает, что размер * \*InfoValuePtr* SQLUSMALLINT или SQLUINTEGER, на основе *свойство*. Если * \*InfoValuePtr* строка в Юникоде (при вызове **SQLGetInfoW**), *BufferLength* аргумент должен быть четным числом; Если нет, SQLSTATE HY090 () Недопустимая длина строки или буфера), возвращается.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в который возвращается общее количество байтов (за исключением знака конечное значение null для символьных данных) для возврата в **InfoValuePtr*.  
  
 Для символьных данных, если количество байтов, доступных для возврата больше или равно *BufferLength*, сведения в \* *InfoValuePtr* усекается до * BufferLength* байт за вычетом длины конечное значение null символов и завершается нулевым байтом драйвером.  
  
 Для всех других типов данных, значение *BufferLength* игнорируется и драйвер предполагает размер \* *InfoValuePtr* — SQLUSMALLINT или SQLUINTEGER, в зависимости от * Свойство*.  
  
## <a name="return-value"></a>Возвращаемое значение  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetInfo** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_DBC и *обработки* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetInfo** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Буфер \* *InfoValuePtr* не был достаточно велик, чтобы вернуть все запрашиваемые данные. Таким образом данные были усечены. Длина запрошенной информации в виде неусеченный возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08003|Соединение не открыто|Тип данных (интеллектуальный анализ данных), запрашиваемый в *свойство* требуется открытое соединение. Типы сведений, зарезервированной с помощью ODBC могут возвращаться только SQL_ODBC_VER без открытого подключения.|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в * \*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY024|Недопустимое значение атрибута|(DM) *свойство* аргумент был SQL_DRIVER_HSTMT, и значение, на который указывает *InfoValuePtr* не была допустимой инструкцией дескриптор.<br /><br /> (DM) *свойство* аргумент был SQL_DRIVER_HDESC, и значение, на который указывает *InfoValuePtr* не был допустимым дескриптора.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное в аргументе *BufferLength* был меньше 0.<br /><br /> (DM) значение, указанное для *BufferLength* было нечетным числом, и * \*InfoValuePtr* имеет тип данных Юникода.|  
|HY096|Тип данных за пределами допустимого диапазона|Значение, указанное для аргумента *свойство* не подходит для версии поддерживаются драйвером ODBC.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательное поле не реализован|Значение, указанное для аргумента *свойство* был специфические для драйвера значение, которое не поддерживается драйвером.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|(DM), соответствующий драйвер *ConnectionHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Типы в настоящее время определены сведения приведены в «Сведения типы» далее в этом разделе; Ожидается более будут определены для использования различных источников данных. Широкий набор типов данных, зарезервированные для ODBC. Разработчики необходимо зарезервировать значения для собственных нужд конкретного драйвера из Open Group. **SQLGetInfo** преобразование Юникода не выполняется или *преобразование* (см. [коды ошибок ODBC приложение A:](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) из *справочнике программиста ODBC*) для определяемые драйвером *InfoTypes*. Дополнительные сведения см. в разделе [типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Формат сведений, возвращаемых в \* *InfoValuePtr* зависит от *свойство* запрошено. **SQLGetInfo** вернет информацию в одном из пяти различных форматов:  
  
-   Строка символов с завершающим нулем  
  
-   Значение типа SQLUSMALLINT  
  
-   Битовая маска SQLUINTEGER  
  
-   Значение типа SQLUINTEGER  
  
-   Двоичное значение SQLUINTEGER  
  
 Формат каждого из следующих типов информации, указывается в описание типа. Приложение должно привести значение, возвращаемое в **InfoValuePtr* соответствующим образом. Пример как приложение удалось извлечь данные из битовой маски SQLUINTEGER в разделе «Пример кода».  
  
 Драйвер должен возвращать значение для каждого типа данных, который определен в следующих таблицах. Если типа данных, не относится к драйверу или источнику данных, драйвер возвращает одно из значений, перечисленных в следующей таблице.  
  
 Строка символов («Y» или «N»)  
 "N"  
  
 Строка символов (не «Y» или «N»)  
 Пустая строка.  
  
 SQLUSMALLINT  
 0  
  
 Битовая маска SQLUINTEGER или двоичное значение SQLUINTEGER  
 0L  
  
 Например, если источник данных не поддерживает процедуры **SQLGetInfo** возвращает значения, перечисленные в следующей таблице для значений *свойство* , относящихся к процедуры.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Пустая строка.  
  
 **SQLGetInfo** возвращает SQLSTATE HY096 (недопустимое значение аргумента) для значений *свойство* , находятся в диапазоне типы информации, зарезервированная для использования в ODBC, но не определены в версии поддерживаются драйвером ODBC. Чтобы определить, какая версия ODBC драйвера соответствует требованиям, приложение вызывает **SQLGetInfo** с типом SQL_DRIVER_ODBC_VER сведения. **SQLGetInfo** возвращает SQLSTATE HYC00 (дополнительная возможность не реализована) для значений *свойство* , находятся в диапазоне, зарезервированная для использования драйвера типы информации, но не поддерживается драйвером.  
  
 Все вызовы **SQLGetInfo** требуется открытое соединение, за исключением случаев *свойство* — SQL_ODBC_VER, который возвращает версии диспетчера драйверов.  
  
## <a name="information-types"></a>Типы данных  
 В этом разделе перечислены сведения типы, поддерживаемые **SQLGetInfo**. Сведения о типах категорически группируются и в алфавитном порядке. Типы данных, которые были добавлены или переименования для ODBC 3*.x* также перечислены.  
  
## <a name="driver-information"></a>Сведения о драйвере  
 Следующие значения для *свойство* аргумент возвращать сведения о драйвере ODBC, например, число активных инструкций, имя источника данных и уровня соответствия стандартам интерфейса:  
  
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
>  При реализации **SQLGetInfo**, драйвер может повысить производительность, сводя к минимуму количество попыток отправки или от сервера требуются сведения.  
  
## <a name="dbms-product-information"></a>Сведения о продукте СУБД  
 Следующие значения для *свойство* аргумент возвращать сведения о продукте СУБД, такие как имя СУБД и номер версии:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Сведения об источнике данных  
 Следующие значения для *свойство* аргумент возвращает сведения из источника данных, например характеристики курсора и возможности транзакций:  
  
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
 Следующие значения для *свойство* аргумент возвращать сведения об инструкциях SQL, который поддерживается источником данных. Синтаксис SQL каждого компонента, описываемого эти типы информации является синтаксис SQL-92. Эти типы информации досконально не описывают все грамматику SQL-92. Вместо этого они описывают те части грамматики для данных, которые обычно обеспечивают разные уровни поддержки источников. В частности рассматриваются большинство инструкций DDL в SQL-92.  
  
 Приложения следует определить общий уровень поддерживаемой грамматики из типа данных SQL_SQL_CONFORMANCE и использовать другие типы информации для определения отклонения от уровень соответствия определенным стандартам.  
  
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
 Следующие значения для *свойство* аргумент возвращать сведения об ограничениях, применяется для идентификаторов и предложений в инструкции SQL, например максимальной длины идентификаторов и максимальное число столбцов в списке выбора. Драйвер или источника данных могут быть наложены ограничения.  
  
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
  
## <a name="scalar-function-information"></a>Сведения о скалярных функциях  
 Следующие значения для *свойство* аргумент возвращать сведения о скалярных функций, поддерживаемых источником данных и драйвера. Дополнительные сведения о скалярных функциях см. в разделе [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Сведения о преобразовании  
 Следующие значения для *свойство* аргумент возвращать список типов данных SQL, к которым источника данных можно преобразовать в указанный тип данных SQL с **преобразовать** скалярной функции:  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Добавлены сведения о типах для ODBC 3.x  
 Следующие значения для *свойство* аргумент были добавлены для ODBC 3*.x*:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Типы информации, переименованы для ODBC 3.x  
 Следующие значения для *свойство* аргумент были переименованы для ODBC 3*.x*.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Типы информации, рекомендуется использовать в ODBC 3.x  
 Следующие значения для *свойство* аргумент являются устаревшими в ODBC 3*.x*. ODBC 3*.x* драйверы должны по-прежнему поддерживает эти типы сведений для обратной совместимости с ODBC 2*.x* приложений. (Дополнительные сведения об этих типах см. в разделе [SQLGetInfo поддержки](../../../odbc/reference/appendixes/sqlgetinfo-support.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Описания типов сведений  
 В следующей таблице перечислены в алфавитном порядке каждого типа данных, версию ODBC, в которой он был представлен и его описание.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Строка символов: «Y», если пользователь может выполнять все процедуры, возвращенных **SQLProcedures**; «N», если может быть процедуры вернул, что пользователь не может выполняться.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Строка символов: «Y», если пользователь гарантируется **ВЫБЕРИТЕ** прав доступа для всех таблиц, возвращаемых функцией **SQLTables**; «N», если может быть таблиц возвращаются, пользователь не имеет доступа.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 SQLUSMALLINT значение, которое указывает максимальное число активных сред, которые поддерживает драйвер. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление поддержка статистических функций:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **ALTER домена** инструкции, как определено в SQL-92, поддерживаемые источником данных. Полный SQL-92 совместимого уровня драйвер всегда будет возвращать все битовые маски. Возвращаемое значение «0» означает, что **ALTER домена** инструкция не поддерживается.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ограничение домена поддерживается добавление (уровень Full)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter домена > \<предложения set в домене по умолчанию > поддерживается (уровень Full)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<предложение определение ограничения имя > поддерживается для именования домена ограничение (промежуточный уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<предложения ограничения для удаления домена > поддерживается (уровень Full)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter домена > \<предложения по умолчанию для удаления домена > поддерживается (уровень Full)  
  
 Укажите поддерживаемые следующих битов \<атрибутов ограничения > Если \<добавить ограничение домена > поддерживается (SQL_AD_ADD_DOMAIN_CONSTRAINT биту присваивается значение):  
  
 SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (уровень Full) SQL_AD_ADD_CONSTRAINT_DEFERRABLE (уровень Full) (уровень Full)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **ALTER TABLE** инструкции, поддерживаемые источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<добавить столбец > предложение поддерживается с помощью средства можно задать параметры сортировки столбца (уровень Full) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<добавить столбец > предложение поддерживается с механизмом для указания столбца значения по умолчанию (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<добавить столбец > является поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<добавить столбец > предложение поддерживается с механизмом для указания столбца ограничений (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<добавить ограничение таблицы > предложение поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > поддерживается для именования ограничения столбцов и таблиц (промежуточный уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<удалением столбца > поддерживается CASCADE (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<изменить столбец > \<предложения по умолчанию для удаления столбца > является поддерживается (промежуточный уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<удалением столбца > ограничение поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<удалением столбца > ограничение поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<изменить столбец > \<предложении default для столбца набора > является поддерживается (промежуточный уровень) (ODBC 3.0)  
  
 Поддержка укажите следующие биты \<атрибутов ограничения > Если поддерживается Указание ограничения столбцов и таблиц (SQL_AT_ADD_CONSTRAINT биту присваивается значение):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (уровень Full) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 SQLUINTEGER значение, указывающее, если драйвер может выполнить функции асинхронно на дескриптор соединения.  
  
 SQL_ASYNC_DBC_CAPABLE = драйвер асинхронного выполнения функции соединения.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = драйверу не удалось выполнить подключение функции асинхронно.  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 SQLUINTEGER значение, указывающее уровень поддержки асинхронных операций в драйвере.  
  
 SQL_AM_CONNECTION = соединение поддерживается уровня асинхронное выполнение. Все дескрипторы инструкции, связанные с дескриптором данного соединения, в асинхронном режиме, либо все находятся в синхронном режиме. Дескриптор инструкции для подключения не может быть в асинхронном режиме, пока другой дескриптора инструкции, в том же соединении в синхронном режиме и наоборот.  
  
 SQL_AM_STATEMENT = поддерживается уровня асинхронное выполнение инструкции. Некоторые дескрипторов инструкций, связанной с дескриптором соединения могут быть в асинхронном режиме, если другие дескрипторы инструкций в том же соединении, в синхронном режиме.  
  
 SQL_AM_NONE = асинхронный режим не поддерживается.  
  
 SQL_ASYNC_NOTIFICATION  
 SQLUINTEGER значение, указывающее, поддерживает ли драйвер асинхронного уведомления:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** асинхронное выполнение уведомления, поддерживаемых драйвером.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** асинхронное выполнение уведомления не поддерживается драйвером.  
  
 Существует две категории ODBC асинхронных операций: уровня асинхронных операций соединения и инструкции уровень асинхронных операций.  Если драйвер возвращает SQL_ASYNC_NOTIFICATION_CAPABLE, он должен поддерживать уведомления для всех интерфейсов API, которые могут выполняться асинхронно.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Подсчитывает SQLUINTEGER битовую маску, которая перечисляет варианты поведения драйвера по отношению к доступности строки. Следующие битовые маски используются вместе с типов данных:  
  
 SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE, суммируются в одно. Если этот бит не задано, счетчики строк будут доступны для каждой инструкции.  
  
 SQL_BRC_PROCEDURES = количество строк, если таковые имеются, доступны при выполнении пакета в хранимой процедуре. Если количество строк, их можно откатить вверх или по отдельности доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
 SQL_BRC_EXPLICIT = количество строк, если, они доступны при выполнении пакета непосредственно, путем вызова **SQLExecute** или **SQLExecDirect**. Если количество строк, их можно откатить вверх или по отдельности доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление драйверов для пакетов. Следующие битовые маски используются для определения, какой уровень поддерживается:  
  
 SQL_BS_SELECT_EXPLICIT = драйвер поддерживает явные пакетов, которые могут результирующего набора инструкции создания.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = драйвер поддерживает явные пакетов, которые может иметь создания инструкций количество строк.  
  
 SQL_BS_SELECT_PROC = драйвер поддерживает явные процедуры, которые могут результирующего набора инструкции создания.  
  
 SQL_BS_ROW_COUNT_PROC = драйвер поддерживает явные процедур можно создания инструкций количество строк.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление операций, выполнении которых закладки сохраняются.  
  
 Для определения, через который закладки параметры сохраняются вместе с флагом используются следующие битовые маски:  
  
 SQL_BP_CLOSE = закладки являются действительными после приложение вызывает **SQLFreeStmt** с параметром SQL_CLOSE или **SQLCloseCursor** для закрытия курсора, связанные с инструкцией.  
  
 SQL_BP_DELETE = закладка для строки, является допустимым после удаления этой строки.  
  
 SQL_BP_DROP = закладки являются действительными после приложение вызывает **SQLFreeHandle** с *HandleType* значение sql_handle_stmt, чтобы удалить оператор.  
  
 SQL_BP_TRANSACTION = закладки являются действительными после приложение фиксирует или откатывает транзакцию.  
  
 SQL_BP_UPDATE = закладка для строки, является допустимым после любой столбец в этой строке обновления, включая ключевые столбцы.  
  
 SQL_BP_OTHER_HSTMT = закладки, связанные с одной инструкцией с другого оператора. Если не указан SQL_BP_CLOSE или SQL_BP_DROP, указатель на первый оператор должен быть открыт.  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает позицию каталога в полном имени таблицы:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Например драйвер Xbase возвращает SQL_CL_START, так как имя каталога (каталог) находится в начале имени таблицы, как и \EMPDATA\EMP. DBF. Сервер ORACLE драйвер возвращает SQL_CL_END, так как каталог находится в конце имени таблицы, как и в ADMIN.EMP@EMPDATA.  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать SQL_CL_START. Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME (ODBC 3.0)  
 Строка символов: «Y», если сервер поддерживает имена каталогов или «N», если это не так.  
  
 Драйвер с SQL-92 полный уровень совместимую всегда возвращает «Y».  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 Строка символов: символ или символы, которые в источнике данных определяется в качестве разделителя между именем каталога и полное имя элемента, следующего за и предшествующий.  
  
 Пустая строка возвращается в том случае, если каталоги не поддерживаются источником данных. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения. Драйвер с SQL-92 полный уровень совместимую всегда возвращает «.».  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для каталога; Например «database» или «directory». Эта строка может быть в верхней, нижней или смешанный регистр.  
  
 Пустая строка возвращается в том случае, если каталоги не поддерживаются источником данных. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения. Драйвер с SQL-92 полный уровень совместимую всегда возвращает «каталог».  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление инструкций, в которых используется каталоги.  
  
 Следующие битовые маски используются для определения, где может использоваться каталоги:  
  
 SQL_CU_DML_STATEMENTS = каталоги, поддерживаются во всех инструкциях языка обработки данных: **ВЫБЕРИТЕ**, **вставить**, **обновление**, **DELETE**и если поддерживается, **ВЫБЕРИТЕ для обновления** и располагается update и delete.  
  
 SQL_CU_PROCEDURE_INVOCATION = каталоги поддерживаются в операторе вызова процедуры ODBC.  
  
 SQL_CU_TABLE_DEFINITION = каталоги, поддерживаются во всех инструкциях определения таблицы: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE **, и **DROP VIEW**.  
  
 SQL_CU_INDEX_DEFINITION = каталоги, поддерживаются во всех инструкциях определение индекса: **CREATE INDEX** и **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = каталоги, поддерживаются во всех инструкциях определения прав доступа: **GRANT** и **ОТОЗВАТЬ**.  
  
 Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения. Драйвер с SQL-92 полный уровень совместимую всегда возвращает битовую маску со всеми набора битов.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 Имя параметров сортировки. Это символьная строка, которая указывает имя параметров сортировки по умолчанию для кодировку по умолчанию для этого сервера (например, "ISO 8859-1" и EBCDIC). Если неизвестно, возвращается пустая строка. Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать непустой строкой.  
  
 SQL_COLUMN_ALIAS (ODBC 2.0)  
 Строка символов: «Y», если источник данных поддерживает псевдонимы столбцов; в противном случае — «N».  
  
 Псевдоним является альтернативным именем, которое можно указать с помощью предложения As для столбца в списке выбора. С драйвером SQL-92 начального уровня совместимую всегда возвращает «Y».  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает, как источник данных обрабатывает сцепление NULL значением символьных столбцов типа данных со столбцами типа данных символа табличное значение отличное от NULL:  
  
 SQL_CB_NULL = результатом будет значение NULL.  
  
 SQL_CB_NON_NULL = результатом является объединением НЕНУЛЕВОЙ столбец или столбцы.  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_ DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Битовая маска SQLUINTEGER. Указывает битовую маску, преобразования, поддерживаемые источником данных с **преобразовать** скалярной функции для данных типа с именем в *свойство*. Если битовая маска равна нулю, источник данных не поддерживает преобразования из данных именованного типа, включая преобразование в тот же тип данных.  
  
 Например, чтобы определить, поддерживает ли источник данных, преобразование в тип данных SQL_BIGINT SQL_INTEGER данных, приложение вызывает **SQLGetInfo** с *свойство* из SQL_CONVERT_INTEGER. Приложение выполняет **AND** операцию с SQL_CVT_BIGINT и возвращаемый битовой маски. Если результирующее значение ненулевое, поддерживается преобразование.  
  
 Следующие битовые маски используются для определения, какие преобразования поддерживаются:  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) (ODBC 1.0) SQL_CVT_BIT SQL_CVT_GUID (ODBC 3.5) (ODBC 1.0) SQL_CVT_CHAR SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL SQL_CVT_ SQL_CVT_TIME (ODBC 1.0) (ODBC 1.0) SQL_CVT_SMALLINT _CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME SQL_CVT_LONGVARBINARY (ODBC 1.0) (ODBC 1.0) SQL_CVT_LONGVARCHAR SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) ОТМЕТКА ВРЕМЕНИ (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) (ODBC 1.0) SQL_CVT_VARBINARY SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1.0)  
 Битовая маска SQLUINTEGER, перечисление функции скалярные преобразования, поддерживаемые драйвера и связанного источника данных.  
  
 Следующие битовой маски используется для определения функции преобразования, которые поддерживаются:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает, поддерживаются ли корреляционные имена таблиц:  
  
 SQL_CN_NONE = корреляции имена не поддерживаются.  
  
 SQL_CN_DIFFERENT = корреляции имена поддерживаются, но должно отличаться от имен таблиц, они представляют.  
  
 SQL_CN_ANY = корреляции имена поддерживаются и может быть любое допустимое имя определяемой пользователем.  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **создать УТВЕРЖДЕНИЕ** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Следующие биты указать атрибут ограничения, если поддерживается возможность явно указывать атрибутов ограничения (см. типы информации SQL_ALTER_TABLE и SQL_CREATE_TABLE):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать все эти возможности как поддерживается. Возвращаемое значение «0» означает, что **создать УТВЕРЖДЕНИЕ** инструкция не поддерживается.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **создать НАБОР символов** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать все эти возможности как поддерживается. Возвращаемое значение «0» означает, что **создать НАБОР символов** инструкция не поддерживается.  
  
 SQL_CREATE_COLLATION (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **создать параметры СОРТИРОВКИ** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовой маски используется для определения, какие предложения поддерживаются:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать этот параметр поддерживается. Возвращаемое значение «0» означает, что **создать параметры СОРТИРОВКИ** инструкция не поддерживается.  
  
 SQL_CREATE_DOMAIN (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **создание домена** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CDO_CREATE_DOMAIN = создание домена инструкция поддерживается (промежуточного уровня).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > поддерживается для именования домена ограничения (промежуточный уровень).  
  
 Следующие биты указать возможность создания столбца ограничений: SQL_CDO_DEFAULT = поддерживается Указание ограничений доменов (промежуточного уровня) SQL_CDO_CONSTRAINT = поддерживается Указание значения по умолчанию домена (промежуточного уровня) SQL_CDO_COLLATION = Поддерживается Указание параметров сортировки домена (уровень Full)  
  
 Следующие биты указать атрибуты ограничения, если поддерживается Указание ограничений доменов (SQL_CDO_DEFAULT имеет значение):  
  
 SQL_CDO_CONSTRAINT_NON_DEFERRABLE SQL_CDO_CONSTRAINT_DEFERRABLE (уровень Full) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (уровень Full) SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (уровень Full)  
  
 Возвращаемое значение «0» означает, что **создание домена** инструкция не поддерживается.  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **CREATE SCHEMA** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 SQL-92 промежуточного уровня — совместимые драйвера всегда будет возвращать параметры SQL_CS_CREATE_SCHEMA и SQL_CS_AUTHORIZATION как поддерживается. Они также должны поддерживаться, на SQL-92 начального уровня, но не обязательно инструкций SQL. Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **CREATE TABLE** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CT_CREATE_TABLE = CREATE TABLE инструкция поддерживается. (Начальный уровень)  
  
 SQL_CT_TABLE_CONSTRAINT = поддерживается Указание ограничений таблицы (FIPS переходные уровень)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > предложение поддерживается для именования ограничения столбцов и таблиц (промежуточный уровень)  
  
 Следующие биты указать возможность создания временных таблиц:  
  
 SQL_CT_COMMIT_PRESERVE = удаленные строки сохраняются при фиксации. (Уровень full) SQL_CT_COMMIT_DELETE = удаленные строки удаляются при фиксации. (Уровень full) SQL_CT_GLOBAL_TEMPORARY = глобальные временные таблицы можно создать. (Уровень full) SQL_CT_LOCAL_TEMPORARY = локальных временных таблиц могут создаваться. (Уровень full)  
  
 Следующие биты указать возможность создания ограничения столбца:  
  
 SQL_CT_COLUMN_CONSTRAINT = поддерживается Указание ограничения столбца (FIPS переходные уровень) SQL_CT_COLUMN_DEFAULT = поддерживается указание значений столбца по умолчанию (FIPS переходные уровень) SQL_CT_COLUMN_COLLATION = Указание параметров сортировки столбца поддерживается (уровень Full)  
  
 Следующие биты задавать атрибуты ограничения, если поддерживается Указание ограничения столбцов и таблиц:  
  
 SQL_CT_CONSTRAINT_NON_DEFERRABLE SQL_CT_CONSTRAINT_DEFERRABLE (уровень Full) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (уровень Full) SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (уровень Full)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **создать перевод** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовой маски используется для определения, какие предложения поддерживаются:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать эти параметры, как поддерживается. Возвращаемое значение «0» означает, что **создать перевод** инструкция не поддерживается.  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **CREATE VIEW** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Возвращаемое значение «0» означает, что **CREATE VIEW** инструкция не поддерживается.  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать параметры SQL_CV_CREATE_VIEW и SQL_CV_CHECK_OPTION как поддерживается.  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 SQLUSMALLINT значение, указывающее, каким образом **ФИКСАЦИИ** операция затрагивает курсоров и подготовленных инструкций в источнике данных (поведение источника данных при фиксации транзакции).  
  
 Значение этого атрибута будет отражать текущее состояние следующий параметр: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = закрытия курсоров и удаление подготовленных инструкций. Еще раз, чтобы использовать курсор приложение должно reprepare и был повторно исполнить инструкцию.  
  
 SQL_CB_CLOSE = закрытия курсоров. Для подготовленных инструкций, приложение может вызвать **SQLExecute** в операторе без вызова **SQLPrepare** еще раз. Значение по умолчанию для драйвера SQL ODBC — SQL_CB_CLOSE. Это означает, что драйвер SQL ODBC закроет вашей курсоры при фиксации транзакции.  
  
 SQL_CB_PRESERVE = Preserve курсоры в той же позиции, как и раньше **ЗАФИКСИРОВАТЬ** операции. Приложение может перейти для получения данных, или его можно закрыть курсор и выполнить инструкцию повторно без подготовки его повторно.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 SQLUSMALLINT значение, указывающее, каким образом **ОТКАТА** операция затрагивает курсоров и подготовленных инструкций в источнике данных:  
  
 SQL_CB_DELETE = закрытия курсоров и удаление подготовленных инструкций. Еще раз, чтобы использовать курсор приложение должно reprepare и был повторно исполнить инструкцию.  
  
 SQL_CB_CLOSE = закрытия курсоров. Для подготовленных инструкций, приложение может вызвать **SQLExecute** в операторе без вызова **SQLPrepare** еще раз.  
  
 SQL_CB_PRESERVE = Preserve курсоры в той же позиции, как и раньше **ОТКАТА** операции. Приложение может перейти для получения данных, или можно закрыть курсор и был повторно исполнить инструкцию без repreparing его.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 SQLUINTEGER значение, которое указывает на поддержку чувствительности курсора:  
  
 SQL_INSENSITIVE = все курсоры на содержат дескриптор инструкции, результирующий набор без отражения любые изменения, внесенные в его с другим курсором в той же транзакции.  
  
 SQL_UNSPECIFIED = не указано ли курсоры для дескриптора инструкции отобразить изменения, внесенные в результирующий набор другого курсора в той же транзакции. Курсоры для дескриптора инструкции может сделать видимым ни один, несколько или все такие изменения.  
  
 SQL_SENSITIVE = курсоры вводятся с учетом изменений, сделанных другими курсорами в той же транзакции.  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать параметр SQL_UNSPECIFIED как поддерживается.  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать параметр SQL_INSENSITIVE, как поддерживается.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1.0)  
 Строка символов с именем источника данных, который был использован во время соединения. Если приложение вызвало **SQLConnect**, это значение *szDSN* аргумент. Если приложение вызвало **SQLDriverConnect** или **SQLBrowseConnect**, это значение ключевого слова DSN в строке подключения, переданный в драйвере. Если строка подключения не содержит **DSN** ключевое слово (например, если он содержит **ДРАЙВЕР** ключевого слова), это пустая строка.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1.0)  
 Строка символов. «Y», если источник данных установлен в режим только для чтения, «N» в случае в противном случае.  
  
 Эта характеристика относится только к источнику данных Это не характеристикой драйвер, который обеспечивает доступ к источнику данных. Можно использовать драйвер, который доступен для чтения и записи с источником данных, доступной только для чтения. Если драйвер доступен только для чтения, все его источники данных должны быть доступны только для чтения и должен возвращать SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME (ODBC 1.0)  
 Символ строка с именем текущей базы данных используется, если источник данных определяет именованный объект, называется «database».  
  
> [!NOTE]  
>  В ODBC 3*.x*, возвращаемое значение для данного *свойство* могут быть возвращены, вызвав **SQLGetConnectAttr** с *атрибута* Аргумент SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление литералами даты и времени SQL-92, поддерживаемые источником данных. Обратите внимание, что они являются литералами даты и времени, перечисленные в спецификации SQL-92 являются отдельными из datetime литерала escape предложений, определенном ODBC. Дополнительные сведения о предложениях литерала escape ODBC datetime см. в разделе [даты, времени и отметок времени литералы](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Переходные FIPS драйвер уровня совместимую всегда возвращает значение «1» в битовой маски для битов в следующем списке. Значение «0» означает, что SQL-92 литералами даты и времени не поддерживаются.  
  
 Следующие битовые маски используются для определения, какие литералы поддерживаются:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_ SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1.0)  
 Строка символов с именем продукта СУБД, который доступен с помощью драйвера.  
  
 SQL_DBMS_VER (ODBC 1.0)  
 Строка символов, указывающее, версия продукта СУБД, доступ к драйверу. Версия представляется в виде ##. ##. ###, где первые две цифры являются основной номер версии, следующие две цифры — дополнительный номер версии, а последние четыре цифры — номер редакции. Драйвер должен представлять версия продукта СУБД в этой форме, но можно также добавить версию конкретного продукта СУБД. Например «04.01.0000 Rdb 4.1».  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 SQLUINTEGER значение, которое указывает на поддержку создания и удаления индексов:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1.0)  
 Значение SQLUINTEGER, которое указывает, что уровень изоляции транзакций по умолчанию поддерживает драйвер или источник данных, или нуль, если источник данных не поддерживает транзакции. Для определения уровней изоляции транзакций используются следующие термины:  
  
 **"Грязный" чтение** 1 транзакция изменяет строку. Транзакция 2 считывает измененные строки до фиксации транзакции 1 изменение. Если 1 отката транзакции изменения транзакции 2 будет считывать строки, считаются никогда не существовавшими.  
  
 **Неповторяющееся чтение** 1 транзакция считывает строку. Транзакция 2 обновляет или удаляет этой строки и фиксирует эти изменения. Если транзакция 1 пытается считать заново строки, будут получать значения в отдельной строке или обнаружить, что строка была удалена.  
  
 **Создание фантома** 1 транзакция считывает набор строк, удовлетворяющих условию некоторые условия поиска. Транзакция 2 создает одну или несколько строк (с помощью операции вставки или обновления), соответствующие критериям поиска. Если транзакция 1 reexecutes инструкцию, которая считывает строки, он получает набор строк.  
  
 Если источник данных поддерживает транзакции, драйвер возвращает одно из следующих битовые маски.  
  
 SQL_TXN_READ_UNCOMMITTED = Dirty возможны операции чтения, неповторяющееся чтение и фантомов.  
  
 SQL_TXN_READ_COMMITTED = Dirty чтения невозможны. Неповторяющееся чтение и фантомов возможны.  
  
 SQL_TXN_REPEATABLE_READ = Dirty операции чтения и неповторяющееся чтение невозможны. Возможны фантомов.  
  
 SQL_TXN_SERIALIZABLE = транзакции являются сериализуемыми. Сериализуемые транзакции «грязные» чтения, неповторяющееся чтение или фантомов запрещены.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 Строка символов: «Y», если можно описать параметры; «N», если это не так.  
  
 Полный SQL-92 драйвер уровень совместимую обычно возвращает «Y», так как он будет поддерживать **входные данные, ОПИСЫВАЮЩИЕ** инструкции. Поскольку это не непосредственно базовой поддержки SQL, тем не менее, описывающие параметры, может не поддерживаться, даже в SQL-92 полный уровень — совместимый драйвер.  
  
 SQL_DM_VER (ODBC 3.0)  
 Строка символов с версией диспетчера драйверов. Версия представляется в виде ##. ##. ###. ###, где:  
  
 Первый набор из двух цифр — основная версия ODBC, предоставленные SQL_SPEC_MAJOR константой.  
  
 Второй набор из двух цифр — дополнительная версия ODBC, предоставленные SQL_SPEC_MINOR константой.  
  
 Третий набор из четырех цифр — диспетчер драйверов основной номер сборки.  
  
 Последний набор из четырех цифр — номер вспомогательной сборки диспетчера драйверов.  
  
 Версия диспетчера драйверов Windows 7, 03.80. Версия диспетчера драйверов Windows 8, 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 SQLUINTEGER значение, указывающее, если драйвер поддерживает организацию пулов с учетом драйвера. (Дополнительные сведения см. в разделе [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE указывает, что драйвер поддерживает учетом драйвера механизм регулирования количества запросов.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE указывает, что драйвер не поддерживает учетом драйвера механизм регулирования количества запросов.  
  
 Драйвер не требуется реализовывать SQL_DRIVER_AWARE_POOLING_SUPPORTED и диспетчер драйверов не будут учитывать к возвращаемому значению драйвера.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 SQLULEN значение, драйвер дескриптора среды или дескриптор соединения, определяется аргументом *свойство*.  
  
 Эти типы информации, реализуются диспетчером драйверов сама по себе.  
  
 SQL_DRIVER_HDESC (ODBC 3.0)  
 Значение SQLULEN драйвера дескриптора определить с помощью диспетчера драйверов дескриптора, который должен быть передан на входе в \* *InfoValuePtr* из приложения. В этом случае *InfoValuePtr* является входным и выходным аргументом. Переданный входного дескриптора \* *InfoValuePtr* необходимо явно или неявно занятых на *ConnectionHandle*.  
  
 Приложение должно создать копию дескриптора диспетчера драйверов обработать перед вызовом **SQLGetInfo** с этот тип данных, чтобы убедиться в том, дескриптор не перезаписывается при выводе.  
  
 Этот тип реализован диспетчером драйверов сама по себе.  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 Значение SQLULEN *hinst* из библиотеки нагрузки возвращены диспетчеру драйверов при его загрузке библиотека DLL драйвера на операционную систему Microsoft Windows, или его эквивалент в другой операционной системе. Дескриптор допустим только для дескриптора соединения, указанный в вызове **SQLGetInfo**.  
  
 Этот тип реализован диспетчером драйверов сама по себе.  
  
 SQL_DRIVER_HSTMT (ODBC 1.0)  
 Значение SQLULEN драйвера дескриптора инструкции, определяется дескриптора инструкции диспетчера драйверов, который должен быть передан на входе в \* *InfoValuePtr* из приложения. В этом случае *InfoValuePtr* входной и выходной аргумент. Входящая инструкция дескриптор, переданный в \* *InfoValuePtr* следует выделить в аргументе *ConnectionHandle*.  
  
 Приложение должно создать копию инструкции диспетчера драйверов обработать перед вызовом **SQLGetInfo** с этот тип данных, чтобы убедиться, что дескриптор не перезаписано на выходе.  
  
 Этот тип реализован диспетчером драйверов сама по себе.  
  
 SQL_DRIVER_NAME (ODBC 1.0)  
 Строка символов с именем файла драйвера, используемого для доступа к источнику данных.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2.0)  
 Строка символов с помощью версии ODBC, который поддерживает драйвер. Версия представляется в виде ##. ##, где первые две цифры являются основной номер версии, а две следующие — дополнительный номер версии. SQL_SPEC_MAJOR и SQL_SPEC_MINOR определяют основной и дополнительный номера версии. Для версии ODBC, описанные в данном руководстве это 3 и 0, а драйвер должен возвращать «03.00».  
  
 Диспетчер драйверов ODBC не изменит значение, возвращаемое SQLGetInfo(SQL_DRIVER_ODBC_VER), чтобы обеспечить обратную совместимость для существующих приложений. Драйвер определяет, какой будет возвращено. Тем не менее, драйвер, который поддерживает возможность расширения типа данных C должен возвращать 3.8 (или более поздней версии) Если приложение вызывает **SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION присваивается 3.8. Дополнительные сведения см. в разделе [типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 Строка символов с версии драйвера и при необходимости Описание драйвера. Как минимум, версии представляется в виде ##. ##. ###, где первые две цифры являются основной номер версии, следующие две цифры — дополнительный номер версии, а последние четыре цифры — номер редакции.  
  
 SQL_DROP_ASSERTION (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **удалить УТВЕРЖДЕНИЕ** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовой маски используется для определения, какие предложения поддерживаются:  
  
 SQL_DA_DROP_ASSERTION  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **DROP КОДИРОВКИ** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовой маски используется для определения, какие предложения поддерживаются:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_COLLATION (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **удалить параметры СОРТИРОВКИ** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовой маски используется для определения, какие предложения поддерживаются:  
  
 SQL_DC_DROP_COLLATION  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_DOMAIN (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **удалить домен** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 SQL-92 промежуточного уровня — совместимые драйвера всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **DROP SCHEMA** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 SQL-92 промежуточного уровня — совместимые драйвера всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_DROP_TABLE (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **DROP TABLE** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Драйвер с FIPS промежуточном уровне совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_DROP_TRANSLATION (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **DROP ПЕРЕВОДА** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовой маски используется для определения, какие предложения поддерживаются:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_VIEW (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **DROP VIEW** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Драйвер с FIPS промежуточном уровне совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты динамического курсора, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножества атрибутов; второй подмножество SQL_DYNAMIC_CURSOR_ATTRIBUTES2 см.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXT = A *FetchOrientation* аргумент для SQL_FETCH_NEXT поддерживается в вызове **SQLFetchScroll** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* аргументы SQL_FETCH_FIRST, SQL_FETCH_LAST и SQL_FETCH_ABSOLUTE поддерживаются при вызове **SQLFetchScroll** когда курсор наведен курсор dynamic. (Набор строк, будут выбираться не зависит от текущей позиции курсора.)  
  
 SQL_CA1_RELATIVE = *FetchOrientation* аргументы SQL_FETCH_PRIOR и SQL_FETCH_RELATIVE поддерживаются при вызове **SQLFetchScroll** когда курсор наведен курсор dynamic. (Набор строк, который извлекается зависит от текущей позиции курсора. Обратите внимание, что это отделяется от SQL_FETCH_NEXT, так как в однонаправленного курсора, поддерживается только SQL_FETCH_NEXT.)  
  
 SQL_CA1_BOOKMARK = A *FetchOrientation* аргумент SQL_FETCH_BOOKMARK поддерживается в вызове **SQLFetchScroll** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_LOCK_EXCLUSIVE = A *LockType* аргумент SQL_LOCK_EXCLUSIVE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_LOCK_NO_CHANGE = A *LockType* аргумент SQL_LOCK_NO_CHANGE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_LOCK_UNLOCK = A *LockType* аргумент SQL_LOCK_UNLOCK поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_POSITION = *операции* аргумент SQL_POSITION поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_UPDATE = *операции* аргумент SQL_UPDATE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_DELETE = *операции* аргумент SQL_DELETE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_REFRESH = *операции* аргумент SQL_REFRESH поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POSITIONED_UPDATE = обновление ГДЕ ТЕКУЩЕГО SQL инструкция поддерживается, если курсор находится динамический курсор. (Драйвер SQL-92 начального уровня совместимую всегда будет возвращать этот параметр поддерживается.)  
  
 SQL_CA1_POSITIONED_DELETE = удаление ГДЕ ТЕКУЩЕГО SQL инструкция поддерживается, если курсор находится динамический курсор. (Драйвер SQL-92 начального уровня совместимую всегда будет возвращать этот параметр поддерживается.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = SELECT для инструкции UPDATE SQL поддерживается, если курсор динамический курсор. (Драйвер SQL-92 начального уровня совместимую всегда будет возвращать этот параметр поддерживается.)  
  
 SQL_CA1_BULK_ADD = *операции* аргумент SQL_ADD поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = *операции* аргумент SQL_UPDATE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = *операции* аргумент SQL_DELETE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = *операции* аргумент SQL_FETCH_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL-92 промежуточного уровня — совместимые драйвера обычно возвращают параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE как поддерживается, так как он поддерживает прокручиваемые курсоры посредством внедренные инструкции SQL FETCH. Так как это не определить непосредственно базовой поддержки SQL, однако Прокручиваемые курсоры может не поддерживаться, даже для SQL-92 промежуточного уровня — совместимого драйвера.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты динамического курсора, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножества атрибутов; Первый набор в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = только для чтения динамический курсор, в которой обновления не разрешены, поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_READ_ONLY для динамического курсора).  
  
 SQL_CA2_LOCK_CONCURRENCY = динамический курсор, который использует самый низкий уровень блокировки достаточно, чтобы убедиться, что строки могут быть обновлены поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_LOCK для динамического курсора.) Эти блокировки должны быть согласованы с уровнем изоляции транзакций с помощью атрибута соединения SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = динамический курсор, поддерживаются ли использует управления оптимистичным параллелизмом Сравнение версий строк. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_ROWVER для динамического курсора.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = динамический курсор, поддерживаются ли использует сравнение значений элементов управления оптимистичным параллелизмом. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_VALUES для динамического курсора.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = Added строк являются видимыми для динамического курсора; курсор можно прокрутить эти строки. (Где они добавляются до текущей позиции курсора зависит от драйвера.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = удалено строк больше не доступны для динамического курсора, а не оставляйте «дыры» в результирующем наборе; После динамический курсор прокручивается из удаленной строки, он не может возвращать для этой строки.  
  
 SQL_CA2_SENSITIVITY_UPDATES = обновления строк являются видимыми для динамического курсора; Если динамический курсор прокручивается и возвращает обновленную строку, данные, возвращенные курсором будут обновленные данные, а не исходные данные.  
  
 SQL_CA2_MAX_ROWS_SELECT = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **ВЫБЕРИТЕ** инструкций, когда курсор находится динамический курсор.  
  
 SQL_CA2_MAX_ROWS_INSERT = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **вставить** инструкций, когда курсор находится динамический курсор.  
  
 SQL_CA2_MAX_ROWS_DELETE = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **удалить** инструкций, когда курсор находится динамический курсор.  
  
 SQL_CA2_MAX_ROWS_UPDATE = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **обновление** инструкций, когда курсор находится динамический курсор.  
  
 SQL_CA2_MAX_ROWS_CATALOG = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **КАТАЛОГА** результирующих наборов, если курсор динамический курсор.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **ВЫБЕРИТЕ**, **вставить**, **удаление**, и **обновление** операторы, и **КАТАЛОГА** результирующих наборов, в том случае, если курсор динамический курсор.  
  
 SQL_CA2_CRC_EXACT = точное число строк доступно в поле диагностики SQL_DIAG_CURSOR_ROW_COUNT курсор динамический курсор.  
  
 SQL_CA2_CRC_APPROXIMATE = приблизительное число строк доступно в поле диагностики SQL_DIAG_CURSOR_ROW_COUNT курсор динамический курсор.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = драйвер не гарантируется, что имитируемые расположен обновления или инструкций delete повлияет только одну строку, если курсор динамический курсор; приложение несет этого гарантировать. (Если инструкция влияет на более чем одной строке **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операции с курсором].) Чтобы установить это приложение вызывает **SQLSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибут SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = драйвер пытается гарантировать, что имитацию позиционированного обновления или инструкций delete повлияют только одну строку при прохождении курсора динамический курсор. Драйвер всегда такие операторы выполняются, даже если они могут повлиять на более чем одной строке, например, если отсутствует уникальный ключ. (Если инструкция влияет на более чем одной строке **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операции с курсором].) Чтобы установить это приложение вызывает **SQLSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибут SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE = драйвер гарантирует, что имитируемые расположен обновления или инструкций delete повлияет только одну строку, если курсор динамический курсор. Если драйвер не может гарантировать это для заданной инструкции **SQLExecDirect** или **SQLPrepare** возвращают SQLSTATE 01001 (конфликт операции курсора). Чтобы установить это приложение вызывает **SQLSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибут SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает выражения в **ORDER BY** списка; «N», если это не так.  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает, как драйвер одноуровневых непосредственно обрабатывает файлы в источнике данных:  
  
 SQL_FILE_NOT_SUPPORTED = драйвер не является драйвером среднего уровня. Например драйвер ORACLE — это двухуровневая драйвер.  
  
 SQL_FILE_TABLE = файлов будет обрабатываться одноуровневых драйвер в источнике данных, как таблицы. Например драйвер Xbase считает каждый файл Xbase таблицы.  
  
 SQL_FILE_CATALOG = одноуровневых обрабатывает драйверы в источнике данных как каталог. Например драйвер Microsoft Access считает каждый файл Microsoft Access всей базы данных.  
  
 Приложения можно использовать для определения того, как пользователи будут выбирать данные. Например Xbase пользователи часто прибегают к данных, хранящихся в файлах, тогда как ORACLE и Microsoft Access пользователей обычно обработки данных, хранящихся в таблицах.  
  
 Когда пользователь выбирает источник данных Xbase, приложение может отобразить окна **Открытие файла** стандартным диалоговым окном, когда пользователь выбирает источник данных Microsoft Access или ORACLE, приложение может отображать пользовательский ** Выберите таблицу** диалоговое окно.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора однонаправленные, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножества атрибутов; второй подмножество SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 см.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_ UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описания эти битовые маски в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить «однонаправленный курсор» для «динамический курсор» в описании).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора однонаправленные, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножества атрибутов; Первый набор в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Описания эти битовые маски в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и заменить «однонаправленный курсор» для «динамический курсор» в описании).  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2.0)  
 Битовая маска SQLUINTEGER перечисление расширения для **SQLGetData**.  
  
 Для определения общих расширений, драйвер поддерживает следующие битовые маски используются вместе с флагом **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** может вызываться для любой несвязанного столбца, включая те, до последнего связанного столбца. Обратите внимание, что столбцы должна вызываться в порядке возрастания номер столбца, если SQL_GD_ANY_ORDER также возвращается.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** может вызываться для несвязанных столбцов в любом порядке. Обратите внимание, что **SQLGetData** может быть вызвана только для столбцов после последнего связанного столбца, если SQL_GD_ANY_COLUMN также возвращается.  
  
 SQL_GD_BLOCK = **SQLGetData** может быть вызван для несвязанного столбца в любой строке блока данных (где размер набора строк больше, чем 1) после размещения для этой строки с **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** может вызываться для привязанных столбцов помимо несвязанных столбцов. Драйвер не может возвращать это значение, если он также возвращает SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** можно вызвать для получения значений выходных параметров. Дополнительные сведения см. в разделе [получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** должна возвращать данные только из несвязанных столбцов, которые произошли после последнего связанного столбца, вызываются в порядке возрастания номеров столбцов, а не в строке в несколько строк.  
  
 Если драйвер поддерживает закладки (фиксированной длины или переменной длины), он должен поддерживать вызова **SQLGetData** на столбец 0. Эта поддержка является обязательным, независимо от того, драйвер возвращает для вызова **SQLGetInfo** с SQL_GETDATA_EXTENSIONS *свойство*.  
  
 SQL_GROUP_BY (ODBC 2.0)  
 Значение SQLUSMALLINT, которое задает связь между столбцами в **GROUP BY** предложения и неагрегированные столбцы в списке выбора:  
  
 SQL_GB_COLLATE = A **COLLATE** предложение может быть указано в конце каждого столбца группирования. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY** предложения не поддерживаются. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = **GROUP BY** предложение должно содержать все неагрегированные столбцы в списке выбора. Он не может содержать другие столбцы. Например **DEPT BY Выбор Подразделений, MAX(SALARY) из СОТРУДНИКОВ группы**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = **GROUP BY** предложение должно содержать все неагрегированные столбцы в списке выбора. Он может содержать столбцы, которые не находятся в списке выбора. Например **DEPT BY Выбор Подразделений, MAX(SALARY) из СОТРУДНИКОВ группы, ВОЗРАСТ**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = столбцов в **GROUP BY** предложения и список выбора не связаны. Зависит от источника данных имеет значение nongrouped, неагрегированные столбцы в списке выбора. Например **DEPT BY Выбор Подразделений, Зарплата из СОТРУДНИКОВ группы, ВОЗРАСТ**. (ODBC 2.0)  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать параметр SQL_GB_GROUP_BY_EQUALS_SELECT как поддерживается. Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать параметр SQL_GB_COLLATE как поддерживается. Если никакие параметры не поддерживаются, **GROUP BY** предложение не поддерживается источником данных.  
  
 SQL_IDENTIFIER_CASE (ODBC 1.0)  
 SQLUSMALLINT значение следующим образом:  
  
 SQL_IC_UPPER = идентификаторов в SQL не зависят от регистра и хранятся в верхнем регистре в системном каталоге.  
  
 SQL_IC_LOWER = идентификаторов в SQL не зависят от регистра и хранятся в нижнем регистре в системном каталоге.  
  
 Sql_ic_mixed, имеющим = идентификаторов в SQL чувствительны к регистру и хранятся в смешанном регистре, в системном каталоге.  
  
 Sql_ic_mixed, имеющим = идентификаторов в SQL не зависят от регистра и хранятся в смешанном регистре, в системном каталоге.  
  
 Так как идентификаторы в SQL-92 никогда не учитывается регистр, драйвер, который соответствует строго SQL-92 (любой уровень) никогда не будут возвращать параметр sql_ic_mixed, имеющим как поддерживается.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1.0)  
 Строка символов, используется как начальный и конечный разделитель заключенные в кавычки (идентификатор с разделителем) в инструкциях SQL. (Идентификаторы передаются как аргументы функции ODBC не должны быть заключены в кавычки.) Если источник данных не поддерживает заключенные в кавычки идентификаторы, возвращается пустое значение.  
  
 Данная строка символов также может использоваться для заключения в кавычки аргументы функции каталога, если атрибут соединения SQL_ATTR_METADATA_ID равно SQL_TRUE.  
  
 Поскольку символ кавычки идентификатор в SQL-92 двойных кавычек ("«), драйвер, который соответствует строго SQL-92 всегда будет возвращать символ двойных кавычек.  
  
 SQL_INDEX_KEYWORDS (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисляет ключевые слова в инструкции CREATE INDEX, поддерживаемых драйвером:  
  
 SQL_IK_NONE = никакие ключевые слова не поддерживаются.  
  
 SQL_IK_ASC = ASC ключевое слово поддерживается.  
  
 SQL_IK_DESC = DESC ключевое слово поддерживается.  
  
 SQL_IK_ALL = All поддерживаются ключевые слова.  
  
 Чтобы узнать, поддерживается ли инструкции CREATE INDEX, приложение вызывает **SQLGetInfo** с типом SQL_DLL_INDEX сведения.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление представления в INFORMATION_SCHEMA, которые поддерживаются драйвером. Представления и содержимое, INFORMATION_SCHEMA, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие представления поддерживаются:  
  
 SQL_ISV_ASSERTIONS = идентифицирует утверждения каталога, принадлежащих указанному пользователю. (Уровень full)  
  
 SQL_ISV_CHARACTER_SETS = определяет каталога кодировки, доступных данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_CHECK_CONSTRAINTS = определяет ПРОВЕРКУ ограничений, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_COLLATIONS = идентифицирует параметров сортировки символов для каталога, доступных данному пользователю. (Уровень full)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = определяет столбцы для каталога, которые зависят от домены, определенные в каталоге и принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_COLUMN_PRIVILEGES = указывает права доступа к столбцам постоянных таблиц, доступных или предоставлены данным пользователем. (FIPS переходные уровень)  
  
 SQL_ISV_COLUMNS = определяет столбцы хранимых таблиц, доступных данному пользователю. (FIPS переходные уровень)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = подобный представление CONSTRAINT_TABLE_USAGE столбцы можно идентифицировать различные ограничения, которые принадлежат данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = определяет таблицы, используемые для ограничения (ссылочной, уникальным и утверждения) и принадлежат данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = указывает ограничения домена (из доменов в каталоге), доступных данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_DOMAINS = определяет домены, определенные в каталог, доступный для пользователя. (Промежуточный уровень)  
  
 SQL_ISV_KEY_COLUMN_USAGE = определяет столбцы, определенные в каталоге, ограниченные как ключи данным пользователем. (Промежуточный уровень)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = указывает ссылочные ограничения, которые принадлежат данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_SCHEMATA = указывает схемы, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_SQL_LANGUAGES = определяет SQL уровни соответствия, параметры и диалекты, поддерживаемые реализацией SQL. (Промежуточный уровень)  
  
 SQL_ISV_TABLE_CONSTRAINTS = указывает ограничения таблицы, принадлежащие данному пользователю. (Промежуточный уровень)  
  
 SQL_ISV_TABLE_PRIVILEGES = указывает права доступа к постоянных таблиц, доступных или предоставлены данным пользователем. (FIPS переходные уровень)  
  
 SQL_ISV_TABLES = определяет определено хранимых таблиц в каталогах, доступных данному пользователю. (FIPS переходные уровень)  
  
 SQL_ISV_TRANSLATIONS = определяет преобразование символов для каталога, доступных данному пользователю. (Уровень full)  
  
 SQL_ISV_USAGE_PRIVILEGES = определяет использование правами на объекты каталога, которые доступны или принадлежит данному пользователю. (FIPS переходные уровень)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = определяет столбцы, на которых представления каталога, которые принадлежат указанному пользователю зависят. (Промежуточный уровень)  
  
 SQL_ISV_VIEW_TABLE_USAGE = определяет таблицы, на которых представления каталога, которые принадлежат указанному пользователю зависят. (Промежуточный уровень)  
  
 SQL_ISV_VIEWS = определяет рассматриваемые таблицы, определенные в этом каталоге, доступных данному пользователю. (FIPS переходные уровень)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 SQLUINTEGER битовую маску, которая указывает на поддержку **вставить** инструкции:  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_INTEGRITY (ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает расширенный контроль целостности; «N», если это не так.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора keyset, поддерживаемых драйвером. Этой битовой маске содержит первый подмножества атрибутов; второй подмножество SQL_KEYSET_CURSOR_ATTRIBUTES2 см.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описания эти битовые маски в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить «курсоры» для «динамический курсор» в описании).  
  
 SQL-92 промежуточного уровня — совместимые драйвера обычно возвращают параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE как поддерживается, так как драйвер поддерживает прокручиваемые курсоры посредством внедренные инструкции SQL FETCH. Так как это не определить непосредственно базовой поддержки SQL, однако Прокручиваемые курсоры может не поддерживаться, даже для SQL-92 промежуточного уровня — совместимого драйвера.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора keyset, поддерживаемых драйвером. Этой битовой маске содержит второй подмножества атрибутов; Первый набор в разделе SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Описания эти битовые маски в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить «курсоры» для «динамический курсор» в описании).  
  
 SQL_KEYWORDS (ODBC 2.0)  
 Строка символов, содержащий список разделенных запятыми все ключевые слова, определяемые источником данных. Этот список не содержит ключевые слова, относящиеся к ODBC или ключевые слова, используемые с источником данных и ODBC. Этот список представляет все зарезервированные ключевые слова. взаимодействующие приложения, не следует использовать эти слова в именах объектов.  
  
 Список ключевых слов ODBC см. в разделе [зарезервированные ключевые слова](../../../odbc/reference/appendixes/reserved-keywords.md) в [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). **#Define** значение SQL_ODBC_KEYWORDS содержит разделенные запятыми список ключевых слов ODBC.  
  
 Приложение в. грамматику SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 Строка символов: «Y», если источник данных поддерживает escape-символ для (%) символ процента и символ подчеркивания (_) символов в в **как** предикат и драйвер поддерживает синтаксис ODBC для определения **как** предиката escape-символа; «N» в противном случае.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3.0)  
 Значение SQLUINTEGER, которое указывает максимальное число активных параллельных инструкций в асинхронном режиме, драйвер может поддерживать в отдельном соединении. Если нет определенных ограничений или число неизвестно, это значение равно нулю.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 Значение SQLUINTEGER, которое указывает максимальную длину (число шестнадцатеричных символов, за исключением литерала префикс и суффикс, возвращенных **SQLGetTypeInfo**) из двоичный литерал в инструкции SQL. Например литерал 0xFFAA двоичный файл имеет длину 4. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени каталога в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 Драйвер с FIPS полный уровень совместимую вернет менее 128.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 Значение SQLUINTEGER, которое указывает максимальную длину (количество символов, за исключением литерала префикс и суффикс, возвращенных **SQLGetTypeInfo**) из символьных литералов в инструкции SQL. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени столбца в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 18. FIPS промежуточного уровня — совместимые драйвера вернет менее 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальное число столбцов в **GROUP BY** предложения. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 6. Возвращает по крайней мере 15 FIPS промежуточного уровня — совместимого драйвера.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает максимальное число столбцов, допустимое в индексе. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальное число столбцов в **ORDER BY** предложения. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 6. Возвращает по крайней мере 15 FIPS промежуточного уровня — совместимого драйвера.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает максимальное число столбцов, допустимое в списке выбора. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 100. Возвращает по крайней мере 250 FIPS промежуточного уровня — совместимого драйвера.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает максимальное число столбцов, допустимое в таблице. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 100. Возвращает по крайней мере 250 FIPS промежуточного уровня — совместимого драйвера.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальное число активных инструкций, поддерживающие драйвер для подключения. Инструкция определена как активные, при наличии результатов, термин «результаты» значение строки из **ВЫБЕРИТЕ** операции или строк, затронутых **вставить**, **обновление**, или **Удалить** операции (например, количество строк), или если он находится в состоянии NEED_DATA. Это значение может отражают ограничение, налагаемое драйверу или источнику данных. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени курсора в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 18. FIPS промежуточного уровня — совместимые драйвера вернет менее 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальное число активных подключений, которые может поддерживать драйвера для среды. Это значение может отражают ограничение, налагаемое драйверу или источнику данных. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 SQLUSMALLINT, который указывает максимальный размер в символах, которая поддерживает источник данных для определяемых пользователем имен.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 18. FIPS промежуточного уровня — совместимые драйвера вернет менее 128.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 Значение SQLUINTEGER, которое указывает максимальное число байтов, разрешенное в объединенный полей индекса. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени процедуры в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 SQL_MAX_ROW_SIZE (ODBC 2.0)  
 SQLUINTEGER значение, которое указывает максимальную длину одной строки в таблице. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 2 000. Возвращает по крайней мере 8 000 FIPS промежуточного уровня — совместимого драйвера.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 Строка символов: «Y», если максимальный размер строки, возвращаемые по типу информации SQL_MAX_ROW_SIZE включает в себя длину всех столбцов, SQL_LONGVARCHAR и SQL_LONGVARBINARY в строке; «N» в противном случае.  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени схемы в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 18. FIPS промежуточного уровня — совместимые драйвера вернет менее 128.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 Значение SQLUINTEGER, которое указывает максимальную длину инструкции SQL (количество символов, включая пробелы). Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени таблицы в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 18. FIPS промежуточного уровня — совместимые драйвера вернет менее 128.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальное число допустимых таблиц в **FROM** предложения **ВЫБЕРИТЕ** инструкции. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 Драйвер уровня — совместимые с FIPS запись будет возвращать по крайней мере 15. Возвращает по крайней мере 50 FIPS промежуточного уровня — совместимого драйвера.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает максимальную длину имени пользователя в источнике данных. Если максимальная длина не или длина неизвестно, это значение будет равен нулю.  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает несколько результирующих наборов, «N», если это не так.  
  
 Дополнительные сведения о нескольких результирующих наборов см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1.0)  
 Строка символов: «Y», если драйвер поддерживает более одной активной транзакции, в то же время «N», если только одна транзакция может быть активной в любое время.  
  
 Сведения, возвращаемые для этого типа данных не применяется в случае распределенных транзакций.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2.0)  
 Строка символов: «Y», если источник данных должен длина значения данных long (тип данных является SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long, определяемые источником данных) перед этим значением отправляется источника данных «N», если это не так. Дополнительные сведения см. в разделе [SQLBindParameter, функция](../../../odbc/reference/syntax/sqlbindparameter-function.md) и [функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1.0)  
 SQLUSMALLINT значение, которое указывает, поддерживает ли источник данных не NULL в столбцах:  
  
 SQL_NNC_NULL = все столбцы должны допускать значения NULL.  
  
 SQL_NNC_NON_NULL = столбцы не могут иметь значение NULL. (Источник данных поддерживает **NOT NULL** ограничение столбца в **CREATE TABLE** инструкции.)  
  
 С драйвером SQL-92 начального уровня совместимую вернет SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает, где сортируются значения NULL в результирующем наборе:  
  
 SQL_NC_END = значения null сортируются в конце результирующего набора, независимо от того, ключевые слова ASC или DESC.  
  
 SQL_NC_HIGH = значения null сортируются в верхней части результирующего набора, в зависимости от того, ключевые слова ASC или DESC.  
  
 SQL_NC_LOW = значения null сортируются в нижней части результирующего набора, в зависимости от того, ключевые слова ASC или DESC.  
  
 SQL_NC_START = значения null сортируются в начале результирующего набора независимо от того, ключевые слова ASC или DESC.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1.0)  
 Примечание: Тип данных был введен в ODBC 1.0; с версией, в которой он был представлен меткой каждой битовой маски.  
  
 Битовая маска SQLUINTEGER, перечисление скалярные числовые функции, поддерживаемые драйвера и связанного источника данных.  
  
 Следующие битовые маски используются для определения того, числовые функции, которые поддерживаются:  
  
 SQL_FN_NUM_ABS (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_ACOS SQL_FN_NUM_ASIN (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_ATAN SQL_FN_NUM_ATAN2 SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_COT-SQL_ SQL_FN_NUM_DEGREES (ODBC 2.0) SQL_FN_NUM_LOG10 SQL_FN_NUM_LOG (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_FLOOR FN_NUM_EXP (ODBC 1.0) SQL_FN_ SQL_FN_NUM_RAND (ODBC 1.0) В SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) (ODBC 2.0) (ODBC 1.0) SQL_FN_NUM_MOD SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_TRUNCATE NUM_ROUND (ODBC 2.0) (ODBC 1.0) SQL_FN_NUM_SIGN SQL_FN_NUM_SIN (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_SQRT SQL_FN_NUM_TAN (ODBC 1.0) (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3.0)  
 Значение SQLUINTEGER, которое указывает уровень ODBC 3*.x* интерфейс, соответствующий драйвер.  
  
 SQL_OIC_CORE: Минимальный уровень, все драйверы ODBC, должно соответствовать. Этот уровень включает базовый интерфейс элементы, такие как подключения функции, функции для подготовки и выполнения инструкции SQL, функции метаданных базовый результирующий набор, каталога основные функции и т. д.  
  
 SQL_OIC_LEVEL1: Уровня, включая основные функции уровня соответствия стандартам, а также Прокручиваемые курсоры закладки, располагается обновляет и удаляет и так далее.  
  
 SQL_OIC_LEVEL2: Уровень включая функциональность уровня соответствия стандартам уровня 1, а также дополнительные функции, такие как Чувствительные курсоры; обновления, удаления и обновления по закладки; Поддержка хранимых процедур; функций каталога для первичного и внешнего ключей; Поддержка нескольких каталога; и т. д.  
  
 Дополнительные сведения см. в разделе [уровни соответствия интерфейс](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER (ODBC 1.0)  
 Строка символов с версией которой соответствует диспетчера драйверов ODBC. Версия представляется в виде ##. ##. 0000, где первые две цифры являются основной номер версии, а две следующие — дополнительный номер версии. Это реализуется только диспетчера драйверов.  
  
 SQL_OJ_CAPABILITIES (ODBC 2.01)  
 Битовая маска SQLUINTEGER, перечисление типа внешнего соединения, поддерживаемые драйвера и источник данных. Следующие битовые маски используются для определения, какие типы поддерживаются:  
  
 SQL_OJ_LEFT = Left поддерживаются внешние соединения.  
  
 SQL_OJ_RIGHT = Right поддерживаются внешние соединения.  
  
 SQL_OJ_FULL = полный поддерживаются внешние соединения.  
  
 SQL_OJ_NESTED = вложенные внешние соединения поддерживаются.  
  
 SQL_OJ_NOT_ORDERED = столбец имен в предложении ON внешнего соединения не должны обязательно находиться в том же порядке, как их имена соответствующей таблицы в **ВНЕШНЕГО СОЕДИНЕНИЯ** предложения.  
  
 SQL_OJ_INNER = Внутренняя таблица (правая таблица в левое внешнее соединение) или левая таблица в правое внешнее соединение можно также в inner join. Это не относится к полные внешние соединения, которые не имеют внутренней таблице.  
  
 SQL_OJ_ALL_COMPARISON_OPS = сравнения оператор в предложении ON может быть любой из операторов сравнения ODBC. Если этот бит не задано, может использоваться только оператора сравнения равно (=) в внешние соединения.  
  
 Если ни один из этих параметров возвращается как поддерживается, поддерживается без предложения внешнего соединения.  
  
 Сведения о поддержке операторов реляционное соединение в инструкции SELECT в соответствии с определением SQL-92, в разделе SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2.0)  
 Строка символов: «Y» Если столбцы в **ORDER BY** предложение должно быть в списке выбора; в противном случае — «N».  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3.0)  
 В выполнении параметризованных подсчитывает SQLUINTEGER перечисление свойств драйвера к доступности строки. Имеет следующие значения:  
  
 SQL_PARC_BATCH = отдельные счетчики строк доступны для каждого набора параметров. Это эквивалентно концептуально драйвер Создание пакетных инструкций SQL, по одному для каждого параметра в массиве. Расширенные сведения об ошибке можно получить с помощью поля дескриптора SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH = имеется только одну строку счетчик доступен, то есть число совокупное строк, возникающие в результате выполнения инструкции для всего массива параметров. Это эквивалентно концептуально обработке инструкции вместе с массива параметров завершения как одно целое. Ошибки обрабатываются так же, как если бы выполнялись одной инструкции.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 При выполнении параметризованных задает SQLUINTEGER перечисление свойств драйвера к доступности результат. Имеет следующие значения:  
  
 SQL_PAS_BATCH = имеется один результирующий набор, доступный для каждого набора параметров. Это эквивалентно концептуально драйвер Создание пакетных инструкций SQL, по одному для каждого параметра в массиве.  
  
 SQL_PAS_NO_BATCH = нет набора только один результирующий набор доступным, представляющий кумулятивный результат, полученный в результате выполнения оператора для полного массива параметров. Это эквивалентно концептуально обработке инструкции вместе с массива параметров завершения как одно целое.  
  
 SQL_PAS_NO_SELECT = A драйвер не допускает создания результирующего набора инструкции должно выполняться с помощью массива параметров.  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для процедуры; Например, «процедуры базы данных», «хранимая процедура», «процедуры», «пакет» или «хранимая запроса».  
  
 SQL_PROCEDURES (ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает процедур и драйвер поддерживает синтаксис вызова процедуры ODBC; «N» в противном случае.  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 Битовая маска SQLINTEGER операции поддержки в перечислении **SQLSetPos**.  
  
 Следующие битовые маски используются вместе с флагом, чтобы определить, какие параметры поддерживаются.  
  
 SQL_POS_POSITION (ODBC 2.0) (ODBC 2.0) SQL_POS_REFRESH SQL_POS_UPDATE (ODBC 2.0) (ODBC 2.0) SQL_POS_DELETE SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2.0)  
 SQLUSMALLINT значение следующим образом:  
  
 SQL_IC_UPPER = кавычках идентификаторов в SQL не зависят от регистра и хранятся в верхнем регистре в системном каталоге.  
  
 SQL_IC_LOWER = кавычках идентификаторов в SQL не зависят от регистра и хранятся в нижнем регистре в системном каталоге.  
  
 Sql_ic_mixed, имеющим = кавычках идентификаторов в SQL чувствительны к регистру и хранятся в смешанном регистре, в системном каталоге. (В базе данных SQL-92 совместимого заключенные в кавычки идентификаторы учитывается регистр.)  
  
 Sql_ic_mixed, имеющим = кавычках идентификаторов в SQL не зависят от регистра и хранятся в смешанном регистре, в системном каталоге.  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать sql_ic_mixed, имеющим.  
  
 SQL_ROW_UPDATES (ODBC 1.0)  
 Строка символов: «Y», если курсор keyset или смешанного поддерживает версии строк или значений для всех выбранных строк и обнаруживаются все обновления, которые были внесены в строку в любой пользователь с момента последней выборки. (Это относится только к обновлению, удаления или вставки). Драйвер может возвращать SQL_ROW_UPDATED флаг состояния строки массива при **SQLFetchScroll** вызывается. В противном случае — «N».  
  
 SQL_SCHEMA_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для схемы; Например «владелец», «Идентификатор авторизации» или «Схема».  
  
 Строка символов могут быть возвращены в верхней, нижней или смешанный регистр.  
  
 С драйвером SQL-92 начального уровня совместимую всегда возвращает «schema».  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление инструкций, в которых используются схемы:  
  
 SQL_SU_DML_STATEMENTS = схемы поддерживаются во всех инструкциях языка обработки данных: **ВЫБЕРИТЕ**, **вставить**, **обновление**, **DELETE**и если поддерживается, **ВЫБЕРИТЕ для обновления** и располагается update и delete.  
  
 SQL_SU_PROCEDURE_INVOCATION = схемы поддерживаются в операторе вызова процедуры ODBC.  
  
 SQL_SU_TABLE_DEFINITION = схемы поддерживаются во всех инструкциях определения таблицы: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE **, и **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = схемы поддерживаются во всех инструкциях определение индекса: **CREATE INDEX** и **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = схемы поддерживаются во всех инструкциях определения прав доступа: **GRANT** и **ОТОЗВАТЬ**.  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать параметры SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION и SQL_SU_PRIVILEGE_DEFINITION как поддерживается.  
  
 Это *свойство* был переименован для ODBC 3.0 из ODBC 2.0 *свойство* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS (ODBC 1.0)  
 Примечание: Тип данных был введен в ODBC 1.0; с версией, в которой он был представлен меткой каждой битовой маски.  
  
 Битовая маска SQLUINTEGER, перечисление параметров прокрутки, поддерживаемых для Прокручиваемые курсоры.  
  
 Чтобы определить, какие параметры поддерживаются используются следующие битовые маски.  
  
 SQL_SO_FORWARD_ONLY = курсор только прокручивается вперед. (ODBC 1.0)  
  
 SQL_SO_STATIC = данные в результирующем наборе является статическим. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = драйвер сохраняет и использует ключи для каждой строки в результирующем наборе. (ODBC 1.0)  
  
 SQL_SO_DYNAMIC = драйвер сохраняет ключи для каждой строки в наборе строк (размер набора ключей является таким же, как размер набора строк). (ODBC 1.0)  
  
 SQL_SO_MIXED = драйвер сохраняет ключи для каждой строки в набор ключей, а размер набора ключей больше, чем размер набора строк. Курсор находится курсоры внутри набора ключей и динамические за пределами набор ключей. (ODBC 1.0)  
  
 Сведения о Прокручиваемые курсоры см. в разделе [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1.0)  
 Строка символов, указав драйвер поддерживает как escape-символ, как допустимые символы для поиска шаблонов и позволяет использовать шаблон соответствия метасимволы подчеркивания (_) и знак процента (%). Escape-символ применяется только для этих аргументов функции каталога, которые поддерживают строки поиска. Если это значение не задано, драйвер не поддерживает escape-символа шаблону поиска.  
  
 Так как этот тип не указывает на общую поддержку escape-символ в **как** предиката, SQL-92 не содержат требований для этой строки символов.  
  
 Это *свойство* относится к функциям каталога. Описание использование escape-символ в строке шаблона поиска см. в разделе [значения аргументов шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME (ODBC 1.0)  
 Строка символов с именем сервера, определяемые источником фактические данные. полезно, когда имя источника данных используется во время **SQLConnect**, **SQLDriverConnect**, и **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2.0)  
 Строка символов, содержащий все специальные символы (то есть все символы, кроме до z, до Z, 0 до 9 и символ подчеркивания), которые могут использоваться в имени идентификатора, например имя таблицы, имя столбца или имя индекса, в источнике данных. Например «#$^». Если идентификатор содержит один или несколько из этих символов, идентификатор должен быть идентификатором с разделителем.  
  
 SQL_SQL_CONFORMANCE (ODBC 3.0)  
 SQLUINTEGER значение, которое указывает уровень SQL-92 поддерживается драйвером:  
  
 SQL_SC_SQL92_ENTRY = запись уровня SQL-92 совместимым.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 переходные уровень совместимым.  
  
 SQL_SC_SQL92_FULL = полный уровень соответствует SQL-92.  
  
 SQL_SC_ SQL92_INTERMEDIATE = промежуточного уровня SQL-92 совместимым.  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление скалярные функции даты и времени, которые поддерживаются драйвером и связанного источника данных, как определено в SQL-92.  
  
 Следующие битовые маски используются для определения функции даты и времени, которые поддерживаются:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 Битовая маска SQLUINTEGER правила для внешнего ключа в перечислении **удалить** инструкции, как определено в SQL-92.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Драйвер с FIPS промежуточном уровне совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 Битовая маска SQLUINTEGER правила для внешнего ключа в перечислении **обновление** инструкции, как определено в SQL-92.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Драйвер с SQL-92 полный уровень совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения, поддерживаемые в перечислении **GRANT** инструкции, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 (SQL_SG_INSERT_COLUMN (промежуточный уровень) (начальный уровень) SQL_SG_INSERT_TABLE SQL_SG_REFERENCES_TABLE (начальный уровень) (начальный уровень) SQL_SG_REFERENCES_COLUMN SQL_SG_SELECT_TABLE (начальный уровень) SQL_SG_UPDATE_COLUMN SQL_SG_DELETE_TABLE (начальный уровень) Начальный уровень) SQL_SG_USAGE_ON_CHARACTER_SET (FIPS переходные уровень) SQL_SG_USAGE_ON_COLLATION (FIPS переходные уровень) SQL_SG_UPDATE_TABLE (начальный уровень) SQL_SG_USAGE_ON_DOMAIN (FIPS переходные уровень) SQL_SG_USAGE_ON_TRANSLATION (FIPS Переходные уровень) SQL_SG_WITH_GRANT_OPTION (начальный уровень)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление числовое значение скалярных функций, которые поддерживаются драйвером и связанного источника данных, как определено в SQL-92.  
  
 Следующие битовые маски используются для определения того, числовые функции, которые поддерживаются:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 Битовая маска SQLUINTEGER предикаты, поддерживаемые в перечислении **ВЫБЕРИТЕ** инструкции, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски.  
  
 SQL_SP_BETWEEN (начальный уровень) (начальный уровень) SQL_SP_COMPARISON SQL_SP_EXISTS (начальный уровень) SQL_SP_IN (начальный уровень) SQL_SP_ISNOTNULL (начальный уровень) SQL_SP_ISNULL (начальный уровень) SQL_SP_LIKE (начальный уровень) (уровень Full) SQL_SP_MATCH_FULL SQL_SP_MATCH_PARTIAL (Уровень full) SQL_SP_MATCH_UNIQUE_FULL (уровень Full) SQL_SP_MATCH_UNIQUE_PARTIAL (уровень Full) SQL_SP_OVERLAPS (FIPS переходные уровень) (начальный уровень) SQL_SP_QUANTIFIED_COMPARISON SQL_SP_UNIQUE (начальный уровень)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 Битовая маска SQLUINTEGER реляционное соединение операторы, поддерживаемые в перечислении **ВЫБЕРИТЕ** инструкции, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски.  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (промежуточный уровень) (уровень Full) SQL_SRJO_CROSS_JOIN SQL_SRJO_EXCEPT_JOIN (промежуточный уровень) SQL_SRJO_FULL_OUTER_JOIN (промежуточный уровень) SQL_SRJO_INNER_JOIN (FIPS переходные уровень) SQL_SRJO_INTERSECT_JOIN (Промежуточный уровень) SQL_SRJO_UNION_JOIN SQL_SRJO_RIGHT_OUTER_JOIN (FIPS переходные уровень) SQL_SRJO_NATURAL_JOIN (FIPS переходные уровень) SQL_SRJO_LEFT_OUTER_JOIN (FIPS переходные уровень) (уровень Full)  
  
 Указывает на поддержку SQL_SRJO_INNER_JOIN **ВНУТРЕННЕЕ соединение** синтаксис, не возможность внутреннее соединение. Поддержка **ВНУТРЕННЕЕ соединение** синтаксис является ПЕРЕХОДНЫЕ FIPS, тогда как поддержка возможностей внутреннего соединения является **входа**.  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения, поддерживаемые в перечислении **ОТОЗВАТЬ** инструкции, как определено в SQL-92, поддерживаемые источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SR_ SQL_SR_REFERENCES_COLUMN (начальный уровень) в SQL_SR_GRANT_OPTION_FOR (промежуточный уровень) SQL_SR_INSERT_COLUMN (промежуточный уровень) SQL_SR_CASCADE (FIPS переходные уровень) SQL_SR_DELETE_TABLE (начальный уровень) SQL_SR_INSERT_TABLE (начальный уровень) REFERENCES_TABLE (начальный уровень) SQL_SR_RESTRICT (FIPS переходные уровень) SQL_SR_SELECT_TABLE (начальный уровень) SQL_SR_UPDATE_COLUMN (начальный уровень) SQL_SR_UPDATE_TABLE (начальный уровень) SQL_SR_USAGE_ON_DOMAIN (FIPS переходные уровень) SQL_SR_USAGE_ON_ SQL_SR_USAGE_ON_TRANSLATION SQL_SR_USAGE_ON_COLLATION (FIPS переходные уровень) CHARACTER_SET (FIPS переходные уровень) (FIPS переходные уровень)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 Битовая маска SQLUINTEGER конструктор выражений значений строк, поддерживаемые в перечислении **ВЫБЕРИТЕ** инструкции, как определено в SQL-92. Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски.  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление строка скалярных функций, которые поддерживаются драйвером и связанного источника данных, как определено в SQL-92.  
  
 Следующие битовые маски используются для определения функции строки, которые поддерживаются:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление значение выражения поддерживаются, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски.  
  
 SQL_SVE_NULLIF SQL_SVE_COALESCE (промежуточный уровень) SQL_SVE_CAST (FIPS переходные уровень) SQL_SVE_CASE (промежуточный уровень) (промежуточный уровень)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление CLI standard или стандарты, которым соответствует драйвер. Чтобы определить, какие уровни драйвер соответствует используются следующие битовые маски:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Драйвер соответствует откройте группу CLI версии 1.  
  
 SQL_SCC_ISO92_CLI: Драйвер соответствует стандарту ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты статического курсора, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножества атрибутов; второй подмножество SQL_STATIC_CURSOR_ATTRIBUTES2 см.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описания эти битовые маски в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить «статический курсор» для «динамический курсор» в описании).  
  
 SQL-92 промежуточного уровня — совместимые драйвера обычно возвращают параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE как поддерживается, так как драйвер поддерживает прокручиваемые курсоры посредством внедренные инструкции SQL FETCH. Так как это не определить непосредственно базовой поддержки SQL, однако Прокручиваемые курсоры может не поддерживаться, даже для SQL-92 промежуточного уровня — совместимого драйвера.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты статического курсора, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножества атрибутов; Первый набор в разделе SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Описания эти битовые маски в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и заменить «статический курсор» для «динамический курсор» в описании).  
  
 SQL_STRING_FUNCTIONS (ODBC 1.0)  
 Примечание: Тип данных был введен в ODBC 1.0; с версией, в которой он был представлен меткой каждой битовой маски.  
  
 Битовая маска SQLUINTEGER, перечисление скалярные строковые функции, поддерживаемые драйвера и связанного источника данных.  
  
 Следующие битовые маски используются для определения функции строки, которые поддерживаются:  
  
 SQL_FN_STR_DIFFERENCE (ODBC 2.0) (ODBC 1.0) SQL_FN_STR_CONCAT SQL_FN_STR_INSERT (ODBC (ODBC 1.0) SQL_FN_STR_ASCII SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) 1.0) (ODBC 1.0) SQL_FN_STR_LCASE SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) (ODBC 3.0) SQL_FN_STR_POSITION SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_ SQL_FN_STR_UCASE SQL_FN_STR_SPACE (ODBC 2.0) (ODBC 1.0) SQL_FN_STR_SUBSTRING ДЛЯ SQL_FN_STR_RIGHT (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_RTRIM STR_REPLACE (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) (ODBC 1.0)  
  
 Если приложение может вызвать **найти** скалярной функции с *строковое_выражение1*, *строковое_выражение2*, и *запустить* аргументы, то драйвер Возвращает битовую маску SQL_FN_STR_LOCATE. Если приложение может вызвать скалярные функции поиск только с *строковое_выражение1* и *строковое_выражение2* аргументы, драйвер возвращает SQL_FN_STR_LOCATE_2 битовой маски. Драйверы с полной поддержкой **найти** скалярные функции возвращают обоих битовые маски.  
  
 (Дополнительные сведения см. в разделе [строковые функции](../../../odbc/reference/appendixes/string-functions.md) в приложении E «скалярные функции.»)  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление предикаты, которые поддерживают вложенные запросы:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Битовая маска SQL_SQ_CORRELATED_SUBQUERIES указывает, что все предикаты, которые поддерживают вложенные запросы поддерживают коррелированные вложенные запросы.  
  
 С драйвером SQL-92 начального уровня совместимую всегда возвращает битовую маску, в которой все эти биты равны.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1.0)  
 Битовая маска SQLUINTEGER, перечисление скалярных системных функций, поддерживаемых драйвером и связанного источника данных.  
  
 Следующие битовые маски используются для определения, какие системные функции поддерживаются:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для таблицы. Например «table» или «файл».  
  
 Данная строка символов может быть в верхней, нижней или смешанный регистр.  
  
 С драйвером SQL-92 начального уровня совместимую всегда возвращает «table».  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление поддерживается драйвером и связанного источника данных скалярная функция TIMESTAMPADD интервалы отметки времени.  
  
 Следующие битовые маски используются для определения, какие интервалы поддерживаются:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Драйвер с FIPS промежуточном уровне совместимую всегда возвращает битовую маску, в которой все эти биты равны.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление поддерживается драйвером и связанного источника данных скалярная функция TIMESTAMPDIFF интервалы отметки времени.  
  
 Следующие битовые маски используются для определения, какие интервалы поддерживаются:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Драйвер с FIPS промежуточном уровне совместимую всегда возвращает битовую маску, в которой все эти биты равны.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1.0)  
 Примечание: Тип данных был введен в ODBC 1.0; с версией, в которой он был представлен меткой каждой битовой маски.  
  
 Битовая маска SQLUINTEGER, перечисление скалярные функции даты и времени поддерживаются драйвером и связанного источника данных.  
  
 Следующие битовые маски используются для определения функции даты и времени, которые поддерживаются:  
  
 SQL_FN_TD_DAYNAME (ODBC 2.0) (ODBC 1.0) SQL_FN_TD_CURTIME SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) (ODBC 1.0) SQL_FN_TD_CURDATE SQL_FN_TD_DAYOFWEEK () ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) (ODBC 3.0) SQL_FN_TD_EXTRACT SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) (ODBC 1.0) SQL_FN_TD_NOW SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_ SQL_FN_TD_WEEK (ODBC 1.0) (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF SQL_FN_TD_YEAR (ODBC 1.0) ДЛЯ ВТОРОГО (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0)  
  
 SQL_TXN_CAPABLE (ODBC 1.0)  
 Примечание: Тип данных был введен в ODBC 1.0; Каждое возвращаемое значение меткой с версией, в которую было включено.  
  
 Значение SQLUSMALLINT, описывающее поддержка транзакций в драйвер или источник данных:  
  
 SQL_TC_NONE = транзакции не поддерживаются. (ODBC 1.0)  
  
 SQL_TC_DML = транзакции может содержать только инструкции языка обработки данных (DML) (**ВЫБЕРИТЕ**, **вставить**, **обновление**, **удаление** ). Инструкции определения языка DDL данных к тому, что для транзакции произошла ошибка. (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = транзакции может содержать только инструкции DML. Инструкции DDL (**CREATE TABLE**, **DROP INDEX**и так далее) обнаружил к тому, что для операции фиксации транзакции. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = транзакции может содержать только инструкции DML. Инструкции DDL в транзакции обрабатываются. (ODBC 2.0)  
  
 SQL_TC_ALL = транзакции может содержать инструкции DDL и DML-инструкций в любом порядке. (ODBC 1.0)  
  
 (Поскольку поддержки транзакций является обязательным в SQL-92 и SQL-92 совместимый драйвер [любой уровень] никогда не будут возвращать SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1.0)  
 Битовая маска SQLUINTEGER, перечисление уровни изоляции транзакций доступны из драйвера или источника данных.  
  
 Следующие битовые маски используются вместе с флагом, чтобы определить, какие параметры поддерживаются:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Описание этих уровней изоляции см. в описании SQL_DEFAULT_TXN_ISOLATION.  
  
 Чтобы задать уровень изоляции транзакции, приложение вызывает **SQLSetConnectAttr** для установки атрибута SQL_ATTR_TXN_ISOLATION. Дополнительные сведения см. в разделе [SQLSetConnectAttr, функция](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать SQL_TXN_SERIALIZABLE как поддерживается. Переходные FIPS драйвер уровня совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_UNION (ODBC 2.0)  
 Битовая маска SQLUINTEGER перечисление поддержка **ОБЪЕДИНЕНИЕ** предложения:  
  
 SQL_U_UNION поддерживает источник данных = **ОБЪЕДИНЕНИЕ** предложения.  
  
 SQL_U_UNION_ALL поддерживает источник данных = **все** ключевое слово в **ОБЪЕДИНЕНИЕ** предложения. (**SQLGetInfo** возвращает SQL_U_UNION и SQL_U_UNION_ALL в данном случае.)  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать оба этих варианта как поддерживается.  
  
 SQL_USER_NAME (ODBC 1.0)  
 Строка символов с имя, используемое в определенной базе данных, который может отличаться от имени входа.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3.0)  
 Строка символов, который указывает год публикации, с которой версия диспетчером драйверов ODBC полностью соответствует спецификации Open Group.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Строка символов: «Y», если пользователь может выполнять все процедуры, возвращенных **SQLProcedures**; «N», если может быть процедуры вернул, что пользователь не может выполняться.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Строка символов: «Y», если пользователь гарантируется **ВЫБЕРИТЕ** прав доступа для всех таблиц, возвращаемых функцией **SQLTables**; «N», если может быть таблиц возвращаются, пользователь не имеет доступа.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 SQLUSMALLINT значение, которое указывает максимальное число активных сред, которые поддерживает драйвер. Если нет указанного ограничения или число неизвестно, это значение будет равен нулю.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление поддержка статистических функций:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 С драйвером SQL-92 начального уровня совместимую всегда будет возвращать все эти возможности как поддерживается.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **ALTER домена** инструкции, как определено в SQL-92, поддерживаемые источником данных. Полный SQL-92 совместимого уровня драйвер всегда будет возвращать все битовой маски. Возвращаемое значение «0» означает, что **ALTER домена** инструкция не поддерживается.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ограничение домена поддерживается добавление (уровень Full)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter домена > \<предложения set в домене по умолчанию > поддерживается (уровень Full)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<предложение определение ограничения имя > поддерживается для именования домена ограничение (промежуточный уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<предложения ограничения для удаления домена > поддерживается (уровень Full)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter домена > \<предложения по умолчанию для удаления домена > поддерживается (уровень Full)  
  
 Укажите поддерживаемые следующих битов \<атрибутов ограничения > Если \<добавить ограничение домена > поддерживается (SQL_AD_ADD_DOMAIN_CONSTRAINT биту присваивается значение):  
  
 SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (уровень Full) SQL_AD_ADD_CONSTRAINT_DEFERRABLE (уровень Full) (уровень Full)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Битовая маска SQLUINTEGER предложения в перечислении **ALTER TABLE** инструкции, поддерживаемые источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должны поддерживаться этой функции отображается в скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<добавить столбец > предложение поддерживается с помощью средства можно задать параметры сортировки столбца (уровень Full) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<добавить столбец > предложение поддерживается с механизмом для указания столбца значения по умолчанию (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<добавить столбец > является поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<добавить столбец > предложение поддерживается с механизмом для указания столбца ограничений (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<добавить ограничение таблицы > предложение поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > поддерживается для именования ограничения столбцов и таблиц (промежуточный уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<удалением столбца > поддерживается CASCADE (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<изменить столбец > \<предложения по умолчанию для удаления столбца > является поддерживается (промежуточный уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<удалением столбца > ограничение поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<удалением столбца > ограничение поддерживается (FIPS переходные уровень) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<изменить столбец > \<предложении default для столбца набора > является поддерживается (промежуточный уровень) (ODBC 3.0)  
  
 Поддержка укажите следующие биты \<атрибутов ограничения > Если поддерживается Указание ограничения столбцов и таблиц (SQL_AT_ADD_CONSTRAINT биту присваивается значение):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (уровень Full) (ODBC 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 SQLUINTEGER значение, которое указывает уровень поддержки асинхронных операций в драйвере:  
  
 SQL_AM_CONNECTION = соединение поддерживается уровня асинхронное выполнение. Все дескрипторы инструкции, связанные с дескриптором данного соединения, в асинхронном режиме, либо все находятся в синхронном режиме. Дескриптор инструкции для подключения не может быть в асинхронном режиме, пока другой дескриптора инструкции, в том же соединении в синхронном режиме и наоборот.  
  
 SQL_AM_STATEMENT = поддерживается уровня асинхронное выполнение инструкции. Некоторые дескрипторов инструкций, связанной с дескриптором соединения может быть в асинхронном режиме, в то время как другие дескрипторы инструкций в том же соединении, в синхронном режиме.  
  
 SQL_AM_NONE = асинхронный режим не поддерживается.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Подсчитывает SQLUINTEGER битовой маски, перечисления поведения драйвера по отношению к доступности строки. Следующие битовые маски используются вместе с типов данных:  
  
 SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE, суммируются в одно. Если этот бит не задано, счетчики строк будут доступны для каждой инструкции.  
  
 SQL_BRC_PROCEDURES = количество строк, если таковые имеются, доступны при выполнении пакета в хранимой процедуре. Если количество строк, их можно откатить вверх или по отдельности доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
 SQL_BRC_EXPLICIT = количество строк, если, они доступны при выполнении пакета непосредственно, путем вызова **SQLExecute** или **SQLExecDirect**. Если количество строк, их можно откатить вверх или по отдельности доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
## <a name="example"></a>Пример  
 **SQLGetInfo** возвращает список поддерживаемых параметров как битовую маску SQLUINTEGER в **InfoValuePtr*. Битовая маска для каждого параметра используется вместе с флагом для определения, является ли этот параметр поддерживается.  
  
 Например приложение может использовать следующий код, чтобы определить, поддерживает ли драйвер, связанный с подключением скалярные функции SUBSTRING.  
  
 Другой пример использования **SQLGetInfo**, в разделе [функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md).  
  
```  
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
  
 Определение, поддерживает ли драйвер функции  
 [Функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Возврат значения атрибута инструкции  
 [Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Возвращение сведений о типах данных для источника данных  
 [Функция SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)

