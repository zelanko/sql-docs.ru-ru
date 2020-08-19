---
description: Возвращаемые значения SQLGetInfo для Excel
title: SQLGetInfo возвращаемые значения для Excel | Документация Майкрософт
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
ms.openlocfilehash: 6eeb52fe564cbb35b9d52583600803c8ebdb05f9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421718"
---
# <a name="sqlgetinfo-returned-values-for-excel"></a>Возвращаемые значения SQLGetInfo для Excel
В следующей таблице перечислены #defines *для аргумента* языка C и соответствующие значения, возвращаемые **SQLGetInfo**. Эти сведения можно получить, передав перечисленный #defines C-Language в **SQLGetInfo** в аргументе *финфотипе* . Дополнительные сведения о значениях, возвращаемых функцией **SQLGetInfo**, см. в *справочнике программиста по ODBC*.  
  
> [!NOTE]  
>  Где **SQLGetInfo** возвращает 32-разрядную битовую маску, вертикальная черта (&#124;) представляет побитовое или.  
  
|инфотипе|Возвращаемое значение|  
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
|SQL_DATA_SOURCE_NAME|DSN из Odbc.ini или "", если в Odbc.ini используется ключевое слово DRIVER|  
|SQL_DATA_SOURCE_READ_ONLY|«Y»|  
|SQL_DATABASE_NAME|Текущий каталог базы данных|  
|SQL_DATETIME_LITERALS|0|  
|SQL_DBMS_NAME|ПРОГРАММЕ|  
|SQL_DBMS_VER|Несколько значений|  
|SQL_DDL_INDEX|0|  
|SQL_DEFAULT_TXN_ISOLATION|0|  
|SQL_DESCRIBE_PARAMETER|0|  
|SQL_DRIVER_HDBC|Обрабатывается диспетчером драйверов.|  
|SQL_DRIVER_HENV|Обрабатывается диспетчером драйверов.|  
|SQL_DRIVER_HLIB|Обрабатывается диспетчером драйверов.|  
|SQL_DRIVER_HSTMT|Обрабатывается диспетчером драйверов.|  
|SQL_DRIVER_NAME|"OdbcJt32.dll"|  
|SQL_DRIVER_ODBC_VER|"3.51.0000"|  
|SQL_DRIVER_VER|"4,00.*nnnn*" (*nnnn* указывает дату сборки)|  
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
|SQL_IDENTIFIER_QUOTE_CHAR|" \` " (Обратная кавычка)|  
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
|SQL_MAX_COLUMNS_IN_TABLE|255<br /><br /> При использовании драйвера Microsoft Excel инструкция CREATE TABLE может допускать 256 столбцов, однако ограничение в 255 столбцов по-прежнему допустимо, и вставка в столбец 256 завершается ошибкой.|  
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
|СООТВЕТСТВИЕ SQL_ODBC_SAG_CLI_|SQL_OSCC_COMPLIANT|  
|SQL_ODBC_SQL_INTEGRITY|"N"|  
|SQL_ODBC_VER|Из диспетчера драйверов|  
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
|SQL_SERVER_NAME|ПРОГРАММЕ|  
|SQL_SPECIAL_CHARACTERS|"~ \` \@ #$%^& \* \_ -+= \\ } {" ";:?/><,.!" [] &#124; "|  
|SQL_STRING_FUNCTIONS|Несколько значений|  
|SQL_SUBQUERIES|Несколько значений|  
|SQL_SYSTEM_FUNCTIONS|0|  
|SQL_TABLE_TERM|Таблица|  
|SQL_TIMEDATE_ADD_INTERVALS|0|  
|SQL_TIMEDATE_DIFF_INTERVALS|0|  
|SQL_TIMEDATE_FUNCTIONS|Несколько значений|  
|SQL_TXN_CAPABLE|SQL_TC_NONE|  
|SQL_TXN_ISOLATION_OPTION|0|  
|SQL_UNION|Несколько значений|  
|SQL_USER_NAME|""|
