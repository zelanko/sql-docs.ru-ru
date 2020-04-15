---
title: СЗЛГетИнфо (Визуальный водитель FoxPro ODBC) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d4b976083b46bf632c4890c7fce3b0f13a9a761
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295194"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Возвращает общую информацию о драйвере Visual FoxPro ODBC и источнике данных, связанном с ручкой соединения, *hdbc*. В следующем списке показано значение, возвращенное Visual FoxPro ODBC Driver для каждого аргумента *fInfoType* и комментариев относительно возвращенных значений.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
## <a name="a"></a>Объект  
 SQL_ACCESSIBLE_PROCEDURES возвращает 'N'.  
  
 SQL_ACCESSIBLE_TABLES возвращает 'Y'.  
  
 SQL_ACTIVE_CONNECTIONS возвращает 0.  
  
 SQL_ACTIVE_STATEMENTS возвращает 0.  
  
 SQL_ALTER_TABLE возвращается либо SQL_AT_ADD_COLUMN, либо SQL_AT_DROP_COLUMN.  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE возвращает SQL_BP_SCROLL.  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIAS возвращает 'Y'.  
  
 SQL_CONCAT_NULL_BEHAVIOR возвращается SQL_CB_NULL.  
  
 SQL_CONVERT_BIGINT возвращает 0. Визуальный водитель FoxPro ODBC не поддерживает *BigInt.*  
  
 SQL_CONVERT_BINARY возвращает 0.  
  
 SQL_CONVERT_BIT возвращает 0.  
  
 SQL_CONVERT_CHAR возвращает 0.  
  
 SQL_CONVERT_DATE возвращает 0.  
  
 SQL_CONVERT_DECIMAL возвращает 0.  
  
 SQL_CONVERT_DOUBLE возвращает 0.  
  
 SQL_CONVERT_FLOAT возвращает 0.  
  
 SQL_CONVERT_INTEGER возвращает 0.  
  
 SQL_CONVERT_LONGVARBINARY возвращает 0.  
  
 SQL_CONVERT_LONGVARCHAR возвращает 0.  
  
 SQL_CONVERT_NUMERIC возвращает 0.  
  
 SQL_CONVERT_REAL возвращает 0.  
  
 SQL_CONVERT_SMALLINT возвращает 0.  
  
 SQL_CONVERT_TIME возвращает 0.  
  
 SQL_CONVERT_TIMESTAMP возвращает 0.  
  
 SQL_CONVERT_TINYINT возвращает 0.  
  
 SQL_CONVERT_VARBINARY возвращает 0.  
  
 SQL_CONVERT_VARCHAR возвращает 0.  
  
 SQL_CONVERT_FUNCTIONS возвращает 0.  
  
 SQL_CORRELATION_NAME возвращается SQL_CN_ANY.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR возвращается SQL_CB_PRESERVE.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR возвращается SQL_CB_PRESERVE.  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME возвращает значение, передаваемые в качестве DSN, в [S'LConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), или [S'LDriverConnect;](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) возвращает пустую строку, если DSN не указан.  
  
 SQL_DATA_SOURCE_READ_ONLY возвращает 'N'.  
  
 SQL_DATABASE_NAME возвращает полный путь КООН к текущей базе данных, если источником данных является [база данных.](../../odbc/microsoft/visual-foxpro-terminology.md) Если источник данных подключается к каталогу [таблиц,](../../odbc/microsoft/visual-foxpro-terminology.md)функция возвращает путь в каталог.  
  
 SQL_DBMS_NAME возвращает "Visual FoxPro".  
  
 SQL_DBMS_VER возвращает "03.00.0000".  
  
 SQL_DEFAULT_TXN_ISOLATION возвращается SQL_TXN_READ_COMMITTED. Грязные чтения невозможны, но неповторимые чтения и фантомы возможны.  
  
 SQL_DRIVER_HDBC реализуется менеджером драйверов.  
  
 SQL_DRIVER_HENV реализуется менеджером драйверов.  
  
 SQL_DRIVER_HLIB реализуется менеджером драйверов.  
  
 SQL_DRIVER_HSTMT реализуется менеджером драйверов.  
  
 SQL_DRIVER_NAME возвращает "vfpodbc.dll".  
  
 SQL_DRIVER_ODBC_VER возвращается "02.50" (SQL_SPEC_MAJOR, SQL_SPEC_MINOR).  
  
 SQL_DRIVER_VER возвращает "01.00.0000".  
  
## <a name="e"></a>E  
 SQL_EXPRESSIONS_IN_ORDERBY возвращает 'N'.  
  
## <a name="f"></a>F  
 SQL_FETCH_DIRECTION возвращается:  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK.  
  
 SQL_FILE_USAGE возвращает SQL_FILE_QUALIFIER как для базы данных (.dbc файл) и для свободных источников таблицы (.dbf) источников данных.  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS возвращается:  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY возвращается SQL_GB_NO_RELATION.  
  
## <a name="i-j"></a>I-J  
 SQL_IDENTIFIER_CASE возвращается SQL_IC_MIXED.  
  
 SQL_IDENTIFIER_QUOTE_CHAR возвращается'.  
  
## <a name="k"></a>K  
 SQL_KEYWORDS возвращается ".  
  
## <a name="l"></a>L  
 SQL_LIKE_ESCAPE_CLAUSE возвращает 'N'.  
  
 SQL_LOCK_TYPES возвращается SQL_LCK_NO_CHANGE.  
  
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
  
 SQL_MAX_PROCEDURE_NAME_LEN возвращает 0. Visual FoxPro ODBC Driver не позволяет прямой доступ к процедурам хранения Visual FoxPro.  
  
 SQL_MAX_QUALIFIER_NAME_LEN возвращает максимальную длину пути операционной системы.  
  
 SQL_MAX_ROW_SIZE возвращает 254'2.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG возвращает 'N'.  
  
 SQL_MAX_STATEMENT_LEN возвращает 8192.  
  
 SQL_MAX_TABLE_NAME_LEN возвращает 128.  
  
 SQL_MAX_TABLES_IN_SELECT возвращает 16.  
  
 SQL_MAX_USER_NAME_LEN возвращает 0.  
  
 SQL_MULT_RESULT_SETS возвращает 'Y'.  
  
 SQL_MULTIPLE_ACTIVE_TXN возвращает 'Y'. Несколько подключений могут открываться сразу несколько транзакций.  
  
## <a name="n"></a>Нет  
 SQL_NEED_LONG_DATA_LEN возвращает 'N'.  
  
 SQL_NON_NULLABLE_COLUMNS возвращается SQL_NNC_NON_NULL.  
  
 SQL_NULL_COLLATION возвращаетSQL_NC_LOW.  
  
 SQL_NUMERIC_FUNCTIONS возвращает все функции, кроме SQL_FN_NUM_POWER, которая не поддерживается Visual FoxPro ODBC Driver. Поддерживаются следующие функции:  
  
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
 SQL_ODBC_API_CONFORMANCE возвращается SQL_OAC_LEVEL1.  
  
 SQL_ODBC_SAG_CLI_CONFORMANCE возвращается SQL_OSCC_COMPLIANT.  
  
 SQL_ODBC_SQL_CONFORMANCE возвращается SQL_OSC_MINIMUM. Поддерживается минимальный синтаксис S'L.  
  
 SQL_ODBC_SQL_OPT_IEF возвращает "N".  
  
 SQL_ODBC_VER реализуется менеджером драйверов.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT возвращает "N".  
  
 SQL_OUTER_JOINS возвращает "N".  
  
 SQL_OWNER_TERM возвращается "." Visual FoxPro ODBC Driver не поддерживает владельцев для своих объектов.  
  
 SQL_OWNER_USAGE возвращает 0. Visual FoxPro ODBC Driver не поддерживает владельцев для своих объектов.  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS возвращается SQL_POS_POSITION.  
  
 SQL_POSITIONED_STATEMENTS возвращает 0.  
  
 SQL_PROCEDURE_TERM возвращается "."  
  
 SQL_PROCEDURES возвращает 'N'.  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION возвращается SQL_QL_START.  
  
 SQL_QUALIFIER_NAME_SEPARATOR возвращается '!\\' или ' '. Сепаратор между базой данных и таблицей является '! для\\источников данных, подключенных к [базам данных,](../../odbc/microsoft/visual-foxpro-terminology.md)и ' для источников данных, которые являются каталогами [свободных таблиц.](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
 SQL_QUALIFIER_TERM возвращает "базу данных" или "каталог". Квалификатор — это «база данных» для источников данных, подключенных к [базам данных,](../../odbc/microsoft/visual-foxpro-terminology.md)и «каталог» для источников данных, которые являются каталогами [свободных таблиц.](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
 SQL_QUALIFIER_USAGE не поддерживает SQL_QU_PRIVILEGE_DEFINITION; он возвращает либо SQL_QU_DML_STATEMENT, либо SQL_QU_TABLE_DEFINITION.  
  
 SQL_QUOTED_IDENTIFIER_CASE возвращается SQL_IC_MIXED.  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATES возвращает "N". Visual FoxPro ODBC Driver поддерживает только статические и вперед курсоры.  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCY возвращается SQL_SCCO_READ_ONLY.  
  
 SQL_SCROLL_OPTIONS возвращается либо SQL_SO_STATIC, либо SQL_SO_READONLY.  
  
 SQL_SEARCH_PATTERN_ESCAPE возвращается "\\.  
  
 SQL_SERVER_NAME возвращается "."  
  
 SQL_SPECIAL_CHARACTERS возвращается: «В долларах США».  
  
 SQL_STATIC_SENSITIVITY возвращает 0. Visual FoxPro ODBC Driver не поддерживает позиционные обновления.  
  
 SQL_STRING_FUNCTIONS не поддерживает SQL_FN_STR_INSERT, SQL_FN_STR_LOCATE, SQL_FN_STR_LOCATE_2 или SQL_FN_STR_SOUNDEX.  
  
 Возвращается следующее:  
  
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
  
 SQL_SUBQUERIES возвращается:  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED.  
  
 SQL_SYSTEM_FUNCTIONS возвращается:  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 но нет:  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM возвращает "стол".  
  
 SQL_TIMEDATE_ADD_INTERVALS возвращается:  
  
-   SQL_FN_TSI_ ВТОРОЙ  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 но нет:  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALS возвращается:  
  
-   SQL_FN_TSI_ ВТОРОЙ  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_TIMEDATE_FUNCTIONS не поддерживает SQL_FN_TD_QUARTER, SQL_FN_TD_TIMESTAMPADD, SQL_FN_TD_DAYOFYEAR или SQL_FN_TD_WEEK.  
  
 Возвращается следующее:  
  
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
  
-   SQL_FN_TD_YEAR .  
  
 SQL_TXN_CAPABLE возвращается SQL_TC_DML.  
  
 SQL_TXN_ISOLATION_OPTION возвращается SQL_TXN_READ_COMMITTED.  
  
## <a name="u-z"></a>U-Z  
 SQL_UNION возвращается либо SQL_U_UNION, либо SQL_U_UNION_ALL.  
  
 SQL_USER_NAME \<возвращает пустые>.
