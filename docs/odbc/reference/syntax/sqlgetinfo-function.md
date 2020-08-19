---
description: SQLGetInfo, функция
title: Функция SQLGetInfo | Документация Майкрософт
ms.custom: ''
ms.date: 05/28/2020
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
ms.openlocfilehash: b60dcdd90c71e1790464f24cd34dedfaa22e7c61
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421278"
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
 Входной Длина \* буфера *инфовалуептр* . Если значение в * \* инфовалуептр* не является символьной строкой или если *инфовалуептр* является пустым указателем, аргумент *BufferLength* игнорируется. Драйвер предполагает, что размер * \* ИНФОВАЛУЕПТР* — склусмаллинт или SQLUINTEGER на основе *инфотипе*. Если * \* инфовалуептр* является строкой Юникода (при вызове **Склжетинфов**), аргумент *BufferLength* должен быть четным числом; в противном случае возвращается значение SQLSTATE HY090 (Недопустимая строка или длина буфера).  
  
 *стрингленгсптр*  
 Проверки Указатель на буфер, в котором возвращается общее число байтов (за исключением символа завершения null для символьных данных), доступных для возврата в **инфовалуептр*.  
  
 Для символьных данных, если число возвращаемых байт больше или равно *BufferLength*, информация в \* *Инфовалуептр* усекается до *BufferLength* байт минус длина символа завершения, равного null, и заканчивается нулем драйвером.  
  
 Для всех других типов данных значение *BufferLength* игнорируется, и драйвер предполагает, что размер \* *ИНФОВАЛУЕПТР* равен склусмаллинт или SQLUINTEGER, в зависимости от *инфотипе*.  
  
## <a name="returns"></a>Возвращаемое значение  

 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  

 Если **SQLGetInfo** возвращает либо SQL_ERROR, либо SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_DBC и *маркером* *коннектионхандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLGetInfo** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, усеченные справа|Буфер \* *инфовалуептр* недостаточно велик для возврата всех запрошенных сведений. Поэтому данные были усечены. Длина запрошенной информации в неусеченной форме возвращается в **стрингленгсптр*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08003|Соединение не открыто|(DM) для типа сведений, запрашиваемых в *инфотипе* , требуется открытое соединение. Из типов данных, зарезервированных ODBC, только SQL_ODBC_VER могут возвращаться без открытого соединения.|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \* MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY024|Недопустимое значение атрибута|(DM) аргумент *инфотипе* был SQL_DRIVER_HSTMT, а значение, на которое указывает *инфовалуептр* , не является допустимым маркером инструкции.<br /><br /> (DM) аргумент *инфотипе* был SQL_DRIVER_HDESC, а значение, на которое указывает *инфовалуептр* , не является допустимым дескриптором дескриптора.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное для аргумента *BufferLength* , было меньше 0.<br /><br /> (DM) значение, указанное для *BufferLength* , было нечетным числом, а * \* Инфовалуептр* — типом данных Юникода.|  
|HY096|Тип данных вне допустимого диапазона|Значение, указанное для аргумента *инфотипе* , недопустимо для версии ODBC, поддерживаемой драйвером.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](sqlendtran-function.md).|  
|HYC00|Необязательное поле не реализовано|Значение, указанное для аргумента *инфотипе* , было зависящим от драйвера значением, которое не поддерживается драйвером.|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, соответствующий *коннектионхандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  

 Типы сведений, определенные в настоящее время, показаны Далее в этом разделе Ожидается, что для использования преимуществ различных источников данных будет определено больше. Диапазон типов данных зарезервирован ODBC. Разработчики драйверов должны зарезервировать значения для собственного использования драйвера из Open Group. **SQLGetInfo** не выполняет преобразование в Юникод или *преобразователь* (см. [приложение A. коды ошибок ODBC](../appendixes/appendix-a-odbc-error-codes.md) *справочника по программированию ODBC*) для определяемого драйвером *инфотипес*. Дополнительные сведения см. в разделе [зависящие от драйвера типы данных, Типы дескрипторов, типы сведений, типы диагностики и атрибуты](../develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Формат сведений, возвращаемых в \* *инфовалуептр* , зависит от запрашиваемого *инфотипе* . **SQLGetInfo** будет возвращать информацию в одном из пяти различных форматов:  
  
- Строка символов, завершающаяся нулем  
  
- Значение СКЛУСМАЛЛИНТ  
  
- Битовая маска SQLUINTEGER  
  
- Значение SQLUINTEGER  
  
- Двоичное значение SQLUINTEGER  
  
 Формат каждого из следующих типов сведений указывается в описании типа. Приложение должно соответствующим образом привести значение, возвращаемое в **инфовалуептр* . Пример того, как приложение может извлечь данные из битовой маски SQLUINTEGER, см. в разделе «пример кода».  
  
 Драйвер должен возвращать значение для каждого типа данных, определенного в следующих таблицах. Если тип сведений не применяется к драйверу или источнику данных, драйвер возвращает одно из значений, перечисленных в следующей таблице.  

|Тип информации|Значение|
|-|-|
|Символьная строка ("Y" или "N")|"N"|
|Символьная строка (не "Y" или "N")|Пустая строка.|
|склусмаллинт|0|
|Битовая маска SQLUINTEGER или SQLUINTEGER двоичное значение|0L|
  
 Например, если источник данных не поддерживает процедуры, **SQLGetInfo** возвращает значения, перечисленные в следующей таблице, для значений *инфотипе* , связанных с процедурами.  

|инфотипе|Значение|
|-|-|
|SQL_PROCEDURES|"N"|
|SQL_ACCESSIBLE_PROCEDURES|"N"|
|SQL_MAX_PROCEDURE_NAME_LEN|0|
|SQL_PROCEDURE_TERM|Пустая строка.|
  
 **SQLGetInfo** ВОЗВРАЩАЕТ SQLSTATE HY096 (недопустимое значение аргумента) для значений *инфотипе* , которые находятся в диапазоне типов данных, зарезервированных для использования ODBC, но не определяются версией ODBC, поддерживаемой драйвером. Чтобы определить, к какой версии ODBC-драйвера соответствует, приложение вызывает **SQLGetInfo** с типом данных SQL_DRIVER_ODBC_VER. **SQLGetInfo** ВОЗВРАЩАЕТ значение SQLSTATE HYC00 (Необязательная функция не реализована) для значений *инфотипе* , которые находятся в диапазоне типов данных, зарезервированных для использования драйвером, но не поддерживаются драйвером.  
  
 Для всех вызовов **SQLGetInfo** требуется открытое соединение, за исключением случаев, когда *инфотипе* имеет значение SQL_ODBC_VER, возвращающее версию диспетчера драйверов.  
  
## <a name="information-types"></a>Типы сведений  

 В этом разделе перечислены типы сведений, поддерживаемые **SQLGetInfo**. Типы сведений группируются по категориям и сортируются в алфавитном порядке. Также перечислены типы сведений, добавленных или переименованных для ODBC 3 *. x* .  
  
## <a name="driver-information"></a>Сведения о драйвере  

 Следующие значения аргумента *инфотипе* возвращают сведения о драйвере ODBC, такие как число активных инструкций, имя источника данных и уровень соответствия стандартам интерфейса:  

:::row:::
    :::column:::
        SQL_ACTIVE_ENVIRONMENTS  
        SQL_ASYNC_DBC_FUNCTIONS  
        SQL_ASYNC_MODE  
        SQL_ASYNC_NOTIFICATION  
        SQL_BATCH_ROW_COUNT  
        SQL_BATCH_SUPPORT  
        SQL_DATA_SOURCE_NAME  
        SQL_DRIVER_AWARE_POOLING_SUPPORTED  
        SQL_DRIVER_HDBC  
        SQL_DRIVER_HDESC  
        SQL_DRIVER_HENV  
        SQL_DRIVER_HLIB  
        SQL_DRIVER_HSTMT  
        SQL_DRIVER_NAME  
        SQL_DRIVER_ODBC_VER  
        SQL_DRIVER_VER  
        SQL_DYNAMIC_CURSOR_ATTRIBUTES1  
        SQL_DYNAMIC_CURSOR_ATTRIBUTES2  
        SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1  
    :::column-end:::
    :::column:::
        SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2  
        SQL_FILE_USAGE  
        SQL_GETDATA_EXTENSIONS  
        SQL_INFO_SCHEMA_VIEWS  
        SQL_KEYSET_CURSOR_ATTRIBUTES1  
        SQL_KEYSET_CURSOR_ATTRIBUTES2  
        SQL_MAX_ASYNC_CONCURRENT_STATEMENTS  
        SQL_MAX_CONCURRENT_ACTIVITIES  
        SQL_MAX_DRIVER_CONNECTIONS  
        SQL_ODBC_INTERFACE_CONFORMANCE  
        SQL_ODBC_STANDARD_CLI_CONFORMANCE  
        SQL_ODBC_VER  
        SQL_PARAM_ARRAY_ROW_COUNTS  
        SQL_PARAM_ARRAY_SELECTS  
        SQL_ROW_UPDATES  
        SQL_SEARCH_PATTERN_ESCAPE  
        SQL_SERVER_NAME  
        SQL_STATIC_CURSOR_ATTRIBUTES1  
        SQL_STATIC_CURSOR_ATTRIBUTES2  
    :::column-end:::
:::row-end:::

> [!NOTE]  
> При реализации **SQLGetInfo**драйвер может повысить производительность, минимизируя количество попыток отправки или запроса информации с сервера.  
  
## <a name="dbms-product-information"></a>Сведения о продукте СУБД  

 Следующие значения аргумента *инфотипе* возвращают сведения о продукте СУБД, такие как имя и версия СУБД:  

:::row:::
    :::column:::
        SQL_DATABASE_NAME  
        SQL_DBMS_NAME  
    :::column-end:::
    :::column:::
        SQL_DBMS_VER  
    :::column-end:::
:::row-end:::

## <a name="data-source-information"></a>Сведения об источнике данных  

 Следующие значения аргумента *инфотипе* возвращают сведения об источнике данных, такие как характеристики курсора и возможности транзакций:  

:::row:::
    :::column:::
        SQL_ACCESSIBLE_PROCEDURES  
        SQL_ACCESSIBLE_TABLES  
        SQL_BOOKMARK_PERSISTENCE  
        SQL_CATALOG_TERM  
        SQL_COLLATION_SEQ  
        SQL_CONCAT_NULL_BEHAVIOR  
        SQL_CURSOR_COMMIT_BEHAVIOR  
        SQL_CURSOR_ROLLBACK_BEHAVIOR  
        SQL_CURSOR_SENSITIVITY  
        SQL_DATA_SOURCE_READ_ONLY  
        SQL_DEFAULT_TXN_ISOLATION  
        SQL_DESCRIBE_PARAMETER  
    :::column-end:::
    :::column:::
        SQL_MULT_RESULT_SETS  
        SQL_MULTIPLE_ACTIVE_TXN  
        SQL_NEED_LONG_DATA_LEN  
        SQL_NULL_COLLATION  
        SQL_PROCEDURE_TERM  
        SQL_SCHEMA_TERM  
        SQL_SCROLL_OPTIONS  
        SQL_TABLE_TERM  
        SQL_TXN_CAPABLE  
        SQL_TXN_ISOLATION_OPTION  
        SQL_USER_NAME  
    :::column-end:::
:::row-end:::

## <a name="supported-sql"></a>Поддерживаемые SQL  

 Следующие значения аргумента *инфотипе* возвращают сведения о ИНСТРУКЦИЯх SQL, поддерживаемых источником данных. Синтаксис SQL каждого компонента, описываемого этими типами данных, является синтаксисом SQL-92. Эти типы сведений не полностью описывают грамматику SQL-92. Вместо этого они описывают эти части грамматики, для которых источники данных обычно предлагают различные уровни поддержки. В частности, рассматриваются большинство инструкций DDL в SQL-92.  
  
 Приложения должны определить общий уровень поддерживаемой грамматики из типа данных SQL_SQL_CONFORMANCE и использовать другие типы сведений для определения вариантов из указанного уровня соответствия стандартам.  

:::row:::
    :::column:::
        SQL_AGGREGATE_FUNCTIONS  
        SQL_ALTER_DOMAIN  
        SQL_ALTER_SCHEMA  
        SQL_ALTER_TABLE  
        SQL_ANSI_SQL_DATETIME_LITERALS  
        SQL_CATALOG_LOCATION  
        SQL_CATALOG_NAME  
        SQL_CATALOG_NAME_SEPARATOR  
        SQL_CATALOG_USAGE  
        SQL_COLUMN_ALIAS  
        SQL_CORRELATION_NAME  
        SQL_CREATE_ASSERTION  
        SQL_CREATE_CHARACTER_SET  
        SQL_CREATE_COLLATION  
        SQL_CREATE_DOMAIN  
        SQL_CREATE_SCHEMA  
        SQL_CREATE_TABLE  
        SQL_CREATE_TRANSLATION  
        SQL_DDL_INDEX  
        SQL_DROP_ASSERTION  
        SQL_DROP_CHARACTER_SET  
        SQL_DROP_COLLATION  
        SQL_DROP_DOMAIN  
        SQL_DROP_SCHEMA  
    :::column-end:::
    :::column:::
        SQL_DROP_TABLE  
        SQL_DROP_TRANSLATION  
        SQL_DROP_VIEW  
        SQL_EXPRESSIONS_IN_ORDERBY  
        SQL_GROUP_BY  
        SQL_IDENTIFIER_CASE  
        SQL_IDENTIFIER_QUOTE_CHAR  
        SQL_INDEX_KEYWORDS  
        SQL_INSERT_STATEMENT  
        SQL_INTEGRITY  
        SQL_KEYWORDS  
        SQL_LIKE_ESCAPE_CLAUSE  
        SQL_NON_NULLABLE_COLUMNS  
        SQL_OJ_CAPABILITIES  
        SQL_ORDER_BY_COLUMNS_IN_SELECT  
        SQL_OUTER_JOINS  
        SQL_PROCEDURES  
        SQL_QUOTED_IDENTIFIER_CASE  
        SQL_SCHEMA_USAGE  
        SQL_SPECIAL_CHARACTERS  
        SQL_SQL_CONFORMANCE  
        SQL_SUBQUERIES  
        SQL_UNION  
    :::column-end:::
:::row-end:::

## <a name="sql-limits"></a>Ограничения SQL  

 Следующие значения аргумента *инфотипе* возвращают сведения об ограничениях, применяемых к идентификаторам и предложениям в инструкциях SQL, например к максимальной длине идентификаторов и максимальному числу столбцов в списке выбора. Ограничения могут быть накладываются либо драйвером, либо источником данных.  

:::row:::
    :::column:::
        SQL_MAX_BINARY_LITERAL_LEN  
        SQL_MAX_CATALOG_NAME_LEN  
        SQL_MAX_CHAR_LITERAL_LEN  
        SQL_MAX_COLUMN_NAME_LEN  
        SQL_MAX_COLUMNS_IN_GROUP_BY  
        SQL_MAX_COLUMNS_IN_INDEX  
        SQL_MAX_COLUMNS_IN_ORDER_BY  
        SQL_MAX_COLUMNS_IN_SELECT  
        SQL_MAX_COLUMNS_IN_TABLE  
        SQL_MAX_CURSOR_NAME_LEN  
    :::column-end:::
    :::column:::
        SQL_MAX_IDENTIFIER_LEN  
        SQL_MAX_INDEX_SIZE  
        SQL_MAX_PROCEDURE_NAME_LEN  
        SQL_MAX_ROW_SIZE  
        SQL_MAX_ROW_SIZE_INCLUDES_LONG  
        SQL_MAX_SCHEMA_NAME_LEN  
        SQL_MAX_STATEMENT_LEN  
        SQL_MAX_TABLE_NAME_LEN  
        SQL_MAX_TABLES_IN_SELECT  
        SQL_MAX_USER_NAME_LEN  
    :::column-end:::
:::row-end:::

## <a name="scalar-function-information"></a>Сведения о скалярной функции  

 Следующие значения аргумента *инфотипе* возвращают сведения о скалярных функциях, поддерживаемых источником данных и драйвером. Дополнительные сведения о скалярных функциях см. в [приложении E: скалярные функции](../appendixes/appendix-e-scalar-functions.md).  

:::row:::
    :::column:::
        SQL_CONVERT_FUNCTIONS  
        SQL_NUMERIC_FUNCTIONS  
        SQL_STRING_FUNCTIONS  
        SQL_SYSTEM_FUNCTIONS  
    :::column-end:::
    :::column:::
        SQL_TIMEDATE_ADD_INTERVALS  
        SQL_TIMEDATE_DIFF_INTERVALS  
        SQL_TIMEDATE_FUNCTIONS  
    :::column-end:::
:::row-end:::

## <a name="conversion-information"></a>Сведения о преобразовании  

 Следующие значения аргумента *инфотипе* возвращают список типов данных SQL, в которые источник данных может преобразовать указанный тип данных SQL с помощью скалярной функции **Convert** :  

:::row:::
    :::column:::
        SQL_CONVERT_BIGINT  
        SQL_CONVERT_BINARY  
        SQL_CONVERT_BIT  
        SQL_CONVERT_CHAR  
        SQL_CONVERT_DATE  
        SQL_CONVERT_DECIMAL  
        SQL_CONVERT_DOUBLE  
        SQL_CONVERT_FLOAT  
        SQL_CONVERT_INTEGER  
        SQL_CONVERT_INTERVAL_DAY_TIME  
        SQL_CONVERT_INTERVAL_YEAR_MONTH  
    :::column-end:::
    :::column:::
        SQL_CONVERT_LONGVARBINARY  
        SQL_CONVERT_LONGVARCHAR  
        SQL_CONVERT_NUMERIC  
        SQL_CONVERT_REAL  
        SQL_CONVERT_SMALLINT  
        SQL_CONVERT_TIME  
        SQL_CONVERT_TIMESTAMP  
        SQL_CONVERT_TINYINT  
        SQL_CONVERT_VARBINARY  
        SQL_CONVERT_VARCHAR  
    :::column-end:::
:::row-end:::

## <a name="information-types-added-for-odbc-3x"></a>Типы сведений, добавленные для ODBC 3. x  

 Для ODBC 3. x были добавлены следующие значения аргумента *инфотипе* :  

:::row:::
    :::column:::
        SQL_ACTIVE_ENVIRONMENTS  
        SQL_AGGREGATE_FUNCTIONS  
        SQL_ALTER_DOMAIN  
        SQL_ALTER_SCHEMA  
        SQL_ANSI_SQL_DATETIME_LITERALS  
        SQL_ASYNC_DBC_FUNCTIONS  
        SQL_ASYNC_MODE  
        SQL_ASYNC_NOTIFICATION  
        SQL_BATCH_ROW_COUNT  
        SQL_BATCH_SUPPORT  
        SQL_CATALOG_NAME  
        SQL_COLLATION_SEQ  
        SQL_CONVERT_INTERVAL_DAY_TIME  
        SQL_CONVERT_INTERVAL_YEAR_MONTH  
        SQL_CREATE_ASSERTION  
        SQL_CREATE_CHARACTER_SET  
        SQL_CREATE_COLLATION  
        SQL_CREATE_DOMAIN  
        SQL_CREATE_SCHEMA  
        SQL_CREATE_TABLE  
        SQL_CREATE_TRANSLATION  
        SQL_CURSOR_SENSITIVITY  
        SQL_DDL_INDEX  
        SQL_DESCRIBE_PARAMETER  
        SQL_DM_VER  
    :::column-end:::
    :::column:::
        SQL_DRIVER_AWARE_POOLING_SUPPORTED  
        SQL_DRIVER_HDESC  
        SQL_DROP_ASSERTION  
        SQL_DROP_CHARACTER_SET  
        SQL_DROP_COLLATION  
        SQL_DROP_DOMAIN  
        SQL_DROP_SCHEMA  
        SQL_DROP_TABLE  
        SQL_DROP_TRANSLATION  
        SQL_DROP_VIEW  
        SQL_DYNAMIC_CURSOR_ATTRIBUTES1  
        SQL_DYNAMIC_CURSOR_ATTRIBUTES2  
        SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1  
        SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2  
        SQL_INFO_SCHEMA_VIEWS  
        SQL_INSERT_STATEMENT  
        SQL_KEYSET_CURSOR_ATTRIBUTES1  
        SQL_KEYSET_CURSOR_ATTRIBUTES2  
        SQL_MAX_ASYNC_CONCURRENT_STATEMENTS  
        SQL_MAX_IDENTIFIER_LEN  
        SQL_PARAM_ARRAY_ROW_COUNTS  
        SQL_PARAM_ARRAY_SELECTS  
        SQL_STATIC_CURSOR_ATTRIBUTES1  
        SQL_STATIC_CURSOR_ATTRIBUTES2  
        SQL_XOPEN_CLI_YEAR  
    :::column-end:::
:::row-end:::

## <a name="information-types-renamed-for-odbc-3x"></a>Типы сведений, переименованные для ODBC 3. x  

 Следующие значения аргумента *инфотипе* были переименованы для ODBC 3. x.  

|Старое имя|Новое имя|  
|-|-|  
|SQL_ACTIVE_CONNECTIONS|SQL_MAX_DRIVER_CONNECTIONS|
|SQL_ACTIVE_STATEMENTS|SQL_MAX_CONCURRENT_ACTIVITIES|
|SQL_MAX_OWNER_NAME_LEN|SQL_MAX_SCHEMA_NAME_LEN|
|SQL_MAX_QUALIFIER_NAME_LEN|SQL_MAX_CATALOG_NAME_LEN|
|SQL_ODBC_SQL_OPT_IEF|SQL_INTEGRITY|
|SQL_OWNER_TERM|SQL_SCHEMA_TERM|
|SQL_OWNER_USAGE|SQL_SCHEMA_USAGE|
|SQL_QUALIFIER_LOCATION|SQL_CATALOG_LOCATION|
|SQL_QUALIFIER_NAME_SEPARATOR|SQL_CATALOG_NAME_SEPARATOR|
|SQL_QUALIFIER_TERM|SQL_CATALOG_TERM|
|SQL_QUALIFIER_USAGE|SQL_CATALOG_USAGE|
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Нерекомендуемые типы сведений в ODBC 3. x  

 Следующие значения аргумента *инфотипе* являются устаревшими в ODBC 3. x. Драйверы ODBC 3. x должны продолжать поддерживать эти типы данных для обеспечения обратной совместимости с приложениями ODBC 2. x. (Дополнительные сведения об этих типах см. в разделе [Поддержка SQLGetInfo](../appendixes/sqlgetinfo-support.md) в приложении G: рекомендации по драйверу для обеспечения обратной совместимости.)  

:::row:::
    :::column:::
        SQL_FETCH_DIRECTION  
        SQL_LOCK_TYPES  
        SQL_ODBC_API_CONFORMANCE  
        SQL_ODBC_SQL_CONFORMANCE  
    :::column-end:::
    :::column:::
        SQL_POS_OPERATIONS  
        SQL_POSITIONED_STATEMENTS  
        SQL_SCROLL_CONCURRENCY  
        SQL_STATIC_SENSITIVITY  
    :::column-end:::
:::row-end:::

## <a name="information-type-descriptions"></a>Описания типов сведений  

В следующей таблице перечислены все типы данных, версия ODBC, в которой они были введены, и описание.  
  
|Тип данных|Версия ODBC|Описание|
|-|-|-|
|SQL_ACCESSIBLE_PROCEDURES|1.0|Строка символов: "Y", если пользователь может выполнить все процедуры, возвращенные **SQLProcedures**; "N", если могут быть возвращены процедуры, которые пользователь не может выполнить.|
|SQL_ACCESSIBLE_TABLES|1.0|Строка символов: "Y", если пользователь гарантированно **выбирает** права доступа ко всем таблицам, возвращаемым функцией **SQLTables**; "N", если могут возвращаться таблицы, к которым пользователь не может получить доступ.|
|SQL_ACTIVE_ENVIRONMENTS|3.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных сред, которое может поддерживать драйвер. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.|
|SQL_AGGREGATE_FUNCTIONS|3.0|SQLUINTEGER битовая маска, поддерживающая агрегатные функции:<br/>SQL_AF_ALL<br/>SQL_AF_AVG<br/>SQL_AF_COUNT<br/>SQL_AF_DISTINCT<br/>SQL_AF_MAX<br/>SQL_AF_MIN<br/>SQL_AF_SUM<br/><br/>Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_ALTER_DOMAIN|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **ALTER Domain** , как определено в SQL-92, поддерживаемое источником данных. Драйвер SQL-92, совместимый с полным уровнем, всегда возвращает все битовые маски. Возвращаемое значение "0" означает, что инструкция **ALTER Domain** не поддерживается.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_AD_ADD_DOMAIN_CONSTRAINT = Добавление ограничения домена поддерживается (полный уровень)<br/>SQL_AD_ADD_DOMAIN_DEFAULT = \<alter domain> \<set domain default clause> поддерживается (полный уровень)<br/>SQL_AD_CONSTRAINT_NAME_DEFINITION = \<constraint name definition clause> поддерживается для ограничения домена именования (промежуточный уровень)<br/>SQL_AD_DROP_DOMAIN_CONSTRAINT = \<drop domain constraint clause> поддерживается (полный уровень)<br/>SQL_AD_DROP_DOMAIN_DEFAULT = \<alter domain> \<drop domain default clause> поддерживается (полный уровень)<br/><br/>Следующие биты задают поддерживаемые, \<constraint attributes> Если \<add domain constraint> поддерживается бит SQL_AD_ADD_DOMAIN_CONSTRAINT установлен.<br/>SQL_AD_ADD_CONSTRAINT_DEFERRABLE (полный уровень)<br/>SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (полный уровень)<br/>SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (полный уровень)<br/>SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)|
|SQL_ALTER_TABLE|2.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **ALTER TABLE** , поддерживаемой источником данных.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>Предложение SQL_AT_ADD_COLUMN_COLLATION = \<add column> поддерживается с помощью средства для указания параметров сортировки столбцов (полный уровень) (ODBC 3,0)<br/>Предложение SQL_AT_ADD_COLUMN_DEFAULT = \<add column> поддерживается с указанием средств для указания значений по умолчанию для столбцов (уровень переходов FIPS) (ODBC 3,0)<br/>SQL_AT_ADD_COLUMN_SINGLE = \<add column> поддерживается (уровень переходов FIPS) (ODBC 3,0)<br/>Предложение SQL_AT_ADD_CONSTRAINT = \<add column> поддерживается с помощью средства для указания ограничений столбца (уровень FIPS) (ODBC 3,0)<br/>Предложение SQL_AT_ADD_TABLE_CONSTRAINT = \<add table constraint> поддерживается (уровень переходов FIPS) (ODBC 3,0)<br/>SQL_AT_CONSTRAINT_NAME_DEFINITION = \<constraint name definition> поддерживается для именования столбцов и ограничений таблицы (промежуточный уровень) (ODBC 3,0)<br/>SQL_AT_DROP_COLUMN_CASCADE = \<drop column> CASCADE поддерживается (уровень переходов FIPS) (ODBC 3,0)<br/>SQL_AT_DROP_COLUMN_DEFAULT = \<alter column> \<drop column default clause> поддерживается (промежуточный уровень) (ODBC 3,0)<br/>SQL_AT_DROP_COLUMN_RESTRICT = \<drop column> ограничение поддерживается (уровень передачи FIPS) (ODBC 3,0)<br/>SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)<br/>SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<drop column> ограничение поддерживается (уровень передачи FIPS) (ODBC 3,0)<br/>SQL_AT_SET_COLUMN_DEFAULT = \<alter column> \<set column default clause> поддерживается (промежуточный уровень) (ODBC 3,0)<br/><br/>Следующие биты задают поддержку \<constraint attributes> при условии, что ограничения столбца или таблицы поддерживаются (бит SQL_AT_ADD_CONSTRAINT установлен):<br/>SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень) (ODBC 3,0)<br/>SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень) (ODBC 3,0)<br/>SQL_AT_CONSTRAINT_DEFERRABLE (полный уровень) (ODBC 3,0)<br/>SQL_AT_CONSTRAINT_NON_DEFERRABLE (полный уровень) (ODBC 3,0)|
|SQL_ASYNC_DBC_FUNCTIONS|3.8|Значение SQLUINTEGER, указывающее, может ли драйвер асинхронно выполнять функции в обработчике соединения.<br/><br/>SQL_ASYNC_DBC_CAPABLE = драйвер может выполнять функции подключения асинхронно.<br/>SQL_ASYNC_DBC_NOT_CAPABLE = драйвер не может выполнять функции подключения асинхронно.|
|SQL_ASYNC_MODE|3.0|Значение SQLUINTEGER, указывающее уровень асинхронной поддержки в драйвере:<br/><br/>SQL_AM_CONNECTION = асинхронное выполнение на уровне соединения поддерживается. Все дескрипторы инструкций, связанные с данным дескриптором соединения, находятся в асинхронном режиме или работают в синхронном режиме. Маркер инструкции в соединении не может находиться в асинхронном режиме, в то время как другой обработчик на том же соединении работает в синхронном режиме и наоборот.<br/>SQL_AM_STATEMENT = асинхронное выполнение уровня инструкции поддерживается. Некоторые дескрипторы инструкций, связанные с дескриптором соединения, могут находиться в асинхронном режиме, в то время как другие дескрипторы инструкций в одном соединении находятся в синхронном режиме.<br/>SQL_AM_NONE = асинхронный режим не поддерживается.|
|SQL_ASYNC_NOTIFICATION|3.8|Значение SQLUINTEGER, указывающее, поддерживает ли драйвер Асинхронное уведомление:<br/><br/>SQL_ASYNC_NOTIFICATION_CAPABLE = драйвер поддерживает асинхронное уведомление о выполнении.<br/>SQL_ASYNC_NOTIFICATION_NOT_CAPABLE = уведомление о асинхронном выполнении не поддерживается драйвером.<br/><br/>Существуют две категории асинхронных операций ODBC: асинхронные операции на уровне соединения и асинхронные операции на уровне инструкций.  Если драйвер возвращает SQL_ASYNC_NOTIFICATION_CAPABLE, он должен поддерживать уведомление для всех интерфейсов API, которые он может выполнять асинхронно.|
|SQL_BATCH_ROW_COUNT|3.0|Битовая маска SQLUINTEGER, которая перечисляет поведение драйвера в отношении доступности количества строк. Вместе с типом данных используются следующие битовые маски:<br/><br/>SQL_BRC_ROLLED_UP = количество строк для последовательных инструкций INSERT, DELETE или UPDATE сведено в один. Если этот бит не установлен, для каждой инструкции доступны счетчики строк.<br/>SQL_BRC_PROCEDURES = количество строк, если таковые имеются, доступны при выполнении пакета в хранимой процедуре. Если счетчики строк доступны, они могут быть сведены или доступны по отдельности в зависимости от SQL_BRC_ROLLED_UP бита.<br/>SQL_BRC_EXPLICIT = количество строк, если таковые имеются, доступны при непосредственном выполнении пакета путем вызова **SQLExecute** или **SQLExecDirect**. Если счетчики строк доступны, они могут быть сведены или доступны по отдельности в зависимости от SQL_BRC_ROLLED_UP бита.|
|SQL_BATCH_SUPPORT|3.0|Битовая маска SQLUINTEGER, которая перечисляет поддержку пакетов в драйвере. Для определения поддерживаемого уровня используются следующие битовые маски.<br/><br/>SQL_BS_SELECT_EXPLICIT = драйвер поддерживает явные пакеты, в которых могут создаваться инструкции результирующего набора.<br/>SQL_BS_ROW_COUNT_EXPLICIT = драйвер поддерживает явные пакеты, которые могут формировать инструкции по количеству строк.<br/>SQL_BS_SELECT_PROC = драйвер поддерживает явные процедуры, в которых могут создаваться инструкции результирующего набора.<br/>SQL_BS_ROW_COUNT_PROC = драйвер поддерживает явные процедуры, которые могут формировать инструкции по количеству строк.|
|SQL_BOOKMARK_PERSISTENCE|2.0|Битовая маска SQLUINTEGER, в которой перечисляются операции, с помощью которых сохраняются закладки. Следующие битовые маски используются вместе с флагом для определения сохраняемых параметров.<br/><br/>SQL_BP_CLOSE = закладки допустимы после того, как приложение вызывает **SQLFreeStmt** с параметром SQL_CLOSE или **SQLCloseCursor** , чтобы закрыть курсор, связанный с инструкцией.<br/>SQL_BP_DELETE = закладка для строки допустима после удаления этой строки.<br/>SQL_BP_DROP = закладки допустимы после того, как приложение вызовет **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_STMT для удаления инструкции.<br/>SQL_BP_TRANSACTION = закладки допустимы после фиксации или отката транзакции приложением.<br/>SQL_BP_UPDATE = закладка для строки допустима после обновления любого столбца в этой строке, включая ключевые столбцы.<br/>SQL_BP_OTHER_HSTMT = Закладка, связанная с одной инструкцией, может использоваться с другой инструкцией. Если не указано SQL_BP_CLOSE или SQL_BP_DROP, курсор в первой инструкции должен быть открыт.|
|SQL_CATALOG_LOCATION|2.0|Значение СКЛУСМАЛЛИНТ, указывающее расположение каталога в полном имени таблицы:<br/><br/>SQL_CL_START<br/>SQL_CL_END<br/>Например, драйвер xbase возвращает SQL_CL_START, так как имя каталога (каталога) находится в начале имени таблицы, как в \ЕМПДАТА\ЕМП. Присоединен. Драйвер сервера ORACLE возвращает SQL_CL_END, так как каталог находится в конце имени таблицы, как в ADMIN.EMP@EMPDATA .<br/><br/>Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать SQL_CL_START. Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_LOCATION ODBC 2,0 *инфотипе* .|
|SQL_CATALOG_NAME|3.0|Строка символов: "Y", если сервер поддерживает имена каталогов, или "N", если нет.<br/><br/>Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать значение "Y".|
|SQL_CATALOG_NAME_SEPARATOR|1.0|Символьная строка. символ или символы, которые источник данных определяет как разделитель между именем каталога и элементом с полным именем, который следует за ним или предшествует ему.<br/><br/>Если каталоги не поддерживаются источником данных, возвращается пустая строка. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME. Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать ".".<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_NAME_SEPARATOR ODBC 2,0 *инфотипе* .|
|SQL_CATALOG_TERM|1.0|Символьная строка с именем поставщика источника данных для каталога; Например, "Database" или "Directory". Эта строка может быть в верхнем, нижнем или смешанном регистре.<br/><br/>Если каталоги не поддерживаются источником данных, возвращается пустая строка. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME. Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать "Catalog".<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_TERM ODBC 2,0 *инфотипе* .|
|SQL_CATALOG_USAGE|2.0|Битовая маска SQLUINTEGER, которая перечисляет инструкции, в которых можно использовать каталоги.<br/><br/>Чтобы определить, где можно использовать каталоги, используются следующие битовые маски:<br/>SQL_CU_DML_STATEMENTS = каталоги поддерживаются во всех инструкциях языка обработки данных: **SELECT**, **INSERT**, **Update**, **Delete**и, если поддерживается, **SELECT для Update** и позиционированных инструкций UPDATE и DELETE.<br/>SQL_CU_PROCEDURE_INVOCATION = каталоги поддерживаются в операторе вызова процедуры ODBC.<br/>SQL_CU_TABLE_DEFINITION = каталоги поддерживаются во всех инструкциях определения таблицы: **CREATE TABLE**, **Создание представления**, **изменение таблицы**, **Удаление таблицы**и **представление Drop**.<br/>SQL_CU_INDEX_DEFINITION = каталоги поддерживаются во всех инструкциях определения индекса: **Создание индекса** и **DROP INDEX**.<br/>SQL_CU_PRIVILEGE_DEFINITION = каталоги поддерживаются во всех инструкциях определения прав: **Grant** и **REVOKE**.<br/><br/>Если каталоги не поддерживаются источником данных, возвращается значение 0. Чтобы определить, поддерживаются ли каталоги, приложение вызывает **SQLGetInfo** с типом сведений SQL_CATALOG_NAME. Драйвер SQL-92 с полным соответствием уровня всегда будет возвращать битовую маску со всеми этими наборами битов.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_QUALIFIER_USAGE ODBC 2,0 *инфотипе* .|
|SQL_COLLATION_SEQ|3.0|Имя последовательности параметров сортировки. Это символьная строка, указывающая имя параметров сортировки по умолчанию для набора символов по умолчанию для данного сервера (например, "ISO 8859-1" или EBCDIC). Если это неизвестно, будет возвращена пустая строка. Драйвер, соотносящийся к полному уровню SQL-92, всегда возвращает непустую строку.|
|SQL_COLUMN_ALIAS|2.0|Символьная строка: "Y", если источник данных поддерживает псевдонимы столбцов; в противном случае — "N".<br/><br/>Псевдоним столбца — это альтернативное имя, которое можно указать для столбца в списке выбора с помощью предложения AS. Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает значение "Y".|
|SQL_CONCAT_NULL_BEHAVIOR|1.0|Значение СКЛУСМАЛЛИНТ, указывающее, как источник данных обрабатывает объединение столбцов символьного типа данных со значением NULL со столбцами типа данных, не являющимися значениями NULL:<br/>SQL_CB_NULL = result имеет значение NULL.<br/>SQL_CB_NON_NULL = Result объединяет столбец или столбцы, не имеющие значений NULL.<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, всегда будет возвращать SQL_CB_NULL.|
|SQL_CONVERT_BIGINT<br/>SQL_CONVERT_BINARY<br/>SQL_CONVERT_BIT<br/>SQL_CONVERT_CHAR<br/>SQL_CONVERT_GUID<br/>SQL_CONVERT_DATE<br/>SQL_CONVERT_DECIMAL<br/>SQL_CONVERT_DOUBLE<br/>SQL_CONVERT_FLOAT<br/>SQL_CONVERT_INTEGER<br/>SQL_CONVERT_INTERVAL_YEAR_MONTH<br/>SQL_CONVERT_INTERVAL_DAY_TIME<br/>SQL_CONVERT_LONGVARBINARY<br/>SQL_CONVERT_LONGVARCHAR<br/>SQL_CONVERT_NUMERIC<br/>SQL_CONVERT_REAL<br/>SQL_CONVERT_SMALLINT<br/>SQL_CONVERT_TIME<br/>SQL_CONVERT_TIMESTAMP<br/>SQL_CONVERT_TINYINT<br/>SQL_CONVERT_VARBINARY<br/>SQL_CONVERT_VARCHAR|1.0|Битовая маска SQLUINTEGER. Битовая маска указывает, какие преобразования поддерживаются источником данных с помощью скалярной функции **Convert** для данных типа, указанного в *инфотипе*. Если битовая маска равна нулю, источник данных не поддерживает преобразования из данных именованного типа, включая преобразование в тот же тип данных.<br/><br/>Например, чтобы определить, поддерживает ли источник данных преобразование SQL_INTEGER данных в SQL_BIGINT тип данных, приложение вызывает **SQLGetInfo** с *инфотипе* SQL_CONVERT_INTEGER. Приложение выполняет операцию **и** с возвращенной битовой маской и SQL_CVT_BIGINT. Если полученное значение не равно нулю, преобразование поддерживается.<br/><br/>Для определения поддерживаемых преобразований используются следующие битовые маски.<br/>SQL_CVT_BIGINT (ODBC 1,0)<br/>SQL_CVT_BINARY (ODBC 1,0)<br/>SQL_CVT_BIT (ODBC 1,0)<br/>SQL_CVT_GUID (ODBC 3,5)<br/>SQL_CVT_CHAR (ODBC 1,0)<br/>SQL_CVT_DATE (ODBC 1,0)<br/>SQL_CVT_DECIMAL (ODBC 1,0)<br/>SQL_CVT_DOUBLE (ODBC 1,0)<br/>SQL_CVT_FLOAT (ODBC 1,0)<br/>SQL_CVT_INTEGER (ODBC 1,0)<br/>SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3,0)<br/>SQL_CVT_INTERVAL_DAY_TIME (ODBC 3,0)<br/>SQL_CVT_LONGVARBINARY (ODBC 1,0)<br/>SQL_CVT_LONGVARCHAR (ODBC 1,0)<br/>SQL_CVT_NUMERIC (ODBC 1,0)<br/>SQL_CVT_REAL (ODBC 1,0)<br/>SQL_CVT_SMALLINT (ODBC 1,0)<br/>SQL_CVT_TIME (ODBC 1,0)<br/>SQL_CVT_TIMESTAMP (ODBC 1,0)<br/>SQL_CVT_TINYINT (ODBC 1,0)<br/>SQL_CVT_VARBINARY (ODBC 1,0)<br/>SQL_CVT_VARCHAR (ODBC 1,0)|
|SQL_CONVERT_FUNCTIONS|1.0|Битовая маска SQLUINTEGER, которая перечисляет скалярные функции преобразования, поддерживаемые драйвером и связанным источником данных.<br/><br/>Для определения поддерживаемых функций преобразования используется следующая битовая маска:<br/>SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT|
|SQL_CORRELATION_NAME|1.0|Значение СКЛУСМАЛЛИНТ, указывающее, поддерживаются ли имена корреляции таблиц:<br/>SQL_CN_NONE = корреляционные имена не поддерживаются.<br/>SQL_CN_DIFFERENT = имена корреляции поддерживаются, но должны отличаться от имен таблиц, которые они представляют.<br/>SQL_CN_ANY = имена корреляции поддерживаются и могут быть любым допустимым именем, определенным пользователем.<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, всегда будет возвращать SQL_CN_ANY.|
|SQL_CREATE_ASSERTION|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE assertion** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_CA_CREATE_ASSERTION<br/><br/>Следующие биты задают атрибут Supported Constraint, если возможность указывать атрибуты ограничения явно поддерживается (см. SQL_ALTER_TABLE и SQL_CREATE_TABLE типы сведений):<br/>SQL_CA_CONSTRAINT_INITIALLY_DEFERRED<br/>SQL_CA_CONSTRAINT_INITIALLY_IMMEDIATE<br/>SQL_CA_CONSTRAINT_DEFERRABLE<br/>SQL_CA_CONSTRAINT_NON_DEFERRABLE<br/><br/>Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые. Возвращаемое значение "0" означает, что инструкция **CREATE assertion** не поддерживается.|
|SQL_CREATE_CHARACTER_SET|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE character set** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_CCS_CREATE_CHARACTER_SET<br/>SQL_CCS_COLLATE_CLAUSE<br/>SQL_CCS_LIMITED_COLLATION<br/><br/>Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые. Возвращаемое значение "0" означает, что инструкция **CREATE character set** не поддерживается.|
|SQL_CREATE_COLLATION|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE collation** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Для определения поддерживаемых предложений используется следующая битовая маска:<br/>SQL_CCOL_CREATE_COLLATION<br/><br/>Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается. Возвращаемое значение "0" означает, что инструкция **CREATE collation** не поддерживается.|
|SQL_CREATE_DOMAIN|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE Domain** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_CDO_CREATE_DOMAIN = поддерживается инструкция CREATE DOMAIN (промежуточный уровень).<br/>SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<constraint name definition> поддерживается для именования ограничений домена (промежуточный уровень).<br/><br/>Следующие биты определяют возможность создания ограничений столбцов.<br/>SQL_CDO_DEFAULT = поддерживается указание ограничений домена (промежуточный уровень)<br/>SQL_CDO_CONSTRAINT = поддерживается указание значений по умолчанию для домена (промежуточный уровень)<br/>SQL_CDO_COLLATION = поддерживается указание параметров сортировки домена (полный уровень)<br/><br/>Следующие биты задают поддерживаемые атрибуты ограничения, если указано, что ограничения домена поддерживаются (SQL_CDO_DEFAULT установлен):<br/>SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (полный уровень)<br/>SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)<br/>SQL_CDO_CONSTRAINT_DEFERRABLE (полный уровень)<br/>SQL_CDO_CONSTRAINT_NON_DEFERRABLE (полный уровень)<br/><br/>Возвращаемое значение "0" означает, что инструкция **CREATE Domain** не поддерживается.|
|SQL_CREATE_SCHEMA|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE SCHEMA** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_CS_CREATE_SCHEMA<br/>SQL_CS_AUTHORIZATION<br/>SQL_CS_DEFAULT_CHARACTER_SET<br/><br/>Драйвер, совместимый с промежуточным уровнем SQL-92, всегда будет возвращать параметры SQL_CS_CREATE_SCHEMA и SQL_CS_AUTHORIZATION, как поддерживается. Они также должны поддерживаться на уровне ввода SQL-92, но не обязательно как инструкции SQL. Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_CREATE_TABLE|3.0|Битовая маска SQLUINTEGER, перечисление предложений в операторе **CREATE TABLE** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_CT_CREATE_TABLE = поддерживается инструкция CREATE TABLE. (Уровень записи)<br/>SQL_CT_TABLE_CONSTRAINT = поддерживается указание ограничений таблицы (уровень FIPS)<br/>SQL_CT_CONSTRAINT_NAME_DEFINITION = \<constraint name definition> предложение поддерживается для именования столбцов и ограничений таблицы (промежуточный уровень)<br/><br/>Следующие биты указывают возможность создания временных таблиц:<br/>SQL_CT_COMMIT_PRESERVE = удаленные строки сохраняются при фиксации. (Полный уровень)<br/>SQL_CT_COMMIT_DELETE = удаленные строки удаляются при фиксации. (Полный уровень)<br/>SQL_CT_GLOBAL_TEMPORARY = можно создавать глобальные временные таблицы. (Полный уровень)<br/>SQL_CT_LOCAL_TEMPORARY = можно создавать локальные временные таблицы. (Полный уровень)<br/><br/>Следующие биты определяют возможность создания ограничений столбцов.<br/>SQL_CT_COLUMN_CONSTRAINT = поддерживается указание ограничений столбца (уровень FIPS)<br/>SQL_CT_COLUMN_DEFAULT = поддерживается указание значений по умолчанию для столбцов (уровень "FIPS")<br/>SQL_CT_COLUMN_COLLATION = поддерживается задание параметров сортировки столбцов (полный уровень)<br/><br/>Следующие биты задают поддерживаемые атрибуты ограничения, если указано ограничение столбца или таблицы.<br/>SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (полный уровень)<br/>SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (полный уровень)<br/>SQL_CT_CONSTRAINT_DEFERRABLE (полный уровень)<br/>SQL_CT_CONSTRAINT_NON_DEFERRABLE (полный уровень)|
|SQL_CREATE_TRANSLATION|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **CREATE Translation** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Для определения поддерживаемых предложений используется следующая битовая маска:<br/>SQL_CTR_CREATE_TRANSLATION<br/><br/>Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать эти параметры, как и поддерживается. Возвращаемое значение "0" означает, что инструкция **CREATE Translation** не поддерживается.|
|SQL_CREATE_VIEW|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Create View** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_CV_CREATE_VIEW<br/>SQL_CV_CHECK_OPTION<br/>SQL_CV_CASCADED<br/>SQL_CV_LOCAL<br/><br/>Возвращаемое значение "0" означает, что инструкция **Create View** не поддерживается.<br/><br/>Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать параметры SQL_CV_CREATE_VIEW и SQL_CV_CHECK_OPTION, как поддерживается.<br/><br/>Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_CURSOR_COMMIT_BEHAVIOR|1.0|Значение СКЛУСМАЛЛИНТ, указывающее, как операция **фиксации** влияет на курсоры и подготовленные инструкции в источнике данных (поведение источника данных при фиксации транзакции).<br/><br/>Значение этого атрибута будет отражать текущее состояние следующего параметра: SQL_COPT_SS_PRESERVE_CURSORS.<br/>SQL_CB_DELETE = закрывающие курсоры и удалять подготовленные инструкции. Для повторного использования курсора приложение должно повторно подготовиться к работе и заново выполнить инструкцию.<br/>SQL_CB_CLOSE = закрывающие курсоры. Для подготовленных инструкций приложение может вызвать **SQLExecute** для инструкции без повторного вызова **SQLPrepare** . Значение по умолчанию для драйвера SQL ODBC — SQL_CB_CLOSE. Это означает, что при фиксации транзакции драйвер ODBC SQL будет закрывать ваши курсоры.<br/>SQL_CB_PRESERVE = сохранять курсоры в той же позиции, что и до операции **фиксации** . Приложение может продолжить выборку данных, или же можно закрыть курсор и повторно выполнить инструкцию, не переподготавливая ее.|
|SQL_CURSOR_ROLLBACK_BEHAVIOR|1.0|Значение СКЛУСМАЛЛИНТ, указывающее, как операция **отката** влияет на курсоры и подготовленные инструкции в источнике данных:<br/>SQL_CB_DELETE = закрывающие курсоры и удалять подготовленные инструкции. Для повторного использования курсора приложение должно повторно подготовиться к работе и заново выполнить инструкцию.<br/>SQL_CB_CLOSE = закрывающие курсоры. Для подготовленных инструкций приложение может вызвать **SQLExecute** для инструкции без повторного вызова **SQLPrepare** .<br/>SQL_CB_PRESERVE = сохранять курсоры в той же позиции, что и перед операцией **отката** . Приложение может продолжить выборку данных, или же можно закрыть курсор и повторно выполнить инструкцию, не переподготавливая ее.|
|SQL_CURSOR_SENSITIVITY|3.0|Значение SQLUINTEGER, указывающее на поддержку чувствительности курсора:<br/>SQL_INSENSITIVE = все курсоры на маркере инструкции показывают результирующий набор, не отражая изменения, внесенные в него любым другим курсором в рамках той же транзакции.<br/>SQL_UNSPECIFIED = не указано, отображаются ли курсоры в маркере инструкции изменения, внесенные в результирующий набор другим курсором в той же транзакции. Курсоры в маркере инструкции могут сделать видимыми ничего, некоторые или все подобные изменения.<br/>SQL_SENSITIVE = курсоры чувствительны к изменениям, внесенным другими курсорами в рамках той же транзакции.<br/><br/>Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать параметр SQL_UNSPECIFIED, как поддерживается.<br/><br/>Драйвер, совместимый с SQL-92, всегда будет возвращать параметр SQL_INSENSITIVE, как поддерживается.|
|SQL_DATA_SOURCE_NAME|1.0|Строка символов с именем источника данных, которое было использовано во время соединения. Если приложение называется **SQLConnect**, это значение аргумента *сздсн* . Если приложение называется **SQLDriverConnect** или **SQLBrowseConnect**, это значение является ЗНАЧЕНИЕМ ключевого слова DSN в строке подключения, передаваемой драйверу. Если строка подключения не содержит ключевого слова **DSN** (например, если оно содержит ключевое слово **Driver** ), это пустая строка.|
|SQL_DATA_SOURCE_READ_ONLY|1.0|Строка символов. "Y", если для источника данных задан режим "только для чтения", в противном случае — "N".<br/><br/>Эта характеристика относится только к самому источнику данных. Он не является характеристикой драйвера, обеспечивающего доступ к источнику данных. Драйвер, доступный для чтения и записи, можно использовать с источником данных, который доступен только для чтения. Если драйвер доступен только для чтения, все его источники данных должны быть доступны только для чтения и должны возвращать SQL_DATA_SOURCE_READ_ONLY.|
|SQL_DATABASE_NAME|1.0|Строка символов с именем текущей базы данных, если источник данных определяет именованный объект с именем "Database".<br/><br/>В ODBC 3. x значение, возвращаемое для этого *инфотипе* , также может возвращаться путем вызова **SQLGetConnectAttr** с аргументом *атрибута* SQL_ATTR_CURRENT_CATALOG.|
|SQL_DATETIME_LITERALS|3.0|Битовая маска SQLUINTEGER, которая перечисляет литералы datetime SQL-92, поддерживаемые источником данных. Обратите внимание, что это литералы datetime, перечисленные в спецификации SQL-92, и они отделены от литеральных предложений литерала DateTime, определенных ODBC. Дополнительные сведения о предложениях escape-выражений ODBC DateTime см. в статье [литералы даты, времени и отметок времени](../develop-app/date-time-and-timestamp-literals.md).<br/><br/> Драйвер, поддерживающий переход на уровне FIPS, всегда возвращает значение "1" в битовой маске для битов, указанных в следующем списке. Значение "0" означает, что литералы datetime в SQL-92 не поддерживаются.<br/><br/>Для определения поддерживаемых литералов используются следующие битовые маски:<br/>SQL_DL_SQL92_DATE<br/>SQL_DL_SQL92_TIME<br/>SQL_DL_SQL92_TIMESTAMP<br/>SQL_DL_SQL92_INTERVAL_YEAR<br/>SQL_DL_SQL92_INTERVAL_MONTH<br/>SQL_DL_SQL92_INTERVAL_DAY<br/>SQL_DL_SQL92_INTERVAL_HOUR<br/>SQL_DL_SQL92_INTERVAL_MINUTE<br/>SQL_DL_SQL92_INTERVAL_SECOND<br/>SQL_DL_SQL92_INTERVAL_YEAR_TO_MONTH<br/>SQL_DL_SQL92_INTERVAL_DAY_TO_HOUR<br/>SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTE<br/>SQL_DL_SQL92_INTERVAL_DAY_TO_SECOND<br/>SQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTE<br/>SQL_DL_SQL92_INTERVAL_HOUR_TO_SECOND<br/>SQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND|
|SQL_DBMS_NAME|1.0|Строка символов с именем продукта СУБД, к которому обращается драйвер.|
|SQL_DBMS_VER|1.0|Символьная строка, указывающая версию продукта СУБД, к которой обращается драйвер. Версия имеет вид # #. # #. # # # #, где первые две цифры являются основной версией, следующие две цифры — дополнительный номер версии, а последние четыре цифры — версия выпуска. Драйвер должен визуализировать версию продукта СУБД в этой форме, но также может добавлять версию СУБД, относящуюся к продукту. Например, "04.01.0000 Rdb 4,1".|
|SQL_DDL_INDEX|3.0|Значение SQLUINTEGER, указывающее поддержку создания и удаления индексов:<br/>SQL_DI_CREATE_INDEX<br/>SQL_DI_DROP_INDEX|
|SQL_DEFAULT_TXN_ISOLATION|1.0|Значение SQLUINTEGER, указывающее уровень изоляции транзакции по умолчанию, поддерживаемый драйвером или источником данных, или нуль, если источник данных не поддерживает транзакции. Для определения уровней изоляции транзакции используются следующие термины.<br/>**"Грязное" чтение** Транзакция 1 изменяет строку. Транзакция 2 считывает измененную строку до того, как транзакция 1 фиксирует изменение. Если транзакция 1 откатывает изменение, то транзакция 2 будет считать строку, которая, как никогда, не существовала.<br/>**Неповторяемое чтение** Транзакция 1 считывает строку. Транзакция 2 обновляет или удаляет эту строку и фиксирует это изменение. Если транзакция 1 пытается повторно прочитать строку, она получит другие значения строки или обнаружит, что строка была удалена.<br/>**Фантомный** Транзакция 1 считывает набор строк, удовлетворяющих некоторым условиям поиска. Транзакция 2 создает одну или несколько строк (с помощью вставок или обновлений), соответствующих условиям поиска. Если транзакция 1 повторно выполняет инструкцию, которая считывает строки, она получает другой набор строк.<br/><br/>Если источник данных поддерживает транзакции, драйвер возвращает одну из следующих битовых масок:<br/>SQL_TXN_READ_UNCOMMITTED = «грязные» операции чтения, неповторяемые операции чтения и фантомы.<br/>SQL_TXN_READ_COMMITTED = "грязные" операции чтения невозможны. Возможны неповторяемые операции чтения и фантомы.<br/>SQL_TXN_REPEATABLE_READ = "грязное" чтение и неповторяемые операции чтения невозможны. Фантомы возможны.<br/>SQL_TXN_SERIALIZABLE = транзакции сериализуемыми. Сериализуемые транзакции не допускают "грязных" операций чтения, неповторяемых операций чтения или фантомов.|
|SQL_DESCRIBE_PARAMETER|3.0|Символьная строка: "Y", если можно описать параметры; "N", если нет.<br/><br/>Драйвер SQL-92 с полным соответствием, как правило, возвращает значение "Y", поскольку оно будет поддерживать оператор **описания входных данных** . Поскольку в этом случае не указывается базовая поддержка SQL, то описанные параметры могут не поддерживаться даже в драйвере SQL-92 с полным уровнем соответствия.|
|SQL_DM_VER|3.0|Символьная строка с версией диспетчера драйверов. Версия имеет вид # #. # #. # # # #. # # # #, где:<br/>Первый набор из двух цифр — это основной номер версии ODBC, заданный константой SQL_SPEC_MAJOR.<br/>Второй набор из двух цифр — это незначительная версия ODBC, заданная константой SQL_SPEC_MINOR.<br/>Третьим набором из четырех цифр является номер основной сборки диспетчера драйверов.<br/>Последний набор из четырех цифр — номер вспомогательной сборки диспетчера драйверов.<br/>Версия диспетчера драйверов Windows 7 — 03,80. Версия диспетчера драйверов для Windows 8 — 03,81.|
|SQL_DRIVER_AWARE_POOLING_SUPPORTED|3.8|Значение SQLUINTEGER, указывающее, поддерживает ли драйвер пулы с учетом драйверов. (Дополнительные сведения см. в статье [Организация пулов соединений с учетом драйверов](../develop-app/driver-aware-connection-pooling.md).<br/><br/>SQL_DRIVER_AWARE_POOLING_CAPABLE указывает, что драйвер может поддерживать механизм пулов с поддержкой драйверов.<br/>SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE указывает, что драйвер не поддерживает механизм пулов с поддержкой драйверов.<br/><br/>Драйверу не требуется реализовывать SQL_DRIVER_AWARE_POOLING_SUPPORTED, а диспетчер драйверов не будет учитывать возвращаемое значение драйвера.|
|SQL_DRIVER_HDBCSQL_DRIVER_HENV|1.0|Значение SQLULEN, обработчик среды или маркер подключения драйвера, определяемый аргументом *инфотипе*.<br/><br/>Эти типы информации реализуются только диспетчером драйверов.|
|SQL_DRIVER_HDESC|3.0|Значение SQLULEN, дескриптор дескриптора драйвера, определяемый дескриптором дескриптора диспетчера драйверов, который должен передаваться в качестве входных данных в \* *инфовалуептр* из приложения. В этом случае *инфовалуептр* является как входным, так и выходным аргументом. Дескриптор входного дескриптора, переданный в \* *инфовалуептр* , должен быть либо явно, либо неявно выделен в *коннектионхандле*.<br/><br/>Приложение должно создать копию дескриптора дескриптора диспетчера драйверов перед вызовом **SQLGetInfo** с этим типом данных, чтобы убедиться в том, что дескриптор не перезаписывается на выходе.<br/><br/>Этот тип информации реализуется только диспетчером драйверов.|
|SQL_DRIVER_HLIB|2.0|Значение SQLULEN, *хинст* из библиотеки загрузки, возвращенное диспетчеру драйверов при загрузке библиотеки DLL драйвера в операционной системе Microsoft Windows или ее эквиваленте в другой операционной системе. Этот маркер допустим только для маркера соединения, указанного в вызове **SQLGetInfo**.<br/><br/>Этот тип информации реализуется только диспетчером драйверов.|
|SQL_DRIVER_HSTMT|1.0|Значение SQLULEN, обработчик инструкций драйвера, определяемый обработчиком драйвера диспетчера драйверов, который должен передаваться в качестве входных данных в \* *инфовалуептр* из приложения. В этом случае *инфовалуептр* является входным и выходным аргументом. Входной маркер инструкции, переданный в \* *инфовалуептр* , должен быть выделен в аргументе *коннектионхандле*.<br/><br/>Приложение должно создать копию обработчика операторов диспетчера драйверов перед вызовом **SQLGetInfo** с этим типом данных, чтобы гарантировать, что этот маркер не перезаписывается на выходе.<br/><br/>Этот тип информации реализуется только диспетчером драйверов.|
|SQL_DRIVER_NAME|1.0|Символьная строка с именем файла драйвера, используемого для доступа к источнику данных.|
|SQL_DRIVER_ODBC_VER|2.0|Символьная строка с версией ODBC, поддерживаемой драйвером. Версия имеет вид # #. # #, где первые две цифры — основной номер версии, а следующие две цифры — дополнительный номер версии. SQL_SPEC_MAJOR и SQL_SPEC_MINOR определяют основной и дополнительный номера версии. Для версии ODBC, описанной в этом руководстве, указаны 3 и 0, а драйвер должен вернуть значение "03,00".<br/><br/>Диспетчер драйверов ODBC не изменит возвращаемое значение SQLGetInfo (SQL_DRIVER_ODBC_VER) для обеспечения обратной совместимости существующих приложений. Драйвер указывает, какое значение будет возвращено. Однако драйвер, поддерживающий расширение типа данных C, должен возвращать 3,8 (или более поздней версии), когда приложение вызывает **SQLSetEnvAttr** для установки SQL_ATTR_ODBC_VERSION в 3,8. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](../develop-app/c-data-types-in-odbc.md).|
|SQL_DRIVER_VER|1.0|Символьная строка с версией драйвера и при необходимости описание драйвера. Как минимум, версия имеет форму # #. # #. # # # #, где первые две цифры — основной номер версии, две следующие цифры — дополнительный номер версии, а последние четыре цифры — версия выпуска.|
|SQL_DROP_ASSERTION|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Assert** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Для определения поддерживаемых предложений используется следующая битовая маска:<br/>SQL_DA_DROP_ASSERTION<br/><br/>Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.|
|SQL_DROP_CHARACTER_SET|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop character set** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используется следующая битовая маска:<br/>SQL_DCS_DROP_CHARACTER_SET<br/><br/>Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.|
|SQL_DROP_COLLATION|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop collation** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Для определения поддерживаемых предложений используется следующая битовая маска:<br/>SQL_DC_DROP_COLLATION<br/><br/>Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.|
|SQL_DROP_DOMAIN|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Domain** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_DD_DROP_DOMAIN<br/>SQL_DD_CASCADE<br/>SQL_DD_RESTRICT<br/><br/>Драйвер, совместимый с промежуточным уровнем SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_DROP_SCHEMA|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Schema** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_DS_DROP_SCHEMA<br/>SQL_DS_CASCADE<br/>SQL_DS_RESTRICT<br/><br/>Драйвер, совместимый с промежуточным уровнем SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_DROP_TABLE|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **DROP TABLE** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_DT_DROP_TABLE<br/>SQL_DT_CASCADE<br/>SQL_DT_RESTRICT<br/><br/>Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.|
|SQL_DROP_TRANSLATION|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **Drop Translation** , как определено в SQL-92, поддерживается источником данных.<br/><br/>Для определения поддерживаемых предложений используется следующая битовая маска:<br/>SQL_DTR_DROP_TRANSLATION<br/><br/>Встроенный драйвер SQL-92 с поддержкой полного уровня всегда будет возвращать этот параметр, как поддерживается.|
|SQL_DROP_VIEW|3.0|Битовая маска SQLUINTEGER, перечисление предложений в инструкции **DROP VIEW** , как определено в SQL-92, поддерживаемое источником данных.<br/><br/>Для определения поддерживаемых предложений используются следующие битовые маски:<br/>SQL_DV_DROP_VIEW<br/>SQL_DV_CASCADE<br/>SQL_DV_RESTRICT<br/><br/>Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.|
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты динамического курсора, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA1_NEXT = аргумент *фетчориентатион* SQL_FETCH_NEXT поддерживается при вызове **SQLFetchScroll** , если курсор является динамическим курсором.<br/>SQL_CA1_ABSOLUTE = *фетчориентатион* аргументы SQL_FETCH_FIRST, SQL_FETCH_LAST и SQL_FETCH_ABSOLUTE поддерживаются при вызове **SQLFetchScroll** , если курсор является динамическим курсором. (Набор строк, который будет извлекаться, не зависит от текущей позиции курсора.)<br/>SQL_CA1_RELATIVE = *фетчориентатион* аргументы SQL_FETCH_PRIOR и SQL_FETCH_RELATIVE поддерживаются при вызове **SQLFetchScroll** , если курсор является динамическим курсором. (Набор строк, который будет извлекаться, зависит от текущей позиции курсора. Обратите внимание, что это отделено от SQL_FETCH_NEXT поскольку в однонаправленном курсоре поддерживается только SQL_FETCH_NEXT.)<br/>SQL_CA1_BOOKMARK = аргумент *фетчориентатион* SQL_FETCH_BOOKMARK поддерживается при вызове **SQLFetchScroll** , если курсор является динамическим курсором.<br/>SQL_CA1_LOCK_EXCLUSIVE = аргумент *LockType* SQL_LOCK_EXCLUSIVE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_LOCK_NO_CHANGE = аргумент *LockType* SQL_LOCK_NO_CHANGE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_LOCK_UNLOCK = аргумент *LockType* SQL_LOCK_UNLOCK поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_POS_POSITION = аргумент *операции* SQL_POSITION поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_POS_UPDATE = аргумент *операции* SQL_UPDATE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_POS_DELETE = аргумент *операции* SQL_DELETE поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_POS_REFRESH = аргумент *операции* SQL_REFRESH поддерживается при вызове функции **SQLSetPos** , если курсор является динамическим курсором.<br/>SQL_CA1_POSITIONED_UPDATE = обновление, в котором поддерживается текущая инструкция SQL, если курсор является динамическим курсором. (Серверный драйвер начального уровня SQL-92 всегда будет возвращать этот параметр, как поддерживается).<br/>SQL_CA1_POSITIONED_DELETE = удаление, где текущая инструкция SQL поддерживается, если курсор является динамическим курсором. (Серверный драйвер начального уровня SQL-92 всегда будет возвращать этот параметр, как поддерживается).<br/>SQL_CA1_SELECT_FOR_UPDATE = инструкция SELECT для инструкции UPDATE SQL поддерживается, если курсор является динамическим курсором. (Серверный драйвер начального уровня SQL-92 всегда будет возвращать этот параметр, как поддерживается).<br/>SQL_CA1_BULK_ADD = аргумент *операции* SQL_ADD поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.<br/>SQL_CA1_BULK_UPDATE_BY_BOOKMARK = аргумент *операции* SQL_UPDATE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.<br/>SQL_CA1_BULK_DELETE_BY_BOOKMARK = аргумент *операции* SQL_DELETE_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.<br/>SQL_CA1_BULK_FETCH_BY_BOOKMARK = аргумент *операции* SQL_FETCH_BY_BOOKMARK поддерживается в вызове **SQLBulkOperations** , если курсор является динамическим курсором.<br/><br/>Драйвер, поддерживающий промежуточный уровень SQL-92, обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE, так как поддерживаются прокручиваемые курсоры посредством внедренной инструкции SQL FETCH. Так как это не определяет непосредственно базовую поддержку SQL, возможно, прокручиваемые курсоры не поддерживаются даже для драйвера, соответствующего промежуточному уровню SQL-92.|
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты динамического курсора, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA2_READ_ONLY_CONCURRENCY = динамический курсор только для чтения, в котором обновления не разрешены, поддерживаются. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_READ_ONLY для динамического курсора).<br/>SQL_CA2_LOCK_CONCURRENCY = динамический курсор, который использует самый низкий уровень блокировки, достаточный для того, чтобы гарантировать, что строка может быть обновлена. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_LOCK для динамического курсора.) Эти блокировки должны соответствовать уровню изоляции транзакций, заданному атрибутом подключения SQL_ATTR_TXN_ISOLATION.<br/>SQL_CA2_OPT_ROWVER_CONCURRENCY = динамический курсор, использующий управление оптимистичным параллелизмом, Сравнение версий строк поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_ROWVER для динамического курсора.)<br/>SQL_CA2_OPT_VALUES_CONCURRENCY = динамический курсор, использующий управление оптимистичным параллелизмом, сравнение значений поддерживается. (Атрибут инструкции SQL_ATTR_CONCURRENCY может быть SQL_CONCUR_VALUES для динамического курсора.)<br/>SQL_CA2_SENSITIVITY_ADDITIONS = добавленные строки видимы динамическому курсору; курсор может перейти к этим строкам. (Когда эти строки добавляются в курсор, зависит от драйвера.)<br/>SQL_CA2_SENSITIVITY_DELETIONS = удаленные строки больше не доступны динамическому курсору и не оставляют "отверстие" в результирующем наборе; После прокрутки динамического курсора из удаленной строки она не может вернуться к этой строке.<br/>SQL_CA2_SENSITIVITY_UPDATES = обновления строк видимы для динамического курсора; Если динамический курсор прокручивается из и возвращается к обновленной строке, то возвращаемые курсором данные являются обновленными, а не исходными данными.<br/>SQL_CA2_MAX_ROWS_SELECT = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **SELECT** , если курсор является динамическим курсором.<br/>SQL_CA2_MAX_ROWS_INSERT = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **INSERT** , если курсор является динамическим курсором.<br/>SQL_CA2_MAX_ROWS_DELETE = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **Delete** , если курсор является динамическим курсором.<br/>SQL_CA2_MAX_ROWS_UPDATE = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **Update** , если курсор является динамическим курсором.<br/>SQL_CA2_MAX_ROWS_CATALOG = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на результирующие наборы **каталога** , когда курсор является динамическим курсором.<br/>SQL_CA2_MAX_ROWS_AFFECTS_ALL = атрибут инструкции SQL_ATTR_MAX_ROWS влияет на инструкции **SELECT**, **INSERT**, **Delete**и **Update** , а также на результирующие наборы **каталога** , если курсор является динамическим курсором.<br/>SQL_CA2_CRC_EXACT = точное число строк доступно в поле диагностики SQL_DIAG_CURSOR_ROW_COUNT, если курсор является динамическим курсором.<br/>SQL_CA2_CRC_APPROXIMATE = приблизительное число строк доступно в поле диагностики SQL_DIAG_CURSOR_ROW_COUNT, если курсор является динамическим курсором.<br/>SQL_CA2_SIMULATE_NON_UNIQUE = драйвер не гарантирует, что смоделированные позиционированные инструкции UPDATE или DELETE повлияют только на одну строку, если курсор является динамическим курсором; Это гарантируется за пределом приложения. (Если инструкция затрагивает более одной строки, **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операций курсора].) Чтобы задать это поведение, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_SIMULATE_CURSOR, для которого задано значение SQL_SC_NON_UNIQUE.<br/>SQL_CA2_SIMULATE_TRY_UNIQUE = драйвер пытается гарантировать, что смоделированные позиционированные обновления или инструкции DELETE будут влиять только на одну строку, если курсор является динамическим курсором. Драйвер всегда выполняет такие инструкции, даже если они могут повлиять на более чем одну строку, например при отсутствии уникального ключа. (Если инструкция затрагивает более одной строки, **SQLExecute** или **SQLExecDirect** возвращает SQLSTATE 01001 [конфликт операций курсора].) Чтобы задать это поведение, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_SIMULATE_CURSOR, для которого задано значение SQL_SC_TRY_UNIQUE.<br/>SQL_CA2_SIMULATE_UNIQUE = драйвер гарантирует, что смоделированные позиционированные инструкции UPDATE или DELETE повлияют только на одну строку, если курсор является динамическим курсором. Если драйвер не может гарантировать это для данной инструкции, **SQLExecDirect** или **SQLPREPARE** возвращают SQLSTATE 01001 (конфликт операций курсора). Чтобы задать это поведение, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_SIMULATE_CURSOR, для которого задано значение SQL_SC_UNIQUE.|
|SQL_EXPRESSIONS_IN_ORDERBY|1.0|Символьная строка: "Y", если источник данных поддерживает выражения в списке **ORDER BY** ; "N", если нет.|
|SQL_FILE_USAGE|2.0|Значение СКЛУСМАЛЛИНТ, указывающее, как одноуровневый драйвер непосредственно обрабатывает файлы в источнике данных:<br/>SQL_FILE_NOT_SUPPORTED = драйвер не является одноуровневое. Например, драйвер ORACLE — это двухуровневый драйвер.<br/>SQL_FILE_TABLE = одноуровневый драйвер рассматривает файлы в источнике данных как таблицы. Например, драйвер xbase обрабатывает каждый файл xbase как таблицу.<br/>SQL_FILE_CATALOG = одноуровневый драйвер рассматривает файлы в источнике данных как каталог. Например, драйвер Microsoft Access обрабатывает каждый файл Microsoft Access как полную базу данных.<br/><br/>Приложение может использовать его для определения того, как пользователи будут выбирать данные. Например, xbase пользователи часто считают данные хранимыми в файлах, тогда как пользователи ORACLE и Microsoft Access обычно считают данные хранимыми в таблицах.<br/><br/>Когда пользователь выбирает источник данных xbase, приложение может отобразить диалоговое окно Открыть общий **файл** Windows. Когда пользователь выбирает источник данных Microsoft Access или ORACLE, приложение может отобразить диалоговое окно Выбор пользовательской **таблицы** .|
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты однопроходного курсора, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA1_NEXT<br/>SQL_CA1_LOCK_EXCLUSIVE<br/>SQL_CA1_LOCK_NO_CHANGE<br/>SQL_CA1_LOCK_UNLOCK<br/>SQL_CA1_POS_POSITION<br/>SQL_CA1_POS_UPDATE<br/>SQL_CA1_POS_DELETE<br/>SQL_CA1_POS_REFRESH<br/>SQL_CA1_POSITIONED_UPDATE<br/>SQL_CA1_POSITIONED_DELETE<br/>SQL_CA1_SELECT_FOR_UPDATE<br/>SQL_CA1_BULK_ADD<br/>SQL_CA1_BULK_UPDATE_BY_BOOKMARK<br/>SQL_CA1_BULK_DELETE_BY_BOOKMARK<br/>SQL_CA1_BULK_FETCH_BY_BOOKMARK<br/><br/>Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и в описаниях замените "однонаправленный курсор" на "динамический курсор").|
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты однопроходного курсора, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA2_READ_ONLY_CONCURRENCY<br/>SQL_CA2_LOCK_CONCURRENCY<br/>SQL_CA2_OPT_ROWVER_CONCURRENCY<br/>SQL_CA2_OPT_VALUES_CONCURRENCY<br/>SQL_CA2_SENSITIVITY_ADDITIONS<br/>SQL_CA2_SENSITIVITY_DELETIONS<br/>SQL_CA2_SENSITIVITY_UPDATES<br/>SQL_CA2_MAX_ROWS_SELECT<br/>SQL_CA2_MAX_ROWS_INSERT<br/>SQL_CA2_MAX_ROWS_DELETE<br/>SQL_CA2_MAX_ROWS_UPDATE<br/>SQL_CA2_MAX_ROWS_CATALOG<br/>SQL_CA2_MAX_ROWS_AFFECTS_ALL<br/>SQL_CA2_CRC_EXACT<br/>SQL_CA2_CRC_APPROXIMATE<br/>SQL_CA2_SIMULATE_NON_UNIQUE<br/>SQL_CA2_SIMULATE_TRY_UNIQUE<br/>SQL_CA2_SIMULATE_UNIQUE<br/><br/>Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (и в описаниях замените "однонаправленный курсор" на "динамический курсор").|
|SQL_GETDATA_EXTENSIONS|2.0|Битовая маска SQLUINTEGER, перечисление расширений в **SQLGetData**.<br/><br/>Следующие битовые маски используются вместе с флагом, чтобы определить, какие общие расширения драйвер поддерживает для **SQLGetData**:<br/>SQL_GD_ANY_COLUMN = **SQLGetData** можно вызывать для любого несвязанного столбца, включая те, которые предшествуют последнему привязанному столбцу. Обратите внимание, что столбцы должны вызываться в порядке возрастания номера столбца, если также не возвращается SQL_GD_ANY_ORDER.<br/>SQL_GD_ANY_ORDER = **SQLGetData** можно вызывать для несвязанных столбцов в любом порядке. Обратите внимание, что **SQLGetData** может вызываться только для столбцов после последнего связанного столбца, если не возвращается значение SQL_GD_ANY_COLUMN.<br/>SQL_GD_BLOCK = **SQLGetData** можно вызывать для непривязанного столбца в любой строке блока (где размер набора строк больше 1) данных после позиционирования в эту строку с помощью функции **SQLSetPos**.<br/>SQL_GD_BOUND = **SQLGetData** можно вызывать для связанных столбцов в дополнение к несвязанным столбцам. Драйвер не может вернуть это значение, если он также не возвращает SQL_GD_ANY_COLUMN.<br/>Для возврата значений выходных параметров можно вызвать SQL_GD_OUTPUT_PARAMS = **SQLGetData** . Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](../develop-app/retrieving-output-parameters-using-sqlgetdata.md).<br/><br/>**SQLGetData** требуется для возврата данных только из несвязанных столбцов, которые происходят после последнего связанного столбца, вызываются в порядке возрастания номера столбца и не находятся в строке блока строк.<br/><br/>Если драйвер поддерживает закладки (с фиксированной длиной или переменной длиной), он должен поддерживать вызов **SQLGetData** для столбца 0. Эта поддержка необходима независимо от того, что возвращает драйвер для вызова **SQLGetInfo** с помощью SQL_GETDATA_EXTENSIONS *инфотипе*.|
|SQL_GROUP_BY|2.0|Значение СКЛУСМАЛЛИНТ, указывающее связь между столбцами в предложении **Group By** и неагрегированными столбцами в списке выбора:<br/>SQL_GB_COLLATE = предложение **COLLATE** можно указать в конце каждого столбца группирования. (ODBC 3,0)<br/>SQL_GB_NOT_SUPPORTED = предложения **Group By** не поддерживаются. (ODBC 2,0)<br/>SQL_GB_GROUP_BY_EQUALS_SELECT = предложение **Group By** должно содержать все неагрегированные столбцы в списке выбора. Он не может содержать другие столбцы. Например, **выберите отдел, Макс (оклад) из группы сотрудников по Отделу**. (ODBC 2,0)<br/>SQL_GB_GROUP_BY_CONTAINS_SELECT = предложение **Group By** должно содержать все неагрегированные столбцы в списке выбора. Он может содержать столбцы, которых нет в списке выбора. Например, **выберите отдел, Макс (зарплата) из группы сотрудников по Отделу, возраст**. (ODBC 2,0)<br/>SQL_GB_NO_RELATION = столбцы в предложении **Group By** и список выбора не связаны. Значение несгруппированных неагрегированных столбцов в списке выбора зависит от источника данных. Например, **выберите отдел, ОКЛАД из группы сотрудников по Отделу, возраст**. (ODBC 2,0)<br/><br/>Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать параметр SQL_GB_GROUP_BY_EQUALS_SELECT, как поддерживается. Драйвер, совместимый с SQL-92, всегда будет возвращать параметр SQL_GB_COLLATE, как поддерживается. Если ни один из параметров не поддерживается, то предложение **Group By** не поддерживается источником данных.|
|SQL_IDENTIFIER_CASE|1.0|Значение СКЛУСМАЛЛИНТ следующим образом:<br/>SQL_IC_UPPER = идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в верхнем регистре.<br/>SQL_IC_LOWER = идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в нижнем регистре.<br/>SQL_IC_SENSITIVE = идентификаторы в SQL учитывают регистр и хранятся в системном каталоге в смешанном регистре.<br/>SQL_IC_MIXED = идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в смешанном регистре.<br/><br/>Поскольку идентификаторы в SQL-92 никогда не учитывают регистр, драйвер, который строго соответствует SQL-92 (любой уровень), никогда не будет возвращать параметр SQL_IC_SENSITIVE, как поддерживается.|
|SQL_IDENTIFIER_QUOTE_CHAR|1.0|Символьная строка, используемая в качестве начального и конечного разделителей (разделенных кавычками) идентификаторов в инструкциях SQL. (Идентификаторы, переданные в качестве аргументов в функции ODBC, не обязательно должны быть заключены в кавычки.) Если источник данных не поддерживает заключенные в кавычки идентификаторы, то возвращается пустое значение.<br/><br/>Эту символьную строку можно также использовать для заключения в кавычки аргументов функции каталога, если атрибут Connection SQL_ATTR_METADATA_ID имеет значение SQL_TRUE.<br/><br/>Поскольку символ кавычки идентификатора в SQL-92 представляет собой двойную кавычку ("), драйвер, который строго соответствует SQL-92, всегда будет возвращать символ двойной кавычки.|
|SQL_INDEX_KEYWORDS|3.0|Битовая маска SQLUINTEGER, которая перечисляет ключевые слова в инструкции CREATE INDEX, поддерживаемые драйвером.<br/>SQL_IK_NONE = ни одно из ключевых слов не поддерживается.<br/>Поддерживается ключевое слово SQL_IK_ASC = ASC.<br/>SQL_IK_DESC = ключевое слово DESC поддерживается.<br/>SQL_IK_ALL = все ключевые слова поддерживаются.<br/><br/>Чтобы узнать, поддерживается ли инструкция CREATE INDEX, приложение вызывает **SQLGetInfo** с типом данных SQL_DLL_INDEX.|
|SQL_INFO_SCHEMA_VIEWS|3.0|Битовая маска SQLUINTEGER, которая перечисляет представления в INFORMATION_SCHEMA, поддерживаемые драйвером. Представления в, а также содержимое INFORMATION_SCHEMA являются определенными в SQL-92.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения поддерживаемых представлений используются следующие битовые маски:<br/>SQL_ISV_ASSERTIONS = определяет утверждения каталога, принадлежащие данному пользователю. (Полный уровень)<br/>SQL_ISV_CHARACTER_SETS = определяет наборы символов каталога, к которым может получить доступ указанный пользователь. (Промежуточный уровень)<br/>SQL_ISV_CHECK_CONSTRAINTS = определяет ПРОВЕРОЧные ограничения, принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_COLLATIONS = определяет параметры сортировки символов для каталога, к которому может получить доступ данный пользователь. (Полный уровень)<br/>SQL_ISV_COLUMN_DOMAIN_USAGE = определяет столбцы для каталога, зависящие от доменов, определенных в каталоге и принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_COLUMN_PRIVILEGES = определяет привилегии для столбцов постоянных таблиц, доступных или предоставленных данным пользователем. (Уровень переходов FIPS)<br/>SQL_ISV_COLUMNS = определяет столбцы постоянных таблиц, к которым может получить доступ данный пользователь. (Уровень переходов FIPS)<br/>SQL_ISV_CONSTRAINT_COLUMN_USAGE — аналогично CONSTRAINT_TABLE_USAGE View, столбцы определяются для различных ограничений, принадлежащих данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_CONSTRAINT_TABLE_USAGE = определяет таблицы, используемые ограничениями (ссылочные, уникальные и проверочные), и принадлежат заданному пользователю. (Промежуточный уровень)<br/>SQL_ISV_DOMAIN_CONSTRAINTS = определяет ограничения домена (для доменов в каталоге), к которым может получить доступ указанный пользователь. (Промежуточный уровень)<br/>SQL_ISV_DOMAINS = определяет домены, определенные в каталоге, к которому может получить доступ пользователь. (Промежуточный уровень)<br/>SQL_ISV_KEY_COLUMN_USAGE = определяет столбцы, определенные в каталоге и ограниченные ключами данного пользователя. (Промежуточный уровень)<br/>SQL_ISV_REFERENTIAL_CONSTRAINTS = определяет ссылочные ограничения, принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_SCHEMATA = определяет схемы, принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_SQL_LANGUAGES = определяет уровни соответствия SQL, параметры и диалекты, поддерживаемые реализацией SQL. (Промежуточный уровень)<br/>SQL_ISV_TABLE_CONSTRAINTS = определяет ограничения таблицы, принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_TABLE_PRIVILEGES = определяет привилегии для постоянных таблиц, доступных или предоставленных данным пользователем. (Уровень переходов FIPS)<br/>SQL_ISV_TABLES = определяет постоянные таблицы, определенные в каталоге, к которым может получить доступ данный пользователь. (Уровень переходов FIPS)<br/>SQL_ISV_TRANSLATIONS = определяет переводы символов для каталога, к которому может получить доступ данный пользователь. (Полный уровень)<br/>SQL_ISV_USAGE_PRIVILEGES = определяет привилегии на использование объектов каталога, доступных или принадлежащих данному пользователю. (Уровень переходов FIPS)<br/>SQL_ISV_VIEW_COLUMN_USAGE = определяет столбцы, от которых зависят представления каталога, принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_VIEW_TABLE_USAGE = определяет таблицы, от которых зависят представления каталога, принадлежащие данному пользователю. (Промежуточный уровень)<br/>SQL_ISV_VIEWS = определяет просмотренные таблицы, определенные в этом каталоге, к которым может получить доступ данный пользователь. (Уровень переходов FIPS)|
|SQL_INSERT_STATEMENT|3.0|Битовая маска SQLUINTEGER, которая указывает на поддержку инструкций **INSERT** :<br/>SQL_IS_INSERT_LITERALS<br/>SQL_IS_INSERT_SEARCHED<br/>SQL_IS_SELECT_INTO<br/><br/>Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_INTEGRITY|1.0|Строка символов: "Y", если источник данных поддерживает функцию улучшения целостности; "N", если нет.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_ODBC_SQL_OPT_IEF ODBC 2,0 *инфотипе* .|
|SQL_KEYSET_CURSOR_ATTRIBUTES1|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты курсора KEYSET, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_KEYSET_CURSOR_ATTRIBUTES2.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA1_NEXT<br/>SQL_CA1_ABSOLUTE<br/>SQL_CA1_RELATIVE<br/>SQL_CA1_BOOKMARK<br/>SQL_CA1_LOCK_EXCLUSIVE<br/>SQL_CA1_LOCK_NO_CHANGE<br/>SQL_CA1_LOCK_UNLOCK<br/>SQL_CA1_POS_POSITION<br/>SQL_CA1_POS_UPDATE<br/>SQL_CA1_POS_DELETE<br/>SQL_CA1_POS_REFRESH<br/>SQL_CA1_POSITIONED_UPDATE<br/>SQL_CA1_POSITIONED_DELETE<br/>SQL_CA1_SELECT_FOR_UPDATE<br/>SQL_CA1_BULK_ADD<br/>SQL_CA1_BULK_UPDATE_BY_BOOKMARK<br/>SQL_CA1_BULK_DELETE_BY_BOOKMARK<br/>SQL_CA1_BULK_FETCH_BY_BOOKMARK<br/><br/>Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и подставьте курсор, управляемый набором ключей, для динамического курсора в описаниях).<br/><br/>Драйвер, поддерживающий промежуточный уровень SQL-92, обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE, так как они поддерживаются, так как драйвер поддерживает прокручиваемые курсоры с помощью внедренной инструкции SQL FETCH. Так как это не определяет непосредственно базовую поддержку SQL, возможно, прокручиваемые курсоры не поддерживаются даже для драйвера, соответствующего промежуточному уровню SQL-92.|
|SQL_KEYSET_CURSOR_ATTRIBUTES2|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты курсора KEYSET, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_KEYSET_CURSOR_ATTRIBUTES1.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA2_READ_ONLY_CONCURRENCY<br/>SQL_CA2_LOCK_CONCURRENCY<br/>SQL_CA2_OPT_ROWVER_CONCURRENCY<br/>SQL_CA2_OPT_VALUES_CONCURRENCY<br/>SQL_CA2_SENSITIVITY_ADDITIONS<br/>SQL_CA2_SENSITIVITY_DELETIONS<br/>SQL_CA2_SENSITIVITY_UPDATES<br/>SQL_CA2_MAX_ROWS_SELECT<br/>SQL_CA2_MAX_ROWS_INSERT<br/>SQL_CA2_MAX_ROWS_DELETE<br/>SQL_CA2_MAX_ROWS_UPDATE<br/>SQL_CA2_MAX_ROWS_CATALOG<br/>SQL_CA2_MAX_ROWS_AFFECTS_ALL<br/>SQL_CA2_CRC_EXACT<br/>SQL_CA2_CRC_APPROXIMATE<br/>SQL_CA2_SIMULATE_NON_UNIQUE<br/>SQL_CA2_SIMULATE_TRY_UNIQUE<br/>SQL_CA2_SIMULATE_UNIQUE<br/><br/>Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (и подставьте курсор, управляемый набором ключей, для динамического курсора в описаниях).|
|SQL_KEYWORDS|2.0|Символьная строка, содержащая разделенный запятыми список всех ключевых слов, зависящих от источника данных. Этот список не содержит ключевые слова, относящиеся к ODBC или ключевым словам, используемым как источником данных, так и ODBC. Этот список представляет все зарезервированные ключевые слова; приложения, поддерживающие взаимодействие, не должны использовать эти слова в именах объектов.<br/><br/>Список ключевых слов ODBC см. в разделе [зарезервированные ключевые слова](../appendixes/reserved-keywords.md) в [приложении C: грамматика SQL](../appendixes/appendix-c-sql-grammar.md). Значение **#define** SQL_ODBC_KEYWORDS содержит список ключевых слов ODBC с разделителями-запятыми.|
|SQL_LIKE_ESCAPE_CLAUSE|2.0|Символьная строка: "Y", если источник данных поддерживает escape-символ для символа процента (%) и символ подчеркивания (_) в предикате **Like** , а драйвер поддерживает синтаксис ODBC для определения escape-символа предиката **Like** ; В противном случае — значение "N".|
|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|3.0|Значение SQLUINTEGER, указывающее максимальное количество активных параллельных операторов в асинхронном режиме, которые драйвер может поддерживать для данного соединения. Если нет какого-либо конкретного ограничения или неизвестного ограничения, это значение равно нулю.|
|SQL_MAX_BINARY_LITERAL_LEN|2.0|Значение SQLUINTEGER, указывающее максимальную длину (число шестнадцатеричных символов, исключая префикс литерала и суффикс, возвращаемый **SQLGetTypeInfo**) двоичного литерала в инструкции SQL. Например, двоичный литерал 0xFFAA имеет длину 4. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.|
|SQL_MAX_CATALOG_NAME_LEN|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени каталога в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.<br/><br/>Драйвер полного соответствия FIPS будет возвращать не менее 128.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_MAX_QUALIFIER_NAME_LEN ODBC 2,0 *инфотипе* .|
|SQL_MAX_CHAR_LITERAL_LEN|2.0|Значение SQLUINTEGER, указывающее максимальную длину (число символов, за исключением префикса литерала и суффикса, возвращаемого **SQLGetTypeInfo**) символьного литерала в инструкции SQL. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.|
|SQL_MAX_COLUMN_NAME_LEN|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени столбца в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.|
|SQL_MAX_COLUMNS_IN_GROUP_BY|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество столбцов, разрешенное в предложении **Group By** . Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 6. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 15.|
|SQL_MAX_COLUMNS_IN_INDEX|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимально допустимое количество столбцов в индексе. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.|
|SQL_MAX_COLUMNS_IN_ORDER_BY|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное число столбцов, разрешенное в предложении **ORDER BY** . Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 6. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 15.|
|SQL_MAX_COLUMNS_IN_SELECT|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное число столбцов, допустимое в списке выбора. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает по крайней мере 100. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 250.|
|SQL_MAX_COLUMNS_IN_TABLE|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимально допустимое количество столбцов в таблице. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает по крайней мере 100. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 250.|
|SQL_MAX_CONCURRENT_ACTIVITIES|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных инструкций, которые драйвер может поддерживать для соединения. Инструкция определена как активная, если она имеет ожидающие результаты, а термин «Results» означает строки из операции **выбора** или строки, на которые повлияла операция **вставки**, **обновления**или **удаления** (например, число строк), или если она находится в NEED_DATA состоянии. Это значение может отражать ограничение, налагаемое либо драйвером, либо источником данных. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_ACTIVE_STATEMENTS ODBC 2,0 *инфотипе* .|
|SQL_MAX_CURSOR_NAME_LEN|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени курсора в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.|
|SQL_MAX_DRIVER_CONNECTIONS|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество активных соединений, которые драйвер может поддерживать для среды. Это значение может отражать ограничение, налагаемое либо драйвером, либо источником данных. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_ACTIVE_CONNECTIONS ODBC 2,0 *инфотипе* .|
|SQL_MAX_IDENTIFIER_LEN|3.0|Объект СКЛУСМАЛЛИНТ, указывающий максимальный размер в символах, поддерживаемый источником данных для определяемых пользователем имен.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.|
|SQL_MAX_INDEX_SIZE|2.0|Значение SQLUINTEGER, указывающее максимальное число байтов, разрешенное в Объединенных полях индекса. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.|
|SQL_MAX_PROCEDURE_NAME_LEN|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени процедуры в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.|
|SQL_MAX_ROW_SIZE|2.0|Значение SQLUINTEGER, указывающее максимальную длину одной строки в таблице. Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает по крайней мере 2 000. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 8 000.|
|SQL_MAX_ROW_SIZE_INCLUDES_LONG|3.0|Строка символов: "Y", если максимальный размер строки, возвращаемый для типа сведений SQL_MAX_ROW_SIZE, содержит длину всех SQL_LONGVARCHAR и SQL_LONGVARBINARY столбцов в строке; В противном случае — значение "N".|
|SQL_MAX_SCHEMA_NAME_LEN|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени схемы в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_MAX_OWNER_NAME_LEN ODBC 2,0 *инфотипе* .|
|SQL_MAX_STATEMENT_LEN|2.0|Значение SQLUINTEGER, указывающее максимальную длину (число символов, включая пробел) инструкции SQL. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.|
|SQL_MAX_TABLE_NAME_LEN|1.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени таблицы в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 18. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 128.|
|SQL_MAX_TABLES_IN_SELECT|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальное количество таблиц, допустимых в предложении **from** инструкции **SELECT** . Если заданное ограничение отсутствует или неизвестен, это значение устанавливается равным нулю.<br/><br/>Драйвер, поддерживающий уровень ввода FIPS, возвращает не менее 15. Драйвер соответствия промежуточного уровня FIPS будет возвращать не менее 50.|
|SQL_MAX_USER_NAME_LEN|2.0|Значение СКЛУСМАЛЛИНТ, указывающее максимальную длину имени пользователя в источнике данных. Если максимальная длина или длина не известны, это значение устанавливается равным нулю.|
|SQL_MULT_RESULT_SETS|1.0|Символьная строка: "Y", если источник данных поддерживает несколько результирующих наборов, "N", если нет.<br/><br/>Дополнительные сведения о нескольких результирующих наборах см. в разделе [несколько результатов](../develop-app/multiple-results.md).|
|SQL_MULTIPLE_ACTIVE_TXN|1.0|Строка символов: "Y", если драйвер поддерживает несколько активных транзакций одновременно, "N", если в любой момент времени может быть активна только одна транзакция.<br/><br/>Сведения, возвращаемые для этого типа данных, не применяются в случае распределенных транзакций.|
|SQL_NEED_LONG_DATA_LEN|2.0|Символьная строка: "Y", если источнику данных требуется длина длинного значения данных (тип данных SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных, зависящий от источника данных), прежде чем это значение будет отправлено в источник данных, "N", если нет. Дополнительные сведения см. в разделе [функция SQLBindParameter](sqlbindparameter-function.md) и [Функция SQLSetPos](sqlsetpos-function.md).|
|SQL_NON_NULLABLE_COLUMNS|1.0|Значение СКЛУСМАЛЛИНТ, указывающее, поддерживает ли источник данных не значение NULL в столбцах:<br/>SQL_NNC_NULL = все столбцы должны допускать значение null.<br/>SQL_NNC_NON_NULL = столбцы не могут допускать значения NULL. (Источник данных поддерживает ограничение столбца **NOT NULL** в инструкциях **CREATE TABLE** .)<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, возвращает SQL_NNC_NON_NULL.|
|SQL_NULL_COLLATION|2.0|Значение СКЛУСМАЛЛИНТ, указывающее, где в результирующем наборе сортируются значения NULL:<br/>SQL_NC_END = NULL сортируются в конце результирующего набора независимо от ключевых слов ASC и DESC.<br/>SQL_NC_HIGH = NULL сортируются по верхнему краю результирующего набора в зависимости от ключевых слов ASC или DESC.<br/>SQL_NC_LOW = NULL сортируются в нижней части результирующего набора в зависимости от ключевых слов ASC или DESC.<br/>SQL_NC_START = NULL сортируются в начале результирующего набора независимо от ключевых слов ASC и DESC.|
|SQL_NUMERIC_FUNCTIONS|1.0|Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.<br/><br/>Битовая маска SQLUINTEGER, которая перечисляет скалярные числовые функции, поддерживаемые драйвером и связанным источником данных.<br/><br/>Для определения поддерживаемых числовых функций используются следующие битовые маски.<br/>SQL_FN_NUM_ABS (ODBC 1,0)<br/>SQL_FN_NUM_ACOS (ODBC 1,0)<br/>SQL_FN_NUM_ASIN (ODBC 1,0)<br/>SQL_FN_NUM_ATAN (ODBC 1,0)<br/>SQL_FN_NUM_ATAN2 (ODBC 1,0)<br/>SQL_FN_NUM_CEILING (ODBC 1,0)<br/>SQL_FN_NUM_COS (ODBC 1,0)<br/>SQL_FN_NUM_COT (ODBC 1,0)<br/>SQL_FN_NUM_DEGREES (ODBC 2,0)<br/>SQL_FN_NUM_EXP (ODBC 1,0)<br/>SQL_FN_NUM_FLOOR (ODBC 1,0)<br/>SQL_FN_NUM_LOG (ODBC 1,0)<br/>SQL_FN_NUM_LOG10 (ODBC 2,0)<br/>SQL_FN_NUM_MOD (ODBC 1,0)<br/>SQL_FN_NUM_PI (ODBC 1,0)<br/>SQL_FN_NUM_POWER (ODBC 2,0)<br/>SQL_FN_NUM_RADIANS (ODBC 2,0)<br/>SQL_FN_NUM_RAND (ODBC 1,0)<br/>SQL_FN_NUM_ROUND (ODBC 2,0)<br/>SQL_FN_NUM_SIGN (ODBC 1,0)<br/>SQL_FN_NUM_SIN (ODBC 1,0)<br/>SQL_FN_NUM_SQRT (ODBC 1,0)<br/>SQL_FN_NUM_TAN (ODBC 1,0)<br/>SQL_FN_NUM_TRUNCATE (ODBC 2,0)|
|SQL_ODBC_INTERFACE_CONFORMANCE|3.0|Значение SQLUINTEGER, указывающее уровень интерфейса ODBC 3 *. x* , который соответствует драйверу.<br/><br/>SQL_OIC_CORE: минимальный уровень, которым должны соответствовать все драйверы ODBC. Этот уровень включает основные элементы интерфейса, такие как функции подключения, функции для подготовки и исполнения инструкции SQL, основные функции метаданных результирующего набора, базовые функции каталога и т. д.<br/>SQL_OIC_LEVEL1: уровень, включая основные функции уровня соответствия стандартам, а также прокручиваемые курсоры, закладки, позиционированные обновления и удаления и т. д.<br/>SQL_OIC_LEVEL2: уровень, включающий функции уровня соответствия стандартам уровня 1, а также расширенные функции, такие как конфиденциальные курсоры; обновление, удаление и обновление по закладкам; Поддержка хранимых процедур; функции каталога для первичных и внешних ключей; Поддержка нескольких каталогов; и т. д.<br/><br/>Дополнительные сведения см. в разделе [уровни соответствия интерфейсов](../develop-app/interface-conformance-levels.md).|
|SQL_ODBC_VER|1.0|Символьная строка с версией ODBC, которая соответствует диспетчеру драйверов. Версия имеет вид # #. # #. 0000, где первые две цифры — основной номер версии, а следующие две цифры — дополнительный номер версии. Это реализовано только в диспетчере драйверов.|
|SQL_OJ_CAPABILITIES|2,01|Битовая маска SQLUINTEGER, которая перечисляет типы внешних соединений, поддерживаемые драйвером и источником данных. Для определения поддерживаемых типов используются следующие битовые маски:<br/>SQL_OJ_LEFT = левые внешние объединения поддерживаются.<br/>SQL_OJ_RIGHT — поддерживаются правая внешние объединения.<br/>SQL_OJ_FULL = поддерживаются полные внешние объединения.<br/>SQL_OJ_NESTED = поддерживаются вложенные внешние объединения.<br/>SQL_OJ_NOT_ORDERED = имена столбцов в предложении ON внешнего объединения не обязательно должны находиться в том же порядке, что и соответствующие имена таблиц в предложении **внешнего объединения** .<br/>SQL_OJ_INNER = внутренняя таблица (правая таблица в левом внешнем соединении или Левая таблица в правом внешнем соединении) также может использоваться во внутреннем соединении. Это не относится к полным внешним объединениям, у которых нет внутренней таблицы.<br/>SQL_OJ_ALL_COMPARISON_OPS = оператор сравнения в предложении ON может быть любым из операторов сравнения ODBC. Если этот бит не задан, в внешних объединениях может использоваться только оператор сравнения Equals (=).<br/><br/>Если ни один из этих параметров не возвращается как поддерживаемый, предложение внешнего объединения не поддерживается.<br/><br/>Сведения о поддержке операторов реляционного объединения в инструкции SELECT, как определено в SQL-92, см. в разделе SQL_SQL92_RELATIONAL_JOIN_OPERATORS.|
|SQL_ORDER_BY_COLUMNS_IN_SELECT|2.0|Строка символов: "Y", если столбцы в предложении **ORDER BY** должны находиться в списке выбора; в противном случае — "N".|
|SQL_PARAM_ARRAY_ROW_COUNTS|3.0|SQLUINTEGER перечисление свойств драйвера, касающихся доступности количества строк в параметризованном выполнении. Имеет следующие значения:<br/>SQL_PARC_BATCH = количество отдельных строк доступно для каждого набора параметров. Это концептуально эквивалентно драйверу, создающему пакет инструкций SQL, по одному для каждого набора параметров в массиве. Расширенные сведения об ошибке можно получить с помощью поля дескриптор SQL_PARAM_STATUS_PTR.<br/>SQL_PARC_NO_BATCH = доступно только одно количество строк, то есть общее число строк, полученное в результате выполнения инструкции для всего массива параметров. Это концептуально эквивалентно обработке инструкции вместе с полным массивом параметров как одной атомарной единицей. Ошибки обрабатываются так же, как если бы выполнялась одна инструкция.|
|SQL_PARAM_ARRAY_SELECTS|3.0|SQLUINTEGER перечисление свойств драйвера, касающихся доступности результирующих наборов в параметризованном выполнении. Имеет следующие значения:<br/>SQL_PAS_BATCH = для каждого набора параметров доступен один результирующий набор. Это концептуально эквивалентно драйверу, создающему пакет инструкций SQL, по одному для каждого набора параметров в массиве.<br/>SQL_PAS_NO_BATCH = доступен только один результирующий набор, который представляет собой совокупный результат, полученный в результате выполнения инструкции для полного массива параметров. Это концептуально эквивалентно обработке инструкции вместе с полным массивом параметров как одной атомарной единицей.<br/>SQL_PAS_NO_SELECT = драйвер не позволяет выполнять инструкцию создания результирующего набора с массивом параметров.|
|SQL_POS_OPERATIONS|2.0|Битовая маска SQLINTEGER, перечисление операций поддержки в **SQLSetPos**.<br/><br/>Следующие битовые маски используются вместе с флагом для определения поддерживаемых параметров.<br/>SQL_POS_POSITION (ODBC 2,0)<br/>SQL_POS_REFRESH (ODBC 2,0)<br/>SQL_POS_UPDATE (ODBC 2,0)<br/>SQL_POS_DELETE (ODBC 2,0)<br/>SQL_POS_ADD (ODBC 2,0)|
|SQL_PROCEDURE_TERM|1.0|Символьная строка с именем поставщика источника данных для процедуры; Например, "процедура базы данных", "хранимая процедура", "процедура", "пакет" или "хранимый запрос".|
|SQL_PROCEDURES|1.0|Символьная строка: "Y", если источник данных поддерживает процедуры, а драйвер поддерживает синтаксис вызова процедур ODBC. В противном случае — значение "N".|
|SQL_QUOTED_IDENTIFIER_CASE|2.0|Значение СКЛУСМАЛЛИНТ следующим образом:<br/>SQL_IC_UPPER = заключенные в кавычки идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в верхнем регистре.<br/>SQL_IC_LOWER = заключенные в кавычки идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в нижнем регистре.<br/>SQL_IC_SENSITIVE = заключенные в кавычки идентификаторы в SQL учитывают регистр и хранятся в системном каталоге в смешанном регистре. (В базе данных, совместимой с SQL-92, заключенные в кавычки идентификаторы всегда чувствительны к регистру.)<br/>SQL_IC_MIXED = заключенные в кавычки идентификаторы в SQL не учитывают регистр и хранятся в системном каталоге в смешанном регистре.<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, всегда будет возвращать SQL_IC_SENSITIVE.|
|SQL_ROW_UPDATES|1.0|Символьная строка: "Y", если курсор, управляемый набором ключей или смешанный, поддерживает версии строк или значения для всех выбранных строк и, следовательно, может обнаруживать любые обновления, внесенные в строку любым пользователем со времени последней выборки строки. (Это относится только к обновлениям, а не к операциям удаления или вставки.) Драйвер может вернуть SQL_ROW_UPDATED флаг к массиву состояния строки при вызове **SQLFetchScroll** . В противном случае — "N".|
|SQL_SCHEMA_TERM|1.0|Символьная строка с именем поставщика источника данных для схемы; Например, "владелец", "идентификатор авторизации" или "схема".<br/><br/>Символьная строка может быть возвращена в верхнем, нижнем или смешанном регистрах.<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает "Schema".<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_OWNER_TERM ODBC 2,0 *инфотипе* .|
|SQL_SCHEMA_USAGE|2.0|Битовая маска SQLUINTEGER, которая перечисляет инструкции, в которых можно использовать схемы:<br/>SQL_SU_DML_STATEMENTS = схемы поддерживаются во всех инструкциях языка обработки данных: **SELECT**, **INSERT**, **Update**, **Delete**и, если поддерживается, **SELECT для Update** и позиционированных инструкций UPDATE и DELETE.<br/>SQL_SU_PROCEDURE_INVOCATION = схемы поддерживаются в операторе вызова процедуры ODBC.<br/>SQL_SU_TABLE_DEFINITION = схемы поддерживаются во всех инструкциях определения таблицы: **CREATE TABLE**, **Create View**, **ALTER TABLE**, **DROP TABLE**и **DROP VIEW**.<br/>SQL_SU_INDEX_DEFINITION = схемы поддерживаются во всех инструкциях определения индекса: **Создание индекса** и **DROP INDEX**.<br/>SQL_SU_PRIVILEGE_DEFINITION = схемы поддерживаются во всех инструкциях определения привилегий: **Grant** и **REVOKE**.<br/><br/>Драйвер на уровне ввода SQL-92 всегда будет возвращать параметры SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION и SQL_SU_PRIVILEGE_DEFINITION, как поддерживается.<br/><br/>Этот *инфотипе* был ПЕРЕИМЕНОВАН для ODBC 3,0 из SQL_OWNER_USAGE ODBC 2,0 *инфотипе* .|
|SQL_SCROLL_OPTIONS|1.0|Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.<br/><br/>Битовая маска SQLUINTEGER, которая перечисляет параметры прокрутки, поддерживаемые для прокручиваемых курсоров.<br/><br/>Для определения поддерживаемых параметров используются следующие битовые маски.<br/>SQL_SO_FORWARD_ONLY = курсор прокручивается вперед. (ODBC 1,0)<br/>SQL_SO_STATIC = данные в результирующем наборе являются статическими. (ODBC 2,0)<br/>SQL_SO_KEYSET_DRIVEN = драйвер сохраняет и использует ключи для каждой строки в результирующем наборе. (ODBC 1,0)<br/>SQL_SO_DYNAMIC = драйвер сохраняет ключи для каждой строки в наборе строк (размер набора ключей совпадает с размером наборов строк). (ODBC 1,0)<br/>SQL_SO_MIXED = драйвер сохраняет ключи для каждой строки набора ключей, а размер набора ключей больше размера набора строк. Курсор, управляемый набором ключей, находится внутри набора ключей и является динамическим за пределами набора ключей. (ODBC 1,0)<br/><br/>Дополнительные сведения о прокручиваемых курсорах см. в разделе [прокручиваемые курсоры](../develop-app/scrollable-cursors.md).|
|SQL_SEARCH_PATTERN_ESCAPE|1.0|Символьная строка, указывающая, что драйвер поддерживает в качестве escape-символа, позволяющего использовать символы подчеркивания шаблона (_) и знак процента (%) в качестве допустимых символов в шаблонах поиска. Этот escape-символ применяется только к тем аргументам функции каталога, которые поддерживают строки поиска. Если эта строка пуста, драйвер не поддерживает escape-символ шаблона поиска.<br/><br/>Так как этот тип информации не указывает на общую поддержку escape-символа в предикате **Like** , SQL-92 не включает требования для этой символьной строки.<br/><br/>Эта *инфотипеа* ограничена функциями каталога. Описание использования escape-символа в строках шаблона поиска см. в разделе [аргументы значения шаблона](../develop-app/pattern-value-arguments.md).|
|SQL_SERVER_NAME|1.0|Символьная строка с фактическим именем сервера, относящимся к источнику данных; полезно, когда имя источника данных используется во время **SQLConnect**, **SQLDriverConnect**и **SQLBrowseConnect**.|
|SQL_SPECIAL_CHARACTERS|2.0|Символьная строка, содержащая все специальные символы (т. е. все символы, за исключением от a до z, от A до Z, от 0 до 9 и символа подчеркивания), которые можно использовать в имени идентификатора, например имя таблицы, имя столбца или имя индекса, в источнике данных. Например, "# $ ^". Если идентификатор содержит один или несколько из этих символов, идентификатор должен быть идентификатором с разделителями.|
|SQL_SQL_CONFORMANCE|3.0|Значение SQLUINTEGER, указывающее уровень поддержки SQL-92, поддерживаемый драйвером.<br/>SQL_SC_SQL92_ENTRY — соответствует уровню ввода SQL-92.<br/>SQL_SC_FIPS127_2_TRANSITIONAL = уровень соответствия FIPS 127-2.<br/>SQL_SC_SQL92_FULL = полный уровень соответствует SQL-92.<br/>SQL_SC_ SQL92_INTERMEDIATE = SQL-92, соответствующий промежуточному уровню.|
|SQL_SQL92_DATETIME_FUNCTIONS|3.0|Битовая маска SQLUINTEGER, которая перечисляет скалярные функции DateTime, поддерживаемые драйвером, и соответствующий источник данных, как определено в SQL-92.<br/><br/>Для определения поддерживаемых функций datetime используются следующие битовые маски:<br/>SQL_SDF_CURRENT_DATE<br/>SQL_SDF_CURRENT_TIME<br/>SQL_SDF_CURRENT_TIMESTAMP|
|SQL_SQL92_FOREIGN_KEY_DELETE_RULE|3.0|Битовая маска SQLUINTEGER, которая перечисляет правила, поддерживаемые внешним ключом в инструкции **Delete** , как определено в SQL-92.<br/><br/>Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:<br/>SQL_SFKD_CASCADE<br/>SQL_SFKD_NO_ACTION<br/>SQL_SFKD_SET_DEFAULT<br/>SQL_SFKD_SET_NULL<br/><br/>Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.|
|SQL_SQL92_FOREIGN_KEY_UPDATE_RULE|3.0|Битовая маска SQLUINTEGER, которая перечисляет правила, поддерживаемые для внешнего ключа в инструкции **Update** , как определено в SQL-92.<br/><br/>Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:<br/>SQL_SFKU_CASCADE<br/>SQL_SFKU_NO_ACTION<br/>SQL_SFKU_SET_DEFAULT<br/>SQL_SFKU_SET_NULL<br/><br/>Драйвер, совместимый с SQL-92, всегда будет возвращать все эти варианты как поддерживаемые.|
|SQL_SQL92_GRANT|3.0|Битовая маска SQLUINTEGER, которая перечисляет предложения, поддерживаемые в инструкции **Grant** , как определено в SQL-92.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:<br/>SQL_SG_DELETE_TABLE (уровень записи)<br/>SQL_SG_INSERT_COLUMN (промежуточный уровень)<br/>SQL_SG_INSERT_TABLE (уровень записи)<br/>SQL_SG_REFERENCES_TABLE (уровень записи)<br/>SQL_SG_REFERENCES_COLUMN (уровень записи)<br/>SQL_SG_SELECT_TABLE (уровень записи)<br/>SQL_SG_UPDATE_COLUMN (уровень записи)<br/>SQL_SG_UPDATE_TABLE (уровень записи)<br/>SQL_SG_USAGE_ON_DOMAIN (уровень переходов FIPS)<br/>SQL_SG_USAGE_ON_CHARACTER_SET (уровень переходов FIPS)<br/>SQL_SG_USAGE_ON_COLLATION (уровень переходов FIPS)<br/>SQL_SG_USAGE_ON_TRANSLATION (уровень переходов FIPS)<br/>SQL_SG_WITH_GRANT_OPTION (уровень записи)|
|SQL_SQL92_NUMERIC_VALUE_FUNCTIONS|3.0|Битовая маска SQLUINTEGER, перечисление скалярных функций числовых значений, поддерживаемых драйвером и связанным источником данных, как определено в SQL-92.<br/><br/>Для определения поддерживаемых числовых функций используются следующие битовые маски.<br/>SQL_SNVF_BIT_LENGTH<br/>SQL_SNVF_CHAR_LENGTH<br/>SQL_SNVF_CHARACTER_LENGTH<br/>SQL_SNVF_EXTRACT<br/>SQL_SNVF_OCTET_LENGTH<br/>SQL_SNVF_POSITION|
|SQL_SQL92_PREDICATES|3.0|Битовая маска SQLUINTEGER, которая перечисляет предикаты, поддерживаемые в инструкции **SELECT** , как определено в SQL-92.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.<br/>SQL_SP_BETWEEN (уровень записи)<br/>SQL_SP_COMPARISON (уровень записи)<br/>SQL_SP_EXISTS (уровень записи)<br/>SQL_SP_IN (уровень записи)<br/>SQL_SP_ISNOTNULL (уровень записи)<br/>SQL_SP_ISNULL (уровень записи)<br/>SQL_SP_LIKE (уровень записи)<br/>SQL_SP_MATCH_FULL (полный уровень)<br/>SQL_SP_MATCH_PARTIAL (полный уровень)<br/>SQL_SP_MATCH_UNIQUE_FULL (полный уровень)<br/>SQL_SP_MATCH_UNIQUE_PARTIAL (полный уровень)<br/>SQL_SP_OVERLAPS (уровень переходов FIPS)<br/>SQL_SP_QUANTIFIED_COMPARISON (уровень записи)<br/>SQL_SP_UNIQUE (уровень записи)|
|SQL_SQL92_RELATIONAL_JOIN_OPERATORS|3.0|Битовая маска SQLUINTEGER, которая перечисляет операторы реляционного объединения, поддерживаемые в инструкции **SELECT** , как определено в SQL-92.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.<br/>SQL_SRJO_CORRESPONDING_CLAUSE (промежуточный уровень)<br/>SQL_SRJO_CROSS_JOIN (полный уровень)<br/>SQL_SRJO_EXCEPT_JOIN (промежуточный уровень)<br/>SQL_SRJO_FULL_OUTER_JOIN (промежуточный уровень)<br/>SQL_SRJO_INNER_JOIN (уровень переходов FIPS)<br/>SQL_SRJO_INTERSECT_JOIN (промежуточный уровень)<br/>SQL_SRJO_LEFT_OUTER_JOIN (уровень переходов FIPS)<br/>SQL_SRJO_NATURAL_JOIN (уровень переходов FIPS)<br/>SQL_SRJO_RIGHT_OUTER_JOIN (уровень переходов FIPS)<br/>SQL_SRJO_UNION_JOIN (полный уровень)<br/><br/>SQL_SRJO_INNER_JOIN указывает поддержку для синтаксиса **внутреннего объединения** , а не для возможности внутреннего объединения. Поддержка синтаксиса **внутреннего объединения** — это переход на стандарт FIPS, тогда как поддержка внутреннего объединения является **записью**.|
|SQL_SQL92_REVOKE|3.0|Битовая маска SQLUINTEGER, которая перечисляет предложения, поддерживаемые в инструкции **REVOKE** , как определено в SQL-92, поддерживаемом источником данных.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Следующие битовые маски используются для определения того, какие предложения поддерживаются источником данных:<br/>SQL_SR_CASCADE (уровень переходов FIPS)<br/>SQL_SR_DELETE_TABLE (уровень записи)<br/>SQL_SR_GRANT_OPTION_FOR (промежуточный уровень)<br/>SQL_SR_INSERT_COLUMN (промежуточный уровень)<br/>SQL_SR_INSERT_TABLE (уровень записи)<br/>SQL_SR_REFERENCES_COLUMN (уровень записи)<br/>SQL_SR_REFERENCES_TABLE (уровень записи)<br/>SQL_SR_RESTRICT (уровень переходов FIPS)<br/>SQL_SR_SELECT_TABLE (уровень записи)<br/>SQL_SR_UPDATE_COLUMN (уровень записи)<br/>SQL_SR_UPDATE_TABLE (уровень записи)<br/>SQL_SR_USAGE_ON_DOMAIN (уровень переходов FIPS)<br/>SQL_SR_USAGE_ON_CHARACTER_SET (уровень переходов FIPS)<br/>SQL_SR_USAGE_ON_COLLATION (уровень переходов FIPS)<br/>SQL_SR_USAGE_ON_TRANSLATION (уровень переходов FIPS)|
|SQL_SQL92_ROW_VALUE_CONSTRUCTOR|3.0|Битовая маска SQLUINTEGER, которая перечисляет выражения конструктора значений строк, поддерживаемые в инструкции **SELECT** , как определено в SQL-92. Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.<br/>SQL_SRVC_VALUE_EXPRESSION<br/>SQL_SRVC_NULL<br/>SQL_SRVC_DEFAULT<br/>SQL_SRVC_ROW_SUBQUERY|
|SQL_SQL92_STRING_FUNCTIONS|3.0|Битовая маска SQLUINTEGER, перечисление строковых скалярных функций, поддерживаемых драйвером, и связанным источником данных, как определено в SQL-92.<br/><br/>Для определения поддерживаемых строковых функций используются следующие битовые маски:<br/>SQL_SSF_CONVERT<br/>SQL_SSF_LOWERSQL_SSF_UPPER<br/>SQL_SSF_SUBSTRING<br/>SQL_SSF_TRANSLATE<br/>SQL_SSF_TRIM_BOTH<br/>SQL_SSF_TRIM_LEADING<br/>SQL_SSF_TRIM_TRAILING|
|SQL_SQL92_VALUE_EXPRESSIONS|3.0|Битовая маска SQLUINTEGER, которая перечисляет поддерживаемые выражения значений, как определено в SQL-92.<br/><br/>Уровень соответствия SQL-92 или FIPS, в котором должна поддерживаться эта функция, отображается в круглых скобках рядом с каждой битовой маской.<br/><br/>Для определения параметров, поддерживаемых источником данных, используются следующие битовые маски.<br/>SQL_SVE_CASE (промежуточный уровень)<br/>SQL_SVE_CAST (уровень переходов FIPS)<br/>SQL_SVE_COALESCE (промежуточный уровень)<br/>SQL_SVE_NULLIF (промежуточный уровень)|
|SQL_STANDARD_CLI_CONFORMANCE|3.0|Битовая маска SQLUINTEGER, которая перечисляет стандарт CLI или стандарты, которым соответствует драйвер. Для определения уровней, которые соответствует драйверу, используются следующие маски.<br/>SQL_SCC_XOPEN_CLI_VERSION1: драйвер соответствует CLI открытой группы, версия 1.<br/>SQL_SCC_ISO92_CLI. драйвер соответствует интерфейсу командной строки ISO 92.|
|SQL_STATIC_CURSOR_ATTRIBUTES1|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты статического курсора, которые поддерживаются драйвером. Эта битовая маска содержит первое подмножество атрибутов; второй набор см. в разделе SQL_STATIC_CURSOR_ATTRIBUTES2.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA1_NEXT<br/>SQL_CA1_ABSOLUTE<br/>SQL_CA1_RELATIVE<br/>SQL_CA1_BOOKMARK<br/>SQL_CA1_LOCK_NO_CHANGE<br/>SQL_CA1_LOCK_EXCLUSIVE<br/>SQL_CA1_LOCK_UNLOCK<br/>SQL_CA1_POS_POSITION<br/>SQL_CA1_POS_UPDATE<br/>SQL_CA1_POS_DELETE<br/>SQL_CA1_POS_REFRESH<br/>SQL_CA1_POSITIONED_UPDATE<br/>SQL_CA1_POSITIONED_DELETE<br/>SQL_CA1_SELECT_FOR_UPDATE<br/>SQL_CA1_BULK_ADD<br/>SQL_CA1_BULK_UPDATE_BY_BOOKMARK<br/>SQL_CA1_BULK_DELETE_BY_BOOKMARK<br/>SQL_CA1_BULK_FETCH_BY_BOOKMARK<br/><br/>Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (в описаниях — "статический курсор" для динамического курсора).<br/><br/>Драйвер, поддерживающий промежуточный уровень SQL-92, обычно возвращает параметры SQL_CA1_NEXT, SQL_CA1_ABSOLUTE и SQL_CA1_RELATIVE, так как они поддерживаются, так как драйвер поддерживает прокручиваемые курсоры с помощью внедренной инструкции SQL FETCH. Так как это не определяет непосредственно базовую поддержку SQL, возможно, прокручиваемые курсоры не поддерживаются даже для драйвера, соответствующего промежуточному уровню SQL-92.|
|SQL_STATIC_CURSOR_ATTRIBUTES2|3.0|Битовая маска SQLUINTEGER, описывающая атрибуты статического курсора, которые поддерживаются драйвером. Эта битовая маска содержит второе подмножество атрибутов; Первое подмножество см. в разделе SQL_STATIC_CURSOR_ATTRIBUTES1.<br/><br/>Для определения поддерживаемых атрибутов используются следующие битовые маски:<br/>SQL_CA2_READ_ONLY_CONCURRENCY<br/>SQL_CA2_LOCK_CONCURRENCY<br/>SQL_CA2_OPT_ROWVER_CONCURRENCY<br/>SQL_CA2_OPT_VALUES_CONCURRENCY<br/>SQL_CA2_SENSITIVITY_ADDITIONS<br/>SQL_CA2_SENSITIVITY_DELETIONS<br/>SQL_CA2_SENSITIVITY_UPDATES<br/>SQL_CA2_MAX_ROWS_SELECT<br/>SQL_CA2_MAX_ROWS_INSERT<br/>SQL_CA2_MAX_ROWS_DELETE<br/>SQL_CA2_MAX_ROWS_UPDATE<br/>SQL_CA2_MAX_ROWS_CATALOG<br/>SQL_CA2_MAX_ROWS_AFFECTS_ALL<br/>SQL_CA2_CRC_EXACT<br/>SQL_CA2_CRC_APPROXIMATE<br/>SQL_CA2_SIMULATE_NON_UNIQUE<br/>SQL_CA2_SIMULATE_TRY_UNIQUE<br/>SQL_CA2_SIMULATE_UNIQUE<br/><br/>Описание этих битовых масок см. в разделе SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (в описаниях — "статический курсор" для динамического курсора).|
|SQL_STRING_FUNCTIONS|1.0|Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.<br/><br/>Битовая маска SQLUINTEGER, перечисление скалярных строковых функций, поддерживаемых драйвером и связанным источником данных.<br/><br/>Для определения поддерживаемых строковых функций используются следующие битовые маски:<br/>SQL_FN_STR_ASCII (ODBC 1,0)<br/>SQL_FN_STR_BIT_LENGTH (ODBC 3,0)<br/>SQL_FN_STR_CHAR (ODBC 1,0)<br/>SQL_FN_STR_CHAR_LENGTH (ODBC 3,0)<br/>SQL_FN_STR_CHARACTER_LENGTH (ODBC 3,0)<br/>SQL_FN_STR_CONCAT (ODBC 1,0)<br/>SQL_FN_STR_DIFFERENCE (ODBC 2,0)<br/>SQL_FN_STR_INSERT (ODBC 1,0)<br/>SQL_FN_STR_LCASE (ODBC 1,0)<br/>SQL_FN_STR_LEFT (ODBC 1,0)<br/>SQL_FN_STR_LENGTH (ODBC 1,0)<br/>SQL_FN_STR_LOCATE (ODBC 1,0)<br/>SQL_FN_STR_LTRIM (ODBC 1,0)<br/>SQL_FN_STR_OCTET_LENGTH (ODBC 3,0)<br/>SQL_FN_STR_POSITION (ODBC 3,0)<br/>SQL_FN_STR_REPEAT (ODBC 1,0)<br/>SQL_FN_STR_REPLACE (ODBC 1,0)<br/>SQL_FN_STR_RIGHT (ODBC 1,0)<br/>SQL_FN_STR_RTRIM (ODBC 1,0)<br/>SQL_FN_STR_SOUNDEX (ODBC 2,0)<br/>SQL_FN_STR_SPACE (ODBC 2,0)<br/>SQL_FN_STR_SUBSTRING (ODBC 1,0)<br/>SQL_FN_STR_UCASE (ODBC 1,0)<br/><br/>Если приложение может вызвать скалярную функцию " **Открыть** " с аргументами *string_exp1*, *string_exp2*и *Start* , драйвер возвращает SQL_FN_STR_LOCATE битовую маску. Если приложение может вызвать скалярную функцию «нахождение» только с аргументами *string_exp1* и *string_exp2* , драйвер возвращает SQL_FN_STR_LOCATE_2 битовую маску. Драйверы, полностью поддерживающие скалярную функцию " **разместить** ", возвращают обе битовые маски.<br/><br/>(Дополнительные сведения см. в разделе [функции строк](../appendixes/string-functions.md) в приложении E "скалярные функции".)|
|SQL_SUBQUERIES|2.0|Битовая маска SQLUINTEGER, перечисление предикатов, которые поддерживают вложенные запросы:<br/>SQL_SQ_CORRELATED_SUBQUERIES<br/>SQL_SQ_COMPARISON<br/>SQL_SQ_EXISTS<br/>SQL_SQ_INSQL_SQ_QUANTIFIED<br/><br/>Битовая маска SQL_SQ_CORRELATED_SUBQUERIES указывает, что все предикаты, поддерживающие вложенные запросы, поддерживают коррелированные вложенные запросы.<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает битовую маску, в которой установлены все эти биты.|
|SQL_SYSTEM_FUNCTIONS|1.0|Битовая маска SQLUINTEGER, перечисление скалярных системных функций, поддерживаемых драйвером и связанным источником данных.<br/><br/>Для определения поддерживаемых системных функций используются следующие битовые маски.<br/>SQL_FN_SYS_DBNAME<br/>SQL_FN_SYS_IFNULL<br/>SQL_FN_SYS_USERNAME|
|SQL_TABLE_TERM|1.0|Символьная строка с именем поставщика источника данных для таблицы; Например, "Table" или "File".<br/><br/>Эта символьная строка может быть в верхнем, нижнем или смешанном регистре.<br/><br/>Драйвер, поддерживающий уровень ввода SQL-92, всегда возвращает "Table".|
|SQL_TIMEDATE_ADD_INTERVALS|2.0|Битовая маска SQLUINTEGER, которая перечисляет интервалы времени, поддерживаемые драйвером, и соответствующий источник данных для скалярной функции ТИМЕСТАМПАДД.<br/><br/>Для определения поддерживаемых интервалов используются следующие битовые маски:<br/>SQL_FN_TSI_FRAC_SECOND<br/>SQL_FN_TSI_SECOND<br/>SQL_FN_TSI_MINUTE<br/>SQL_FN_TSI_HOUR<br/>SQL_FN_TSI_DAY<br/>SQL_FN_TSI_WEEK<br/>SQL_FN_TSI_MONTH<br/>SQL_FN_TSI_QUARTER<br/>SQL_FN_TSI_YEAR<br/><br/>Драйвер, поддерживающий переход на уровне FIPS, всегда возвращает битовую маску, в которой установлены все эти биты.|
|SQL_TIMEDATE_DIFF_INTERVALS|2.0|Битовая маска SQLUINTEGER, которая перечисляет интервалы времени, поддерживаемые драйвером, и соответствующий источник данных для скалярной функции ТИМЕСТАМПДИФФ.<br/><br/>Для определения поддерживаемых интервалов используются следующие битовые маски:<br/>SQL_FN_TSI_FRAC_SECOND<br/>SQL_FN_TSI_SECOND<br/>SQL_FN_TSI_MINUTE<br/>SQL_FN_TSI_HOUR<br/>SQL_FN_TSI_DAY<br/>SQL_FN_TSI_WEEK<br/>SQL_FN_TSI_MONTH<br/>SQL_FN_TSI_QUARTER<br/>SQL_FN_TSI_YEAR<br/><br/>Драйвер, поддерживающий переход на уровне FIPS, всегда возвращает битовую маску, в которой установлены все эти биты.|
|SQL_TIMEDATE_FUNCTIONS|1.0|Примечание. Этот тип информации появился в ODBC 1,0; Каждая битовая маска помечается версией, в которой она была представлена.<br/><br/>Битовая маска SQLUINTEGER, которая перечисляет скалярные функции даты и времени, поддерживаемые драйвером, и связанным источником данных.<br/><br/>Для определения поддерживаемых функций даты и времени используются следующие битовые маски:<br/>SQL_FN_TD_CURRENT_DATE (ODBC 3,0)<br/>SQL_FN_TD_CURRENT_TIME (ODBC 3,0)<br/>SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3,0)<br/>SQL_FN_TD_CURDATE (ODBC 1,0)<br/>SQL_FN_TD_CURTIME (ODBC 1,0)<br/>SQL_FN_TD_DAYNAME (ODBC 2,0)<br/>SQL_FN_TD_DAYOFMONTH (ODBC 1,0)<br/>SQL_FN_TD_DAYOFWEEK (ODBC 1,0)<br/>SQL_FN_TD_DAYOFYEAR (ODBC 1,0)<br/>SQL_FN_TD_EXTRACT (ODBC 3,0)<br/>SQL_FN_TD_HOUR (ODBC 1,0)<br/>SQL_FN_TD_MINUTE (ODBC 1,0)<br/>SQL_FN_TD_MONTH (ODBC 1,0)<br/>SQL_FN_TD_MONTHNAME (ODBC 2,0)<br/>SQL_FN_TD_NOW (ODBC 1,0)<br/>SQL_FN_TD_QUARTER (ODBC 1,0)<br/>SQL_FN_TD_SECOND (ODBC 1,0)<br/>SQL_FN_TD_TIMESTAMPADD (ODBC 2,0)<br/>SQL_FN_TD_TIMESTAMPDIFF (ODBC 2,0)<br/>SQL_FN_TD_WEEK (ODBC 1,0)<br/>SQL_FN_TD_YEAR (ODBC 1,0)|
|SQL_TXN_CAPABLE|1.0|Примечание. Этот тип информации появился в ODBC 1,0; каждое возвращаемое значение помечено версией, в которой оно было введено.<br/><br/>Значение СКЛУСМАЛЛИНТ, описывающее поддержку транзакций в драйвере или источнике данных:<br/>SQL_TC_NONE = транзакции не поддерживаются. (ODBC 1,0)<br/>SQL_TC_DML = транзакции могут содержать только инструкции языка обработки данных DML (**Выбор**, **Вставка**, **Обновление**, **Удаление**). Инструкции языка описания данных DDL, обнаруженные в транзакции, приводят к ошибке. (ODBC 1,0)<br/>SQL_TC_DDL_COMMIT = транзакции могут содержать только инструкции DML. Инструкции DDL (**CREATE TABLE**, **DROP INDEX**и т. д.), обнаруженные в транзакции, приводят к фиксации транзакции. (ODBC 2,0)<br/>SQL_TC_DDL_IGNORE = транзакции могут содержать только инструкции DML. Инструкции DDL, обнаруженные в транзакции, игнорируются. (ODBC 2,0)<br/>SQL_TC_ALL = транзакции могут содержать инструкции DDL и инструкции DML в любом порядке. (ODBC 1,0)<br/><br/>(Поскольку поддержка транзакций обязательна в SQL-92, встроенный драйвер SQL-92 [любой уровень] никогда не возвращает SQL_TC_NONE.)|
|SQL_TXN_ISOLATION_OPTION|1.0|Битовая маска SQLUINTEGER, которая перечисляет уровни изоляции транзакций, доступные из драйвера или источника данных.<br/><br/>Следующие битовые маски используются вместе с флагом для определения поддерживаемых параметров:<br/>SQL_TXN_READ_UNCOMMITTED<br/>SQL_TXN_READ_COMMITTED<br/>SQL_TXN_REPEATABLE_READ<br/>SQL_TXN_SERIALIZABLE<br/><br/>Описание этих уровней изоляции см. в описании SQL_DEFAULT_TXN_ISOLATION.<br/><br/>Чтобы задать уровень изоляции транзакции, приложение вызывает **SQLSetConnectAttr** , чтобы установить атрибут SQL_ATTR_TXN_ISOLATION. Дополнительные сведения см. в разделе [функция SQLSetConnectAttr](sqlsetconnectattr-function.md).<br/><br/>Драйвер на уровне ввода SQL-92 всегда будет возвращать SQL_TXN_SERIALIZABLE, как поддерживается. Драйвер согласованного уровня FIPS всегда будет возвращать все эти параметры, как поддерживается.|
|SQL_UNION|2.0|Битовая маска SQLUINTEGER, которая перечисляет поддержку предложения **Union** :<br/>SQL_U_UNION = источник данных поддерживает предложение **Union** .<br/>SQL_U_UNION_ALL = источник данных поддерживает ключевое слово **ALL** в предложении **Union** . (В данном случае**SQLGetInfo** возвращает как SQL_U_UNION, так SQL_U_UNION_ALL.)<br/><br/>Драйвер, совместимый с уровнями ввода SQL-92, всегда будет возвращать оба этих параметра, как поддерживается.|
|SQL_USER_NAME|1.0|Символьная строка с именем, используемой в конкретной базе данных, которая может отличаться от имени для входа.|
|SQL_XOPEN_CLI_YEAR|3.0|Символьная строка, указывающая год публикации спецификации Open Group, с которой полностью согласуется версия диспетчера драйверов ODBC.|
  
## <a name="example"></a>Пример  

 **SQLGetInfo** возвращает списки поддерживаемых параметров в виде битовой маски SQLUINTEGER в **инфовалуептр*. Битовая маска для каждого параметра используется вместе с флагом, чтобы определить, поддерживается ли параметр.  
  
 Например, приложение может использовать следующий код, чтобы определить, поддерживается ли скалярная функция подстроки драйвером, связанным с соединением.  
  
 Еще один пример использования **SQLGetInfo**см. в разделе [Функция SQLTables](sqltables-function.md).  
  
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
 [Функция SQLGetConnectAttr](sqlgetconnectattr-function.md)  
  
 Определение того, поддерживает ли драйвер функцию  
 [Функция SQLGetFunctions](sqlgetfunctions-function.md)  
  
 Возврат значения атрибута инструкции  
 [Функция SQLGetStmtAttr](sqlgetstmtattr-function.md)  
  
 Возврат сведений о типах данных источника данных  
 [Функция SQLGetTypeInfo](sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>См. также:  

 [Справочник по API ODBC](odbc-api-reference.md)  
 [Файлы заголовков ODBC](../install/odbc-header-files.md)
