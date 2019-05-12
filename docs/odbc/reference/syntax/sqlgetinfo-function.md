---
title: SQLGetInfo, функция | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af4b2b5546e8b084afbdd769fb93c416964b0c13
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537992"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo, функция
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetInfo** возвращает общие сведения об источнике драйвера и данные, связанные с подключением.  
  
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
 *ConnectionHandle*  
 [Вход] Дескриптор соединения.  
  
 *Свойство*  
 [Вход] Тип данных.  
  
 *InfoValuePtr*  
 [Выход] Указатель на буфер, в котором для возвращения сведений. В зависимости от *InfoType* запрошено, данные, возвращаемые будет иметь одно из следующих: строка символов с завершающим нулем, значение SQLUSMALLINT, SQLUINTEGER битовой маски, с флагом SQLUINTEGER, двоичное значение SQLUINTEGER, или Значение SQLULEN.  
  
 Если *InfoType* аргументом является SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT, *InfoValuePtr* аргумент как входные и выходные. (См. в разделе SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT дескрипторы позже в этом описании функции подробнее.)  
  
 Если *InfoValuePtr* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее число байтов (за исключением символа конечное значение null для символьных данных) для возврата в буфере, на которые указывают *InfoValuePtr*.  
  
 *BufferLength*  
 [Вход] Длина \* *InfoValuePtr* буфера. Если значение в  *\*InfoValuePtr* не представляет собой строку символов или если *InfoValuePtr* является пустым указателем, *BufferLength* аргумент учитывается. Драйвер предполагает, что размер  *\*InfoValuePtr* SQLUSMALLINT или SQLUINTEGER, на основе *InfoType*. Если  *\*InfoValuePtr* строка в Юникоде (при вызове **SQLGetInfoW**), *BufferLength* аргумент должен быть четным числом; Если нет, SQLSTATE HY090 () Недопустимая длина строки или буфера) возвращается.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число байтов (за исключением символа конечное значение null для символьных данных) для возврата в **InfoValuePtr*.  
  
 Для символьных данных, если количество байтов, доступных для возврата больше или равно *BufferLength*, заполните \* *InfoValuePtr* усекается до  *BufferLength* символ байтов минус длина конечное значение null и заканчивается нулевым байтом драйвером.  
  
 Для всех других типов данных, значение *BufferLength* игнорируется и драйвер предполагает, что размер \* *InfoValuePtr* является SQLUSMALLINT или SQLUINTEGER, в зависимости от  *Свойство*.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetInfo** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, можно получить путем вызова связанного значения SQLSTATE **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_DBC и *обрабатывать* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLGetInfo** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Буфер \* *InfoValuePtr* не был достаточно велик для того, чтобы вернуть все запрашиваемые данные. Таким образом данные были усечены. Длина требуемые сведения в форме неусеченный возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08003|Соединение не открыто|Тип данных (DM), запрашиваемый в *InfoType* требуется открытое соединение. Типы сведений, зарезервированной с помощью ODBC не устанавливая соединений могут возвращаться только SQL_ODBC_VER.|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимая для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY024|Недопустимое значение атрибута|(DM) *InfoType* аргумент был SQL_DRIVER_HSTMT, и значение, на которые указывают *InfoValuePtr* не дескриптор допустимую инструкцию.<br /><br /> (DM) *InfoType* аргумент был SQL_DRIVER_HDESC, и значение, на которые указывают *InfoValuePtr* не был допустимым дескриптора.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное для аргумента *BufferLength* меньше 0.<br /><br /> (DM) значение, заданное для *BufferLength* было нечетным числом, и  *\*InfoValuePtr* был тип данных Юникода.|  
|HY096|Тип сведений за пределы диапазона|Значение, указанное для аргумента *InfoType* недопустимо для версии ODBC, поддерживаемых драйвером.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательное поле не реализован|Значение, указанное для аргумента *InfoType* был специфические для драйвера значение, которое не поддерживается драйвером.|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|(DM), соответствующий драйвер *ConnectionHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Типы в настоящее время определены сведения приведены в «Типов сведений» ниже в данном разделе; предполагается, что сведения будут определены пользоваться преимуществами различных источников данных. Широкий набор типов сведений зарезервировано для ODBC. разработчики драйверов необходимо зарезервировать значения для собственных нужд конкретного драйвера из Open Group. **SQLGetInfo** выполняет преобразование в формате Юникод или *преобразование* (см. в разделе [приложении a. Коды ошибок ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) из *Справочник по программированию ODBC*) для определенных драйвером *InfoTypes*. Дополнительные сведения см. в разделе [типов данных драйвера, типы дескрипторов, типы сведений, диагностические типы и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Формат сведений, возвращаемых в \* *InfoValuePtr* зависит от *InfoType* запрошено. **SQLGetInfo** вернет информацию в одном из пяти различных форматов:  
  
-   Строка символов с завершающим нулем  
  
-   Значение SQLUSMALLINT  
  
-   Битовая маска SQLUINTEGER  
  
-   An SQLUINTEGER value  
  
-   Двоичное значение SQLUINTEGER  
  
 Формат каждого из следующих типов сведений указывается в описании типа. Приложение должно привести значение, возвращаемое в **InfoValuePtr* соответствующим образом. Пример того, как приложение смогло извлечь данные с SQLUINTEGER битовую маску см. в разделе «Пример кода».  
  
 Драйвер должен возвращать значение для каждого типа данных, который определен в следующих таблицах. Если для типа данных не применяется к драйверу или источнику данных, драйвер возвращает одно из значений, перечисленных в следующей таблице.  
  
 Символьная строка («Y» или «N»)  
 "N"  
  
 Строка символов (не «Y» или «N»)  
 Пустая строка.  
  
 SQLUSMALLINT  
 0  
  
 SQLUINTEGER битовой маски или двоичное значение SQLUINTEGER  
 0L  
  
 Например, если источник данных не поддерживает процедуры **SQLGetInfo** возвращает значения, перечисленные в следующей таблице для значений *InfoType* , связанные с процедурами.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Пустая строка.  
  
 **SQLGetInfo** возвращает SQLSTATE HY096 (недопустимое значение аргумента) для значений *InfoType* , находятся в диапазоне типов сведений, зарезервированные для использования в ODBC, но не определяется используемая версия ODBC, поддерживаемых драйвером. Чтобы определить, какая версия ODBC драйвер соответствует требованиям, приложение вызывает **SQLGetInfo** с типом SQL_DRIVER_ODBC_VER сведения. **SQLGetInfo** возвращает SQLSTATE HYC00 (дополнительная возможность не реализована) для значений *InfoType* , находятся в диапазоне типов сведений, зарезервированные для использования драйвера, но не поддерживается драйвером.  
  
 Все вызовы **SQLGetInfo** требуется открытое соединение, за исключением случаев *InfoType* является SQL_ODBC_VER, который возвращает версии диспетчера драйверов.  
  
## <a name="information-types"></a>Типы сведений  
 В этом разделе перечислены поддерживаемые типы сведений **SQLGetInfo**. Типы сведений категорически группируются и перечислены в алфавитном порядке. Типы сведений, которые были добавлены или любое удобное для ODBC 3 *.x* также перечислены.  
  
## <a name="driver-information"></a>Сведения о драйвере  
 Следующие значения *InfoType* аргумент возвращать сведения о драйвере ODBC, например число активных инструкций, имя источника данных и уровень соответствия стандартам интерфейса:  
  
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
>  При реализации **SQLGetInfo**, драйвер может повысить производительность, сводя к минимуму количество попыток отправки или от сервера сведения.  
  
## <a name="dbms-product-information"></a>Сведения о продукте СУБД  
 Следующие значения *InfoType* аргумент возвращать сведения о продукте, СУБД, например имя СУБД и номер версии:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Сведения об источнике данных  
 Следующие значения *InfoType* аргумент возвращать сведения об источнике данных, таких как характеристики курсора и возможностями выполнения транзакций:  
  
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
 Следующие значения *InfoType* аргумент возвращать сведения об инструкциях SQL, поддерживаемых источником данных. Синтаксис SQL каждого компонента, описываемого этих типов сведений является синтаксис SQL-92. Эти типы сведений тщательное не описывают весь грамматику SQL-92. Вместо этого они описывают те части грамматики для данных источники обычно предлагают разные уровни поддержки. В частности рассматриваются большинство инструкций языка DDL в SQL-92.  
  
 Приложения должны определить общий уровень поддерживаемых грамматики из типа данных SQL_SQL_CONFORMANCE и использовать другие типы сведений для определения отклонения от уровня соответствия указанных стандартов.  
  
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
 Следующие значения *InfoType* аргумент возвращать сведения об ограничениях, применяется для идентификаторов и предложений в инструкции SQL, такие как максимальную длину идентификаторов и максимальное число столбцов в списке выбора. Драйвер или источника данных могут быть наложены ограничения.  
  
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
 Следующие значения *InfoType* аргумент возвращать сведения о скалярных функциях, поддерживаемых источником данных и драйвера. Дополнительные сведения о скалярных функциях см. в разделе [приложении E: Скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Сведения о преобразовании  
 Следующие значения *InfoType* аргумент возвращает список типов данных SQL, к которым источника данных можно преобразовать указанный тип данных SQL с **преобразовать** скалярной функции:  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Добавлены типы сведений для ODBC 3.x  
 Следующие значения *InfoType* аргумент были добавлены для ODBC 3 *.x*:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Типы сведений, любое удобное для ODBC 3.x  
 Следующие значения *InfoType* аргумент были переименованы для ODBC 3 *.x*.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Типы сведений, рекомендуется использовать в ODBC 3.x  
 Следующие значения *InfoType* аргумент стали нерекомендуемыми в ODBC 3 *.x*. ODBC 3 *.x* драйверы должны по-прежнему поддерживает эти типы сведений для обеспечения обратной совместимости с ODBC 2 *.x* приложений. (Дополнительные сведения об этих типах см. в разделе [поддержка SQLGetInfo](../../../odbc/reference/appendixes/sqlgetinfo-support.md) в приложении G: Драйвер рекомендации для обеспечения обратной совместимости.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Описания типов сведений  
 В следующей таблице перечислены в алфавитном порядке каждого типа данных, версию ODBC, в которую было включено и его описание.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Строка символов: «Y», если пользователь может выполнять все процедуры, возвращенный **SQLProcedures**; «N», если возможно, процедуры возвращено, что пользователь не может выполняться.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Строка символов: «Y», если пользователь гарантируется **ВЫБЕРИТЕ** привилегий для всех таблиц, возвращаемых функцией **SQLTables**; «N», если может быть таблиц возвращаются, что пользователь не может получить доступ к.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Возвращает SQLUSMALLINT значение, указывающее максимальное количество активных средах, которые поддерживает драйвер. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление поддержка статистических функций:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **ALTER домена** инструкции, как определено в SQL-92, поддерживаемых источником данных. Уровень с драйвером SQL-92 полный всегда будет возвращать все битовые маски. Возвращаемое значение «0» означает, что **ALTER домена** инструкция не поддерживается.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ограничение домена поддерживается добавление (полная уровень)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter домена > \<предложения по умолчанию домена set > поддерживается (полная уровень)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<предложение определение имя ограничения > поддерживается для именования ограничение для доменов (средний уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<предложения ограничения удаления домена > поддерживается (полная уровень)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter домена > \<предложения по умолчанию для удаления домена > поддерживается (полная уровень)  
  
 Укажите поддерживаемые следующие биты \<атрибутов ограничения > Если \<добавить ограничение домена > поддерживается (SQL_AD_ADD_DOMAIN_CONSTRAINT бита):  
  
 SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (уровень Full) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE SQL_AD_ADD_CONSTRAINT_DEFERRABLE (уровень Full) (уровень Full)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **ALTER TABLE** инструкции, поддерживаемых источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<добавить столбец > предложение поддерживается с помощью средства, чтобы указать параметры сортировки столбца (уровень Full) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<добавить столбец > предложение поддерживается с помощью средства для указания значений столбца по умолчанию (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<добавить столбец > — поддерживается (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<добавить столбец > предложение поддерживается с помощью средства для указания столбца ограничений (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<добавить ограничение таблицы > предложение поддерживается (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > поддерживается для именования ограничения столбцов и таблиц (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<удалением столбца > поддерживается CASCADE (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<изменить столбец > \<предложения по умолчанию для удаления столбца > — поддерживается (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<удалением столбца > поддерживается RESTRICT (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<удалением столбца > поддерживается RESTRICT (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<изменить столбец > \<предложении default для столбца набора > — поддерживается (средний уровень) (ODBC 3.0)  
  
 Следующие биты укажите поддержки \<атрибутов ограничения > Если поддерживается Указание ограничений столбец или таблицу (SQL_AT_ADD_CONSTRAINT бита):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (уровень Full) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 SQLUINTEGER значение, указывающее, если драйвер могут выполнять функции асинхронно на дескриптор соединения.  
  
 SQL_ASYNC_DBC_CAPABLE = драйвер может исполняться асинхронно функции подключения.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = драйверу не удалось выполнить подключение функции асинхронно.  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 SQLUINTEGER значение, указывающее уровень поддержку асинхронных операций в драйвере:  
  
 SQL_AM_CONNECTION = соединение поддерживается уровня асинхронное выполнение. Все дескрипторы инструкций, связанных с дескриптором данного соединения, в асинхронном режиме, либо все находятся в синхронном режиме. Дескриптор инструкции для подключения, не может быть в асинхронном режиме, пока другой дескриптора инструкции относительно одного подключения — в синхронном режиме и наоборот.  
  
 SQL_AM_STATEMENT = поддерживается уровня асинхронное выполнение инструкции. Некоторые дескрипторов инструкций, связанных с дескриптором соединения может быть в асинхронном режиме, хотя другие дескрипторы инструкций по тому же соединению в синхронном режиме.  
  
 SQL_AM_NONE = асинхронный режим не поддерживается.  
  
 SQL_ASYNC_NOTIFICATION  
 SQLUINTEGER значение, указывающее, поддерживает ли драйвер асинхронное уведомление:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** асинхронное выполнение уведомлений, поддерживаемых драйвером.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** асинхронное выполнение уведомлений не поддерживается драйвером.  
  
 Существует две категории ODBC асинхронных операций: уровня асинхронных операций соединения и инструкции уровня асинхронных операций.  Если драйвер возвращает SQL_ASYNC_NOTIFICATION_CAPABLE, он должен поддерживать уведомления для всех интерфейсов API, которые могут выполняться асинхронно.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Подсчитывает SQLUINTEGER битовую маску, которая перечисляет варианты поведения драйвера по отношению к доступности строки. Следующие битовые маски используются вместе с типов данных:  
  
 SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE, суммируются в одну. Если этот бит не задано, количество строк будут доступны для каждой инструкции.  
  
 SQL_BRC_PROCEDURES = количество строк, если, они доступны при выполнении пакета в хранимой процедуре. Если количество строк, они могут выполнить откат вверх или по отдельности способность в зависимости от бита SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = количество строк, если, они доступны при выполнении пакета напрямую путем вызова **SQLExecute** или **SQLExecDirect**. Если количество строк, они могут выполнить откат вверх или по отдельности способность в зависимости от бита SQL_BRC_ROLLED_UP.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление драйверов для пакетов. Следующие битовые маски используются для определения, какой уровень поддерживается:  
  
 SQL_BS_SELECT_EXPLICIT = драйвер поддерживает явные пакетов, которые могут результирующего набора создания инструкций.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = явные пакетов поддерживает драйвер, содержащих инструкции создания количество строк.  
  
 SQL_BS_SELECT_PROC = драйвер поддерживает явные процедуры, которые могут результирующего набора создания инструкций.  
  
 SQL_BS_ROW_COUNT_PROC = драйвер поддерживает явные процедуры, которые могут иметь инструкции создания количество строк.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление операций, выполнении которых закладки сохраняются.  
  
 Следующие битовые маски используются вместе с флагом для определения, через который закладки параметры сохраняются:  
  
 SQL_BP_CLOSE = закладки являются действительными после приложение вызывает **SQLFreeStmt** с параметром SQL_CLOSE или **SQLCloseCursor** для закрытия курсора, связанные с инструкцией.  
  
 SQL_BP_DELETE = закладка для строки является допустимым, после удаления этой строки.  
  
 SQL_BP_DROP = закладки являются действительными после приложение вызывает **SQLFreeHandle** с *HandleType* инструкция drop значение sql_handle_stmt.  
  
 SQL_BP_TRANSACTION = закладки являются действительными после приложение фиксирует или откатывает транзакцию.  
  
 SQL_BP_UPDATE = закладка для строки является допустимым, после любой столбец в этой строке будет обновлен, включая ключевые столбцы.  
  
 SQL_BP_OTHER_HSTMT = закладки, связанные с одной инструкции можно использовать с другим оператором. Если не указан SQL_BP_CLOSE или SQL_BP_DROP, курсор на первой инструкции должен быть открыт.  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 SQLUSMALLINT значение, которое показывает положение каталога в полном имени таблицы:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Например драйвером Xbase возвращает SQL_CL_START, так как имя каталога (каталог) — начало имени таблицы, как и в \EMPDATA\EMP. DBF. Драйвер ORACLE Server возвращает SQL_CL_END, так как каталог находится в конце имени таблицы, как показано на ADMIN.EMP@EMPDATA.  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать SQL_CL_START. Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME (ODBC 3.0)  
 Строка символов: «Y» Если сервер поддерживает имена каталогов, или «N», если это не так.  
  
 В полный SQL-92 уровень совместимого драйвера всегда возвращает «Y».  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 Строка символов: символы, которые определяет источник данных в качестве разделителя имени каталога и полное имя элемента, который следует за или после нее.  
  
 Если каталоги не поддерживаются источником данных, возвращается пустая строка. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения. Всегда будет возвращать полный SQL-92 уровень совместимого драйвера «.».  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 Строка символов, с именем поставщика источника данных для каталога; Например «database» или «каталог». Эта строка может быть в верхней, нижней или смешанный регистр.  
  
 Если каталоги не поддерживаются источником данных, возвращается пустая строка. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения. В полный SQL-92 уровень совместимого драйвера всегда возвращает «каталог».  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление инструкций, в которых используется каталоги.  
  
 Следующие битовые маски используются для определения, где могут использоваться каталоги:  
  
 SQL_CU_DML_STATEMENTS = каталоги поддерживаются во всех инструкциях языка обработки данных: **ВЫБЕРИТЕ**, **вставить**, **обновление**, **удалить**и если поддерживается, **ВЫБЕРИТЕ для обновления** и позиционированного обновления и удаления инструкции.  
  
 SQL_CU_PROCEDURE_INVOCATION = каталоги поддерживаются в операторе вызова процедуры ODBC.  
  
 SQL_CU_TABLE_DEFINITION = каталоги поддерживаются во всех инструкциях определения таблицы: **СОЗДАТЬ ТАБЛИЦУ**, **ПРЕДСТАВЛЕНИЯ СОЗДАНИЯ**, **ALTER TABLE**, **DROP TABLE**, и **DROP VIEW**.  
  
 SQL_CU_INDEX_DEFINITION = каталоги поддерживаются во всех инструкциях определение индекса: **Создание ИНДЕКСА** и **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = каталоги поддерживаются во всех инструкциях определения прав доступа: **Предоставление** и **ОТОЗВАТЬ**.  
  
 Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживается ли каталоги, приложение вызывает **SQLGetInfo** с типом SQL_CATALOG_NAME сведения. В полный SQL-92 уровень совместимого драйвера всегда будет возвращать Битовая маска, со всеми этими установленных битов.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ(ODBC 3.0)  
 Имя параметров сортировки. Это символьная строка, которая указывает имя параметров сортировки по умолчанию для кодировки по умолчанию для этого сервера (например, "ISO 8859-1" и EBCDIC). Если неизвестно, возвращается пустая строка. В полный SQL-92 уровень совместимого драйвера всегда будет возвращать непустой строкой.  
  
 SQL_COLUMN_ALIAS(ODBC 2.0)  
 Строка символов: «Y», если источник данных поддерживает псевдонимы столбцов; в противном случае — «N».  
  
 Псевдоним является альтернативным именем, которое можно указать для столбца в списке выбора с помощью предложения AS. Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать «Y».  
  
 SQL_CONCAT_NULL_BEHAVIOR(ODBC 1.0)  
 SQLUSMALLINT значение, указывающее, как источник данных обрабатывает объединения NULL табличные значения для столбцов типа символьных данных со столбцами типа данных отличное от NULL значениями символов:  
  
 SQL_CB_NULL = результатом будет значение NULL.  
  
 SQL_CB_NON_NULL = результатом является объединение, отличных от NULL значениями столбца или столбцов.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_ DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Битовая маска SQLUINTEGER. Битовая маска указывает преобразования, поддерживаемые источником данных с помощью **преобразовать** скалярной функции для данных типа с именем в *InfoType*. Если битовой маске равен нулю, источник данных не поддерживает любые преобразования данных именованного типа, включая преобразование в тот же тип данных.  
  
 Например, чтобы определить, поддерживает ли источник данных преобразования в тип данных SQL_BIGINT SQL_INTEGER данных, приложение вызывает **SQLGetInfo** с *InfoType* из SQL_CONVERT_INTEGER. Приложение выполняет **AND** операцию с SQL_CVT_BIGINT и возвращаемый битовой маски. Если результирующее значение имеет ненулевое значение, то преобразование поддерживается.  
  
 Следующие битовые маски используются для определения, какие преобразования поддерживаются:  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) (ODBC 1.0) SQL_CVT_BIT SQL_CVT_GUID (ODBC 3.5) (ODBC 1.0) SQL_CVT_CHAR SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL SQL_CVT_ SQL_CVT_TIME (ODBC 1.0) (ODBC 1.0) SQL_CVT_SMALLINT _CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME SQL_CVT_LONGVARBINARY (ODBC 1.0) (ODBC 1.0) SQL_CVT_LONGVARCHAR SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) МЕТКА ВРЕМЕНИ (ODBC 1.0) (ODBC 1.0) SQL_CVT_TINYINT SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS(ODBC 1.0)  
 Битовая маска SQLUINTEGER, перечисление преобразование скалярных функций, поддерживаемых драйвером и связанного источника данных.  
  
 Следующие Битовая маска используется для определения функции преобразования, которые поддерживаются:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 SQLUSMALLINT значение, указывающее, поддерживаются ли корреляционные имена таблиц:  
  
 SQL_CN_NONE = корреляции, имена не поддерживаются.  
  
 SQL_CN_DIFFERENT = корреляции имена поддерживаются, но должно отличаться от имен таблиц, они представляют.  
  
 SQL_CN_ANY = корреляции имена поддерживаются и может быть любое допустимое имя определяемого пользователем.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **создать УТВЕРЖДЕНИЕ** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Следующие биты указать атрибут ограничения, если поддерживается возможность явным образом указать ограничения атрибутов (см. в разделе типы сведений SQL_ALTER_TABLE и SQL_CREATE_TABLE):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Драйвером SQL-92 полный уровень соответствующего стандарту всегда будет возвращать все эти возможности, поддерживаемой. Возвращаемое значение «0» означает, что **создать УТВЕРЖДЕНИЕ** инструкция не поддерживается.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **создать НАБОР символов** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Драйвером SQL-92 полный уровень соответствующего стандарту всегда будет возвращать все эти возможности, поддерживаемой. Возвращаемое значение «0» означает, что **создать НАБОР символов** инструкция не поддерживается.  
  
 SQL_CREATE_COLLATION (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **создать параметры СОРТИРОВКИ** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие Битовая маска используется для определения, какие предложения поддерживаются:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать этот параметр поддерживается. Возвращаемое значение «0» означает, что **создать параметры СОРТИРОВКИ** инструкция не поддерживается.  
  
 SQL_CREATE_DOMAIN(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **создание домена** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CDO_CREATE_DOMAIN = создание домена поддерживается оператор (промежуточный уровень).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > поддерживается для именования ограничений для доменов (средний уровень).  
  
 Следующие биты указать возможность создания столбца ограничений: SQL_CDO_DEFAULT = Указание ограничений для доменов поддерживается (промежуточный уровень) SQL_CDO_CONSTRAINT = Указание значения по умолчанию домена поддерживается (промежуточный уровень) SQL_CDO_COLLATION = Указание параметров сортировки домена поддерживается (полная уровень)  
  
 Следующие биты указать атрибуты ограничения, если поддерживается Указание ограничений для доменов (SQL_CDO_DEFAULT имеет значение):  
  
 SQL_CDO_CONSTRAINT_NON_DEFERRABLE SQL_CDO_CONSTRAINT_DEFERRABLE (уровень Full) (уровень Full) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (уровень Full)  
  
 Возвращаемое значение «0» означает, что **создание домена** инструкция не поддерживается.  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **CREATE SCHEMA** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 SQL-92 промежуточного уровня совместимого драйвера всегда будет возвращать параметры SQL_CS_CREATE_SCHEMA и SQL_CS_AUTHORIZATION, так как поддерживается. Они также должны поддерживаться, на уровне записи SQL-92, но не обязательно, как инструкции SQL. Драйвером SQL-92 полный уровень соответствующего стандарту всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **CREATE TABLE** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CT_CREATE_TABLE = CREATE TABLE поддерживается оператор. (Начальный уровень)  
  
 SQL_CT_TABLE_CONSTRAINT = поддерживается Указание ограничения таблицы (FIPS Transitional уровень)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > предложение поддерживается для именования ограничения столбцов и таблиц (средний уровень)  
  
 Следующие биты указать возможность создания временных таблиц:  
  
 SQL_CT_COMMIT_PRESERVE = Deleted строк сохраняются при фиксации. (Полный уровень) SQL_CT_COMMIT_DELETE = удаленные строки удаляются при фиксации. (Полный уровень) SQL_CT_GLOBAL_TEMPORARY = глобальные временные таблицы можно создать. (Полный уровень) SQL_CT_LOCAL_TEMPORARY = Local временные таблицы можно создать. (Полный уровень)  
  
 Следующие биты указать возможность создания ограничения столбца:  
  
 SQL_CT_COLUMN_CONSTRAINT = поддерживается Указание ограничения столбца (FIPS Transitional уровень) SQL_CT_COLUMN_DEFAULT = указание значений столбца по умолчанию поддерживается (FIPS Transitional уровень) SQL_CT_COLUMN_COLLATION = Указание параметров сортировки столбца поддерживается (уровень Full)  
  
 Следующие биты указать атрибуты ограничения, если поддерживается Указание ограничений столбца или таблицы:  
  
 SQL_CT_CONSTRAINT_NON_DEFERRABLE SQL_CT_CONSTRAINT_DEFERRABLE (уровень Full) (уровень Full) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (уровень Full)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **создать перевод** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие Битовая маска используется для определения, какие предложения поддерживаются:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать эти параметры, как поддерживаются. Возвращаемое значение «0» означает, что **создать перевод** инструкция не поддерживается.  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **CREATE VIEW** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Возвращаемое значение «0» означает, что **CREATE VIEW** инструкция не поддерживается.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать параметры SQL_CV_CREATE_VIEW и SQL_CV_CHECK_OPTION, так как поддерживается.  
  
 Драйвером SQL-92 полный уровень соответствующего стандарту всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 Значение, указывающее SQLUSMALLINT как **ФИКСАЦИИ** операция затрагивает курсоры и подготовленные инструкции в источнике данных (поведение источника данных при фиксации транзакции).  
  
 Значение этого атрибута будет отражать текущее состояние следующий параметр: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = закрыть курсоров и удаление подготовленных инструкций. Опять же, чтобы использовать курсор приложение должно reprepare и был повторно исполнить инструкцию.  
  
 SQL_CB_CLOSE = закрыть курсоров. Для подготовленных инструкций, приложение может вызвать **SQLExecute** в операторе без вызова **SQLPrepare** еще раз. Значение по умолчанию для драйвера SQL ODBC — SQL_CB_CLOSE. Это означает, что драйвер SQL ODBC закроет вашей курсоры при фиксации транзакции.  
  
 SQL_CB_PRESERVE = Preserve курсоры в той же позиции, как и раньше **ЗАФИКСИРОВАТЬ** операции. Приложение может продолжать получать данные, или его можно закрыть курсор и повторно выполните инструкцию без подготовки его повторно.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 Значение, указывающее SQLUSMALLINT как **ОТКАТА** операция затрагивает курсоры и подготовленные инструкции в источнике данных:  
  
 SQL_CB_DELETE = закрыть курсоров и удаление подготовленных инструкций. Опять же, чтобы использовать курсор приложение должно reprepare и был повторно исполнить инструкцию.  
  
 SQL_CB_CLOSE = закрыть курсоров. Для подготовленных инструкций, приложение может вызвать **SQLExecute** в операторе без вызова **SQLPrepare** еще раз.  
  
 SQL_CB_PRESERVE = Preserve курсоры в той же позиции, как и раньше **ОТКАТА** операции. Приложение может продолжать получать данные, или его можно закрыть курсор и был повторно исполнить инструкцию без repreparing его.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 Значение SQLUINTEGER, который указывает на поддержку чувствительности курсора:  
  
 SQL_INSENSITIVE = все курсоры шоу дескриптор инструкции, результирующий набор не отражает все изменения, внесенные с другим курсором в той же транзакции.  
  
 SQL_UNSPECIFIED = не указано ли курсоры для дескриптора инструкции отобразить изменения, внесенные в результирующий набор с другим курсором в той же транзакции. Курсоры для дескриптора инструкции может сделать видимыми none, некоторые или все такие изменения.  
  
 SQL_SENSITIVE = курсоры чувствительные к изменениям, сделанных другими курсорами в той же транзакции.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать параметр SQL_UNSPECIFIED, так как поддерживается.  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать параметр SQL_INSENSITIVE, как поддерживаются.  
  
 SQL_DATA_SOURCE_NAME(ODBC 1.0)  
 Строка символов, с именем источника данных, который использовался во время соединения. Если приложение вызвало **SQLConnect**, это значение *szDSN* аргумент. Если приложение вызвало **SQLDriverConnect** или **SQLBrowseConnect**, это значение ключевого слова DSN в строке подключения, переданной в драйвер. Если строка подключения не содержал **DSN** ключевое слово (например, когда он содержит **ДРАЙВЕР** ключевое слово), это является пустой строкой.  
  
 SQL_DATA_SOURCE_READ_ONLY(ODBC 1.0)  
 Строка символов. «Y», если источник данных устанавливается в режим только для чтения, «N», если он имеет в противном случае.  
  
 Эта особенность относится только к источнику данных Это не характеристика драйвера, который обеспечивает доступ к источнику данных. Драйвер, чтение и запись может использоваться с источником данных, доступный только для чтения. Если драйвер доступен только для чтения, все его источники данных должны быть доступны только для чтения и должен возвращать SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME(ODBC 1.0)  
 Символ строка с именем текущей базы данных используется, если источник данных определяет именованный объект, называемый «database».  
  
> [!NOTE]
>  В ODBC 3 *.x*, возвращаемое значение для данного *InfoType* также может быть получен путем вызова **SQLGetConnectAttr** с *атрибут* Аргумент SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление литералами даты и времени SQL-92, поддерживаемых источником данных. Обратите внимание на то, что они являются литералами даты и времени, перечисленные в спецификации SQL-92 они отделены от datetime литерала escape предложения определенном ODBC. Дополнительные сведения о предложениях литерала escape ODBC datetime см. в разделе [Timestamp литералы даты, времени и](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Переходные FIPS уровень совместимого драйвера всегда возвращает значение «1» в Битовая маска для битов в следующем списке. Значение «0» означает, что литералами даты и времени SQL-92 не поддерживаются.  
  
 Следующие битовые маски используются для определения, какие литералы поддерживаются:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_ SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME(ODBC 1.0)  
 Строка символов, с именем продукта СУБД, доступ к драйверу.  
  
 SQL_DBMS_VER(ODBC 1.0)  
 Строка, указывающее, версия продукта СУБД, доступ к драйверу. Версия имеет вид ##. ##. ###, где первые две цифры являются основной номер версии, следующие две цифры — дополнительный номер версии, а последние четыре цифры — номер редакции. Драйвер должен представлять версия продукта СУБД в этой форме, но можно также добавить версию конкретного продукта СУБД. Например «04.01.0000 Rdb 4.1».  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 Значение типа SQLUINTEGER, указывает на поддержку создания и удаления индексов:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION(ODBC 1.0)  
 Значение SQLUINTEGER, которое указывает, что уровень изоляции транзакций по умолчанию поддерживает драйвер или источник данных, или нуль, если источник данных не поддерживает транзакции. Чтобы определить уровни изоляции транзакций используются следующие термины:  
  
 **"Грязных" чтения** 1 транзакция изменяет строку. Транзакция 2 считывает измененной строки, прежде чем транзакция 1 фиксирует изменение. Если транзакция 1 откат изменений, транзакция 2 будет считывать строки, которая считается никогда не существовавшими.  
  
 **Неповторяющееся чтение** 1 транзакция считывает строки. Транзакция 2 обновляет или удаляет эту строку и фиксирует эти изменения. Если транзакция 1 пытается считать заново строки, он будет получать значения различных строк или обнаружить, что строка была удалена.  
  
 **Количество затронутых фантомных** 1 транзакция считывает набор строк, отвечающих некоторым критериям поиска. Транзакция 2 создает одну или несколько строк (с помощью операции вставки или обновления), соответствующие критериям поиска. Если транзакция 1 reexecutes инструкцию, которая считывает строки, он получает другой набор строк.  
  
 Если источник данных поддерживает транзакции, драйвер возвращает одно из следующих битовой маски:  
  
 Значениями SQL_TXN_READ_UNCOMMITTED = Dirty возможны операции чтения, неповторяющееся чтение и появляться фантомы.  
  
 SQL_TXN_READ_COMMITTED = Dirty операций чтения невозможны. Возможны неповторяющееся чтение и появляться фантомы.  
  
 SQL_TXN_REPEATABLE_READ = Dirty операции чтения и будет неповторяемое считывание невозможны. Возможны и появляться фантомы.  
  
 SQL_TXN_SERIALIZABLE = транзакции являются сериализуемыми. Сериализуемые транзакции не разрешать грязных, чего будет неповторяемое чтение или фантомные объекты.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 Строка символов: «Y», если можно описать параметры; «N», если это не так.  
  
 Полный SQL-92 драйвер уровень соответствующего стандарту обычно вернет «Y», так как он будет поддерживать **входные данные, ОПИСЫВАЮЩИЕ** инструкции. Так как это не соответствует непосредственно базовой поддержки SQL, тем не менее, описывающие параметры могут не поддерживаться, даже в полный SQL-92 уровень совместимого драйвера.  
  
 SQL_DM_VER(ODBC 3.0)  
 Строка символов, с помощью версии диспетчера драйверов. Версия имеет вид ##. ##. ###. ###, где:  
  
 Первый набор из двух цифр, — это основной номер версии ODBC, как задано постоянное SQL_SPEC_MAJOR.  
  
 Второй набор из двух цифр, — это дополнительный номер версии ODBC, как задано постоянное SQL_SPEC_MINOR.  
  
 Третий набор из четырех цифр — номер сборки основной диспетчер драйверов.  
  
 Последний набор из четырех цифр является диспетчер драйверов дополнительного номера построения.  
  
 Версия диспетчера драйверов Windows 7 — 03.80. Версия диспетчера драйверов Windows 8 — 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 SQLUINTEGER значение, указывающее, если драйвер поддерживает драйвер с поддержкой пулов. (Дополнительные сведения см. в разделе [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE указывает, что драйвер поддерживает драйвер с поддержкой механизм регулирования количества запросов.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE указывает, что драйвер не поддерживает драйвер с поддержкой механизм регулирования количества запросов.  
  
 Драйвер не нужно реализовать SQL_DRIVER_AWARE_POOLING_SUPPORTED и диспетчера драйверов, не будут учитывать к возвращаемому значению драйвера.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 SQLULEN значение, драйвер дескриптора среды или дескриптора соединения, определяется аргументом *InfoType*.  
  
 Эти типы сведений, реализуются диспетчером драйверов отдельно.  
  
 SQL_DRIVER_HDESC(ODBC 3.0)  
 Значение SQLULEN, определяется дескриптора для диспетчера драйверов, который должен быть передан на входе в драйвер дескриптора \* *InfoValuePtr* из приложения. В этом случае *InfoValuePtr* является входных и выходных аргументом. Входного дескриптора переданной \* *InfoValuePtr* должен быть явно или неявно выделен на *ConnectionHandle*.  
  
 Приложение следует создать копию дескриптора диспетчера драйверов обработать перед вызовом **SQLGetInfo** с этим типом сведения, чтобы убедиться в том, что дескриптор не перезаписывается на выходе.  
  
 Этот тип реализуется диспетчером драйверов отдельно.  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 Значение SQLULEN *hinst* из библиотеки нагрузки возвращены диспетчеру драйверов при его загрузке библиотека DLL драйвера в операционной системе Microsoft Windows, или его эквивалент в другой операционной системе. Дескриптор допустим только для дескриптора соединения, указанный в вызове **SQLGetInfo**.  
  
 Этот тип реализуется диспетчером драйверов отдельно.  
  
 SQL_DRIVER_HSTMT(ODBC 1.0)  
 Значение SQLULEN драйвера дескриптора инструкции, определяется дескриптора инструкции диспетчера драйверов, который должен быть передан на входе в \* *InfoValuePtr* из приложения. В этом случае *InfoValuePtr* входной и выходной аргумент. Переданный дескриптор ввода инструкции \* *InfoValuePtr* должен быть выделен в аргументе *ConnectionHandle*.  
  
 Приложение следует создать копию диспетчера драйверов инструкции обработать перед вызовом **SQLGetInfo** с этим типом сведения, чтобы убедиться, что дескриптор не перезаписывается на выходе.  
  
 Этот тип реализуется диспетчером драйверов отдельно.  
  
 SQL_DRIVER_NAME(ODBC 1.0)  
 Строка с именем файла драйвера, используемого для доступа к источнику данных.  
  
 SQL_DRIVER_ODBC_VER(ODBC 2.0)  
 Строка символов, с помощью версии ODBC, который поддерживает драйвер. Версия имеет вид ##. ##, где первые две цифры являются основной номер версии, а две следующие — дополнительный номер версии. SQL_SPEC_MAJOR и SQL_SPEC_MINOR определяют основной и дополнительный номера версии. Для версии ODBC, описанные в данном руководстве это 3 и 0, а драйвер должен возвращать «03.00».  
  
 Диспетчер драйверов ODBC не будет изменять возвращаемое значение SQLGetInfo(SQL_DRIVER_ODBC_VER), чтобы обеспечить обратную совместимость для существующих приложений. Драйвер определяет, какое значение будет возвращаться. Тем не менее драйвер, который поддерживает возможность расширения типа данных C должен возвращать 3,8 (или более поздней версии) когда приложение вызывает **SQLSetEnvAttr** присвоено значение SQL_ATTR_ODBC_VERSION 3.8. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 Строка символов, с помощью версии драйвера и при необходимости Описание драйвера. Как минимум, версии имеет вид ##. ##. ###, где первые две цифры являются основной номер версии, следующие две цифры — дополнительный номер версии, а последние четыре цифры — номер редакции.  
  
 SQL_DROP_ASSERTION(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **удалить УТВЕРЖДЕНИЕ** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие Битовая маска используется для определения, какие предложения поддерживаются:  
  
 SQL_DA_DROP_ASSERTION  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_CHARACTER_SET(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **DROP КОДИРОВКА** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие Битовая маска используется для определения, какие предложения поддерживаются:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_COLLATION(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **удалить параметры СОРТИРОВКИ** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие Битовая маска используется для определения, какие предложения поддерживаются:  
  
 SQL_DC_DROP_COLLATION  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_DOMAIN(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **DROP домена** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 SQL-92 промежуточного уровня совместимого драйвера всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **DROP SCHEMA** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 SQL-92 промежуточного уровня совместимого драйвера всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_DROP_TABLE(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **DROP TABLE** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Драйвером уровень соответствующего стандарту FIPS Transitional всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_DROP_TRANSLATION(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **DROP ПЕРЕВОДА** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие Битовая маска используется для определения, какие предложения поддерживаются:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 В полный SQL-92 уровень совместимого драйвера всегда будет возвращать этот параметр поддерживается.  
  
 SQL_DROP_VIEW(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **DROP VIEW** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Драйвером уровень соответствующего стандарту FIPS Transitional всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Маска SQLUINTEGER, которая описывает атрибуты динамического курсора, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножество атрибутов; второй подмножество см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXT = A *FetchOrientation* аргумент для SQL_FETCH_NEXT поддерживается в вызове **SQLFetchScroll** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* аргументы SQL_FETCH_FIRST, SQL_FETCH_LAST и SQL_FETCH_ABSOLUTE поддерживаются при вызове **SQLFetchScroll** когда курсор наведен курсор dynamic. (Набор строк, полученных в результате не зависит от текущей позиции курсора.)  
  
 SQL_CA1_RELATIVE = *FetchOrientation* аргументы SQL_FETCH_PRIOR и SQL_FETCH_RELATIVE поддерживаются при вызове **SQLFetchScroll** когда курсор наведен курсор dynamic. (Набор строк, полученных в результате зависит от текущей позиции курсора. Обратите внимание, что это отделяется от SQL_FETCH_NEXT, так как в однопроходный курсор, поддерживается только SQL_FETCH_NEXT.)  
  
 SQL_CA1_BOOKMARK = A *FetchOrientation* аргумент инструкция SQL_FETCH_BOOKMARK поддерживается в вызове **SQLFetchScroll** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_LOCK_EXCLUSIVE = A *LockType* аргумент SQL_LOCK_EXCLUSIVE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_LOCK_NO_CHANGE = A *LockType* аргумент SQL_LOCK_NO_CHANGE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_LOCK_UNLOCK = A *LockType* аргумент SQL_LOCK_UNLOCK поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_POSITION = *операции* аргумент SQL_POSITION поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_UPDATE = *операции* аргумент SQL_UPDATE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_DELETE = *операции* аргумент SQL_DELETE поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POS_REFRESH = *операции* аргумент SQL_REFRESH поддерживается в вызове **SQLSetPos** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_POSITIONED_UPDATE = UPDATE ГДЕ ТЕКУЩЕГО SQL инструкция поддерживается в том случае, когда курсор наведен курсор dynamic. (Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать этот параметр поддерживается.)  
  
 SQL_CA1_POSITIONED_DELETE = удаление ГДЕ ТЕКУЩЕГО SQL инструкция поддерживается в том случае, когда курсор наведен курсор dynamic. (Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать этот параметр поддерживается.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = SELECT для инструкции UPDATE SQL поддерживается в том случае, когда курсор наведен курсор dynamic. (Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать этот параметр поддерживается.)  
  
 SQL_CA1_BULK_ADD = *операции* аргумент SQL_ADD поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = *операции* аргумент SQL_UPDATE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = *операции* аргумент SQL_DELETE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = *операции* аргумент SQL_FETCH_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** когда курсор наведен курсор dynamic.  
  
 SQL-92 промежуточного уровня совместимого драйвера обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE поддерживается, так как он поддерживает прокручиваемые курсоры через внедренный оператор SQL FETCH. Так как это не определить непосредственно базовой поддержки SQL, тем не менее, Прокручиваемые курсоры могут не поддерживаться, даже для SQL-92 промежуточного уровня совместимого драйвера.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Маска SQLUINTEGER, которая описывает атрибуты динамического курсора, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножество атрибутов; Первый набор см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = только для чтения поддерживается динамический курсор, в которой обновления не разрешены,. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_READ_ONLY для динамического курсора).  
  
 SQL_CA2_LOCK_CONCURRENCY = динамический курсор, который использует самый низкий уровень блокировки достаточно, чтобы убедиться, что строки могут обновляться поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_LOCK к динамическому курсору.) Эти блокировки должны быть согласованы с уровнем изоляции транзакций, задается атрибут соединения SQL_ATTR_TXN_ISOLATION.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = динамический курсор, поддерживаются ли использует элемент управления оптимистичного параллелизма, сравнение версий строк. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_ROWVER к динамическому курсору.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = динамический курсор, поддерживаются ли использует сравнение значения элемента управления оптимистичного параллелизма. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_VALUES к динамическому курсору.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = Added строк являются видимыми для динамического курсора; курсор можно перейти к эти строки. (Где они добавляются к курсору зависит от драйвера.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = Deleted строк больше не доступны для динамический курсор, а не оставляйте «путь» в результирующем наборе; После динамический курсор прокручивает из удаленной строки, он не может возвращать для этой строки.  
  
 SQL_CA2_SENSITIVITY_UPDATES = обновления строк являются видимыми для динамического курсора; Если динамический курсор прокручивается и возвращает обновленную строку, данные, возвращенные курсором, обновленные данные, а не исходные данные.  
  
 SQL_CA2_MAX_ROWS_SELECT = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **ВЫБЕРИТЕ** инструкций, когда курсор наведен курсор dynamic.  
  
 SQL_CA2_MAX_ROWS_INSERT = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **вставить** инструкций, когда курсор наведен курсор dynamic.  
  
 SQL_CA2_MAX_ROWS_DELETE = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **удалить** инструкций, когда курсор наведен курсор dynamic.  
  
 SQL_CA2_MAX_ROWS_UPDATE = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **обновления** инструкций, когда курсор наведен курсор dynamic.  
  
 SQL_CA2_MAX_ROWS_CATALOG = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **КАТАЛОГА** результирующие наборы, когда курсор наведен курсор dynamic.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = влияет на атрибут инструкции SQL_ATTR_MAX_ROWS **ВЫБЕРИТЕ**, **вставить**, **удалить**, и **обновления** инструкции, и **КАТАЛОГА** результирующие наборы, в том случае, когда курсор наведен курсор dynamic.  
  
 SQL_CA2_CRC_EXACT = точное число строк доступно в диагностическое поле SQL_DIAG_CURSOR_ROW_COUNT курсор динамический курсор.  
  
 SQL_CA2_CRC_APPROXIMATE = приблизительное число строк доступно в диагностическое поле SQL_DIAG_CURSOR_ROW_COUNT курсор динамический курсор.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = драйвер не гарантирует, что simulated расположен обновления или инструкций delete повлияет только одну строку, когда курсор находится динамический курсор; приложения отвечает этого гарантировать. (Если инструкция влияет на более чем одной строке **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операции с курсором].) Чтобы задать такое поведение, приложение вызывает **SQLSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибут SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = драйвер пытается гарантировать, что имитации позиционированного обновления и удаления в повлияют только одну строку при прохождении курсора динамический курсор. Драйвер всегда такие операторы выполняются, даже если они могут повлиять на более чем одной строке, например, когда отсутствует уникальный ключ. (Если инструкция влияет на более чем одной строке **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операции с курсором].) Чтобы задать такое поведение, приложение вызывает **SQLSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибут SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE = драйвер гарантирует, что simulated расположен обновления или инструкций delete повлияет только одну строку, когда курсор наведен курсор dynamic. Если драйвер не может гарантировать это для данной инструкции, **SQLExecDirect** или **SQLPrepare** возвращают SQLSTATE 01001 (конфликт операции с курсором). Чтобы задать такое поведение, приложение вызывает **SQLSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибут SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY(ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает выражения в **ORDER BY** список; «N», если это не так.  
  
 SQL_FILE_USAGE(ODBC 2.0)  
 SQLUSMALLINT значение, указывающее, как драйвер одноуровневых напрямую обрабатывает файлы в источнике данных:  
  
 SQL_FILE_NOT_SUPPORTED = драйвер не является драйвером среднего уровня. Например драйвер ORACLE — это двухуровневая драйвер.  
  
 SQL_FILE_TABLE = файлы рассматривает одноуровневых драйвера в источнике данных как таблицы. Например драйвером Xbase считает каждый файл Xbase таблицы.  
  
 SQL_FILE_CATALOG = одноуровневых рассматривает драйверы в качестве каталога источника данных. Например драйвером Microsoft Access обрабатывает каждый файл Microsoft Access как всей базы данных.  
  
 Приложение может использовать это, чтобы определить, каким образом пользователи будут выбирать данные. Например Xbase пользователи часто прибегают к данных, хранящиеся в файлах, в то время как ORACLE и Microsoft Access пользователи обычно думают о данных, хранящихся в таблицах.  
  
 Когда пользователь выбирает источник данных Xbase, приложение может отобразить Windows **Открытие файла** общее диалоговое окно, когда пользователь выбирает источник данных Microsoft Access или ORACLE, приложение может отобразить пользовательский  **Выберите таблицу** диалоговое окно.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора последовательного доступа, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножество атрибутов; второй подмножество см. в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_ UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описание этих битовой маски см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и замените «однопроходный курсор» для «динамический курсор», в соответствии с описанием).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора последовательного доступа, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножество атрибутов; Первый набор см. в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Описание этих битовой маски см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и замените «однопроходный курсор» для «динамический курсор», в соответствии с описанием).  
  
 SQL_GETDATA_EXTENSIONS(ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление расширений для **SQLGetData**.  
  
 Следующие битовые маски используются вместе с флаг, чтобы определить, какие модули драйвер поддерживает для **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** может вызываться для любой несвязанного столбца, в том числе до последнего связанного столбца. Обратите внимание на то, что столбцы должны вызываться в порядке по возрастанию номера столбца, если SQL_GD_ANY_ORDER также возвращается.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** может вызываться для несвязанных столбцов в любом порядке. Обратите внимание, что **SQLGetData** может быть вызван только для столбцов после последнего привязанного столбца, если не SQL_GD_ANY_COLUMN также возвращается.  
  
 SQL_GD_BLOCK = **SQLGetData** можно вызывать для несвязанного столбца в любую строку в блок данных (где размер набора строк больше, чем 1) после размещения для этой строки с **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** может вызываться для привязанных столбцов в дополнение к несвязанных столбцов. Драйвер не может возвращать это значение, если он также возвращает SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** может вызываться для возврата значения выходных параметров. Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** должна возвращать данные только непривязанные столбцы, которые произошли после последнего привязанного столбца, вызываются в порядке возрастания номеров столбцов, а не в строку в блоке строк.  
  
 Если драйвер поддерживает закладки (фиксированной или переменной длины), он должен поддерживать вызова **SQLGetData** на столбец 0. Эта поддержка является обязательным, независимо от того, что драйвер возвращает для вызова **SQLGetInfo** с SQL_GETDATA_EXTENSIONS *InfoType*.  
  
 SQL_GROUP_BY(ODBC 2.0)  
 Значение типа SQLUSMALLINT, определяет связь между столбцами в **GROUP BY** предложение и неагрегированными столбцами в списке выбора:  
  
 SQL_GB_COLLATE = A **COLLATE** предложение может быть указано в конце каждого столбца группирования. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY** предложения не поддерживаются. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = **GROUP BY** предложение должно содержать все неагрегированные столбцы в списке выбора. Он не может содержать другие столбцы. Например **DEPT BY Выбор DEPT, MAX(SALARY) из СОТРУДНИКОВ группы**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = **GROUP BY** предложение должно содержать все неагрегированные столбцы в списке выбора. Оно может содержать столбцы, которых нет в списке выбора. Например **DEPT BY Выбор DEPT, MAX(SALARY) из СОТРУДНИКОВ группы, ВОЗРАСТ**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = столбцы в **GROUP BY** предложения и список выбора не связаны. Зависит от источника данных имеет значение nongrouped, неагрегированные столбцы в списке выбора. Например **DEPT BY Выбор DEPT, Зарплата из СОТРУДНИКОВ группы, ВОЗРАСТ**. (ODBC 2.0)  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать параметр SQL_GB_GROUP_BY_EQUALS_SELECT, так как поддерживается. В полный SQL-92 уровень совместимого драйвера всегда будет возвращать параметр SQL_GB_COLLATE поддерживается. Если ни один из вариантов поддерживается, **GROUP BY** предложение не поддерживается источником данных.  
  
 SQL_IDENTIFIER_CASE(ODBC 1.0)  
 SQLUSMALLINT значение следующим образом:  
  
 SQL_IC_UPPER = идентификаторов в SQL, регистр не учитывается и хранятся в верхнем регистре в системном каталоге.  
  
 SQL_IC_LOWER = идентификаторов в SQL, регистр не учитывается и хранятся в нижнем регистре в системном каталоге.  
  
 Sql_ic_mixed, имеющим = чувствительны к регистру идентификаторов в SQL и хранятся в смешанном регистре, в системном каталоге.  
  
 Sql_ic_mixed, имеющим = идентификаторов в SQL, регистр не учитывается и хранятся в смешанном регистре, в системном каталоге.  
  
 Так как идентификаторы в SQL-92 никогда не учитывается регистр, драйвер, который соответствует строго SQL-92 (любой уровень) никогда не будет возвращать параметр sql_ic_mixed, имеющим, пока поддерживается.  
  
 SQL_IDENTIFIER_QUOTE_CHAR(ODBC 1.0)  
 Символьная строка, используемый в качестве начальный и конечный разделитель в кавычках (идентификатор с разделителем) в инструкциях SQL. (Идентификаторы передаются как аргументы функции ODBC не должны быть заключены в кавычки.) Если источник данных не поддерживает заключенные в кавычки идентификаторы, возвращается пустое значение.  
  
 Данная строка символов также может использоваться для заключения в кавычки аргументы функции каталога, если атрибут соединения SQL_ATTR_METADATA_ID имеет значение SQL_TRUE.  
  
 Так как символ кавычки идентификатор в SQL-92 двойных кавычек ("«), драйвер, который соответствует строго SQL-92 всегда будет возвращать символ двойной кавычки.  
  
 SQL_INDEX_KEYWORDS(ODBC 3.0)  
 Маска SQLUINTEGER, которая перечисляет ключевые слова в инструкции CREATE INDEX, которые поддерживаются драйвером:  
  
 SQL_IK_NONE = поддерживается ни один из ключевых слов.  
  
 SQL_IK_ASC = ASC поддерживается ключевое слово.  
  
 SQL_IK_DESC = DESC поддерживается ключевое слово.  
  
 SQL_IK_ALL = All поддерживаются ключевые слова.  
  
 Чтобы узнать, поддерживается ли в инструкции CREATE INDEX, приложение вызывает **SQLGetInfo** с типом SQL_DLL_INDEX сведения.  
  
 SQL_INFO_SCHEMA_VIEWS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление представления INFORMATION_SCHEMA, которые поддерживаются драйвером. Представления и содержимое, INFORMATION_SCHEMA, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие представления поддерживаются:  
  
 SQL_ISV_ASSERTIONS = идентифицирует утверждения каталога, принадлежащие данному пользователю. (Полный уровень)  
  
 SQL_ISV_CHARACTER_SETS = идентифицирует каталога кодировки, который доступен указанному пользователю. (Средний уровень)  
  
 SQL_ISV_CHECK_CONSTRAINTS = идентифицирует проверки ограничений, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_COLLATIONS = идентифицирует параметров сортировки символов для каталога, который доступен указанному пользователю. (Полный уровень)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = идентифицирует столбцы для каталога, которые зависят от домены, определенные в каталоге и принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_COLUMN_PRIVILEGES = определяет права доступа к столбцам из постоянных таблиц, доступных или предоставлены данным пользователем. (FIPS Transitional уровень)  
  
 SQL_ISV_COLUMNS = идентифицирует столбцы постоянных таблиц, доступных данному пользователю. (FIPS Transitional уровень)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = аналогично представлению CONSTRAINT_TABLE_USAGE, столбцы можно идентифицировать для различных ограничений, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = указывает таблицы, используемые ограничения (ссылочной, unique и утверждения) и которые принадлежат данному пользователю. (Средний уровень)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = указывает ограничения домена (из доменов в каталоге), доступных данному пользователю. (Средний уровень)  
  
 SQL_ISV_DOMAINS = идентифицирует домены, определенные в каталоге, который может осуществляться пользователем. (Средний уровень)  
  
 SQL_ISV_KEY_COLUMN_USAGE = идентифицирует столбцы, определенные в каталоге, которые являются ограниченными как ключи данным пользователем. (Средний уровень)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = указывает ссылочные ограничения, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_SCHEMATA = указывает схемы, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_SQL_LANGUAGES = идентифицирует уровни соответствия SQL, параметры и диалекты, поддерживаемые реализацией SQL. (Средний уровень)  
  
 SQL_ISV_TABLE_CONSTRAINTS = указывает ограничения таблицы, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_TABLE_PRIVILEGES = указывает права доступа к постоянных таблиц, доступных или предоставлены данным пользователем. (FIPS Transitional уровень)  
  
 SQL_ISV_TABLES = идентифицирует хранимых таблиц, определенные в каталоге, который может осуществляться по данному пользователю. (FIPS Transitional уровень)  
  
 SQL_ISV_TRANSLATIONS = идентифицирует преобразования символов для каталога, который доступен указанному пользователю. (Полный уровень)  
  
 SQL_ISV_USAGE_PRIVILEGES = идентифицирует использования привилегии на объектах каталога, которые доступны или принадлежит указанному пользователю. (FIPS Transitional уровень)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = идентифицирует столбцы, на которых представления каталога, которые принадлежат данному пользователю зависят. (Средний уровень)  
  
 SQL_ISV_VIEW_TABLE_USAGE = идентифицирует таблиц, на которых представления каталога, которые принадлежат данному пользователю зависят. (Средний уровень)  
  
 SQL_ISV_VIEWS = идентифицирует, рассматриваемые таблицы, определенные в этом каталоге, который доступен указанному пользователю. (FIPS Transitional уровень)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 SQLUINTEGER битовую маску, которая указывает на поддержку **вставить** инструкции:  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_INTEGRITY(ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает расширенный контроль целостности; «N», если это не так.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора набора ключей, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножество атрибутов; второй подмножество см. в разделе SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описание этих битовой маски см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и замените «курсоры» для «динамический курсор», в соответствии с описанием).  
  
 SQL-92 промежуточного уровня совместимого драйвера обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE поддерживается, так как драйвер поддерживает прокручиваемые курсоры через внедренный оператор SQL FETCH. Так как это не определить непосредственно базовой поддержки SQL, тем не менее, Прокручиваемые курсоры могут не поддерживаться, даже для SQL-92 промежуточного уровня совместимого драйвера.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Битовая маска SQLUINTEGER, описывающий атрибуты курсора набора ключей, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножество атрибутов; Первый набор см. в разделе SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Описание этих битовой маски см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и замените «курсоры» для «динамический курсор», в соответствии с описанием).  
  
 SQL_KEYWORDS(ODBC 2.0)  
 Строка символов, содержащий список с разделителями запятыми всех ключевых слов, зависящие от источника данных. Этот список не содержит ключевые слова, относящиеся к ODBC или ключевые слова, используемые ODBC и источника данных. Этот список представляет все зарезервированные ключевые слова; взаимодействующие приложения, не следует использовать эти слова в именах объектов.  
  
 Список ключевых слов ODBC, см. в разделе [зарезервированные ключевые слова](../../../odbc/reference/appendixes/reserved-keywords.md) в [приложение в: Грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). **#Define** значение SQL_ODBC_KEYWORDS содержит разделенный запятыми список ключевых слов ODBC.  
  
 Приложение В. Грамматика SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE(ODBC 2.0)  
 Строка символов: «Y», если источник данных поддерживает escape-символа для символ процента (%) и символу подчеркивания (_) в **как** предиката и драйвер поддерживает синтаксис ODBC при определении **как** предиката escape-символ; «N» в противном случае.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS(ODBC 3.0)  
 Значение SQLUINTEGER, которое указывает максимальное число активных параллельных инструкций в асинхронном режиме, драйвер может поддерживать для данного соединения. Если нет определенного ограничения или число неизвестно, это значение равно нулю.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 Возвращает значение SQLUINTEGER, указывающее максимальную длину (число шестнадцатеричных символов, за исключением литерала префикс и суффикс, возвращенный **SQLGetTypeInfo**) из двоичный литерал в инструкции SQL. Например литерал 0xFFAA двоичный файл имеет длину 4. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени каталога в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 Возвращает по крайней мере 128 драйвером уровень соответствующего стандарту FIPS полный.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 Возвращает значение SQLUINTEGER, указывающее максимальную длину (число символов, за исключением литерала префикс и суффикс, возвращенный **SQLGetTypeInfo**) из символьных литералов в инструкции SQL. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 SQL_MAX_COLUMN_NAME_LEN(ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени столбца в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 Драйвером уровень соответствующего стандарту FIPS запись возвратит меньше 18. Возвращает по крайней мере 128 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 Возвращает значение SQLUSMALLINT, указывающее максимальное количество столбцов в **GROUP BY** предложение. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Возвращает по крайней мере 6 драйвером уровень соответствующего стандарту FIPS запись. Возвращает по крайней мере 15 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_COLUMNS_IN_INDEX(ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальное число столбцов, допустимое в индексе. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 Возвращает значение SQLUSMALLINT, указывающее максимальное количество столбцов в **ORDER BY** предложение. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Возвращает по крайней мере 6 драйвером уровень соответствующего стандарту FIPS запись. Возвращает по крайней мере 15 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_COLUMNS_IN_SELECT(ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальное число столбцов, допустимое в списке выбора. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Возвращает по крайней мере 100 драйвером уровень соответствующего стандарту FIPS запись. FIPS промежуточного уровня совместимого драйвера вернет менее 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальное число столбцов, допустимое в таблице. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Возвращает по крайней мере 100 драйвером уровень соответствующего стандарту FIPS запись. FIPS промежуточного уровня совместимого драйвера вернет менее 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES(ODBC 1.0)  
 Возвращает SQLUSMALLINT значение, указывающее максимальное число активных инструкций, которые может поддерживать драйвер для подключения. Инструкция определена как активные, если он имеет ожидает, результаты с термин «результаты» значение строки из **ВЫБЕРИТЕ** операции или строк, затронутых **вставить**, **обновления**, или **Удалить** операции (например, количество строк), или если он находится в состоянии NEED_DATA. Это значение может отражать ограничения, накладываемые драйвер или источника данных. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN(ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени курсора в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 Драйвером уровень соответствующего стандарту FIPS запись возвратит меньше 18. Возвращает по крайней мере 128 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_DRIVER_CONNECTIONS(ODBC 1.0)  
 Возвращает SQLUSMALLINT значение, указывающее максимальное число активных подключений, которые может поддерживать драйвера для среды. Это значение может отражать ограничения, накладываемые драйвер или источника данных. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 SQLUSMALLINT, который указывает максимальный размер в символах, которые поддерживает источник данных для определяемых пользователем имен.  
  
 Драйвером уровень соответствующего стандарту FIPS запись возвратит меньше 18. Возвращает по крайней мере 128 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 Возвращает значение SQLUINTEGER, указывающее максимальное число байтов, разрешенное в объединенный полей индекса. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 SQL_MAX_PROCEDURE_NAME_LEN(ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени процедуры в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 SQL_MAX_ROW_SIZE(ODBC 2.0)  
 Значение SQLUINTEGER, которое указывает максимальную длину строки в таблице. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Возвращает по крайней мере 2 000 драйвером уровень соответствующего стандарту FIPS запись. Возвращает по крайней мере 8 000 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 Строка символов: «Y», если возвращается максимальный размер строки для типа данных SQL_MAX_ROW_SIZE включает длину всех SQL_LONGVARCHAR и SQL_LONGVARBINARY столбцов в строке; «N» в противном случае.  
  
 SQL_MAX_SCHEMA_NAME_LEN(ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени схемы в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 Драйвером уровень соответствующего стандарту FIPS запись возвратит меньше 18. Возвращает по крайней мере 128 FIPS промежуточного уровня совместимого драйвера.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 Возвращает значение SQLUINTEGER, указывающее максимальную длину инструкции SQL (количество символов, включая пробелы). Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 SQL_MAX_TABLE_NAME_LEN(ODBC 1.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени таблицы в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 Драйвером уровень соответствующего стандарту FIPS запись возвратит меньше 18. Возвращает по крайней мере 128 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 Возвращает значение SQLUSMALLINT, указывающее максимальное число допустимых таблиц в **FROM** предложении **ВЫБЕРИТЕ** инструкции. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 Возвращает по крайней мере 15 драйвером уровень соответствующего стандарту FIPS запись. Возвращает по крайней мере 50 FIPS промежуточного уровня совместимого драйвера.  
  
 SQL_MAX_USER_NAME_LEN(ODBC 2.0)  
 Значение SQLUSMALLINT, которое указывает максимальную длину имени пользователя в источнике данных. Если происходит без ограничения длины или длина данных неизвестна, это значение равным нулю.  
  
 SQL_MULT_RESULT_SETS(ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает несколько результирующих наборов, «N», если это не так.  
  
 Дополнительные сведения о нескольких результирующих наборов, см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN(ODBC 1.0)  
 Строка символов: «Y» Если драйвер поддерживает более одной активной транзакции, в то же время, «N», если только одна транзакция может быть активна в любое время.  
  
 Сведения, возвращаемые для этого типа данных не применяется в случае распределенных транзакций.  
  
 SQL_NEED_LONG_DATA_LEN(ODBC 2.0)  
 Строка символов: «Y», если источник данных должен длину значение данных long (тип данных является SQL_LONGVARCHAR SQL_LONGVARBINARY и зависящие от источника данных тип данных long) прежде, чем это значение отправляется к источнику данных, «N», если это не так. Дополнительные сведения см. в разделе [функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) и [функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS(ODBC 1.0)  
 SQLUSMALLINT значение, указывающее, поддерживает ли источник данных не NULL в столбцах:  
  
 SQL_NNC_NULL = все столбцы должны допускать значение NULL.  
  
 SQL_NNC_NON_NULL = столбцы не допускает значения NULL. (Источник данных поддерживает **NOT NULL** ограничение столбца в **CREATE TABLE** инструкций.)  
  
 Возвращает SQL_NNC_NON_NULL драйвером уровень соответствующего стандарту SQL-92 запись.  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 SQLUSMALLINT значение, которое указывает, где сортируются значения NULL в результирующем наборе:  
  
 SQL_NC_END = значения null сортируются в конце результирующего набора, независимо от того, ключевые слова ASC или DESC.  
  
 SQL_NC_HIGH = значения null сортируются в верхней части результирующего набора, в зависимости от того, ключевые слова ASC или DESC.  
  
 SQL_NC_LOW = значения null сортируются в нижней части результирующего набора, в зависимости от того, ключевые слова ASC или DESC.  
  
 SQL_NC_START = значения null сортируются в начале результирующего набора, независимо от того, ключевые слова ASC или DESC.  
  
 SQL_NUMERIC_FUNCTIONS(ODBC 1.0)  
 Примечание. Тип данных был введен в ODBC 1.0; Каждая маска помечается версии, в котором он был представлен.  
  
 Битовая маска SQLUINTEGER, перечисление скалярные числовые функции, поддерживаемые драйвера и связанного источника данных.  
  
 Следующие битовые маски используются для определения того, числовые функции, которые поддерживаются:  
  
 SQL_FN_NUM_ABS (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_ACOS SQL_FN_NUM_ASIN (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_ATAN SQL_FN_NUM_ATAN2 SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_COT-SQL_ SQL_FN_NUM_DEGREES (ODBC 2.0) SQL_FN_NUM_LOG10 SQL_FN_NUM_LOG (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_FLOOR FN_NUM_EXP (ODBC 1.0) SQL_FN_ SQL_FN_NUM_RAND (ODBC 1.0) В SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) (ODBC 2.0) (ODBC 1.0) SQL_FN_NUM_MOD SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_TRUNCATE NUM_ROUND (ODBC 2.0) (ODBC 1.0) SQL_FN_NUM_SIGN SQL_FN_NUM_SIN (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_SQRT SQL_FN_NUM_TAN (ODBC 1.0) (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE(ODBC 3.0)  
 SQLUINTEGER значение, указывающее уровень ODBC 3 *.x* интерфейс, соответствующий драйвер.  
  
 SQL_OIC_CORE: Минимальный уровень, все драйверы ODBC должны соответствовать. Этот уровень включает элементы базового интерфейса, такие как подключения функций, функции для подготовки и выполнения инструкции SQL, функции метаданных базовый результирующий набор, базовый каталог функции и т. д.  
  
 SQL_OIC_LEVEL1: Уровень, включая основных функций уровня соответствия стандартам, а также Прокручиваемые курсоры, закладки, расположенный обновляет и удаляет и т.д.  
  
 SQL_OIC_LEVEL2: Уровень, включая функции уровня соответствия стандартам уровень 1, а также дополнительные функции, такие как конфиденциальные курсоры; обновлять, удалять и обновлять с закладки; Поддержка хранимых процедур; функции работы с каталогами для первичных и внешних ключей; Поддержка нескольких каталога; и т. д.  
  
 Дополнительные сведения см. в разделе [уровни соответствия интерфейса](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER(ODBC 1.0)  
 Строка символов, с версией которой соответствует диспетчер драйверов ODBC. Версия имеет вид ##. ##. 0000, где первые две цифры являются основной номер версии, а также следующие две цифры — дополнительный номер версии. Это реализуется только диспетчера драйверов.  
  
 SQL_OJ_CAPABILITIES(ODBC 2.01)  
 Битовая маска SQLUINTEGER, перечисление типа внешнего соединения, поддерживаемых источником драйвер и данных. Следующие битовые маски используются для определения, какие типы поддерживаются:  
  
 SQL_OJ_LEFT = Left поддерживаются внешние соединения.  
  
 SQL_OJ_RIGHT = Right поддерживаются внешние соединения.  
  
 SQL_OJ_FULL = полный поддерживаются внешние соединения.  
  
 SQL_OJ_NESTED = вложенные внешние соединения поддерживаются.  
  
 SQL_OJ_NOT_ORDERED = имена в предложении ON внешнего соединения не обязательно должны быть в том же порядке, как их имена соответствующей таблицы в столбец **ВНЕШНЕГО СОЕДИНЕНИЯ** предложение.  
  
 SQL_OJ_INNER = Внутренняя таблица (правой таблицей в левое внешнее соединение) или левой таблицы в правое внешнее соединение может использоваться в inner join. Это относится к полные внешние соединения, которые не имеют внутренней таблице.  
  
 SQL_OJ_ALL_COMPARISON_OPS = сравнения оператор в предложении ON может быть любым из операторов сравнения ODBC. Если этот бит не установлен, можно использовать только оператор сравнения равенства (=) в внешние соединения.  
  
 Если ни один из этих параметров возвращается, так как поддерживается, поддерживается без предложения внешнего соединения.  
  
 Сведения о поддержке операторов реляционное соединение в инструкции SELECT как определено SQL-92, см. в разделе SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT(ODBC 2.0)  
 Строка символов: «Y» Если столбцы в **ORDER BY** предложение должно быть в списке выбора; в противном случае — «N».  
  
 SQL_PARAM_ARRAY_ROW_COUNTS(ODBC 3.0)  
 При выполнении параметризованных подсчитывает SQLUINTEGER, перечисление свойств драйвера к доступности строки. Имеет следующие значения:  
  
 SQL_PARC_BATCH = частное лицо количество строк, доступны для каждого набора параметров. Это эквивалентно концептуально драйвера, создание пакета инструкций SQL, по одному для каждого параметра, устанавливаемое в массиве. Сведения об ошибке можно получить с помощью поля дескриптора SQL_PARAM_STATUS_PTR.  
  
 SQL_PARC_NO_BATCH = имеется только одна строка число доступны, то есть число накопительного пакета строк, полученные в результате выполнения инструкции для всего массива параметров. Это эквивалентно концептуально обработке инструкцию вместе с массива параметров завершения как неделимым единицам. Ошибки обрабатываются так же, как если бы были выполнены в одной инструкции.  
  
 SQL_PARAM_ARRAY_SELECTS(ODBC 3.0)  
 При выполнении параметризованных задает SQLUINTEGER, перечисление свойств драйвера к доступности результата. Имеет следующие значения:  
  
 SQL_PAS_BATCH = имеется один результирующий набор, доступный для каждого набора параметров. Это эквивалентно концептуально драйвера, создание пакета инструкций SQL, по одному для каждого параметра, устанавливаемое в массиве.  
  
 SQL_PAS_NO_BATCH = имеется только один набор доступным, результат, представляющий кумулятивный результат задать, полученные в результате выполнения инструкции для полного массива параметров. Это эквивалентно концептуально обработке инструкцию вместе с массива параметров завершения как неделимым единицам.  
  
 SQL_PAS_NO_SELECT = A драйвер не поддерживает инструкцию создания результирующего набора, выполняемый с помощью массива параметров.  
  
 SQL_PROCEDURE_TERM(ODBC 1.0)  
 Строка символов, с именем поставщика источника данных для процедуры; Например, «процедуры базы данных», «хранимая процедура», «процедуры», «package» или «хранимого запроса».  
  
 SQL_PROCEDURES(ODBC 1.0)  
 Строка символов: «Y», если источник данных поддерживает процедур и драйвер поддерживает синтаксис вызова процедуры ODBC; «N» в противном случае.  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 Битовая маска SQLINTEGER перечисление поддерживать работу в **SQLSetPos**.  
  
 Следующие битовые маски используются вместе с флагом, чтобы определить, какие параметры поддерживаются.  
  
 SQL_POS_POSITION (ODBC 2.0) (ODBC 2.0) SQL_POS_REFRESH SQL_POS_UPDATE (ODBC 2.0) (ODBC 2.0) SQL_POS_DELETE SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE(ODBC 2.0)  
 SQLUSMALLINT значение следующим образом:  
  
 SQL_IC_UPPER = кавычках идентификаторов в SQL, регистр не учитывается и хранятся в верхнем регистре в системном каталоге.  
  
 SQL_IC_LOWER = кавычках идентификаторов в SQL, регистр не учитывается и хранятся в нижнем регистре в системном каталоге.  
  
 Sql_ic_mixed, имеющим = кавычках чувствительны к регистру идентификаторов в SQL и хранятся в смешанном регистре, в системном каталоге. (В базе данных SQL-92-совместимые идентификаторы в кавычках, всегда с учетом регистра.)  
  
 Sql_ic_mixed, имеющим = кавычках идентификаторов в SQL, регистр не учитывается и хранятся в смешанном регистре, в системном каталоге.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать sql_ic_mixed, имеющим.  
  
 SQL_ROW_UPDATES(ODBC 1.0)  
 Строка символов: «Y», если курсор управляемых набором ключей или смешанный сохраняет сведения о версии строк или значений для всех выбранных строк и таким образом, можно обнаружить все обновления, внесенные в строку любой пользователь с момента последней выборки. (Это относится только к обновлению, удаления или вставки). Драйвер может возвращать SQL_ROW_UPDATED флаг состояния строк массива, когда **SQLFetchScroll** вызывается. В противном случае — «N».  
  
 SQL_SCHEMA_TERM(ODBC 1.0)  
 Строка символов, с именем поставщика источника данных для схемы; Например «владелец», «Авторизации ID» или «Schema».  
  
 Строка символов могут быть возвращены в верхней, нижней или смешанный регистр.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда возвращает «schema».  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE(ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление инструкций, в которых можно использовать схемы:  
  
 SQL_SU_DML_STATEMENTS = схемы поддерживаются во всех инструкциях языка обработки данных: **ВЫБЕРИТЕ**, **вставить**, **обновление**, **удалить**и если поддерживается, **ВЫБЕРИТЕ для обновления** и позиционированного обновления и удаления инструкции.  
  
 SQL_SU_PROCEDURE_INVOCATION = схемы поддерживаются в операторе вызова процедуры ODBC.  
  
 SQL_SU_TABLE_DEFINITION = схемы поддерживаются во всех инструкциях определения таблицы: **СОЗДАТЬ ТАБЛИЦУ**, **ПРЕДСТАВЛЕНИЯ СОЗДАНИЯ**, **ALTER TABLE**, **DROP TABLE**, и **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = схемы поддерживаются во всех инструкциях определение индекса: **Создание ИНДЕКСА** и **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = схемы поддерживаются во всех инструкциях определения прав доступа: **Предоставление** и **ОТОЗВАТЬ**.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать параметры SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION и SQL_SU_PRIVILEGE_DEFINITION, так как поддерживается.  
  
 Это *InfoType* был переименован для ODBC 3.0 из ODBC 2.0 *InfoType* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS (ODBC 1.0)  
 Примечание. Тип данных был введен в ODBC 1.0; Каждая маска помечается версии, в котором он был представлен.  
  
 Битовая маска SQLUINTEGER, перечисление параметров прокрутки, поддерживаемых для прокручиваемых курсоров.  
  
 Следующие битовые маски используются для определения, какие параметры поддерживаются:  
  
 SQL_SO_FORWARD_ONLY = курсор только выполняет прокрутку вперед. (ODBC 1.0)  
  
 SQL_SO_STATIC = данные в результирующем наборе является статическим. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = драйвер сохраняет и использует ключи для каждой строки в результирующем наборе. (ODBC 1.0)  
  
 SQL_SO_DYNAMIC = драйвер сохраняет ключи для каждой строки в наборе строк (размер набора ключей совпадает со значением размера набора строк). (ODBC 1.0)  
  
 SQL_SO_MIXED = драйвер сохраняет ключи для каждой строки в набор ключей и размер набора ключей, больше размера набора строк. Курсор, управляемые набором ключей в набор ключей и динамические за пределами набор ключей. (ODBC 1.0)  
  
 Сведения о Прокручиваемые курсоры, см. в разделе [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE(ODBC 1.0)  
 Строка символов, указывающая, что драйвер поддерживает в качестве escape-символ, который позволяет использовать шаблон match метасимволы подчеркивания (_) и знак процента (%) как допустимые символы для шаблонов поиска. Escape-символ применяется только к аргументы функции каталога, которые поддерживают строки поиска. Если это значение не задано, драйвер не поддерживает escape-символа шаблону поиска.  
  
 Так как этот тип не указывает общей поддержке escape-символ в **как** предиката, SQL-92 не поддерживает требования для этой строки символов.  
  
 Это *InfoType* ограничено функций каталога. Описание использования escape-символ в строке шаблона поиска, см. в разделе [аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME (ODBC 1.0)  
 Строка символов, с именем сервера, зависящие от источника фактические данные. полезно, когда имя источника данных используется во время **SQLConnect**, **SQLDriverConnect**, и **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS(ODBC 2.0)  
 Строка символов, которая содержит все специальные символы (то есть все символы, за исключением до z, до Z, 0 до 9 и символ подчеркивания), которые могут использоваться в имени идентификатора, например имя таблицы, имя столбца или имя индекса, в источнике данных. Например «#$^». Если идентификатор содержит один или несколько из этих символов, идентификатор должен быть идентификатором с разделителем.  
  
 SQL_SQL_CONFORMANCE(ODBC 3.0)  
 SQLUINTEGER значение, указывающее уровень SQL-92, поддерживаемых драйвером:  
  
 SQL_SC_SQL92_ENTRY = запись уровня SQL-92 требованиям.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 transitional уровень соответствует.  
  
 SQL_SC_SQL92_FULL = полный уровень соответствует SQL-92.  
  
 SQL_SC_ SQL92_INTERMEDIATE = промежуточного уровня SQL-92 требованиям.  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление скалярные функции даты и времени, поддерживаемых драйвером и связанного источника данных, как определено в SQL-92.  
  
 Следующие битовые маски используются для определения функции даты и времени, которые поддерживаются:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление правил, поддерживаемые для внешнего ключа в **удалить** инструкции, как определено в SQL-92.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Драйвером уровень соответствующего стандарту FIPS Transitional всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление правил, поддерживаемые для внешнего ключа в **обновления** инструкции, как определено в SQL-92.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Драйвером SQL-92 полный уровень соответствующего стандарту всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложений, поддерживаемые в **GRANT** инструкции, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 ((Средний уровень) SQL_SG_INSERT_COLUMN SQL_SG_INSERT_TABLE (начальный уровень) SQL_SG_REFERENCES_TABLE (начальный уровень) SQL_SG_REFERENCES_COLUMN (начальный уровень) SQL_SG_SELECT_TABLE (начальный уровень) SQL_SG_UPDATE_COLUMN SQL_SG_DELETE_TABLE (начальный уровень) Начальный уровень) SQL_SG_USAGE_ON_CHARACTER_SET (FIPS Transitional уровень) SQL_SG_USAGE_ON_COLLATION (FIPS Transitional уровень) SQL_SG_UPDATE_TABLE (начальный уровень) SQL_SG_USAGE_ON_DOMAIN (FIPS Transitional уровень) SQL_SG_USAGE_ON_TRANSLATION (FIPS Переходные уровень) SQL_SG_WITH_GRANT_OPTION (начальный уровень)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление числовое значение скалярных функций, поддерживаемых драйвером и связанного источника данных, как определено в SQL-92.  
  
 Следующие битовые маски используются для определения того, числовые функции, которые поддерживаются:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предикаты, поддерживаемые в **ВЫБЕРИТЕ** инструкции, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SP_BETWEEN (начальный уровень) SQL_SP_COMPARISON (начальный уровень) SQL_SP_EXISTS (начальный уровень) SQL_SP_IN (начальный уровень) SQL_SP_ISNOTNULL (начальный уровень) SQL_SP_ISNULL (начальный уровень) SQL_SP_LIKE (начальный уровень) (уровень Full) SQL_SP_MATCH_FULL SQL_SP_MATCH_PARTIAL (Полный уровень) SQL_SP_MATCH_UNIQUE_FULL (уровень Full) (уровень Full) SQL_SP_MATCH_UNIQUE_PARTIAL SQL_SP_OVERLAPS (FIPS Transitional уровень) SQL_SP_QUANTIFIED_COMPARISON (начальный уровень) SQL_SP_UNIQUE (начальный уровень)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление реляционное соединение операторы, поддерживаемые в **ВЫБЕРИТЕ** инструкции, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (средний уровень) (уровень Full) SQL_SRJO_CROSS_JOIN SQL_SRJO_EXCEPT_JOIN (средний уровень) SQL_SRJO_FULL_OUTER_JOIN (средний уровень) SQL_SRJO_INNER_JOIN (FIPS Transitional уровень) SQL_SRJO_INTERSECT_JOIN (Средний уровень) SQL_SRJO_UNION_JOIN SQL_SRJO_RIGHT_OUTER_JOIN (FIPS Transitional уровень) SQL_SRJO_NATURAL_JOIN (FIPS Transitional уровень) SQL_SRJO_LEFT_OUTER_JOIN (FIPS Transitional уровень) (уровень Full)  
  
 SQL_SRJO_INNER_JOIN указывает на поддержку **ВНУТРЕННЕЕ соединение** синтаксис, не в течение внутреннее соединение. Поддержка **ВНУТРЕННЕЕ соединение** синтаксис является FIPS переходном состоянии, тогда как поддержка возможности внутреннего соединения является **запись**.  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложений, поддерживаемые в **ОТОЗВАТЬ** инструкции, как определено в SQL-92, поддерживаемых источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие предложения поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SR_ SQL_SR_REFERENCES_COLUMN (начальный уровень) для SQL_SR_GRANT_OPTION_FOR (средний уровень) SQL_SR_INSERT_COLUMN (средний уровень) SQL_SR_CASCADE (FIPS Transitional уровень) SQL_SR_DELETE_TABLE (начальный уровень) SQL_SR_INSERT_TABLE (начальный уровень) SQL_SR_USAGE_ON_ SQL_SR_USAGE_ON_DOMAIN (FIPS Transitional уровень) в SQL_SR_SELECT_TABLE (начальный уровень) SQL_SR_UPDATE_COLUMN (начальный уровень) REFERENCES_TABLE (начальный уровень) SQL_SR_RESTRICT (FIPS Transitional уровень) SQL_SR_UPDATE_TABLE (начальный уровень) SQL_SR_USAGE_ON_TRANSLATION SQL_SR_USAGE_ON_COLLATION (FIPS Transitional уровень) CHARACTER_SET (FIPS Transitional уровень) (FIPS Transitional уровень)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление конструктор выражений значений строк, поддерживаемые в **ВЫБЕРИТЕ** инструкции, как определено в SQL-92. Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление строковых скалярных функций, которые поддерживаются драйвером и связанного источника данных, как определено в SQL-92.  
  
 Следующие битовые маски используются для определения функции строки, которые поддерживаются:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление значение выражения поддерживаются, как определено в SQL-92.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Чтобы определить, какие параметры поддерживаются источником данных используются следующие битовые маски:  
  
 SQL_SVE_NULLIF SQL_SVE_COALESCE (средний уровень) SQL_SVE_CAST (FIPS Transitional уровень) SQL_SVE_CASE (средний уровень) (средний уровень)  
  
 SQL_STANDARD_CLI_CONFORMANCE(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление стандартный интерфейс командной строки или стандарты, которых соответствует драйвер. Чтобы определить, какие уровни, драйвер соответствует используются следующие битовые маски:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Драйвер соответствует группе интерфейса командной строки открытым версии 1.  
  
 SQL_SCC_ISO92_CLI: Драйвер соответствует стандарту ISO 92 интерфейса командной строки.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Маска SQLUINTEGER, которая описывает атрибуты статического курсора, которые поддерживаются драйвером. Этой битовой маске содержит первый подмножество атрибутов; второй подмножество см. в разделе SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Описание этих битовой маски см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и замените «статический курсор» для «динамический курсор», в соответствии с описанием).  
  
 SQL-92 промежуточного уровня совместимого драйвера обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE поддерживается, так как драйвер поддерживает прокручиваемые курсоры через внедренный оператор SQL FETCH. Так как это не определить непосредственно базовой поддержки SQL, тем не менее, Прокручиваемые курсоры могут не поддерживаться, даже для SQL-92 промежуточного уровня совместимого драйвера.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Маска SQLUINTEGER, которая описывает атрибуты статического курсора, которые поддерживаются драйвером. Этой битовой маске содержит второй подмножество атрибутов; Первый набор см. в разделе SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Следующие битовые маски используются для определения, какие атрибуты поддерживаются:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Описание этих битовой маски см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и замените «статический курсор» для «динамический курсор», в соответствии с описанием).  
  
 SQL_STRING_FUNCTIONS(ODBC 1.0)  
 Примечание. Тип данных был введен в ODBC 1.0; Каждая маска помечается версии, в котором он был представлен.  
  
 Битовая маска SQLUINTEGER, перечисление скалярные строковые функции, поддерживаемые драйвера и связанного источника данных.  
  
 Следующие битовые маски используются для определения функции строки, которые поддерживаются:  
  
 SQL_FN_STR_ASCII (ODBC 1.0) (ODBC 3.0) SQL_FN_STR_BIT_LENGTH SQL_FN_STR_CHAR (ODBC 1.0) (ODBC 3.0) SQL_FN_STR_CHAR_LENGTH SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_INSERT SQL_FN_STR_DIFFERENCE (ODBC 2.0) (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LEFT SQL_FN_STR_LENGTH (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_ SQL_FN_STR_UCASE SQL_FN_STR_SPACE (ODBC 2.0) (ODBC 1.0) SQL_FN_STR_SUBSTRING ДЛЯ SQL_FN_STR_RIGHT (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_RTRIM STR_REPLACE (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) (ODBC 1.0)  
  
 Если приложение может вызвать **найти** скалярной функции с *строковое_выражение1*, *строковое_выражение2*, и *запустить* аргументов, драйвер Возвращает битовую маску SQL_FN_STR_LOCATE. Если приложение может вызвать скалярной функции найти только с *строковое_выражение1* и *строковое_выражение2* аргументы, драйвер возвращает битовую маску SQL_FN_STR_LOCATE_2. Драйверы с полной поддержкой **найти** скалярные функции возвращают обоих битовой маски.  
  
 (Дополнительные сведения см. в разделе [строковые функции](../../../odbc/reference/appendixes/string-functions.md) в приложении Д «скалярные функции.»)  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление предикаты, которые поддерживают вложенные запросы:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Битовая маска SQL_SQ_CORRELATED_SUBQUERIES означает, что все предикаты, которые поддерживают вложенные запросы поддерживает коррелированные вложенные запросы.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать Битовая маска, в котором все биты равны.  
  
 SQL_SYSTEM_FUNCTIONS(ODBC 1.0)  
 Битовая маска SQLUINTEGER, перечисление скалярные системные функции, поддерживаемые драйвера и связанного источника данных.  
  
 Следующие битовые маски используются для определения, какие системные функции поддерживаются:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM(ODBC 1.0)  
 Строка символов, с именем поставщика источника данных для таблицы. Например «table» или «файл».  
  
 Эта строка символов может быть в верхней, нижней или смешанный регистр.  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать «table».  
  
 SQL_TIMEDATE_ADD_INTERVALS(ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление интервалы отметки времени, поддерживаемые драйвера и связанного источника данных для скалярной функции TIMESTAMPADD.  
  
 Следующие битовые маски используются для определения, какие интервалы поддерживаются:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Драйвером уровень соответствующего стандарту FIPS Transitional всегда будет возвращать Битовая маска, в котором все биты равны.  
  
 SQL_TIMEDATE_DIFF_INTERVALS(ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление интервалы отметки времени, поддерживаемые драйвера и связанного источника данных для скалярной функции TIMESTAMPDIFF.  
  
 Следующие битовые маски используются для определения, какие интервалы поддерживаются:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Драйвером уровень соответствующего стандарту FIPS Transitional всегда будет возвращать Битовая маска, в котором все биты равны.  
  
 SQL_TIMEDATE_FUNCTIONS(ODBC 1.0)  
 Примечание. Тип данных был введен в ODBC 1.0; Каждая маска помечается версии, в котором он был представлен.  
  
 Битовая маска SQLUINTEGER, перечисление скалярные функции даты и времени поддерживаются драйвером и связанного источника данных.  
  
 Следующие битовые маски используются для определения функции даты и времени, которые поддерживаются:  
  
 SQL_FN_TD_DAYOFMONTH SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0) ДЛЯ SQL_FN_TD_CURRENT_TIME (ODBC 3.0) (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) (ODBC 1.0) SQL_FN_TD_DAYOFWEEK () ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) (ODBC 3.0) SQL_FN_TD_EXTRACT SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) (ODBC 1.0) SQL_FN_TD_NOW SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_ SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) (ODBC 2.0) SQL_FN_TD_TIMESTAMPADD ВТОРОЙ (ODBC 1.0) – SQL_FN_TD_YEAR SQL_FN_TD_WEEK (ODBC 1.0) (ODBC 1.0)  
  
 SQL_TXN_CAPABLE(ODBC 1.0)  
 Примечание. Тип данных был введен в ODBC 1.0; Каждое возвращаемое значение меткой с версией, в которую было включено.  
  
 Значение SQLUSMALLINT, описывающий поддержка транзакций в драйвер или источник данных:  
  
 SQL_TC_NONE = транзакции не поддерживаются. (ODBC 1.0)  
  
 SQL_TC_DML = транзакции может содержать только инструкции языка обработки данных DML (**ВЫБЕРИТЕ**, **вставить**, **обновление**, **удалить** ). Инструкции языка определения (DDL) данных в причина транзакции произошла ошибка. (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = транзакции может содержать только инструкции DML. Инструкции DDL (**CREATE TABLE**, **DROP INDEX**, и т. д) обнаружена в причина транзакции фиксации транзакции. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = транзакции может содержать только инструкции DML. Инструкции DDL, в транзакции учитываются. (ODBC 2.0)  
  
 SQL_TC_ALL = транзакции может содержать инструкции DDL и DML-инструкций в любом порядке. (ODBC 1.0)  
  
 (Так как поддержка транзакций является обязательным в SQL-92, драйвером соответствующие стандарту SQL-92 [любой уровень] никогда не будут возвращать SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION(ODBC 1.0)  
 Битовая маска SQLUINTEGER, перечисление уровни изоляции транзакций доступны из драйвера или источника данных.  
  
 Следующие битовые маски используются вместе с флагом, чтобы определить, какие параметры поддерживаются:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Описание этих уровней изоляции см. в описании SQL_DEFAULT_TXN_ISOLATION.  
  
 Чтобы задать уровень изоляции транзакции, приложение вызывает **SQLSetConnectAttr** установить атрибут SQL_ATTR_TXN_ISOLATION. Дополнительные сведения см. в разделе [SQLSetConnectAttr, функция](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать SQL_TXN_SERIALIZABLE, так как поддерживается. Переходные FIPS уровень совместимого драйвера всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_UNION(ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление поддержка **ОБЪЕДИНЕНИЕ** предложение:  
  
 SQL_U_UNION = источник данных поддерживает **ОБЪЕДИНЕНИЕ** предложение.  
  
 SQL_U_UNION_ALL = источник данных поддерживает **все** ключевое слово в **ОБЪЕДИНЕНИЕ** предложение. (**SQLGetInfo** возвращает SQL_U_UNION и SQL_U_UNION_ALL в данном случае.)  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать оба этих варианта, поддерживаемой.  
  
 SQL_USER_NAME(ODBC 1.0)  
 Строка символов, с именем, используемых в определенной базе данных, который может отличаться от имени входа.  
  
 SQL_XOPEN_CLI_YEAR(ODBC 3.0)  
 Строка символов, который указывает год публикации, с помощью которого диспетчер драйверов ODBC версии полностью соответствует спецификации Open Group.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Строка символов: «Y», если пользователь может выполнять все процедуры, возвращенный **SQLProcedures**; «N», если возможно, процедуры возвращено, что пользователь не может выполняться.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Строка символов: «Y», если пользователь гарантируется **ВЫБЕРИТЕ** привилегий для всех таблиц, возвращаемых функцией **SQLTables**; «N», если может быть таблиц возвращаются, что пользователь не может получить доступ к.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Возвращает SQLUSMALLINT значение, указывающее максимальное количество активных средах, которые поддерживает драйвер. Если не ограничено указанной или число неизвестно, это значение равным нулю.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление поддержка статистических функций:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Драйвером уровень соответствующего стандарту SQL-92 запись всегда будет возвращать все эти возможности, поддерживаемой.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **ALTER домена** инструкции, как определено в SQL-92, поддерживаемых источником данных. Уровень с драйвером SQL-92 полный всегда будет возвращать все битовой маски. Возвращаемое значение «0» означает, что **ALTER домена** инструкция не поддерживается.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ограничение домена поддерживается добавление (полная уровень)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter домена > \<предложения по умолчанию домена set > поддерживается (полная уровень)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<предложение определение имя ограничения > поддерживается для именования ограничение для доменов (средний уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<предложения ограничения удаления домена > поддерживается (полная уровень)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter домена > \<предложения по умолчанию для удаления домена > поддерживается (полная уровень)  
  
 Укажите поддерживаемые следующие биты \<атрибутов ограничения > Если \<добавить ограничение домена > поддерживается (SQL_AD_ADD_DOMAIN_CONSTRAINT бита):  
  
 SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (уровень Full) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE SQL_AD_ADD_CONSTRAINT_DEFERRABLE (уровень Full) (уровень Full)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 Битовая маска SQLUINTEGER, перечисление предложения в **ALTER TABLE** инструкции, поддерживаемых источником данных.  
  
 Уровень соответствия SQL-92 или FIPS, по которому должен поддерживаться этой функции отображается в круглых скобках рядом с каждой битовой маски.  
  
 Следующие битовые маски используются для определения, какие предложения поддерживаются:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<добавить столбец > предложение поддерживается с помощью средства, чтобы указать параметры сортировки столбца (уровень Full) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<добавить столбец > предложение поддерживается с помощью средства для указания значений столбца по умолчанию (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<добавить столбец > — поддерживается (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<добавить столбец > предложение поддерживается с помощью средства для указания столбца ограничений (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<добавить ограничение таблицы > предложение поддерживается (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<имя определения ограничения > поддерживается для именования ограничения столбцов и таблиц (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<удалением столбца > поддерживается CASCADE (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<изменить столбец > \<предложения по умолчанию для удаления столбца > — поддерживается (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<удалением столбца > поддерживается RESTRICT (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<удалением столбца > поддерживается RESTRICT (FIPS Transitional уровень) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<изменить столбец > \<предложении default для столбца набора > — поддерживается (средний уровень) (ODBC 3.0)  
  
 Следующие биты укажите поддержки \<атрибутов ограничения > Если поддерживается Указание ограничений столбец или таблицу (SQL_AT_ADD_CONSTRAINT бита):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (уровень Full) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (уровень Full) (ODBC 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 SQLUINTEGER значение, указывающее уровень поддержку асинхронных операций в драйвере:  
  
 SQL_AM_CONNECTION = соединение поддерживается уровня асинхронное выполнение. Все дескрипторы инструкций, связанных с дескриптором данного соединения, в асинхронном режиме, либо все находятся в синхронном режиме. Дескриптор инструкции для подключения, не может быть в асинхронном режиме, пока другой дескриптора инструкции относительно одного подключения — в синхронном режиме и наоборот.  
  
 SQL_AM_STATEMENT = поддерживается уровня асинхронное выполнение инструкции. Некоторые дескрипторов инструкций, связанных с дескриптором соединения может быть в асинхронном режиме, тогда как другие дескрипторы инструкций для одного соединения являются в синхронном режиме.  
  
 SQL_AM_NONE = асинхронный режим не поддерживается.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Подсчитывает SQLUINTEGER битовой маски, перечисления поведение драйвера с точки зрения доступности строки. Следующие битовые маски используются вместе с типов данных:  
  
 SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE, суммируются в одну. Если этот бит не задано, количество строк будут доступны для каждой инструкции.  
  
 SQL_BRC_PROCEDURES = количество строк, если, они доступны при выполнении пакета в хранимой процедуре. Если количество строк, они могут выполнить откат вверх или по отдельности способность в зависимости от бита SQL_BRC_ROLLED_UP.  
  
 SQL_BRC_EXPLICIT = количество строк, если, они доступны при выполнении пакета напрямую путем вызова **SQLExecute** или **SQLExecDirect**. Если количество строк, они могут выполнить откат вверх или по отдельности способность в зависимости от бита SQL_BRC_ROLLED_UP.  
  
## <a name="example"></a>Пример  
 **SQLGetInfo** возвращает список поддерживаемых параметров в виде битовой маски SQLUINTEGER в **InfoValuePtr*. Битовая маска для каждого параметра используется вместе с флаг, чтобы определить, поддерживается ли параметр.  
  
 К примеру приложение может использовать следующий код, чтобы определить, поддерживается ли скалярные функции SUBSTRING с помощью драйвера, связанный с подключением.  
  
 Еще один пример использования **SQLGetInfo**, см. в разделе [функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md).  
  
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
 Возвращает значение атрибута соединения  
 [Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Определение, поддерживает ли драйвер функции  
 [Функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Возвращает значение атрибута инструкции  
 [Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Возвращение сведений о типах данных к источнику данных  
 [Функция SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
