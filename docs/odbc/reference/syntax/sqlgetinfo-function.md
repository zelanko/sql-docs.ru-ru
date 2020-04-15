---
title: Функция S'LGetInfo Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303346"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo, функция
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **Компания SLGetInfo** возвращает общую информацию о драйвере и источнике данных, связанных с подключением.  
  
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
 *ПодключениеРучка*  
 [Input] Дескриптор подключения  
  
 *InfoType*  
 (Вход) Тип информации.  
  
 *InfoValuePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть информацию. В зависимости от запрошенной *InfoType* возвращенная информация будет одной из следующих: строка с нулевым завершением символов, значение S'LUSMALLINT, битная маска СЗЛУИНТЕГЕР, флаг СЗЛУИНТЕГЕР, двоичное значение S'LUINTEGER или значение S'LULEN.  
  
 Если аргумент *InfoType* является SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT, аргумент *InfoValuePtr* является как вход, так и выход. (См. SQL_DRIVER_HDESC или SQL_DRIVER_HSTMT дескрипторы позже в этом описании функции для получения дополнительной информации.)  
  
 Если *InfoValuePtr* является NULL, *StringLengthPtr* по-прежнему возвращает общее количество байтов (за исключением символа нулевого прекращения для данных символов), доступного для возврата в буфере, на который указывает *InfoValuePtr.*  
  
 *BufferLength*  
 (Вход) Длина \*буфера *InfoValuePtr.* Если значение в * \*InfoValuePtr* не является строкой символов или если *InfoValuePtr* является нулевой указатель, *аргумент BufferLength* игнорируется. Драйвер предполагает, что размер * \*InfoValuePtr* является СЗЛУМЛИНКТ или СЗЛУИНТЕГЕР, на основе *InfoType*. Если * \*InfoValuePtr* является строкой Unicode (при вызове **S'LGetInfoW),** аргумент *BufferLength* должен быть четным числом; в противном случае возвращается S'LSTATE HY090 (недействительная длина строки или буфера).  
  
 *СтрунныйДлинПтр*  
 (Выход) Указатель на буфер, в котором можно вернуть общее количество байтов (за исключением символа нулевого прекращения для данных о символах), доступного для возврата в*no InfoValuePtr*.  
  
 Для данных о персонажах, если количество байтов, доступных для \*возврата, больше или равно *BufferLength,* информация в *InfoValuePtr* усечена до байтов *BufferLength* за вычетом длины персонажа с нулевым прекращением и сведена к нулю водителю.  
  
 Для всех других типов данных значение *BufferLength* игнорируется, и драйвер \*предполагает, что размер *InfoValuePtr* является СЗЛУСМЕЛИНТ или СЗЛУИНТЕГЕР, в зависимости от *InfoType.*  
  
## <a name="return-value"></a>Возвращаемое значение  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetInfo** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанная с этим стоимость S'LSTATE может быть получена, позвонив по **телефону s'LGetDiagRec** с *помощью HandleType* of SQL_HANDLE_DBC и *ручки* *ConnectionHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **s'LGetInfo,** и разъясняется каждая из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|Буфер \* *InfoValuePtr* не был достаточно большим, чтобы вернуть всю запрашиваемую информацию. Таким образом, информация была усечена. Длина запрошенной информации в ее неутомимых формах возвращается в*строке StringLengthPtr*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08003|Подключение не открыто|(DM) Тип информации, запрашиваемый в *InfoType,* требует открытого подключения. Из типов информации, зарезервированных ODBC, только SQL_ODBC_VER могут быть возвращены без открытого соединения.|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY024|Значение недействительных атрибутов|(DM) Аргумент *InfoType* был SQL_DRIVER_HSTMT, и значение, на что указывает *InfoValuePtr,* не является действительной ручкой оператора.<br /><br /> (DM) Аргумент *InfoType* был SQL_DRIVER_HDESC, и значение, на что указывает *InfoValuePtr,* не является действительной ручкой дескриптора.|  
|HY090|Недействительная длина строки или буфера|(DM) Значение, указанное для *аргумента BufferLength* было меньше, чем 0.<br /><br /> (DM) Значение, указанное для *BufferLength,* было нечетным числом, а * \*InfoValuePtr* — типом данных Unicode.|  
|HY096|Информационный тип вне диапазона|Значение, указанное для аргумента *InfoType,* не было допустимо для версии ODBC, поддерживаемой водителем.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYC00|Дополнительное поле не реализовано|Значение, указанное для аргумента *InfoType,* было значением для драйвера, которое не поддерживается драйвером.|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, соответствующий *ConnectionHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 В настоящее время определенные типы информации отображаются в "Типах информации", позже в этом разделе; ожидается, что будет определено больше, с тем чтобы использовать различные источники данных. Диапазон типов информации зарезервирован ODBC; разработчики драйверов должны резервировать значения для использования в открытом составе для собственного использования драйверов. **СЗЛГетИнфо** не выполняет преобразования Unicode или *thunking* [(см. Приложение A: КОДы ошибки ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) *справочника ODBC программиста*) для драйвера определяемых *InfoTypes*. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md) Формат информации, возвращенной в \* *InfoValuePtr,* зависит от запрошенного *InfoType.* **СЗЛГетИнфо** вернет информацию в одном из пяти различных форматов:  
  
-   Строка символов с нулевым завершением  
  
-   Значение СЛЮМЛУИТТ  
  
-   Битная маска СЗЛУИНТЕГЕР  
  
-   Значение СЗЛУИНТЕГЕР  
  
-   Двоичная стоимость СЗЛУИНТЕГЕР  
  
 Формат каждого из следующих типов информации указан в описании типа. Приложение должно отбросить значение, возвращенное в*InfoValuePtr* соответственно. Например, как приложение может получить данные из битовой маски S'LUINTEGER, см.  
  
 Водитель должен вернуть значение для каждого типа информации, которое определено в следующих таблицах. Если тип информации не применяется к водителю или источнику данных, водитель возвращает одно из значений, перечисленных в следующей таблице.  
  
 Строка символов ("Y" или "N")  
 "N"  
  
 Строка характера (не "Y" или "N")  
 Пустая строка.  
  
 СЛЮМЛМИНТ  
 0  
  
 Битмаска ссЛЮИНТЕГЕР или бинарное значение СЗЛУИНТЕГЕР  
 0L  
  
 Например, если источник данных не поддерживает процедуры, **s'LGetInfo** возвращает значения, перечисленные в следующей таблице, для значений *InfoType,* связанных с процедурами.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Пустая строка.  
  
 **SLGetInfo** возвращает S'LSTATE HY096 (недействительное значение аргумента) для значений *InfoType,* которые находятся в диапазоне типов информации, зарезервированных для использования ODBC, но не определяемых версией ODBC, поддерживаемой драйвером. Чтобы определить, какую версию ODBC выполняет драйвер, приложение вызывает **S'LGetInfo** с SQL_DRIVER_ODBC_VER типом информации. **SLGetInfo** возвращает S'LSTATE HYC00 (необязательная функция не реализована) для значений *InfoType,* которые находятся в диапазоне типов информации, зарезервированных для конкретного использования драйвером, но не поддерживаемых драйвером.  
  
 Все вызовы в **S'LGetInfo** требуют открытого подключения, за исключением случаев, когда *InfoType* SQL_ODBC_VER, который возвращает версию менеджера драйвера.  
  
## <a name="information-types"></a>Типы информации  
 В этом разделе перечислены типы информации, поддерживаемые **S'LGetInfo**. Типы информации группируются категорично и перечислены в алфавитном порядке. Также перечислены типы информации, которые были добавлены или переименованы в ODBC 3 *.x.*  
  
## <a name="driver-information"></a>Информация о драйверах  
 Следующие значения аргумента *InfoType* возвращают информацию о драйвере ODBC, например количество активных заявлений, имя источника данных и уровень соответствия стандартам интерфейса:  
  
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
>  При реализации **S'LGetInfo**драйвер может повысить производительность, свести к минимуму количество раз, когда информация отправляется или запрашивается с сервера.  
  
## <a name="dbms-product-information"></a>Информация о продуктах DBMS  
 Следующие значения аргумента *InfoType* возвращают информацию о продукте DBMS, такие как имя и версия DBMS:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Информация об источнике данных  
 Следующие значения аргумента *InfoType* возвращают информацию об источнике данных, такие как характеристики курсора и возможности транзакций:  
  
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
  
## <a name="supported-sql"></a>Поддерживаемая СЗЛ  
 Следующие значения аргумента *InfoType* возвращают информацию о заявлениях, поддерживаемых источником данных. Синтаксис каждого объекта, описанного этими типами информации, является синтаксисом S'L-92. Эти типы информации не полностью описывают всю грамматику S'L-92. Вместо этого они описывают те части грамматики, для которых источники данных обычно предлагают различные уровни поддержки. В частности, большинство заявлений DDL в S'L-92 охвачены.  
  
 Приложения должны определять общий уровень поддерживаемой грамматики из SQL_SQL_CONFORMANCE типа информации и использовать другие типы информации для определения отклонений от заявленного уровня соответствия стандартам.  
  
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
  
## <a name="sql-limits"></a>Ограничения S'L  
 Следующие значения аргумента *InfoType* возвращают информацию о ограничениях, применяемых к идентификаторам и положениям в заявлениях S'L, таким как максимальная длина идентификаторов и максимальное количество столбцов в списке выбора. Ограничения могут быть введены либо драйвером, либо источником данных.  
  
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
  
## <a name="scalar-function-information"></a>Информация о функциях scalar  
 Следующие значения аргумента *InfoType* возвращают информацию о функциях масштабирования, поддерживаемых источником данных и драйвером. Для получения дополнительной информации о [Appendix E: Scalar Functions](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)функциях масштабирования см.  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Информация о конверсии  
 Следующие значения аргумента *InfoType* возвращают список типов данных S'L, в которые источник данных может преобразовать указанный тип данных СЗЛ с функцией **масштабирования CONVERT:**  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Типы информации Добавлены для ODBC 3.x  
 Следующие значения аргумента *InfoType* были добавлены для ODBC 3 *.x:*  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Типы информации, переименованные в ODBC 3.x  
 Следующие значения аргумента *InfoType* были переименованы в ODBC 3 *.x*.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Типы информации, обезображенные в ODBC 3.x  
 Следующие значения аргумента *InfoType* были обесцвечены в ODBC 3 *.x*. Драйверы ODBC 3 *.x* должны продолжать поддерживать эти типы информации для обратной совместимости с приложениями ODBC 2 *.x.* (Для получения более подробной [SQLGetInfo Support](../../../odbc/reference/appendixes/sqlgetinfo-support.md) информации об этих типах, см.  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Описания типа информации  
 В следующей таблице в алфавитном порядке перечислены каждый тип информации, версия ODBC, в которой она была введена, и его описание.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Строка символов: "Y", если пользователь может выполнить все процедуры, возвращенные **S'LProcedures;** "N", если могут быть возвращены процедуры, которые пользователь не может выполнить.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Строка символов: "Y", если пользователю гарантированы привилегии **SELECT** для всех таблиц, возвращенных **S'LTables;** "N", если могут быть возвращены таблицы, к которым пользователь не может получить доступ.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество активных сред, которые может поддерживать драйвер. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая поддержку функций агрегирования:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Водитель, отвечающий уровню входа, всегда будет возвращать все эти опции в соответствии с поддержкой.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Битовая маска СЗЛЭГЕР, перечисляющая положения в заявлении **ALTER DOMAIN,** как это определено в S'L-92, поддерживается источником данных. Водитель полного уровня S'L-92 всегда будет возвращать все битмаски. Значение возврата "0" означает, что заявление **ALTER DOMAIN** не поддерживается.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT- Добавление ограничения домена поддерживается (полный уровень)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT \<- изменить \<положение о домене> набор домена по умолчанию> поддерживается (полный уровень)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION \<- оговорка об определении имен ограничений> поддерживается для определения ограничения домена (средний уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT \<- оговорка о ограничении домена> поддерживается (полный уровень)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT \<- изменять пункт о домене> \<домена по умолчанию> поддерживается (полный уровень)  
  
 Следующие биты указывают \<поддерживаемые атрибуты \<ограничения>, если поддерживается ограничение домена> (набор SQL_AD_ADD_DOMAIN_CONSTRAINT бита):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)  
  
 SQL_ALTER_TABLE (ODBc 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **ALTER TABLE,** поддерживаемом источником данных.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_AT_ADD_COLUMN_COLLATION \<и добавить столбец> оговорка поддерживается, с возможностью указать столбец коллажа (полный уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT \<- добавить столбец> оговорка поддерживается, с возможностью указать столбец по умолчанию (FiPS Переходный уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE \<- добавить столбец> поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT \<- добавить столбец> оговорка поддерживается, с возможностью указать ограничения столбца (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT \<- добавить ограничение таблицы> положение поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION \<- определение определения ограниченного имени> поддерживается для именования столбцов и ограничений таблицы (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE \<столбец падения> casCADE поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT \<- изменить \<столбец> оговорку о снижении столбца по умолчанию> поддерживается (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT \<- колонка падения> RESTRICT поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT \<столбец падения> RESTRICT поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT \<- изменить \<столбец> набор столбец по умолчанию> поддерживается (средний уровень) (ODBC 3.0)  
  
 Следующие биты указывают \<атрибуты ограничения поддержки>, поддерживается ли ограничение столбца или таблицы (SQL_AT_ADD_CONSTRAINT бит установлен):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (полный уровень) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 Значение S-LUINTEGER, которое указывает, может ли драйвер выполнять функции асинхронно на ручке соединения.  
  
 SQL_ASYNC_DBC_CAPABLE - Драйвер может выполнять функции соединения асинхронно.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE - Драйвер не может выполнять функции соединения асинхронно.  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 Значение S-LUINTEGER, которое указывает уровень асинхронной поддержки в драйвере:  
  
 SQL_AM_CONNECTION поддерживается асинхронное исполнение уровня соединения. Все ручки оператора, связанные с данной ручкой соединения, находятся в асинхронном режиме, либо все они находятся в синхронном режиме. Ручка оператора на соединении не может находиться в асинхронном режиме, в то время как другая ручка оператора в том же соединении находится в синхронном режиме, и наоборот.  
  
 SQL_AM_STATEMENT поддерживается асинхронное выполнение уровня оператора. Некоторые ручки оператора, связанные с ручкой соединения, могут находиться в асинхронном режиме, в то время как другие ручки оператора в том же соединении находятся в синхронном режиме.  
  
 SQL_AM_NONE асинхронный режим не поддерживается.  
  
 SQL_ASYNC_NOTIFICATION  
 Значение S'LUINTEGER, указывававое, поддерживает ли драйвер асинхронное уведомление:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** Уведомление об асинхронном исполнении поддерживается драйвером.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** Уведомление о асинхронном исполнении не поддерживается драйвером.  
  
 Существует две категории асинхронных операций ODBC: асинхронные операции уровня соединения и асинхронные операции уровня оператора.  Если водитель возвращает SQL_ASYNC_NOTIFICATION_CAPABLE, он должен поддерживать уведомление для всех AI, что он может выполнять асинхронно.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Битовая маска S'LUINTEGER, которая перечисляет поведение водителя в отношении наличия количества строк. Следующие бит-маски используются вместе с типом информации:  
  
 SQL_BRC_ROLLED_UP строки подсчитывают для последовательных вставка, DELETE, или ОБНОВЛЕНИЕ заявления свернуты в один. Если этот бит не установлен, для каждой выписки доступны строки.  
  
 SQL_BRC_PROCEDURES и строки, если таковые имеются, доступны, когда пакет выполняется в сохраненной процедуре. Если количество строк доступно, они могут быть свернуты или индивидуально доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
 SQL_BRC_EXPLICIT количество строк, если таковые имеются, доступны, когда партия выполняется непосредственно по телефону **S'L'LExecute** или **S'LExecDirect**. Если количество строк доступно, они могут быть свернуты или индивидуально доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая поддержку драйвера для партий. Для определения того, какой уровень поддерживается, используются следующие бит-маски:  
  
 SQL_BS_SELECT_EXPLICIT драйвер поддерживает явные пакеты, которые могут иметь генерирующие операторы, настроенные в результате.  
  
 SQL_BS_ROW_COUNT_EXPLICIT - Драйвер поддерживает явные пакеты, которые могут иметь генерирующие операторы, генерирующие количество строк.  
  
 SQL_BS_SELECT_PROC - Драйвер поддерживает четкие процедуры, которые могут иметь генерирующие заявления, генерирующие результаты.  
  
 SQL_BS_ROW_COUNT_PROC - Драйвер поддерживает четкие процедуры, которые могут иметь заявления, генерирующие количество строк.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая операции, с помощью которых сохраняются закладки.  
  
 Следующие битмаски используются вместе с флагом, чтобы определить, через какие варианты сохраняются закладки:  
  
 SQL_BP_CLOSE - Закладки действительны после того, как приложение вызывает **s'LFreeStmt** с SQL_CLOSE опцией, или **S'LCloseCursor,** чтобы закрыть курсор, связанный с заявлением.  
  
 SQL_BP_DELETE - закладка для строки действительна после удаления строки.  
  
 SQL_BP_DROP - Закладки действительны после того, как приложение вызывает **S'LFreeHandle** с *SQL_HANDLE_STMT,* чтобы отказаться от оператора.  
  
 SQL_BP_TRANSACTION - Закладки действительны после того, как приложение совершает или откатывает транзакцию.  
  
 SQL_BP_UPDATE - закладка для строки действительна после обновления любого столбца в этой строке, включая ключевые столбцы.  
  
 SQL_BP_OTHER_HSTMT - закладка, связанная с одним утверждением, может быть использована с другим утверждением. Если не указано SQL_BP_CLOSE или SQL_BP_DROP, курсор на первом заявлении должен быть открытым.  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 Значение S'LUSMALLINT, которое указывает положение каталога в квалифицированном названии таблицы:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Например, драйвер Xbase возвращает SQL_CL_START, поскольку имя каталога (каталога) находится в начале названия таблицы, как в «EMPDATA»EMP. Dbf. Водитель ORACLE Server возвращает SQL_CL_END, потому что каталог находится ADMIN.EMP@EMPDATAв конце названия таблицы, как в .  
  
 Водитель полного уровня S'L-92 всегда будет возвращаться SQL_CL_START. Значение 0 возвращается, если каталоги не поддерживаются источником данных. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **s'LGetInfo** с SQL_CATALOG_NAME тип информации.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME (ODBc 3.0)  
 Строка символов: "Y", если сервер поддерживает имена каталогов, или "N", если это не так.  
  
 Водитель полного уровня S'L-92 всегда будет возвращать "Y".  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 Строка символов: символ или символ, который источник данных определяет как сепаратор между именем каталога и квалифицированным элементом имени, который следует за ним или предшествует ему.  
  
 Пустая строка возвращается, если каталоги не поддерживаются источником данных. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **s'LGetInfo** с SQL_CATALOG_NAME тип информации. Водитель полного уровня S'L-92 всегда будет возвращаться ".".  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для каталога; например, "база данных" или "каталог". Эта строка может быть в верхнем, нижнем или смешанном случае.  
  
 Пустая строка возвращается, если каталоги не поддерживаются источником данных. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **s'LGetInfo** с SQL_CATALOG_NAME тип информации. Водитель полного уровня S'L-92 всегда будет возвращать "каталог".  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая заявления, в которых можно использовать каталоги.  
  
 Для определения того, где можно использовать каталоги, используются следующие бит-маски:  
  
 SQL_CU_DML_STATEMENTS - Каталоги поддерживаются во всех заявлениях языка манипулирования данными: **SELECT**, **INSERT**, **ОБНОВЛЕНИЕ**, **DELETE**, и при поддержке, **SELECT ДЛЯ ОБНОВЛЕНИЕ** и позиционированные обновления и удаления заявлений.  
  
 SQL_CU_PROCEDURE_INVOCATION - Каталоги поддерживаются в заявлении о вызове процедуры ODBC.  
  
 SQL_CU_TABLE_DEFINITION - Каталоги поддерживаются во всех заявлениях определения таблицы: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE,** **DROP TABLE**и **DROP VIEW**.  
  
 SQL_CU_INDEX_DEFINITION - Каталоги поддерживаются во всех заявлениях определения **индекса: CREATE INDEX** и **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION - Каталоги поддерживаются во всех заявлениях определения привилегий: **GRANT** и **REVOKE**.  
  
 Значение 0 возвращается, если каталоги не поддерживаются источником данных. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **s'LGetInfo** с SQL_CATALOG_NAME тип информации. Водитель с полным уровнем, соответствующий уровню, всегда будет возвращать битную маску со всеми этими битами.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 Название последовательности коллажа. Это строка символов, которая указывает имя сопоставления по умолчанию для набора символов по умолчанию для этого сервера (например, 'ISO 8859-1' или EBCDIC). Если это неизвестно, пустая строка будет возвращена. Водитель полного уровня S'L-92 всегда возвращает непустую строку.  
  
 SQL_COLUMN_ALIAS (ODBC 2.0)  
 Строка символов: "Y", если источник данных поддерживает псевдонимы столбца; в противном случае, "N".  
  
 Псевдоним столбец — это альтернативное имя, которое может быть указано для столбца в списке выбора с помощью оговорки AS. Водитель, отвечающий уровню входа, всегда будет возвращаться "Y".  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1.0)  
 Значение S'LUSMALLINT, которое показывает, как источник данных обрабатывает конкатацию столбцов типа данных значения NULL с не-NULL ценными столбцов типа данных символов:  
  
 SQL_CB_NULL - Результат оценивается.  
  
 SQL_CB_NON_NULL - Результатом является конкатация столбцов или столбцов, не ценных в нейнуле.  
  
 Водитель, отвечающий уровню входа, всегда будет возвращаться SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Битовая маска СЗЛУИНТЕГЕР. Битовая маска указывает на конверсии, поддерживаемые источником данных с функцией **масштабирования CONVERT** для данных типа, названного в *InfoType.* Если битовая маска равна нулю, источник данных не поддерживает никаких конверсий из данных названного типа, включая преобразование в тот же тип данных.  
  
 Например, чтобы определить, поддерживает ли источник данных преобразование SQL_INTEGER данных в SQL_BIGINT тип данных, приложение вызывает **S'LGetInfo** с *InfoType* SQL_CONVERT_INTEGER. Приложение выполняет **и** выполняет и операцию с возвращенной битовой машкой и SQL_CVT_BIGINT. Если полученное значение ненулевое, конверсия поддерживается.  
  
 Для определения того, какие преобразования поддерживаются, используются следующие бит-маски:  
  
 SQL_CVT_BIGINT (ODBC 1.0)SQL_CVT_BINARY (ODBC 1.0)SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5)SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0)SQL_CVT_DECIMAL (ODBC 1.0)SQL_CVT_DOUBLE (ODBC 1) 0)SQL_CVT_FLOAT (ODBC 1.0)SQL_CVT_INTEGER (ODBC 1.0)SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0)SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARCHAR (ODBC 1.0)SQL_CVT_NUMERIC (ODBC 1.0)SQL_ CVT_REAL ODBC 1.0)SQL_CVT_SMALLINT (ODBC 1.0)SQL_CVT_TIME (ODBC 1.0)SQL_CVT_TIMESTAMP (ODBC 1.0)SQL_CVT_TINYINT (ODBC 1.0)SQL_CVT_VARBINARY (ODBC 1.0)SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1.0)  
 Битовая маска S'LUINTEGER, перечисляющая функции конверсии масштабирования, поддерживаемые драйвером и связанным с ним источником данных.  
  
 Для определения того, какие функции преобразования поддерживаются, используется следующая битовая маска:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 Значение S'LUSMALLINT, которое указывает, поддерживаются ли имена корреляции таблицы:  
  
 SQL_CN_NONE имена корреляции не поддерживаются.  
  
 SQL_CN_DIFFERENT - Имена корреляции поддерживаются, но должны отличаться от названий таблиц, которые они представляют.  
  
 SQL_CN_ANY - Имена корреляции поддерживаются и могут быть любым действительным именем, определяемым пользователем.  
  
 Водитель, отвечающий уровню входа, всегда будет возвращаться SQL_CN_ANY.  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE ASSERTION,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Следующие биты указывают на поддерживаемый атрибут ограничения, если поддерживается возможность четкого указания атрибутов ограничения (см. SQL_ALTER_TABLE и SQL_CREATE_TABLE типов информации):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Водитель полного уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой. Возвратное значение "0" означает, что заявление **CREATE ASSERTION** не поддерживается.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE CHARACTER SET,** как это определено в S'L-92, поддерживаемом источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Водитель полного уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой. Значение возврата "0" означает, что заявление **CREATE CHARACTER SET** не поддерживается.  
  
 SQL_CREATE_COLLATION (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE COLLATION,** как это определено в S'L-92, поддерживаемом источником данных.  
  
 Для определения того, какие положения поддерживаются, используется следующая битовая маска:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Водитель полного уровня S'L-92 всегда возвращает эту опцию в соответствии с поддержкой. Значение возврата "0" означает, что заявление **CREATE COLLATION** не поддерживается.  
  
 SQL_CREATE_DOMAIN (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE DOMAIN,** как это определено в S'L-92, поддерживаемая источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_CDO_CREATE_DOMAIN - поддерживается заявление CREATE DOMAIN (средний уровень).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION \<- определение имен с ограничениями> поддерживается для именования ограничений домена (средний уровень).  
  
 Следующие биты указывают возможность создания ограничений столбца: SQL_CDO_DEFAULT - Указание ограничений домена поддерживается (средний уровень) SQL_CDO_CONSTRAINT - Указание домена по умолчанию поддерживается (промежуточный уровень) SQL_CDO_COLLATION - Указано, что коллаж домена поддерживается (полный уровень)  
  
 Следующие биты указывают поддерживаемые атрибуты ограничения, если указано ограничение домена (SQL_CDO_DEFAULT установлено):  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) SQL_CDO_CONSTRAINT_DEFERRABLE (полный уровень) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (полный уровень)  
  
 Значение возврата "0" означает, что заявление **CREATE DOMAIN** не поддерживается.  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE SCHEMA,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Водитель среднего уровня S'L-92 всегда возвращает SQL_CS_CREATE_SCHEMA и SQL_CS_AUTHORIZATION варианты в соответствии с поддержкой. Они также должны поддерживаться на уровне входа в S'L-92, но не обязательно в виде заявлений s'L. Водитель полного уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой.  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE TABLE,** как это определено в S'L-92, поддерживаемая источником данных.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_CT_CREATE_TABLE - поддерживается заявление CREATE TABLE. (Уровень входа)  
  
 SQL_CT_TABLE_CONSTRAINT поддерживается ограничения к таблице уточнения (переходный уровень FIPS)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION - \<Определение определения имени ограничения> поддерживается для именования столбцов и ограничений таблицы (средний уровень)  
  
 Следующие биты указывают возможность создания временных таблиц:  
  
 SQL_CT_COMMIT_PRESERVE - Удаленные строки сохраняются при коммите. (Полный уровень) SQL_CT_COMMIT_DELETE - Удаленные строки удаляются при коммите. (Полный уровень) SQL_CT_GLOBAL_TEMPORARY - могут быть созданы глобальные временные таблицы. (Полный уровень) SQL_CT_LOCAL_TEMPORARY могут быть созданы локальные временные таблицы. (Полный уровень)  
  
 Следующие биты указывают возможность создания ограничений столбца:  
  
 SQL_CT_COLUMN_CONSTRAINT - Поддерживается ограничения столбца (переходный уровень FIPS) SQL_CT_COLUMN_DEFAULT - Поддерживается определение по умолчанию столбца (переходный уровень FIPS) SQL_CT_COLUMN_COLLATION - поддерживаемый коллаж определяющих столбцов (полный уровень)  
  
 Следующие биты указывают на поддерживаемые атрибуты ограничения ограничения, если поддерживается ограничение столбца или таблицы:  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) SQL_CT_CONSTRAINT_DEFERRABLE (полный уровень) SQL_CT_CONSTRAINT_NON_DEFERRABLE (полный уровень)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE TRANSLATION,** как это определено в S'L-92, поддерживаемом источником данных.  
  
 Для определения того, какие положения поддерживаются, используется следующая битовая маска:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Водитель полного уровня S'L-92 всегда будет возвращать эти варианты в соответствии с поддержкой. Возвратное значение "0" означает, что заявление **CREATE TRANSLATION** не поддерживается.  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **CREATE VIEW,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Значение возврата "0" означает, что заявление **CREATE VIEW** не поддерживается.  
  
 Водитель, отвечающий уровню входа, всегда возвращает SQL_CV_CREATE_VIEW и SQL_CV_CHECK_OPTION варианты в соответствии с поддержкой.  
  
 Водитель полного уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 Значение S'LUSMALLINT, которое показывает, как операция **COMMIT** влияет на курсоры и подготовленные операторы в источнике данных (поведение источника данных при совершении транзакции).  
  
 Значение этого атрибута будет отражать текущее состояние следующего параметра: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE - Закрыть курсоры и удалить подготовленные заявления. Чтобы снова использовать курсор, приложение должно переподготовить и перевыполнить заявление.  
  
 SQL_CB_CLOSE - Закрыть курсоры. Для подготовленных инструкций приложение может вызвать **s'LExecute** на выписке, не вызывая **s'LPrepare** снова. По умолчанию для драйвера ODBC является SQL_CB_CLOSE. Это означает, что при совершении транзакции драйвер ODBC закроет курсор.  
  
 SQL_CB_PRESERVE - Сохранить курсоры в том же положении, что и до операции **COMMIT.** Приложение может продолжать получать данные, или оно может закрыть курсор и повторно выполнить заявление без повторной подготовки.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 Значение S'LUSMALLINT, которое показывает, как операция **ROLLBACK** влияет на курсоры и подготовленные операторы в источнике данных:  
  
 SQL_CB_DELETE - Закрыть курсоры и удалить подготовленные заявления. Чтобы снова использовать курсор, приложение должно переподготовить и перевыполнить заявление.  
  
 SQL_CB_CLOSE - Закрыть курсоры. Для подготовленных инструкций приложение может вызвать **s'LExecute** на выписке, не вызывая **s'LPrepare** снова.  
  
 SQL_CB_PRESERVE - Сохранить курсоры в том же положении, что и до операции **ROLLBACK.** Приложение может продолжать получать данные, или оно может закрыть курсор и перевыполнить заявление без его повторной подготовки.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 Значение S-LUINTEGER, которое указывает на поддержку чувствительности курсора:  
  
 SQL_INSENSITIVE - Все курсоры на рукоятке оператора показывают набор результатов, не отражая никаких изменений, внесенных в него любым другим курсором в рамках той же транзакции.  
  
 SQL_UNSPECIFIED не уточняется, вносят ли курсоры на рукоятке оператора видимые изменения, внесенные в результат, установленный другим курсором в рамках той же транзакции. Курсоры на рукоятке оператора могут сделать видимыми ни, ни некоторые, ни все такие изменения.  
  
 SQL_SENSITIVE - Курсоры чувствительны к изменениям, внесенным другими курсорами в рамках той же транзакции.  
  
 Водитель, отвечающий уровню входа, всегда возвращает SQL_UNSPECIFIED вариант в соответствии с поддерживаемым уровнем.  
  
 Водитель полного уровня S'L-92 всегда вернет SQL_INSENSITIVE вариант в соответствии с поддержкой.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1.0)  
 Строка символов с именем источника данных, которая использовалась во время соединения. Если приложение называется **S'LConnect,** это значение аргумента *szDSN.* Если приложение, называемое **S'LDriverConnect** или **S'LBrowseConnect,** это значение ключевого слова DSN в строке соединения, переданной водителю. Если строка соединения не содержит ключевое слово **DSN** (например, когда она содержит ключевое слово **DRIVER),** это пустая строка.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1.0)  
 Строка символов. "Y", если источник данных установлен в режиме READ ONLY, "N", если это иное.  
  
 Эта характеристика относится только к самому источнику данных; это не является характеристикой драйвера, который позволяет получить доступ к источнику данных. Драйвер, который читается/записывается, может использоваться с исходным ресурсом данных, который читается только для чтения. Если водитель читается только по чтению, все его источники данных должны быть прочитаны только и должны вернуться SQL_DATA_SOURCE_READ_ONLY.  
  
 SQL_DATABASE_NAME (ODBC 1.0)  
 Строка символов с именем текущей базы данных, если источник данных определяет названный объект под названием "база данных".  
  
> [!NOTE]
>  В ODBC 3 *.x,* значение, возвращенное для этого *InfoType,* также может быть возвращено, позвонив по **s'LGetConnectAttr** с аргументом *атрибута* SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBc 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая буквы датного времени S'L-92, поддерживаемые источником данных. Обратите внимание, что это буквы дат, перечисленные в спецификации S'L-92, и отделены от буквальных положений о побеге, определенных ODBC. Для получения дополнительной информации о ODBC дата буквального побега положения, см [Дата, Время, и Timestamp Литературы](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Водитель, соответствующий уровню FIPS, всегда возвращает значение "1" в битной маске для битов в следующем списке. Значение "0" означает, что буквы времени датсе S'L-92 не поддерживаются.  
  
 Для определения того, какие буквы поддерживаются, используются следующие бит-маски:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1.0)  
 Строка символов с названием продукта DBMS, доступ к нему осуществляется водителем.  
  
 SQL_DBMS_VER (ODBC 1.0)  
 Строка символов, оточароваваемых на версии продукта DBMS, доступ к нему осуществляется водителем. Версия имеет форму, где первые две цифры являются основной версией, следующие две цифры являются второстепенной версией, а последние четыре цифры — релизной версией. Драйвер должен отобразить версию продукта DBMS в этой форме, но также может прибывать к определенной версии продукта DBMS. Например, "04.01.0000 Rdb 4.1".  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 Значение S-LUINTEGER, указывавое поддержку создания и падения индексов:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1.0)  
 Значение S'LUINTEGER, указывающего уровень изоляции транзакции по умолчанию, поддерживаемый драйвером или источником данных, или ноль, если источник данных не поддерживает транзакции. Для определения уровней изоляции транзакций используются следующие термины:  
  
 **Грязные Читать** Транзакция 1 изменяет строку. Транзакция 2 считывает измененную строку перед транзакцией 1, коммитирует изменение. Если транзакция 1 откатывает изменение, транзакция 2 будет читать строку, которая, как считается, никогда не существовала.  
  
 **Неповторимое чтение** Транзакция 1 читает строку. Транзакция 2 обновляет или удаляет эту строку и фиксирует это изменение. Если транзакция 1 попытается перечитать строку, она получит различные значения строки или обнаружит, что строка была удалена.  
  
 **Фантом** Транзакция 1 считывает набор строк, удовлетворяющих некоторым критериям поиска. Транзакция 2 генерирует одну или несколько строк (через вставки или обновления), которые соответствуют критериям поиска. Если транзакция 1 выполняет оператора, считываемого строки, она получает другой набор строк.  
  
 Если источник данных поддерживает транзакции, водитель возвращает одну из следующих битмас:  
  
 SQL_TXN_READ_UNCOMMITTED - Грязные читает, неповторимые читает, и фантомы возможны.  
  
 SQL_TXN_READ_COMMITTED и грязные чтения невозможны. Возможны неповторимые чтения и фантомы.  
  
 SQL_TXN_REPEATABLE_READ - Грязные чтения и неповторимые чтения невозможны. Фантомы возможны.  
  
 SQL_TXN_SERIALIZABLE - Транзакции можно использовать серийно. Сериализируемые транзакции не позволяют делать грязные чтения, неповторимые чтения или фантомы.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 Строка символов: "Y", если параметры могут быть описаны; "N", если нет.  
  
 Водитель полного уровня S'L-92 обычно возвращается "Y", поскольку он будет поддерживать заявление **DESCRIBE INPUT.** Однако, поскольку это не указывает на прямую поддержку, описывая параметры, даже в драйвере полного уровня S'L-92.  
  
 SQL_DM_VER (ODBC 3.0)  
 Строка символов с версией менеджера драйвера. Версия имеет форму . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .  
  
 Первый набор из двух цифр является основной версией ODBC, как это делается постоянным SQL_SPEC_MAJOR.  
  
 Второй набор из двух цифр является незначительной версией ODBC, как это приводит сяпопостоянная SQL_SPEC_MINOR.  
  
 Третий набор из четырех цифр — это основной номер сборки менеджера драйверов.  
  
 Последний набор из четырех цифр — это номер незначительной сборки менеджера драйверов.  
  
 Версия для менеджера драйверов Windows 7 составляет 03,80. Версия для менеджера драйверов Windows 8 составляет 03,81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 Значение S'LUINTEGER, которое указывает, поддерживает ли пулинг драйвера. (Для получения дополнительной [информации](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)см.  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE указывает на то, что водитель может поддерживать механизм объединения водителей.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE указывает на то, что водитель не может поддерживать механизм объединения водителей.  
  
 Водитель не должен реализовывать SQL_DRIVER_AWARE_POOLING_SUPPORTED и менеджер драйвера не будет соблюдать значение возврата водителя.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 Значение S'LULEN, ручка среды драйвера или ручка соединения, определяемые аргументом *InfoType.*  
  
 Эти типы информации реализуются только менеджером драйверов.  
  
 SQL_DRIVER_HDESC (ODBC 3.0)  
 Значение S-LULEN, дескрипторная ручка драйвера, определяемый дескрипторной ручкой \*менеджера драйвера, которая должна быть передана на входвввввввом *данных infoValuePtr* из приложения. В этом случае *InfoValuePtr* является аргументом ввода и вывода. Ручка дескриптора ввода, пройденное в \* *InfoValuePtr,* должна быть четко или косвенно выделена на *ConnectionHandle.*  
  
 Приложение должно сделать копию дескриптора менеджера драйвера, прежде чем он вызывает **S'LGetInfo** с этим типом информации, чтобы убедиться, что ручка не перезаписана на выходе.  
  
 Этот тип информации реализуется только менеджером драйверов.  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 Значение S'LULEN, *hinst* из библиотеки нагрузки вернулся к менеджеру драйвера, когда он загрузил драйвер DLL на операционной системе Microsoft Windows, или его эквивалент на другой операционной системе. Ручка действительна только для ручки соединения, указанной в вызове в **S'LGetInfo.**  
  
 Этот тип информации реализуется только менеджером драйверов.  
  
 SQL_DRIVER_HSTMT (ODBC 1.0)  
 Значение S'LULEN, ручка выписки драйвера, определяемый ручкой \*оператора драйвера менеджера, которая должна быть передана при входе в *InfoValuePtr* из приложения. В этом случае *InfoValuePtr* является как входиным, так и выходным аргументом. Ручка ввода оператора, пройденное в \* *InfoValuePtr,* должна быть выделена на *аргументе ConnectionHandle.*  
  
 Приложение должно сделать копию оператора драйвера менеджера, прежде чем он вызывает **S'LGetInfo** с этим типом информации, чтобы убедиться, что ручка не перезаписана на выходе.  
  
 Этот тип информации реализуется только менеджером драйверов.  
  
 SQL_DRIVER_NAME (ODBC 1.0)  
 Строка символов с именем файла драйвера, используемого для доступа к источнику данных.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2.0)  
 Строка символов с версией ODBC, которую поддерживает драйвер. Версия имеет форму, где первые две цифры являются основной версией, а следующие две цифры – второстепенной версией. SQL_SPEC_MAJOR и SQL_SPEC_MINOR определяют основные и второстепенные номера версий. Для версии ODBC, описанной в данном руководстве, это 3 и 0, и водитель должен вернуться "03.00".  
  
 Диспетчер драйверов ODBC не будет изменять значение возврата s'LGetInfo (SQL_DRIVER_ODBC_VER) для поддержания обратной совместимости для существующих приложений. Водитель определяет, какое значение будет возвращено. Тем не менее, драйвер, поддерживающий расширение типа C, должен вернуть 3.8 (или выше), когда приложение вызывает **S'LSetEnvAttr,** чтобы установить SQL_ATTR_ODBC_VERSION до 3.8. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 Строка характера с версией драйвера и опционально, описание драйвера. Как минимум, версия имеет форму, где первые две цифры являются основной версией, следующие две цифры являются второстепенной версией, а последние четыре цифры — релизной версией.  
  
 SQL_DROP_ASSERTION (ODBC 3.0)  
 Битовая маска СЗЛЭГЕР, перечисляющая положения в заявлении **DROP ASSERTION,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используется следующая битовая маска:  
  
 SQL_DA_DROP_ASSERTION  
  
 Водитель полного уровня S'L-92 всегда возвращает эту опцию в соответствии с поддержкой.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **DROP CHARACTER SET,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используется следующая битовая маска:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Водитель полного уровня S'L-92 всегда возвращает эту опцию в соответствии с поддержкой.  
  
 SQL_DROP_COLLATION (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **DROP COLLATION,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используется следующая битовая маска:  
  
 SQL_DC_DROP_COLLATION  
  
 Водитель полного уровня S'L-92 всегда возвращает эту опцию в соответствии с поддержкой.  
  
 SQL_DROP_DOMAIN (ODBC 3.0)  
 Битовая маска СЗЛЭГЕР, перечисляющая положения в заявлении **DROP DOMAIN,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Водитель среднего уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой.  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **DROP SCHEMA,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Водитель среднего уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой.  
  
 SQL_DROP_TABLE (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **DROP TABLE,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Водитель, соответствующий уровню FIPS, всегда возвращает все эти варианты в соответствии с поддержкой.  
  
 SQL_DROP_TRANSLATION (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **DROP TRANSLATION,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используется следующая битовая маска:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Водитель полного уровня S'L-92 всегда возвращает эту опцию в соответствии с поддержкой.  
  
 SQL_DROP_VIEW (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **DROP VIEW,** как это определено в S'L-92, поддерживается источником данных.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Водитель, соответствующий уровню FIPS, всегда возвращает все эти варианты в соответствии с поддержкой.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты динамического курсора, поддерживаемого водителем. Эта битовая маска содержит первый подмножество атрибутов; для второго подмноза с SQL_DYNAMIC_CURSOR_ATTRIBUTES2м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA1_NEXT - Аргумент *SQL_FETCH_NEXT fetchOrientation* подтверждается в вызове к **S'LFetchScroll,** когда курсор является динамическим курсором.  
  
 SQL_CA1_ABSOLUTE и *аргументы FetchOrientation* SQL_FETCH_FIRST, SQL_FETCH_LAST и SQL_FETCH_ABSOLUTE поддерживаются при вызове на **S'LFetchScroll,** когда курсор является динамическим курсором. (Набор строк, который будет извлечен, не зависит от текущего положения курсора.)  
  
 SQL_CA1_RELATIVE - *аргументы SQL_FETCH_PRIOR* и SQL_FETCH_RELATIVE FetchOrientation поддерживаются в вызове к **S'LFetchScroll,** когда курсор является динамическим курсором. (Набор строк, который будет извлечен, зависит от текущего положения курсора. Обратите внимание, что это отделено от SQL_FETCH_NEXT потому что в курсоре только вперед, только SQL_FETCH_NEXT поддерживается.)  
  
 SQL_CA1_BOOKMARK - SQL_FETCH_BOOKMARK Аргумент *fetchOrientation* подтверждается в вызове к **S'LFetchScroll,** когда курсор является динамическим курсором.  
  
 SQL_CA1_LOCK_EXCLUSIVE - аргумент *SQL_LOCK_EXCLUSIVE LockType* поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_LOCK_NO_CHANGE - аргумент *SQL_LOCK_NO_CHANGE LockType* поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_LOCK_UNLOCK - аргумент *LockType* SQL_LOCK_UNLOCK поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_POS_POSITION - *Аргумент операции* SQL_POSITION поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_POS_UPDATE : *Аргумент операции* SQL_UPDATE поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_POS_DELETE : *Аргумент операции* SQL_DELETE поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_POS_REFRESH : *Аргумент операции* SQL_REFRESH поддерживается при вызове в **S'LSetPos,** когда курсор является динамическим курсором.  
  
 SQL_CA1_POSITIONED_UPDATE - ОБНОВЛЕНИЕ, где CURRENT of S'L заявление поддерживается, когда курсор является динамическим курсором. (Водитель, отвечающий уровню входа, всегда будет возвращать эту опцию в соответствии с поддержкой.)  
  
 SQL_CA1_POSITIONED_DELETE - DELETE WHERE CURRENT OF S'L- заявление поддерживается, когда курсор является динамическим курсором. (Водитель, отвечающий уровню входа, всегда будет возвращать эту опцию в соответствии с поддержкой.)  
  
 SQL_CA1_SELECT_FOR_UPDATE - заявление SELECT ДЛЯ ОБНОВЛЕНИЕ S'L поддерживается, когда курсор является динамическим курсором. (Водитель, отвечающий уровню входа, всегда будет возвращать эту опцию в соответствии с поддержкой.)  
  
 SQL_CA1_BULK_ADD - *Аргумент SQL_ADD операции* поддерживается при вызове в **S'LBulkOperations,** когда курсор является динамическим курсором.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK - *Аргумент SQL_UPDATE_BY_BOOKMARK операции* поддерживается при вызове в **S'LBulkOperations,** когда курсор является динамическим курсором.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK : *Аргумент операции* SQL_DELETE_BY_BOOKMARK поддерживается в вызове к **S'LBulkOperations,** когда курсор является динамическим курсором.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK : *Аргумент операции* SQL_FETCH_BY_BOOKMARK поддерживается при вызове к **S'LBulkOperations,** когда курсор является динамическим курсором.  
  
 Водитель среднего уровня S'L-92 обычно возвращает SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE варианты в качестве поддержки, поскольку он поддерживает прокрутки курсоры через встроенное заявление S'L FETCH. Однако, поскольку это не определяет непосредственной поддержки S'L, прокрутки курсоры могут не поддерживаться даже для драйвера среднего уровня S'L-92.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты динамического курсора, поддерживаемого водителем. Эта битовая маска содержит второй подмножество атрибутов; для первого подмноза с SQL_DYNAMIC_CURSOR_ATTRIBUTES1м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY поддерживается динамический курсор только для чтения, в котором не допускается никаких обновлений. (Атрибут SQL_ATTR_CONCURRENCY оператора может быть SQL_CONCUR_READ_ONLY для динамического курсора).  
  
 SQL_CA2_LOCK_CONCURRENCY динамический курсор, который использует наименьший уровень блокировки достаточно, чтобы убедиться, что строка может быть обновлена поддерживается. (Атрибут SQL_ATTR_CONCURRENCY оператора может быть SQL_CONCUR_LOCK для динамического курсора.) Эти блокировки должны соответствовать уровню изоляции транзакций, установленному атрибутом SQL_ATTR_TXN_ISOLATION соединения.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY поддерживается динамический курсор, который использует оптимистичный параллелиз-контроль, сравнивая версии строки. (Атрибут SQL_ATTR_CONCURRENCY оператора может быть SQL_CONCUR_ROWVER для динамического курсора.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY поддерживается динамический курсор, который использует оптимистичный параллелический контроль, сравнивая значения. (Атрибут SQL_ATTR_CONCURRENCY оператора может быть SQL_CONCUR_VALUES для динамического курсора.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS - Добавленные строки видны динамическому курсору; курсор может прокрутить к этим строкам. (В тех случаях, когда эти строки добавляются в курсор, зависит от драйвера.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS - Удаленные строки больше не доступны динамическому курсору и не оставляют "дыры" в наборе результатов; после прокрутки динамического курсора из удаленной строки он не может вернуться в эту строку.  
  
 SQL_CA2_SENSITIVITY_UPDATES - Обновления строк видны динамическому курсору; если динамический курсор прокручивается из обновленной строки и возвращается, данные, возвращенные курсором, являются обновленными данными, а не исходными данными.  
  
 SQL_CA2_MAX_ROWS_SELECT - атрибут SQL_ATTR_MAX_ROWS оператора влияет на операторы **SELECT,** когда курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_INSERT - атрибут SQL_ATTR_MAX_ROWS оператора влияет на операторы **INSERT,** когда курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_DELETE - Атрибут SQL_ATTR_MAX_ROWS оператора влияет на операторы **DELETE,** когда курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_UPDATE - атрибут SQL_ATTR_MAX_ROWS оператора влияет на операторы **UPDATE,** когда курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_CATALOG - атрибут SQL_ATTR_MAX_ROWS оператора влияет на наборы результатов **CATALOG,** когда курсор является динамическим курсором.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL - атрибут SQL_ATTR_MAX_ROWS оператора влияет на **SELECT,** **INSERT**, **DELETE**и операторы **UPDATE,** а также наборы результатов **CATALOG,** когда курсор является динамическим курсором.  
  
 SQL_CA2_CRC_EXACT - Точное количество строк доступно в диагностическом поле SQL_DIAG_CURSOR_ROW_COUNT, когда курсор является динамическим курсором.  
  
 SQL_CA2_CRC_APPROXIMATE - Приблизительное количество строк доступно в диагностическом поле SQL_DIAG_CURSOR_ROW_COUNT, когда курсор является динамическим курсором.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE драйвер не гарантирует, что смоделированное позиционирование обновления или удаления операторов повлияет только на одну строку, когда курсор является динамическим курсором; это ответственность приложения, чтобы гарантировать это. (Если выписка затрагивает более одной строки, **s'LExecute** или **S'LExecDirect** возвращает S'Lstate 01001 «Конфликт операции Cursor».) Чтобы установить это поведение, приложение вызывает **S'LSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибутом, установленным для SQL_SC_NON_UNIQUE.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE драйвер пытается гарантировать, что смоделированное позиционированное обновление или удаление операторов повлияет только на одну строку, когда курсор является динамическим курсором. Драйвер всегда выполняет такие операторы, даже если они могут повлиять на более чем одну строку, например, когда нет уникального ключа. (Если выписка затрагивает более одной строки, **s'LExecute** или **S'LExecDirect** возвращает S'Lstate 01001 «Конфликт операции Cursor».) Чтобы установить это поведение, приложение вызывает **S'LSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибутом, установленным на SQL_SC_TRY_UNIQUE.  
  
 SQL_CA2_SIMULATE_UNIQUE драйвер гарантирует, что смоделированные операторы обновления или удаления будут влиять только на одну строку, когда курсор является динамическим курсором. Если драйвер не может гарантировать это для данного оператора, **s'LExecDirect** или **S'LPrepare** возвращают S'LSTATE 01001 (конфликт операции Cursor). Чтобы установить это поведение, приложение вызывает **S'LSetStmtAttr** с SQL_ATTR_SIMULATE_CURSOR атрибутом, установленным SQL_SC_UNIQUE.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 Строка символов: "Y", если источник данных поддерживает выражения в списке **ORDER BY;** "N", если это не так.  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 Значение S'LUSMALLINT, которое показывает, как одноуровневый драйвер непосредственно обрабатывает файлы в источнике данных:  
  
 SQL_FILE_NOT_SUPPORTED - Драйвер не является одноуровневым драйвером. Например, драйвер ORACLE является двухъярусным драйвером.  
  
 SQL_FILE_TABLE - одноуровневый драйвер рассматривает файлы в источнике данных как таблицы. Например, драйвер Xbase рассматривает каждый файл Xbase как таблицу.  
  
 SQL_FILE_CATALOG - одноуровневый драйвер рассматривает файлы в источнике данных как каталог. Например, драйвер Microsoft Access рассматривает каждый файл Microsoft Access как полную базу данных.  
  
 Приложение может использовать это для определения того, как пользователи будут выбирать данные. Например, пользователи Xbase часто думают о данных как о хранимых файлах, в то время как пользователи ORACLE и Microsoft Access обычно считают данные хранящимися в таблицах.  
  
 Когда пользователь выбирает источник данных Xbase, приложение может отображать общий диалоговый ящик Windows **File Open;** когда пользователь выбирает источник данных Microsoft Access или ORACLE, приложение может отображать пользовательский диалоговый ящик **Select Table.**  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты курсора только вперед, поддерживаемого водителем. Эта битовая маска содержит первый подмножество атрибутов; для второго подмноза с SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Для описания этих бит-масок, см SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить "вперед только курсор" для "динамического курсора" в описаниях).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты курсора только вперед, поддерживаемого водителем. Эта битовая маска содержит второй подмножество атрибутов; для первого подмноза, см SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Для описания этих бит-масок, см SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и заменить "вперед только курсор" для "динамического курсора" в описаниях).  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая расширения на **S'LGetData.**  
  
 Следующие бит-маски используются вместе с флагом, чтобы определить, какие общие расширения поддерживает драйвер для **S'LGetData:**  
  
 SQL_GD_ANY_COLUMN s **S'LGetData** можно вызвать для любого несвязанного столбца, в том числе и перед последним столбцом. Обратите внимание, что столбцы должны вызываться в порядке восходящего номера столбца, если SQL_GD_ANY_ORDER также не возвращен.  
  
 SQL_GD_ANY_ORDER **s-LGetData** можно вызывать для несвязанных столбцов в любом порядке. Обратите внимание, что **S'LGetData** может быть вызван только для столбцов после последнего связанного столбца, если SQL_GD_ANY_COLUMN также возвращен.  
  
 SQL_GD_BLOCK **s-LGetData** можно вызвать для неограниченного столбца в любом ряду в блоке (где размер строки больше, чем 1) данных после позиционирования в этот ряд с **S'LSetPos**.  
  
 SQL_GD_BOUND **s-LGetData** можно вызывать для связанных столбцов в дополнение к несвязанным столбцам. Водитель не может вернуть это значение, если оно также не возвращает SQL_GD_ANY_COLUMN.  
  
 SQL_GD_OUTPUT_PARAMS **s-LGetData** можно вызвать для возврата значений параметра вывода. Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SLGetData** обязана возвращать данные только из несвязанных столбцов, которые возникают после последнего связанного столбца, вызываются в порядке увеличения числа столбцов и не находятся в ряду в блоке строк.  
  
 Если драйвер поддерживает закладки (либо фиксированной длины или переменной длины), он должен поддерживать вызов **S'LGetData** на столбец 0. Эта поддержка требуется независимо от того, что водитель возвращает для вызова в **S'LGetInfo** с SQL_GETDATA_EXTENSIONS *InfoType.*  
  
 SQL_GROUP_BY (ODBC 2.0)  
 Значение S'LUSMALLINT, оценивающее взаимосвязь между столбиками в оговорке **GROUP BY** и неагрегированными столбиками в списке выбора:  
  
 SQL_GB_COLLATE пункт **COLLATE** может быть указан в конце каждого столбца группировки. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED и **положения GROUP BY** не поддерживаются. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT - **оговорка GROUP BY** должна содержать все неагрегированные столбцы в списке избранных. Он не может содержать никаких других столбцов. Например, **SELECT DEPT, MAX(SALARY) ОТ EMPLOYEE GROUP BY DEPT**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT - **оговорка GROUP BY** должна содержать все неагрегированные столбцы в списке избранных. Он может содержать столбцы, которые не входят в список избранных. Например, **SELECT DEPT, MAX(SALARY) ОТ EMPLOYEE GROUP BY DEPT, AGE**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION - столбцы в оговорке **GROUP BY** и список выбора не связаны между собой. Значение негруппированных, неагрегированных столбцов в списке выбора зависит от источников данных. Например, **SELECT DEPT, SALARY FROM EMPLOYEE GROUP BY DEPT, AGE**. (ODBC 2.0)  
  
 Водитель, отвечающий уровню входа, всегда вернет SQL_GB_GROUP_BY_EQUALS_SELECT вариант в соответствии с поддержкой. Водитель полного уровня S'L-92 всегда будет возвращать SQL_GB_COLLATE вариант в соответствии с поддержкой. Если ни один из вариантов не поддерживается, положение **GROUP BY** не поддерживается источником данных.  
  
 SQL_IDENTIFIER_CASE (ODBC 1.0)  
 Значение СЗЛУМЛИНТ следующим образом:  
  
 SQL_IC_UPPER идентификаторы в S'L не чувствительны к случаям и хранятся в верхнем регистре в каталоге системы.  
  
 SQL_IC_LOWER идентификаторы в S'L не чувствительны к случаям и хранятся в нижнем регистре в каталоге системы.  
  
 SQL_IC_SENSITIVE идентификаторы в S'L чувствительны к делу и хранятся в смешанном случае в каталоге системы.  
  
 SQL_IC_MIXED идентификаторы в S'L не чувствительны к случаям и хранятся в смешанном случае в каталоге системы.  
  
 Поскольку идентификаторы в S'L-92 никогда не чувствительны к случаям, драйвер, который строго соответствует S'L-92 (любой уровень), никогда не вернет SQL_IC_SENSITIVE вариант в соответствии с поддержкой.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1.0)  
 Строка символов, используемая в качестве стартового и конечного делимитера закавыченного (ограниченного) идентификатора в инструкциях S'L. (Идентификаторы, переданные в качестве аргументов для функций ODBC, не должны быть процитированы.) Если источник данных не поддерживает указанные идентификаторы, возвращается пробел.  
  
 Эта строка символов также может быть использована для цитирования аргументов функции каталога, когда атрибут соединения SQL_ATTR_METADATA_ID установлен на SQL_TRUE.  
  
 Поскольку символ цитаты идентификатора в S'L-92 является двойной отметкой котировок (), драйвер, который строго соответствует S'L-92, всегда возвращает символ двойной отметки котировок.  
  
 SQL_INDEX_KEYWORDS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, которая перечисляет ключевые слова в заявлении CREATE INDEX, которые поддерживаются драйвером:  
  
 SQL_IK_NONE - Ни одно из ключевых слов не поддерживается.  
  
 SQL_IK_ASC и asC ключевое слово поддерживается.  
  
 SQL_IK_DESC и desC ключевое слово поддерживается.  
  
 SQL_IK_ALL - Все ключевые слова поддерживаются.  
  
 Чтобы узнать, поддерживается ли выписка CREATE INDEX, приложение вызывает **s'LGetInfo** с SQL_DLL_INDEX типом информации.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая представления в INFORMATION_SCHEMA, которые поддерживаются водителем. Представления в INFORMATION_SCHEMA и содержание, как это определено в S'L-92.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие представления поддерживаются, используются следующие бит-маски:  
  
 SQL_ISV_ASSERTIONS - определяет утверждения каталога, принадлежащие данному пользователю. (Полный уровень)  
  
 SQL_ISV_CHARACTER_SETS - определяет наборы символов каталога, к которым может получить доступ данный пользователь. (Средний уровень)  
  
 SQL_ISV_CHECK_CONSTRAINTS - определяет ограничения CHECK, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_COLLATIONS - определяет коллайции символов для каталога, к которым может получить доступ данный пользователь. (Полный уровень)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE - Определяет столбцы для каталога, которые зависят от доменов, определенных в каталоге и принадлежащих данному пользователю. (Средний уровень)  
  
 SQL_ISV_COLUMN_PRIVILEGES - Определяет привилегии на столбцах постоянных таблиц, которые доступны или предоставлены данным пользователем. (Переходный уровень FIPS)  
  
 SQL_ISV_COLUMNS - определяет столбцы постоянных таблиц, к которым может получить доступ данный пользователь. (Переходный уровень FIPS)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE - Как и CONSTRAINT_TABLE_USAGE представление, столбцы идентифицируются для различных ограничений, принадлежащих данному пользователю. (Средний уровень)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE - определяет таблицы, которые используются ограничениями (референтные, уникальные и утверждения) и принадлежат данному пользователю. (Средний уровень)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS - определяет ограничения домена (доменов в каталоге), к которым может получить доступ данный пользователь. (Средний уровень)  
  
 SQL_ISV_DOMAINS - определяет домены, определенные в каталоге, к которым может получить доступ пользователь. (Средний уровень)  
  
 SQL_ISV_KEY_COLUMN_USAGE - Идентифицирует столбцы, определенные в каталоге, которые ограничены в качестве ключей для данного пользователя. (Средний уровень)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS - определяет референтные ограничения, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_SCHEMATA - определяет схемы, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_SQL_LANGUAGES - Определяет уровни соответствия, опций и диалектов, поддерживаемых реализацией S'L. (Средний уровень)  
  
 SQL_ISV_TABLE_CONSTRAINTS - определяет ограничения таблицы, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_TABLE_PRIVILEGES - Определяет привилегии на стойких таблицах, которые доступны или предоставлены данным пользователем. (Переходный уровень FIPS)  
  
 SQL_ISV_TABLES - определяет стойкие таблицы, определенные в каталоге, к которым может получить доступ данный пользователь. (Переходный уровень FIPS)  
  
 SQL_ISV_TRANSLATIONS - Определяет переводы символов для каталога, к которым может получить доступ данный пользователь. (Полный уровень)  
  
 SQL_ISV_USAGE_PRIVILEGES - определяет привилегии USE на объектах каталога, которые доступны или принадлежат данному пользователю. (Переходный уровень FIPS)  
  
 SQL_ISV_VIEW_COLUMN_USAGE - определяет столбцы, на которых зависят представления каталога, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_VIEW_TABLE_USAGE - определяет таблицы, на которых зависят представления каталога, принадлежащие данному пользователю. (Средний уровень)  
  
 SQL_ISV_VIEWS - определяет просмотренные таблицы, определенные в этом каталоге, к которым может получить доступ данный пользователь. (Переходный уровень FIPS)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 Битовая маска СЗЛУИНТЕГЕР, которая указывает на поддержку **заявлений INSERT:**  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Водитель, отвечающий уровню входа, всегда будет возвращать все эти опции в соответствии с поддержкой.  
  
 SQL_INTEGRITY (ODBC 1.0)  
 Строка символов: "Y", если источник данных поддерживает Механизм повышения целостности; "N", если это не так.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты курсора ключа, поддерживаемого драйвером. Эта битовая маска содержит первый подмножество атрибутов; для второго подмноза с SQL_KEYSET_CURSOR_ATTRIBUTES2м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Для описания этих бит-масок, см SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить "ключ-управляемый курсор" для "динамического курсора" в описаниях).  
  
 Водитель среднего уровня S'L-92 обычно возвращает SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE варианты в качестве поддержки, потому что драйвер поддерживает прокрутки курсоры через встроенное заявление S'L FETCH. Однако, поскольку это не определяет непосредственной поддержки S'L, прокрутки курсоры могут не поддерживаться даже для драйвера среднего уровня S'L-92.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты курсора ключа, поддерживаемого драйвером. Эта битовая маска содержит второй подмножество атрибутов; для первого подмноза с SQL_KEYSET_CURSOR_ATTRIBUTES1м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Для описания этих бит-масок, см SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить "ключ-управляемый курсор" для "динамического курсора" в описаниях).  
  
 SQL_KEYWORDS (ODBC 2.0)  
 Строка символов, содержащая список разделенных запятой всех ключевых слов, связанных с исходным элементом данных. Этот список не содержит ключевых слов, характерных для ODBC, или ключевых слов, используемых как источником данных, так и ODBC. Этот список представляет все зарезервированные ключевые слова; совместимые приложения не должны использовать эти слова в именах объектов.  
  
 Список ключевых слов ODBC [можно](../../../odbc/reference/appendixes/reserved-keywords.md) узнать в [приложении C: Грамматика S'L.](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) **Значение #define** SQL_ODBC_KEYWORDS содержит список ключевых слов ODBC, разделенных запятой.  
  
 Приложение В. Грамматика SQL  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 Строка символов: "Y", если источник данных поддерживает символ побега для символа процента (%) и подчеркнуть характер (я) в предикате **LIKE** и драйвер поддерживает синтаксис ODBC для определения персонажа побега **like** predicate; "N" в противном случае.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3.0)  
 Значение S'LUINTEGER, которое определяет максимальное количество активных одновременных инструкций в асинхронном режиме, которое драйвер может поддерживать при данном подключении. Если нет определенного предела или предел неизвестен, это значение равно нулю.  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 Значение S'LUINTEGER, которое определяет максимальную длину (количество гексадецимальных символов, за исключением буквальной приставки и суффикса, возвращенного **СЗЛГетИпИнфо**) двоичного буквального в выписке s'L. Например, двоичная буквальная 0xFFAA имеет длину 4. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени каталога в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 Водитель FIPS Full-conformant вернет не менее 128.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 Значение S'LUINTEGER, которое определяет максимальную длину (количество символов, за исключением буквальной приставки и суффикса, возвращенного **s'LGetTypeInfo**) символа буквального в выписке S'L. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени столбца в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 18. Водитель среднего уровня FIPS вернется не менее 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество столбцов, разрешенных в оговорке **GROUP BY.** Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 6. Водитель среднего уровня FIPS вернется не менее 15.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество столбцов, разрешенных в индексе. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество столбцов, разрешенных в пункте **ORDER BY.** Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 6. Водитель среднего уровня FIPS вернется не менее 15.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество столбцов, разрешенных в списке выбора. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернет не менее 100. Водитель среднего уровня FIPS вернется не менее 250.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество столбцов, разрешенных в таблице. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернет не менее 100. Водитель среднего уровня FIPS вернется не менее 250.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество активных инструкций, которые водитель может поддерживать для подключения. Заявление определяется как активное, если в нем ожидаются результаты, с термином "результаты", означающего строки из операции **SELECT** или строки, затронутые **операцией INSERT,** **UPDATE**, или **DELETE** (например, количество строк), или если оно находится в NEED_DATA состоянии. Это значение может отражать ограничение, налагаемое либо драйвером, либо источником данных. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени курсора в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 18. Водитель среднего уровня FIPS вернется не менее 128.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество активных подключений, которые драйвер может поддерживать для среды. Это значение может отражать ограничение, налагаемое либо драйвером, либо источником данных. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 СЗЛУСМЕЛИНТ, указывающий максимальный размер символов, который источник данных поддерживает для имен, определенных пользователем.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 18. Водитель среднего уровня FIPS вернется не менее 128.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 Значение S-LUINTEGER, которое определяет максимальное количество байтов, разрешенных в комбинированных полях индекса. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени процедуры в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 SQL_MAX_ROW_SIZE (ODBC 2.0)  
 Значение S'LUINTEGER, которое определяет максимальную длину одного ряда в таблице. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернет не менее 2000. Водитель среднего уровня FIPS возвращает не менее 8000.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 Строка символов: "Y", если максимальный размер строки, возвращенный для SQL_MAX_ROW_SIZE типа информации, включает длину всех SQL_LONGVARCHAR и SQL_LONGVARBINARY столбцов в строке; "N" в противном случае.  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени схемы в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 18. Водитель среднего уровня FIPS вернется не менее 128.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 Значение S'LUINTEGER, которое определяет максимальную длину (количество символов, включая белое пространство) оператора S'L. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени таблицы в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 18. Водитель среднего уровня FIPS вернется не менее 128.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество таблиц, разрешенных в пункте **FROM** заявления **SELECT.** Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 Водитель, отвечающий уровню FIPS Entry, вернется не менее 15. Водитель среднего уровня FIPS возвращает не менее 50.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2.0)  
 Значение S'LUSMALLINT, которое определяет максимальную длину имени пользователя в источнике данных. Если нет максимальной длины или длина неизвестна, это значение устанавливается до нуля.  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 Строка символов: "Y", если источник данных поддерживает несколько наборов результатов, "N", если это не так.  
  
 Для получения дополнительной информации о нескольких наборах результатов [см.](../../../odbc/reference/develop-app/multiple-results.md)  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1.0)  
 Строка символов: "Y", если драйвер поддерживает более одной активной транзакции одновременно, "N", если только одна транзакция может быть активна в любое время.  
  
 Информация, возвращенная для этого типа информации, не применяется в случае распределенных транзакций.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2.0)  
 Строка символов: "Y", если источнику данных требуется длина длинного значения данных (тип данных SQL_LONGVARCHAR, SQL_LONGVARBINARY или длинный тип данных, специфичный для конкретного источника данных), прежде чем это значение будет отправлено в источник данных , "N", если он этого не делает. Для получения более подробной информации, [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md)см. [SQLBindParameter Function](../../../odbc/reference/syntax/sqlbindparameter-function.md)  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1.0)  
 Значение S'LUSMALLINT, которое определяет, поддерживает ли источник данных НЕ NULL в столбцах:  
  
 SQL_NNC_NULL - Все столбцы должны быть аннулированы.  
  
 SQL_NNC_NON_NULL - колонки не могут быть аннулированы. (Источник данных поддерживает ограничение столбца **NOT NULL** в **заявлениях CREATE TABLE.)**  
  
 Водитель, отвечающий уровню входа, вернется SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 Значение СЛЮСМУЛМИНТ, которое указывает, где nULLs сортируются в наборе результатов:  
  
 SQL_NC_END nULL сортируются в конце набора результатов, независимо от ключевых слов ASC или DESC.  
  
 SQL_NC_HIGH nULLs сортируются на высоком конце набора результатов, в зависимости от ключевых слов ASC или DESC.  
  
 SQL_NC_LOW nULL сортируются на низком конце набора результатов, в зависимости от ключевых слов ASC или DESC.  
  
 SQL_NC_START nULL сортируются в начале набора результатов, независимо от ключевых слов ASC или DESC.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1.0)  
 Примечание: Информационный тип был введен в ODBC 1.0; каждая битовая маска помечена версией, в которой она была введена.  
  
 Битовая маска S'LUINTEGER, перечисляющая масштабальные числовые функции, поддерживаемые драйвером и связанным с ним источником данных.  
  
 Для определения численных функций используются следующие битмаски:  
  
 SQL_FN_NUM_ABS (ODBC 1.0)SQL_FN_NUM_ACOS (ODBC 1.0)SQL_FN_NUM_ASIN (ODBC 1.0)SQL_FN_NUM_ATAN (ODBC 1.0)SQL_FN_NUM_ATAN2 (ODBC 1.0)SQL_FN_NUM_CEILING (ODBC 1.0)SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 2.0)SQL_FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (SQL_FN_ SQL_FN_NUM_LOG10 ODBC 1.0) NUM_MOD (ODBC 1.0)SQL_FN_NUM_PI (ODBC 1.0)SQL_FN_NUM_POWER (ODBC 2.0)SQL_FN_NUM_RADIANS (ODBC 2.0)SQL_FN_NUM_RAND (ODBC 1.0)SQL_FN_NUM_ROUND (ODBC 2.0)SQL_FN_NUM_SIGN (ODBC 1.0)SQL_FN_NUM_SIN (ODBC 1.0)SQL_FN_NUM_SQRT (ODBC 1.0)SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3.0)  
 Значение S'LUINTEGER, которое указывает уровень интерфейса ODBC 3 *.x,* который соответствует требованиям драйвера.  
  
 SQL_OIC_CORE: Минимальный уровень, который должны соблюдать все драйверы ODBC. Этот уровень включает в себя основные элементы интерфейса, такие как функции соединения, функции для подготовки и выполнения оператора S'L, основные функции метаданных, основные функции каталога и так далее.  
  
 SQL_OIC_LEVEL1: уровень, включающая функциональность уровня соответствия основным стандартам, а также прокрутки курсоров, закладки, позиционированные обновления и удаления и так далее.  
  
 SQL_OIC_LEVEL2: уровень, включающая функциональность уровня соответствия стандартам уровня 1, а также расширенные функции, такие как чувствительные курсоры; обновление, удаление и обновление закладками; поддержка процедуры хранения; функции каталога для первичных и иностранных ключей; мультикаталогная поддержка; и так далее.  
  
 Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/interface-conformance-levels.md)  
  
 SQL_ODBC_VER (ODBC 1.0)  
 Строка символов с версией ODBC, к которой соответствует менеджер драйвера. Версия имеет форму ..0000, где первые две цифры являются основной версией, а следующие две цифры являются второстепенной версией. Это реализовано только в менеджере драйвера.  
  
 SQL_OJ_CAPABILITIES (ODBC 2.01)  
 Битовая маска S'LUINTEGER, перечисляющая типы внешних соединений, поддерживаемых драйвером и источником данных. Для определения того, какие типы поддерживаются, используются следующие битмаски:  
  
 SQL_OJ_LEFT - поддерживаются левые внешние соединения.  
  
 SQL_OJ_RIGHT - поддерживаются правые внешние соединения.  
  
 SQL_OJ_FULL - поддерживаются полные внешние соединения.  
  
 SQL_OJ_NESTED - поддерживаются вложенные внешние соединения.  
  
 SQL_OJ_NOT_ORDERED - Названия столбцов в пункте ON внешнего соединения не должны быть в том же порядке, что и их имена таблиц в пункте **OUTER JOIN.**  
  
 SQL_OJ_INNER - Внутренняя таблица (правая таблица в левом внешнем соединении или левая таблица в правом внешнем соединении) также может быть использована во внутреннем соединении. Это не относится к полным внешним соединениям, которые не имеют внутренней таблицы.  
  
 SQL_OJ_ALL_COMPARISON_OPS - Оператором сравнения в оговорке ON может быть любой из операторов сравнения ODBC. Если этот бит не установлен, то в внешних соединениях можно использовать только оператора сравнения равных (кв) .  
  
 Если ни один из этих вариантов не возвращается в качестве поддержки, ни одно внешнее предложение о присоединении не поддерживается.  
  
 Информацию о поддержке реляционных операторов можно узнать в выписке SELECT, определяемой S'L-92, с SQL_SQL92_RELATIONAL_JOIN_OPERATORSм.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2.0)  
 Строка символов: "Y", если столбцы в оговорке **ORDER BY** должны быть в списке выбора; в противном случае, "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3.0)  
 СЗЛУИНТЕГЕР, перечисляющий свойства драйвера относительно наличия строки, учитывается в параметризированном исполнении. Имеет следующие значения:  
  
 SQL_PARC_BATCH - Для каждого набора параметров доступны индивидуальные строки. Это концептуально эквивалентно драйверу, генерирующего пакет инструкций s'L, по одному для каждого параметра, установленного в массиве. Расширенная информация об ошибке может быть получена с помощью поля SQL_PARAM_STATUS_PTR дескриптора.  
  
 SQL_PARC_NO_BATCH - Доступно только одно количество строк, которое представляет собой кумулятивное количество строк, полученное в результате выполнения оператора для всего массива параметров. Это концептуально эквивалентно обработке оператора вместе с полным набором параметров как одной атомной единицей. Ошибки обрабатываются так же, как если бы одна выписка была выполнена.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 СЗЛУИНТЕГЕР, перечисляющий свойства драйвера относительно наличия результатов, устанавливает параметризированное выполнение. Имеет следующие значения:  
  
 SQL_PAS_BATCH - Существует один набор результатов, доступных на набор параметров. Это концептуально эквивалентно драйверу, генерирующего пакет инструкций s'L, по одному для каждого параметра, установленного в массиве.  
  
 SQL_PAS_NO_BATCH - Существует только один набор результатов, который представляет собой набор совокупных результатов, возникающих в результате выполнения оператора для полного массива параметров. Это концептуально эквивалентно обработке оператора вместе с полным набором параметров как одной атомной единицей.  
  
 SQL_PAS_NO_SELECT драйвер не позволяет выполнять генерирующую выписку по набору результатов с набором параметров.  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для процедуры; например, "процедура базы данных", "процедура хранения", "процедура", "пакет" или "сохраненный запрос".  
  
 SQL_PROCEDURES (ODBC 1.0)  
 Строка символов: "Y", если источник данных поддерживает процедуры, а драйвер поддерживает синтаксис вызова процедуры ODBC; "N" в противном случае.  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 Битовая маска S'LINTEGER, перечисляющая операции поддержки в **S'LSetPos.**  
  
 Следующие бит-маски используются вместе с флагом, чтобы определить, какие варианты поддерживаются.  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2.0)  
 Значение СЗЛУМЛИНТ следующим образом:  
  
 SQL_IC_UPPER - Указанные идентификаторы в S'L не чувствительны к случаям и хранятся в верхнем регистре в каталоге системы.  
  
 SQL_IC_LOWER - Указанные идентификаторы в S'L не чувствительны к случаям и хранятся в нижнем регистре в каталоге системы.  
  
 SQL_IC_SENSITIVE игноеи в S'L чувствительны к делу и хранятся в смешанном случае в каталоге системы. (В базе данных, соответствующей требованиям S'L-92, указанные идентификаторы всегда чувствительны к случаям.)  
  
 SQL_IC_MIXED - Указанные идентификаторы в S'L не чувствительны к случаям и хранятся в смешанном случае в каталоге системы.  
  
 Водитель, отвечающий уровню входа, всегда будет возвращаться SQL_IC_SENSITIVE.  
  
 SQL_ROW_UPDATES (ODBC 1.0)  
 Строка символов: "Y", если клавиша или смешанный курсор поддерживает строки версии или значения для всех извлеченных строк и, следовательно, может обнаружить любые обновления, которые были сделаны в строку любым пользователем, так как строка была в последний раз извлечены. (Это относится только к обновлениям, а не к удалениям или вставкам.) Водитель может вернуть SQL_ROW_UPDATED флаг в массив состояния строки при вызове **S'LFetchScroll.** В противном случае, "N".  
  
 SQL_SCHEMA_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для схемы; например, "владелец", "Удостоверение личности авторизации" или "Схема".  
  
 Строка символов может быть возвращена в верхнем, нижнем или смешанном корпусе.  
  
 Водитель, отвечающий уровню входа, всегда будет возвращать «схему».  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая операторы, в которых могут быть использованы схемы:  
  
 SQL_SU_DML_STATEMENTS - Схемы поддерживаются во всех заявлениях языка манипулирования данными: **SELECT**, **INSERT**, **ОБНОВЛЕНИЕ**, **DELETE**, и при поддержке, **SELECT ДЛЯ ОБНОВЛЕНИЕ** и позиционированные обновления и удаления заявлений.  
  
 SQL_SU_PROCEDURE_INVOCATION - Схемы поддерживаются в заявлении о вызове процедуры ODBC.  
  
 SQL_SU_TABLE_DEFINITION - Схемы поддерживаются во всех заявлениях определения таблицы: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE,** **DROP TABLE**и **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION - Схемы поддерживаются во всех заявлениях определения **индекса: CREATE INDEX** и **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION - Схемы поддерживаются во всех заявлениях о определении привилегий: **GRANT** и **REVOKE**.  
  
 Водитель, отвечающий уровню входа, всегда возвращает SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION и SQL_SU_PRIVILEGE_DEFINITION варианты в соответствии с поддержкой.  
  
 Этот *InfoType* был переименован в ODBC 3.0 от ODBC 2.0 *InfoType* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS (ODBC 1.0)  
 Примечание: Информационный тип был введен в ODBC 1.0; каждая битовая маска помечена версией, в которой она была введена.  
  
 Битовая маска S'LUINTEGER, перечисляющая параметры прокрутки, поддерживаемые для прокрутки курсоров.  
  
 Для определения того, какие параметры поддерживаются, используются следующие битмаски:  
  
 SQL_SO_FORWARD_ONLY - Курсор только прокручивается вперед. (ODBC 1.0)  
  
 SQL_SO_STATIC - данные в наборе результатов статичны. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN - Драйвер сохраняет и использует клавиши для каждой строки в наборе результатов. (ODBC 1.0)  
  
 SQL_SO_DYNAMIC - Драйвер сохраняет ключи для каждой строки в наборе (размер ключа совпадает с размером рядового набора). (ODBC 1.0)  
  
 SQL_SO_MIXED - Драйвер сохраняет ключи для каждой строки в клавиатуре, а размер ключа больше, чем размер рядового. Курсор является ключом-управляемым внутри клавиатуры и динамическим за пределами клавиатуры. (ODBC 1.0)  
  
 Для получения информации о прокрутки курсоры, см [Прокрутки Курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1.0)  
 Строка символов, определяющая, что драйвер поддерживает в качестве символа побега, что позволяет использовать метасимволы соответствия шаблона, подчеркивая (я) и знак процента (%) действительные символы в поисковых шаблонах. Этот символ побега применяется только для тех аргументов функции каталога, которые поддерживают строки поиска. Если эта строка пуста, драйвер не поддерживает символ побега поискового шаблона.  
  
 Поскольку этот тип информации не указывает на общую поддержку символа побега в предикате **LIKE,** S'L-92 не включает требования к этой строке символов.  
  
 Этот *InfoType* ограничен функциями каталога. Для описания использования персонажа побега в строках шаблона поиска [см.](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
 SQL_SERVER_NAME (ODBC 1.0)  
 Строка символов с фактическим именем сервера, конкретного источника данных; полезно, когда имя источника данных используется во время **S'LConnect,** **S'LDriverConnect,** и **S'LBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2.0)  
 Строка символов, содержащая все специальные символы (т.е. все символы, кроме z, A through, a through, 0 до 9, и подчеркивать), которая может быть использована в идентификаторе, например, имя таблицы, имя столбца или имя индекса, на источнике данных. Например, "З$". Если идентификатор содержит один или несколько из этих символов, идентификатор должен быть разграниченным идентификатором.  
  
 SQL_SQL_CONFORMANCE (ODBC 3.0)  
 Значение S-LUINTEGER, указывававание уровня S'L-92, поддерживаемого водителем:  
  
 SQL_SC_SQL92_ENTRY - Входной уровень S'L-92 соответствует.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL - FIPS 127-2 переходный уровень совместим.  
  
 SQL_SC_SQL92_FULL - Полностью соответствует полууровню S'L-92.  
  
 SQL_SC_ SQL92_INTERMEDIATE - промежуточный уровень S'L-92.  
  
 SQL_SQL92_DATETIME_FUNCTIONS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая функции времени времени времени времени, которые поддерживаются драйвером и соответствующим источником данных, как это определено в S'L-92.  
  
 Для определения того, какие функции дата поддержки поддерживаются, используются следующие бит-маски:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая правила, поддерживаемые для иностранного ключа в заявлении **DELETE,** как это определено в S'L-92.  
  
 Для определения того, какие положения поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Водитель, соответствующий уровню FIPS, всегда возвращает все эти варианты в соответствии с поддержкой.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая правила, поддерживаемые для иностранного ключа, в заявлении **UPDATE,** как это определено в s'L-92.  
  
 Для определения того, какие положения поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Водитель полного уровня S'L-92 всегда будет возвращать все эти варианты в соответствии с поддержкой.  
  
 SQL_SQL92_GRANT (ODBC 3.0)  
 Битовая маска СЗЛ-92, перечисляющая положения, подтвержденные в заявлении **GRANT,** как это определено в S'L-92.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SG_DELETE_TABLE (Уровень входа) SQL_SG_INSERT_COLUMN (средний уровень)SQL_SG_INSERT_TABLE (уровень входа) SQL_SG_REFERENCES_TABLE (уровень входа) SQL_SG_REFERENCES_COLUMN (уровень входа)SQL_SG_SELECT_TABLE (уровень входа) SQL_SG_UPDATE_COLUMN (уровень входа)SQL_SG_UPDATE_TABLE (Уровень входа) SQL_SG_USAGE_ON_DOMAIN (переходный уровень FIPS)SQL_SG_USAGE_ON_CHARACTER_SET (переходный уровень FIPS)SQL_SG_USAGE_ON_COLLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION (переходный уровень FIPS)SQL_SG_USAGE_ON_TRANSLATION уровень) SQL_SG_WITH_GRANT_OPTION (уровень входа)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS (ODBc 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая функции масштабирования значений, которые поддерживаются драйвером и соответствующим источником данных, как это определено в S'L-92.  
  
 Для определения численных функций используются следующие битмаски:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая предикаты, поддерживаемые в заявлении **SELECT,** как это определено в S'L-92.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие параметры поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SP_BETWEEN (Уровень входа) SQL_SP_COMPARISON (уровень входа) SQL_SP_EXISTS (уровень входа) SQL_SP_IN (Уровень входа) SQL_SP_ISNOTNULL (уровень входа)SQL_SP_ISNULL (Уровень входа) SQL_SP_LIKE (Уровень входа)SQL_SP_MATCH_FULL (Полный уровень)SQL_SP_MATCH_PARTIAL (Полный уровень) SQL_SP_MATCH_UNIQUE_FULL (Полный уровень) SQL_SP_MATCH_UNIQUE_PARTIAL (Полный уровень)SQL_SP_OVERLAPS (Уровень начального) SQL_SP_QUANTIFIED_COMPARISON (Уровень входа) SQL_SP_UNIQUE (Уровень входа)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая реляционные операторы, поддерживаемые в заявлении **SELECT,** как это определено в S'L-92.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие параметры поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (средний уровень) SQL_SRJO_CROSS_JOIN (полный уровень) SQL_SRJO_EXCEPT_JOIN (средний уровень) SQL_SRJO_FULL_OUTER_JOIN (промежуточный уровень) SQL_SRJO_INNER_JOIN (переходный уровень FIPS) SQL_SRJO_INTERSECT_JOIN (промежуточный уровень) SQL_SRJO_LEFT_OUTER_JOIN (переходный уровень FIPS) SQL_SRJO_NATURAL_JOIN (переходный уровень FIPS) SQL_SRJO_RIGHT_OUTER_JOIN (Переходный уровень FIPS) SQL_SRJO_UNION_JOIN (полный уровень)  
  
 SQL_SRJO_INNER_JOIN указывает на поддержку синтаксиса **INNER JOIN,** а не для внутреннего соединения. Поддержка синтаксиса **INNER JOIN** – это FIPS TRANSITIONAL, в то время как поддержка внутреннего соединения **entry**.  
  
 SQL_SQL92_REVOKE (ODBC 3.0)  
 Битовая маска СЗЛ-ИЗЛ, перечисляющая положения, подтвержденные в заявлении **REVOKE,** как это определено в S'L-92, поддерживается источником данных.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SR_CASCADE (переходный уровень FIPS) SQL_SR_DELETE_TABLE (уровень входа) SQL_SR_GRANT_OPTION_FOR (средний уровень) SQL_SR_INSERT_COLUMN (уровень среднего) SQL_SR_INSERT_TABLE (уровень входа) SQL_SR_REFERENCES_COLUMN (уровень входа) SQL_SR_REFERENCES_TABLE (уровень входа) SQL_SR_RESTRICT (уровень начального(начального уровня) SQL_SR_SELECT_TABLE (уровень входа) SQL_SR_UPDATE_COLUMN (уровень входа) SQL_SR_UPDATE_TABLE (уровень входа) SQL_SR_USAGE_ON_DOMAIN (уровень FIPS Transitional)SQL_SR_USAGE_ON_CHARACTER_ SET (Переходный уровень FIPS) SQL_SR_USAGE_ON_COLLATION (Переходный уровень FIPS) SQL_SR_USAGE_ON_TRANSLATION (переходный уровень FIPS)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая выражения конструктора значений строки, поддерживаемые в заявлении **SELECT,** как это определено в S'L-92. Для определения того, какие параметры поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая функции масштабирования строки, которые поддерживаются драйвером и соответствующим источником данных, как это определено в S'L-92.  
  
 Для определения того, какие функции строки поддерживаются, используются следующие бит-маски:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая поддерживаемые выражения значений, как это определено в S'L-92.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие параметры поддерживаются источником данных, используются следующие битмаски:  
  
 SQL_SVE_CASE (средний уровень) SQL_SVE_CAST (переходный уровень FIPS)SQL_SVE_COALESCE (средний уровень) SQL_SVE_NULLIF (средний уровень)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая стандарт CLI или стандарты, которым соответствует водитель. Следующие бит-маски используются для определения того, какие уровни водитель соответствует:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Водитель соответствует версии CLI Open Group.  
  
 SQL_SCC_ISO92_CLI: Водитель соблюдает ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты статического курсора, поддерживаемого драйвером. Эта битовая маска содержит первый подмножество атрибутов; для второго подмноза с SQL_STATIC_CURSOR_ATTRIBUTES2м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Для описания этих бит-масок, см. SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и заменить "статический курсор" для "динамического курсора" в описаниях).  
  
 Водитель среднего уровня S'L-92 обычно возвращает SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE варианты в качестве поддержки, потому что драйвер поддерживает прокрутки курсоры через встроенное заявление S'L FETCH. Однако, поскольку это не определяет непосредственной поддержки S'L, прокрутки курсоры могут не поддерживаться даже для драйвера среднего уровня S'L-92.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 Битовая маска S'LUINTEGER, описывающая атрибуты статического курсора, поддерживаемого драйвером. Эта битовая маска содержит второй подмножество атрибутов; для первого подмноза с SQL_STATIC_CURSOR_ATTRIBUTES1м.  
  
 Для определения того, какие атрибуты поддерживаются, используются следующие бит-маски:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Для описания этих бит-масок, см SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и заменить "статический курсор" для "динамического курсора" в описаниях).  
  
 SQL_STRING_FUNCTIONS (ODBC 1.0)  
 Примечание: Информационный тип был введен в ODBC 1.0; каждая битовая маска помечена версией, в которой она была введена.  
  
 Битовая маска S'LUINTEGER, перечисляющая функции строки scalar, поддерживаемые драйвером и связанным с ним источником данных.  
  
 Для определения того, какие функции строки поддерживаются, используются следующие бит-маски:  
  
 SQL_FN_STR_ASCII (ODBC 1.0)SQL_FN_STR_BIT_LENGTH (ODBC 3.0)SQL_FN_STR_CHAR (ODBC 1.0)SQL_FN_STR_CHAR_LENGTH (ODBC 3.0)SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0)SQL_FN_STR_CONCAT (ODBC 1.0)SQL_FN_STR_DIFFERENCE (ODBC 2.0)SQL_FN_STR_INSERT (ODBC 1.0)SQL_FN_STR_LCASE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0 SQL_FN_STR_LTRIM) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) ( 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0)SQL_FN_STR_REPEAT (ODBC 1.0)SQL_FN_STR_REPLACE (ODBC 1.0)SQL_FN_STR_RIGHT (ODBC 1.0)SQL_FN_STR_RTRIM (ODBC 1.0)SQL_FN_STR_SOUNDEX (ODBC 2.0)SQL_FN_STR_SPACE (ODBC 1.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0)  
  
 Если приложение может вызвать функцию **scalar LOCATE** с *string_exp1,* *string_exp2,* и *начать* аргументы, водитель возвращает SQL_FN_STR_LOCATE битную маску. Если приложение может вызвать функцию scalar LOCATE только с *string_exp1* и *string_exp2* аргументами, водитель возвращает SQL_FN_STR_LOCATE_2 битную маску. Драйверы, полностью поддерживающие функцию **масштабирования LOCATE,** возвращают обе битмаски.  
  
 (Для получения дополнительной информации см. [Функции строки](../../../odbc/reference/appendixes/string-functions.md) в приложении E, "Функции scalar.")  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая предикаты, поддерживающие подзапросы:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 SQL_SQ_CORRELATED_SUBQUERIES битмаска указывает на то, что все предикаты, поддерживающие подзапросы, поддерживают коррелированные подзапросы.  
  
 Водитель, отвечающий уровню входа, всегда будет возвращать битную маску, в которой установлены все эти биты.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1.0)  
 Битовая маска S'LUINTEGER, перечисляющая функции системы масштабирования, поддерживаемые драйвером и связанным с ним источником данных.  
  
 Для определения того, какие системные функции поддерживаются, используются следующие бит-маски:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1.0)  
 Строка символов с именем поставщика источника данных для таблицы; например, "стол" или "файл".  
  
 Эта строка символов может быть в верхнем, нижнем или смешанном случае.  
  
 Водитель, отвечающий уровню входа, всегда будет возвращаться к «столу».  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая интервалы временных меток, поддерживаемые драйвером и связанным с ним источником данных для функции масштабирования TIMESTAMPADD.  
  
 Для определения того, какие интервалы поддерживаются, используются следующие битмаски:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Водитель, соответствующий уровню FIPS, всегда возвращает битмаску, в которой установлены все эти биты.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая интервалы временных меток, поддерживаемые драйвером и связанным с ним источником данных для функции масштабирования TIMESTAMPDIFF.  
  
 Для определения того, какие интервалы поддерживаются, используются следующие битмаски:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Водитель, соответствующий уровню FIPS, всегда возвращает битмаску, в которой установлены все эти биты.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1.0)  
 Примечание: Информационный тип был введен в ODBC 1.0; каждая битовая маска помечена версией, в которой она была введена.  
  
 Битовая маска S'LUINTEGER, перечисляющая функции даты и времени масштабирования, поддерживаемые драйвером и связанным с ним источником данных.  
  
 Для определения того, какие функции даты и времени поддерживаются, используются следующие бит-маски:  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0)SQL_FN_TD_CURRENT_TIME (ODBC 3.0)SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0)SQL_FN_TD_CURDATE (ODBC 1.0)SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0)SQL_FN_TD_DAYOFMONTH (ODBC 1.0)SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) (ODBC 1.SQL_FN_TD_MONTH 0 SQL_FN_TD_MINUTE) 1.0)SQL_FN_TD_MONTHNAME (ODBC 2.0)SQL_FN_TD_NOW (ODBC 1.0)SQL_FN_TD_QUARTER (ODBC 1.0)SQL_FN_TD_SECOND (ODBC 1.0)SQL_FN_TD_TIMESTAMPADD (ODBC 2.0)SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0)SQL_FN_TD_WEEK (ODBC 1.0)SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE (ODBC 1.0)  
 Примечание: Информационный тип был введен в ODBC 1.0; каждое значение возврата помечено версией, в которой оно было введено.  
  
 Значение S'LUSMALLINT, описывающее поддержку транзакции в драйвере или источнике данных:  
  
 SQL_TC_NONE и транзакции не поддерживаются. (ODBC 1.0)  
  
 SQL_TC_DML - Транзакции могут содержать только язык манипулирования данными (DML) заявления **(SELECT**, **INSERT**, **ОБНОВЛЕНИЕ**, **DELETE**). Язык определения данных (DDL), обнаруженные в транзакции, вызывает ошибку. (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT транзакции могут содержать только DML-выписки. DDL-выписки **(CREATE TABLE,** **DROP INDEX**и т.д.), возникающие в транзакции, приводят к совершению транзакции. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE транзакции могут содержать только DML-выписки. Заявления DDL, возникающие в транзакции, игнорируются. (ODBC 2.0)  
  
 SQL_TC_ALL транзакции могут содержать dDL-выписки и DML-выписки в любом порядке. (ODBC 1.0)  
  
 (Поскольку поддержка транзакций является обязательной в S'L-92, конформистский драйвер S'L-92 никогда не вернется SQL_TC_NONE.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1.0)  
 Битовая маска S'LUINTEGER, перечисляющая уровни изоляции транзакций, доступные из драйвера или источника данных.  
  
 Следующие бит-маски используются вместе с флагом, чтобы определить, какие варианты поддерживаются:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Описания этих уровней изоляции можно SQL_DEFAULT_TXN_ISOLATION см.  
  
 Чтобы установить уровень изоляции транзакций, приложение вызывает **S'LSetConnectAttr,** чтобы установить SQL_ATTR_TXN_ISOLATION атрибут. Для получения дополнительной информации, [см.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
 Водитель, отвечающий уровню входа, всегда будет возвращаться SQL_TXN_SERIALIZABLE в соответствии с поддержкой. Водитель, соответствующий уровню FIPS, всегда возвращает все эти варианты в соответствии с поддержкой.  
  
 SQL_UNION (ODBC 2.0)  
 Битовая маска СЗЛУИНТЕГЕР, перечисляющая поддержку положения **UNION:**  
  
 SQL_U_UNION - Источник данных поддерживает положение **UNION.**  
  
 SQL_U_UNION_ALL - Источник данных поддерживает **ВСЕ** ключевое слово в оговорке **UNION.** ( В данном случае **«СЗЛГетИнфо»** возвращает сяи как SQL_U_UNION, так и SQL_U_UNION_ALL.)  
  
 Водитель, отвечающий уровню входа, всегда будет возвращать оба этих варианта в соответствии с поддержкой.  
  
 SQL_USER_NAME (ODBC 1.0)  
 Строка символов с именем, используемым в определенной базе данных, которая может отличаться от имени входа.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3.0)  
 Строка символов, оточаровающая год публикации спецификации Open Group, с которой полностью соответствует версия менеджера драйверов ODBC.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 Строка символов: "Y", если пользователь может выполнить все процедуры, возвращенные **S'LProcedures;** "N", если могут быть возвращены процедуры, которые пользователь не может выполнить.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 Строка символов: "Y", если пользователю гарантированы привилегии **SELECT** для всех таблиц, возвращенных **S'LTables;** "N", если могут быть возвращены таблицы, к которым пользователь не может получить доступ.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Значение S'LUSMALLINT, которое определяет максимальное количество активных сред, которые может поддерживать драйвер. Если нет указанного предела или ограничение неизвестно, это значение устанавливается до нуля.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая поддержку функций агрегирования:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Водитель, отвечающий уровню входа, всегда будет возвращать все эти опции в соответствии с поддержкой.  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 Битовая маска СЗЛЭГЕР, перечисляющая положения в заявлении **ALTER DOMAIN,** как это определено в S'L-92, поддерживается источником данных. Водитель полного уровня S'L-92 всегда будет возвращать все битмаски. Значение возврата "0" означает, что заявление **ALTER DOMAIN** не поддерживается.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT- Добавление ограничения домена поддерживается (полный уровень)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT \<- изменить \<положение о домене> набор домена по умолчанию> поддерживается (полный уровень)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION \<- оговорка об определении имен ограничений> поддерживается для определения ограничения домена (средний уровень)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT \<- оговорка о ограничении домена> поддерживается (полный уровень)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT \<- изменять пункт о домене> \<домена по умолчанию> поддерживается (полный уровень)  
  
 Следующие биты указывают \<поддерживаемые атрибуты \<ограничения>, если поддерживается ограничение домена> (набор SQL_AD_ADD_DOMAIN_CONSTRAINT бита):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)  
  
 SQL_ALTER_TABLE (ODBc 2.0)  
 Битовая маска S'LUINTEGER, перечисляющая положения в заявлении **ALTER TABLE,** поддерживаемом источником данных.  
  
 Уровень соответствия S'L-92 или FIPS, на котором эта функция должна быть поддержана, отображается в скобках рядом с каждой битовой маской.  
  
 Для определения того, какие положения поддерживаются, используются следующие бит-маски:  
  
 SQL_AT_ADD_COLUMN_COLLATION \<и добавить столбец> оговорка поддерживается, с возможностью указать столбец коллажа (полный уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT \<- добавить столбец> оговорка поддерживается, с возможностью указать столбец по умолчанию (FiPS Переходный уровень) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE \<- добавить столбец> поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT \<- добавить столбец> оговорка поддерживается, с возможностью указать ограничения столбца (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT \<- добавить ограничение таблицы> положение поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION \<- определение определения ограниченного имени> поддерживается для именования столбцов и ограничений таблицы (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE \<столбец падения> casCADE поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT \<- изменить \<столбец> оговорку о снижении столбца по умолчанию> поддерживается (средний уровень) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT \<- колонка падения> RESTRICT поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT \<столбец падения> RESTRICT поддерживается (переходный уровень FIPS) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT \<- изменить \<столбец> набор столбец по умолчанию> поддерживается (средний уровень) (ODBC 3.0)  
  
 Следующие биты указывают \<атрибуты ограничения поддержки>, поддерживается ли ограничение столбца или таблицы (SQL_AT_ADD_CONSTRAINT бит установлен):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (полный уровень) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (полный уровень) (ODBC 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 Значение S-LUINTEGER, которое указывает уровень асинхронной поддержки в драйвере:  
  
 SQL_AM_CONNECTION поддерживается асинхронное исполнение уровня соединения. Все ручки оператора, связанные с данной ручкой соединения, находятся в асинхронном режиме, либо все они находятся в синхронном режиме. Ручка оператора на соединении не может находиться в асинхронном режиме, в то время как другая ручка оператора в том же соединении находится в синхронном режиме, и наоборот.  
  
 SQL_AM_STATEMENT поддерживается асинхронное выполнение уровня оператора. Некоторые ручки оператора, связанные с ручкой соединения, могут находиться в асинхронном режиме, в то время как другие ручки оператора в том же соединении находятся в синхронном режиме.  
  
 SQL_AM_NONE асинхронный режим не поддерживается.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Битовая маска S'LUINTEGER, перечисляющая поведение водителя в отношении наличия количества строк. Следующие бит-маски используются вместе с типом информации:  
  
 SQL_BRC_ROLLED_UP строки подсчитывают для последовательных вставка, DELETE, или ОБНОВЛЕНИЕ заявления свернуты в один. Если этот бит не установлен, для каждой выписки доступны строки.  
  
 SQL_BRC_PROCEDURES и строки, если таковые имеются, доступны, когда пакет выполняется в сохраненной процедуре. Если количество строк доступно, они могут быть свернуты или индивидуально доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
 SQL_BRC_EXPLICIT количество строк, если таковые имеются, доступны, когда партия выполняется непосредственно по телефону **S'L'LExecute** или **S'LExecDirect**. Если количество строк доступно, они могут быть свернуты или индивидуально доступны, в зависимости от SQL_BRC_ROLLED_UP бит.  
  
## <a name="example"></a>Пример  
 **SLGetInfo** возвращает списки поддерживаемых вариантов в качестве битовой маски S'LUINTEGER в*infoValuePtr*. Битовая маска для каждого параметра используется вместе с флагом, чтобы определить, поддерживается ли парабитель.  
  
 Например, приложение может использовать следующий код для определения того, поддерживается ли функция subSTRING scalar драйвером, связанным с соединением.  
  
 В другом примере использования **S'LGetInfo** [см.](../../../odbc/reference/syntax/sqltables-function.md)  
  
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
 Возвращение параметра атрибута соединения  
 [Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Определение того, поддерживает ли драйвер функцию  
 [Функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Возвращение атрибута оператора  
 [Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Возвращение информации о типах данных источника данных  
 [Функция SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
