---
title: S'LGetInfo Вернула значения для Excel (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], returned values for dBase
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
ms.assetid: a0f4c3e4-5906-4ab3-ad34-c606f173169a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e285e8978ae357201458ca9289616df7d404811
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298544"
---
# <a name="sqlgetinfo-returned-values-for-excel"></a>Возвращаемые значения SQLGetInfo для Excel
В следующей таблице перечислены #defines на c-языке для аргумента *fInfoType* и соответствующие значения, возвращенные **S'LGetInfo.** Эта информация может быть получена путем передачи перечисленных C-языкового #defines в **S'LGetInfo** в аргументе *fInfoType.* Для получения более подробной информации о значениях, возвращенных **s'LGetInfo,** см. *ODBC Programmer's Reference*  
  
> [!NOTE]  
>  В тех случаях, когда **S'LGetInfo** возвращает 32-битную битовую маску, вертикальная панель (&#124;) представляет собой битраго-или.  
  
|InfoType|Возвращаемое значение|  
|--------------|--------------------|  
|SQL_ACCESSIBLE_PROCEDURES|"N"|  
|SQL_ACCESSIBLE_TABLES|«Y»|  
|SQL_ACTIVE_ENVIRONMENTS|0|  
|SQL_AGGREGATE_FUNCTIONS|Все наборы|  
|SQL_ALTER_DOMAIN|0|  
|SQL_ALTER_TABLE|0|  
|SQL_ASYNC_MODE|0|  
|SQL_BATCH_ROW_COUNT|0|  
|SQL_BATCH_SUPPORT|0|  
|SQL_BOOKMARK_PERSISTENCE|Несколько значений|  
|SQL_CATALOG_LOCATION|SQL_QL_START|  
|SQL_CATALOG_NAME|«Y»|  
|SQL_CATALOG_NAME_SEPARATOR|Несколько значений|  
|SQL_CATALOG_TERM|Несколько значений|  
|SQL_CATALOG_USAGE|Несколько значений|  
|SQL_COLLATION_SEQ|""|  
|SQL_COLUMN_ALIAS|«Y»|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_CB_NON_NULL|  
|SQL_CONVERT_BIGINT|0|  
|SQL_CONVERT_BINARY|Несколько значений|  
|SQL_CONVERT_BIT|0|  
|SQL_CONVERT_CHAR|Несколько значений|  
|SQL_CONVERT_DATE|Несколько значений|  
|SQL_CONVERT_DECIMAL|0|  
|SQL_CONVERT_DOUBLE|Несколько значений|  
|SQL_CONVERT_FLOAT|Несколько значений|  
|SQL_CONVERT_FUNCTIONS|SQL_FN_CVT_CONVERT|  
|SQL_CONVERT_INTEGER|Несколько значений|  
|SQL_CONVERT_LONGVARBINARY|Несколько значений|  
|SQL_CONVERT_LONGVARCHAR|Несколько значений|  
|SQL_CONVERT_NUMERIC|Несколько значений|  
|SQL_CONVERT_REAL|Несколько значений|  
|SQL_CONVERT_SMALLINT|Несколько значений|  
|SQL_CONVERT_TIME|Несколько значений|  
|SQL_CONVERT_TIMESTAMP|Несколько значений|  
|SQL_CONVERT_TINYINT|Несколько значений|  
|SQL_CONVERT_VARBINARY|Несколько значений|  
|SQL_CONVERT_VARCHAR|Несколько значений|  
|SQL_CORRELATION_NAME|SQL_CN_ANY|  
|SQL_CREATE_ASSERTION|0|  
|SQL_CREATE_CHARACTER_SET|0|  
|SQL_CREATE_COLLATION|0|  
|SQL_CREATE_DOMAIN|0|  
|SQL_CREATE_SCHEMA|0|  
|SQL_CREATE_TABLE|SQL_CT_CREATE_TABLE|  
|SQL_CREATE_TRANSLATION|0|  
|SQL_CREATE_VIEW|0|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_DATA_SOURCE_NAME|DSN от Odbc.ini, или ", если ключевое слово DRIVER используется в Odbc.ini|  
|SQL_DATA_SOURCE_READ_ONLY|«Y»|  
|SQL_DATABASE_NAME|Текущий каталог баз данных|  
|SQL_DATETIME_LITERALS|0|  
|SQL_DBMS_NAME|"EXCEL"|  
|SQL_DBMS_VER|Несколько значений|  
|SQL_DDL_INDEX|0|  
|SQL_DEFAULT_TXN_ISOLATION|0|  
|SQL_DESCRIBE_PARAMETER|0|  
|SQL_DRIVER_HDBC|Обработано менеджером водителя.|  
|SQL_DRIVER_HENV|Обработано менеджером водителя.|  
|SQL_DRIVER_HLIB|Обработано менеджером водителя.|  
|SQL_DRIVER_HSTMT|Обработано менеджером водителя.|  
|SQL_DRIVER_NAME|"OdbcJt32.dll"|  
|SQL_DRIVER_ODBC_VER|"3.51.0000"|  
|SQL_DRIVER_VER|"4.00.*nnnn*"*(nnnn* указывает дату сборки)|  
|SQL_DROP_ASSERTION|0|  
|SQL_DROP_CHARACTER_SET|0|  
|SQL_DROP_COLLATION|0|  
|SQL_DROP_DOMAIN|0|  
|SQL_DROP_SCHEMA|0|  
|SQL_DROP_TABLE|SQL_DT_DROP_TABLE|  
|SQL_DROP_TRANSLATION|0|  
|SQL_DROP_VIEW|SQL_DV_DROP_VIEW|  
|SQL_EXPRESSIONS_IN_ORDERBY|«Y»|  
|SQL_FILE_USAGE|Несколько значений|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT|  
|SQL_GETDATA_EXTENSIONS|Несколько значений|  
|SQL_GROUP_BY|SQL_GB_GROUP_BY_CONTAINS_SELECT|  
|SQL_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_IDENTIFIER_QUOTE_CHAR|"\`(назад цитата)|  
|SQL_KEYWORDS|Несколько значений|  
|SQL_LIKE_ESCAPE_CLAUSE|"N"|  
|SQL_MAX_BINARY_LITERAL_LEN|255|  
|SQL_MAX_CATALOG_NAME_LEN|66|  
|SQL_MAX_CHAR_LITERAL_LEN|Несколько значений|  
|SQL_MAX_COLUMN_NAME_LEN|Несколько значений|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|10|  
|SQL_MAX_COLUMNS_IN_INDEX|0|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|10|  
|SQL_MAX_COLUMNS_IN_SELECT|255|  
|SQL_MAX_COLUMNS_IN_TABLE|255<br /><br /> При использовании Драйвера Microsoft Excel заявление CREATE TABLE может позволить 256 столбцов, но ограничение в 255 столбцов по-прежнему действует, и вставка в столбец 256 выйдет из строя.|  
|SQL_MAX_CONCURRENT_ACTIVITIES|0|  
|SQL_MAX_CURSOR_NAME_LEN|64|  
|SQL_MAX_DRIVER_CONNECTIONS|64|  
|SQL_MAX_INDEX_SIZE|0|  
|SQL_MAX_PROCEDURE_NAME_LEN|0|  
|SQL_MAX_ROW_SIZE|65535|  
|SQL_MAX_ROW_SIZE_INCLUDES_LONG|«Y»|  
|SQL_MAX_SCHEMA_NAME_LEN|0|  
|SQL_MAX_STATEMENT_LEN|65000|  
|SQL_MAX_TABLE_NAME_LEN|Несколько значений|  
|SQL_MAX_TABLES_IN_SELECT|16|  
|SQL_MAX_USER_NAME_LEN|0|  
|SQL_MULT_RESULT_SETS|"N"|  
|SQL_MULTIPLE_ACTIVE_TXN|«Y»|  
|SQL_NEED_LONG_DATA_LEN|"N"|  
|SQL_NON_NULLABLE_COLUMNS|SQL_NNC_NON_NULL|  
|SQL_NULL_COLLATION|SQL_NC_LOW|  
|SQL_NUMERIC_FUNCTIONS|Несколько значений|  
|SQL_ODBC_SAG_CLI_ CONFORMANCE|SQL_OSCC_COMPLIANT|  
|SQL_ODBC_SQL_INTEGRITY|"N"|  
|SQL_ODBC_VER|От менеджера по драйверам|  
|SQL_OJ_CAPABILITIES|Несколько значений|  
|SQL_ORDER_BY_COLUMNS_IN_SELECT|"N"|  
|SQL_OUTER_JOINS|«Y»|  
|SQL_PROCEDURE_TERM|""|  
|SQL_PROCEDURES|"N"|  
|SQL_QUOTED_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_ROW_UPDATES|"N"|  
|SQL_SCHEMA_TERM|""|  
|SQL_SCHEMA_USAGE|0|  
|SQL_SCROLL_OPTIONS|Несколько значений|  
|SQL_SEARCH_PATTERN_ESCAPE|"\\"|  
|SQL_SERVER_NAME|"EXCEL"|  
|SQL_SPECIAL_CHARACTERS|"Я";:?/><,.!'\`\@#$%^&\*\_-+=\\ (&#124;»|  
|SQL_STRING_FUNCTIONS|Несколько значений|  
|SQL_SUBQUERIES|Несколько значений|  
|SQL_SYSTEM_FUNCTIONS|0|  
|SQL_TABLE_TERM|"ТАБЛИЦА"|  
|SQL_TIMEDATE_ADD_INTERVALS|0|  
|SQL_TIMEDATE_DIFF_INTERVALS|0|  
|SQL_TIMEDATE_FUNCTIONS|Несколько значений|  
|SQL_TXN_CAPABLE|SQL_TC_NONE|  
|SQL_TXN_ISOLATION_OPTION|0|  
|SQL_UNION|Несколько значений|  
|SQL_USER_NAME|""|
