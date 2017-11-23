---
title: "Создание приложений ODBC 3.x | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b0c0701ce83e4d1d30bd8f69f94ddc90e7a60a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="writing-odbc-3x-applications"></a>Написание ODBC 3.x приложений
Когда ODBC 2. *x* обновить приложение ODBC 3. *x*, должны быть написаны таким образом, что она работает с обоих ODBC 2. *x* и 3. *x* драйверы. Приложение должно учитываться код условия, чтобы воспользоваться всеми преимуществами ODBC 3. *x* функции.  
  
 Атрибут SQL_ATTR_ODBC_VERSION окружения должно быть присвоено SQL_OV_ODBC2. Это позволит гарантировать, что драйвер ведет себя как ODBC 2*.x* драйвера с учетом изменений, описанных в разделе [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Если приложение будет использовать все функции, описанные в разделе [новые возможности](../../../odbc/reference/develop-app/new-features.md), условного кода следует использовать, чтобы определить, является ли драйвер ODBC 3. *x* или ODBC 2*.x* драйвера. Приложение использует **SQLGetDiagField** и **SQLGetDiagRec** для получения ODBC 3. *x* SQLSTATE во время выполнения в следующих фрагментах кода условной обработки ошибок. Следует учитывать следующие моменты, касающиеся новых функциональных возможностей.  
  
-   Приложение повлияло изменение в поведении размер набора строк следует соблюдать осторожность и не вызвать **SQLFetch** Если размер массива больше 1. Эти приложения следует заменить вызовы **SQLExtendedFetch** с вызовами **SQLSetStmtAttr** установить атрибут инструкции SQL_ATTR_ARRAY_STATUS_PTR и **SQLFetchScroll**, после чего они имеют общий код, который работает с обоих ODBC 3. *x* и ODBC 2. *x* драйверы. Поскольку **SQLSetStmtAttr** с SQL_ATTR_ROW_ARRAY_SIZE будут сопоставлены **SQLSetStmtAttr** с SQL_ROWSET_SIZE для ODBC 2. *x* драйверы, приложения можно просто установить SQL_ATTR_ROW_ARRAY_SIZE функционирование многострочные выборки.  
  
-   Большинство приложений, обновления, изменения в кодах SQLSTATE фактически не затрагиваются. Для приложений, которые изменяются они механические поиска и замены в большинстве случаев использования таблицы преобразования ошибки в разделе «Сопоставление SQLSTATE» для преобразования ODBC 3. *x* коды ошибок ODBC 2*.x* коды. Поскольку ODBC 3*.x* сопоставления выполнит диспетчера драйверов ODBC 2. *x* SQLSTATE для ODBC 3. *x* SQLSTATE эти авторы приложений должны только проверка для ODBC 3. *x* SQLSTATE и не беспокойтесь о включении ODBC 2. *x* SQLSTATE условного кода.  
  
-   Если приложение использует большое даты, времени и типы данных timestamp, приложение может объявить себя быть ODBC 2. *x* приложения и используйте его существующий код вместо использования кондиционирования кода.  
  
 Обновления также должен включать следующие этапы:  
  
-   Вызовите **SQLSetEnvAttr** перед выделением соединения для задания атрибута среды SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
-   Замените все вызовы **SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt** с вызовами **SQLAllocHandle** с соответствующими *HandleType* аргумент SQL_HANDLE_ENV, установленным в значение sql_handle_stmt или значение SQL_HANDLE_STMT.  
  
-   Замените все вызовы **SQLFreeEnv** или **SQLFreeConnect** с вызовами **SQLFreeHandle** с соответствующими *HandleType* аргумент SQL_HANDLE_DBC или значение SQL_HANDLE_STMT.  
  
-   Замените все вызовы **SQLSetConnectOption** с вызовами **SQLSetConnectAttr**. Если параметр атрибута, значение которого является строкой, значение *StringLength* аргумент соответствующим образом. Изменение *атрибута* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLGetConnectOption** с вызовами **SQLGetConnectAttr**. Если строка или двоичное значение атрибута, задайте *BufferLength* соответствующее значение и передайте его в *StringLength* аргумент. Изменение *атрибута* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLSetStmtOption** с вызовами **SQLSetStmtAttr**. Если параметр атрибута, значение которого является строкой, значение *StringLength* аргумент соответствующим образом. Изменение *атрибута* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLGetStmtOption** с вызовами **SQLGetStmtAttr**. Если строка или двоичное значение атрибута, задайте *BufferLength* соответствующее значение и передайте его в *StringLength* аргумент. Изменение *атрибута* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLTransact** с вызовами **SQLEndTran**. Если правых допустимый дескриптор в **SQLTransact** вызывается дескриптор среды *HandleType* аргумента, установленным в значение sql_handle_env, следует использовать в **SQLEndTran** вызвать с соответствующий *обработки* аргумент. Если правых допустимый дескриптор в вашей **SQLTransact** вызывается дескриптор соединения *HandleType* аргумента, установленным в значение sql_handle_dbc, следует использовать в **SQLEndTran** вызвать с соответствующий *обработки* аргумент.  
  
-   Замените все вызовы **SQLColAttributes** с вызовами **SQLColAttribute**. Если *FieldIdentifier* аргумент SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE или SQL_COLUMN_LENGTH, не изменяйте ничего, кроме имя функции. Если нет, замените *FieldIdentifier* из SQL_COLUMN_XXXX для SQL_DESC_XXXX. Если *FieldIdentifier* является SQL_DESC_CONCISE_TYPE и тип данных типом данных datetime, измените соответствующий ODBC 3*.x* тип данных.  
  
-   При использовании блочных курсоров и Прокручиваемые курсоры, приложение выполняет следующие задачи.  
  
    -   Задает размер набора строк, тип курсора и параллелизма курсора с помощью **SQLSetStmtAttr**.  
  
    -   Вызовы **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, чтобы он указывал на массив записей состояния.  
  
    -   Вызовы **SQLSetStmtAttr** для задания SQL_ATTR_ROWS_FETCHED_PTR, чтобы она указывала на SQLINTEGER.  
  
    -   Выполняет необходимые привязки и выполняет инструкцию SQL.  
  
    -   Вызовы **SQLFetchScroll** в цикле для выборки строк и перемещать в результирующем наборе.  
  
    -   Если необходимо извлечь закладкой, приложение вызывает **SQLSetStmtAttr** SQL_ATTR_FETCH_BOOKMARK_PTR присваивается переменной, которая будет содержать закладка для строки, ему нужно извлечь и вызовы **SQLFetchScroll** с *FetchOrientation* SQL_FETCH_BOOKMARK аргумента.  
  
-   При использовании массивов параметров, приложение выполняет следующие задачи.  
  
    -   Вызовы **SQLSetStmtAttr** для задания атрибута sql_attr_paramset_size задайте размер массива параметров.  
  
    -   Вызовы **SQLSetStmtAttr** для задания SQL_ATTR_ROWS_PROCESSED_PTR, чтобы она указывала на внутреннюю переменную UDWORD.  
  
    -   Выполняется подготовка, привязки и выполнять операции, соответствующим образом.  
  
    -   Если прерывается для какой-либо причине (например, SQL_NEED_DATA), его можно найти «текущая» строки параметров, проверяя расположении, указанном SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставление замещающих функций для обеспечения обратной совместимости приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Вызов SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Вызов SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Вызов SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Операции с библиотекой курсоров](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Сопоставление типов сведений атрибутов1 курсора](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
