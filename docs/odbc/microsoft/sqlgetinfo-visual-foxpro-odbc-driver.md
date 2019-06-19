---
title: SQLGetInfo (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 015ea45d1383e6813973aeb1e4c86451a506a2aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213329"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Возвращает общие сведения о драйвер ODBC для Visual FoxPro и источник данных, связанный с дескриптором соединения, *hdbc*. В следующем списке показано значение, возвращаемое для каждого драйвера ODBC для Visual FoxPro *fInfoType* аргумент и комментарии, касающиеся возвращаемые значения.  
  
 Дополнительные сведения см. в разделе [SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md) в *Справочник по программированию ODBC*.  
  
## <a name="a"></a>Объект  
 Возвращает SQL_ACCESSIBLE_PROCEDURES 'N'.  
  
 SQL_ACCESSIBLE_TABLES возвращает «Y».  
  
 SQL_ACTIVE_CONNECTIONS возвращает 0.  
  
 SQL_ACTIVE_STATEMENTS возвращает 0.  
  
 SQL_ALTER_TABLE возвращает SQL_AT_ADD_COLUMN или SQL_AT_DROP_COLUMN.  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE возвращает SQL_BP_SCROLL.  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIAS возвращает «Y».  
  
 SQL_CONCAT_NULL_BEHAVIOR возвращает SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINT возвращает 0. Драйвер ODBC для Visual FoxPro не поддерживает *BigInt*.  
  
 SQL_CONVERT_BINARY возвращает 0.  
  
 SQL_CONVERT_BIT возвращает 0.  
  
 SQL_CONVERT_CHAR возвращает 0.  
  
 SQL_CONVERT_DATE возвращает 0.  
  
 Раздел SQL_CONVERT_DECIMAL возвращает 0.  
  
 SQL_CONVERT_DOUBLE возвращает 0.  
  
 Раздел SQL_CONVERT_FLOAT возвращает 0.  
  
 SQL_CONVERT_INTEGER возвращает 0.  
  
 SQL_CONVERT_LONGVARBINARY возвращает 0.  
  
 SQL_CONVERT_LONGVARCHAR возвращает 0.  
  
 SQL_CONVERT_NUMERIC возвращает 0.  
  
 SQL_CONVERT_REAL возвращает 0.  
  
 SQL_CONVERT_SMALLINT возвращает 0.  
  
 SQL_CONVERT_TIME возвращает 0.  
  
 Раздел SQL_CONVERT_TIMESTAMP возвращает 0.  
  
 SQL_CONVERT_TINYINT возвращает 0.  
  
 SQL_CONVERT_VARBINARY возвращает 0.  
  
 SQL_CONVERT_VARCHAR возвращает 0.  
  
 SQL_CONVERT_FUNCTIONS возвращает 0.  
  
 SQL_CORRELATION_NAME возвращает SQL_CN_ANY.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR возвращает SQL_CB_PRESERVE.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR возвращает SQL_CB_PRESERVE.  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME возвращает значение, переданное в качестве источника данных для [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), или [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md); возвращает пустую строку в том случае, если не указано без имени DSN.  
  
 Возвращает SQL_DATA_SOURCE_READ_ONLY 'N'.  
  
 SQL_DATABASE_NAME возвращает полный путь UNC к текущей базе данных, если источником данных является [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md). Если источник данных подключается к каталогу [таблиц](../../odbc/microsoft/visual-foxpro-terminology.md), функция возвращает путь к каталогу.  
  
 SQL_DBMS_NAME возвращает «Visual FoxPro».  
  
 SQL_DBMS_VER возвращает «03.00.0000».  
  
 SQL_DEFAULT_TXN_ISOLATION возвращает SQL_TXN_READ_COMMITTED. «Грязные» чтения невозможны, но возможны неповторяющееся чтение и появляться фантомы.  
  
 SQL_DRIVER_HDBC реализуется диспетчером драйверов.  
  
 SQL_DRIVER_HENV реализуется диспетчером драйверов.  
  
 SQL_DRIVER_HLIB реализуется диспетчером драйверов.  
  
 SQL_DRIVER_HSTMT реализуется диспетчером драйверов.  
  
 SQL_DRIVER_NAME возвращает «vfpodbc.dll».  
  
 SQL_DRIVER_ODBC_VER возвращает «02.50» (SQL_SPEC_MAJOR, SQL_SPEC_MINOR).  
  
 SQL_DRIVER_VER возвращает «01.00.0000».  
  
## <a name="e"></a>E  
 Возвращает SQL_EXPRESSIONS_IN_ORDERBY 'N'.  
  
## <a name="f"></a>Ж  
 Возвращает SQL_FETCH_DIRECTION:  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK.  
  
 SQL_FILE_USAGE бесплатно таблицы источников данных (DBF-файл) и возвращает оба SQL_FILE_QUALIFIER для базы данных (файл .dbc).  
  
## <a name="g-h"></a>G-H  
 Возвращает SQL_GETDATA_EXENSIONS:  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY возвращает SQL_GB_NO_RELATION.  
  
## <a name="i-j"></a>Я-J  
 SQL_IDENTIFIER_CASE возвращает sql_ic_mixed, имеющим.  
  
 Возвращает SQL_IDENTIFIER_QUOTE_CHAR ".  
  
## <a name="k"></a>Л  
 Возвращает SQL_KEYWORDS «».  
  
## <a name="l"></a>L  
 Возвращает SQL_LIKE_ESCAPE_CLAUSE 'N'.  
  
 SQL_LOCK_TYPES возвращает SQL_LCK_NO_CHANGE.  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LEN возвращает 0.  
  
 SQL_MAX_CHAR_LITERAL_LEN возвращает 254.  
  
 SQL_MAX_COLUMN_NAME_LEN возвращает 128.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY возвращает 16.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY возвращает 16.  
  
 SQL_MAX_COLUMNS_IN_INDEX возвращает 0.  
  
 SQL_MAX_COLUMNS_IN_SELECT возвращает 254.  
  
 SQL_MAX_COLUMNS_IN_TABLE возвращает 254.  
  
 SQL_MAX_CURSOR_NAME_LEN возвращает 254.  
  
 SQL_MAX_INDEX_SIZE возвращает 0.  
  
 SQL_MAX_OWNER_NAME_LEN возвращает 0.  
  
 SQL_MAX_PROCEDURE_NAME_LEN возвращает 0. Драйвер ODBC для Visual FoxPro не поддерживает прямой доступ к Visual FoxPro хранимых процедур.  
  
 SQL_MAX_QUALIFIER_NAME_LEN возвращает длину пути максимальное операционной системы.  
  
 SQL_MAX_ROW_SIZE возвращает 254 ^ 2.  
  
 Возвращает SQL_MAX_ROW_SIZE_INCLUDES_LONG 'N'.  
  
 SQL_MAX_STATEMENT_LEN возвращает 8192.  
  
 SQL_MAX_TABLE_NAME_LEN возвращает 128.  
  
 SQL_MAX_TABLES_IN_SELECT возвращает 16.  
  
 SQL_MAX_USER_NAME_LEN возвращает 0.  
  
 SQL_MULT_RESULT_SETS возвращает «Y».  
  
 SQL_MULTIPLE_ACTIVE_TXN возвращает «Y». Несколько подключений может иметь несколько транзакций за один раз открыть.  
  
## <a name="n"></a>Нет  
 Возвращает SQL_NEED_LONG_DATA_LEN 'N'.  
  
 SQL_NON_NULLABLE_COLUMNS возвращает SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION возвращает SQL_NC_LOW.  
  
 SQL_NUMERIC_FUNCTIONS возвращает всех функций за исключением SQL_FN_NUM_POWER, который не поддерживается драйвером ODBC для Visual FoxPro. Поддерживаются следующие функции:  
  
-   SQL_FN_NUM_ABS  
  
-   SQL_FN_NUM_ACOS  
  
-   SQL_FN_NUM_ASIN  
  
-   SQL_FN_NUM_ATAN  
  
-   SQL_FN_NUM_ATAN2  
  
-   SQL_FN_NUM_CELING  
  
-   SQL_FN_NUM_COS  
  
-   SQL_FN_NUM_COT  
  
-   SQL_FN_NUM_DEGREES  
  
-   SQL_FN_NUM_EXP  
  
-   SQL_FN_NUM_FLOOR  
  
-   SQL_FN_NUM_LOG  
  
-   SQL_FN_NUM_LOG10  
  
-   SQL_FN_NUM_MOD  
  
-   SQL_FN_NUM_PI  
  
-   SQL_FN_NUM_RADIANS  
  
-   SQL_FN_NUM_RAND  
  
-   SQL_FN_NUM_ROUND  
  
-   SQL_FN_NUM_SIGN  
  
-   SQL_FN_NUM_SIN  
  
-   SQL_FN_NUM_SQRT  
  
-   SQL_FN_NUM_TAN  
  
## <a name="o"></a>O  
 SQL_ODBC_API_CONFORMANCE возвращает SQL_OAC_LEVEL1.  
  
 SQL_ODBC_SAG_CLI_CONFORMANCE возвращает SQL_OSCC_COMPLIANT.  
  
 SQL_ODBC_SQL_CONFORMANCE возвращает SQL_OSC_MINIMUM. Минимальный синтаксис SQL поддерживается.  
  
 Возвращает SQL_ODBC_SQL_OPT_IEF «N».  
  
 SQL_ODBC_VER реализуется диспетчером драйверов.  
  
 Возвращает SQL_ORDER_BY_COLUMNS_IN_SELECT «N».  
  
 Возвращает SQL_OUTER_JOINS «N».  
  
 Возвращает SQL_OWNER_TERM «». Драйвер ODBC для Visual FoxPro не поддерживает владельцев для своих объектов.  
  
 SQL_OWNER_USAGE возвращает 0. Драйвер ODBC для Visual FoxPro не поддерживает владельцев для своих объектов.  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS возвращает SQL_POS_POSITION.  
  
 SQL_POSITIONED_STATEMENTS возвращает 0.  
  
 Возвращает SQL_PROCEDURE_TERM «».  
  
 Возвращает SQL_PROCEDURES 'N'.  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION возвращает SQL_QL_START.  
  
 Возвращает SQL_QUALIFIER_NAME_SEPARATOR "!" или "\\". Разделитель между базой данных и таблицы — "!" для источников данных, подключенных к [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md), и "\\" для источников данных, которые являются каталоги [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 SQL_QUALIFIER_TERM возвращает «database» или «каталог». Квалификатор не» базы данных «источники данных с подключением к [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md)и «каталог» для источников данных, которые являются каталоги [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 SQL_QUALIFIER_USAGE не поддерживает SQL_QU_PRIVILEGE_DEFINITION; он возвращает SQL_QU_DML_STATEMENT или SQL_QU_TABLE_DEFINITION.  
  
 SQL_QUOTED_IDENTIFIER_CASE возвращает sql_ic_mixed, имеющим.  
  
## <a name="r"></a>Чтение  
 Возвращает SQL_ROW_UPDATES «N». Драйвер ODBC для Visual FoxPro поддерживает только статические и прямой курсоры.  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCY возвращает SQL_SCCO_READ_ONLY.  
  
 SQL_SCROLL_OPTIONS возвращает SQL_SO_STATIC или SQL_SO_READONLY.  
  
 Возвращает SQL_SEARCH_PATTERN_ESCAPE "\\«.  
  
 Возвращает SQL_SERVER_NAME «».  
  
 Возвращает SQL_SPECIAL_CHARACTERS «~ @# $% ^».  
  
 SQL_STATIC_SENSITIVITY возвращает 0. Драйвер ODBC для Visual FoxPro не поддерживает позиционные обновления.  
  
 SQL_FN_STR_INSERT, SQL_FN_STR_LOCATE, SQL_FN_STR_LOCATE_2 или SQL_FN_STR_SOUNDEX SQL_STRING_FUNCTIONS не поддерживает.  
  
 Он возвращает:  
  
-   SQL_FN_STR_ASCII  
  
-   SQL_FN_STR_CHAR  
  
-   SQL_FN_STR_CONCAT  
  
-   SQL_FN_STR_DIFFERENCE  
  
-   SQL_FN_STR_LCASE  
  
-   SQL_FN_STR_LEFT  
  
-   SQL_FN_STR_LENGTH  
  
-   SQL_FN_STR_LTRIM  
  
-   SQL_FN_STR_REPEAT  
  
-   SQL_FN_STR_REPLACE  
  
-   SQL_FN_STR_RIGHT  
  
-   SQL_FN_STR_RTRIM  
  
-   SQL_FN_STR_SUBSTRING  
  
-   SQL_FN_STR_UCASE  
  
-   SQL_FN_STR_SPACE.  
  
 Возвращает SQL_SUBQUERIES:  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED.  
  
 Возвращает SQL_SYSTEM_FUNCTIONS:  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 но не:  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM возвращает «table».  
  
 Возвращает SQL_TIMEDATE_ADD_INTERVALS:  
  
-   SQL_FN_TSI_ SECOND  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 но не:  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 Возвращает SQL_TIMEDATE_DIFF_INTERVALS:  
  
-   SQL_FN_TSI_ SECOND  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_FN_TD_QUARTER, SQL_FN_TD_TIMESTAMPADD, SQL_FN_TD_DAYOFYEAR или SQL_FN_TD_WEEK SQL_TIMEDATE_FUNCTIONS не поддерживает.  
  
 Он возвращает:  
  
-   SQL_FN_TD_CURDATE  
  
-   SQL_FN_TD_CURTIME  
  
-   SQL_FN_TD_DAYNAME  
  
-   SQL_FN_TD_DAYOFMONTH  
  
-   SQL_FN_TD_DAYOFWEEK  
  
-   SQL_FN_TD_HOUR  
  
-   SQL_FN_TD_MINUTE  
  
-   SQL_FN_TD_MONTH  
  
-   SQL_FN_TD_MONTHNAME  
  
-   SQL_FN_TD_NOW  
  
-   SQL_FN_TD_SECOND  
  
-   SQL_FN_TD_TIMESTAMPDIFF  
  
-   SQL_FN_TD_YEAR.  
  
 SQL_TXN_CAPABLE возвращает SQL_TC_DML.  
  
 SQL_TXN_ISOLATION_OPTION возвращает SQL_TXN_READ_COMMITTED.  
  
## <a name="u-z"></a>U-Z  
 SQL_UNION возвращает SQL_U_UNION или SQL_U_UNION_ALL.  
  
 Возвращает SQL_USER_NAME \<пустой >.
