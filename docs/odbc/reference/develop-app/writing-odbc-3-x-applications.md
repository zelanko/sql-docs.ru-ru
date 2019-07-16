---
title: Написание приложений ODBC 3.x | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9939d11e3a779cc25d7faeb4950783353947f140
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081449"
---
# <a name="writing-odbc-3x-applications"></a>Написание приложений ODBC 3.x
Когда ODBC *2.x* обновлении приложения до ODBC *3.x*, должны быть написаны таким образом, что она работает с и ODBC *2.x* и *3.x* драйверы . Приложение должно предусматривать условный код, чтобы воспользоваться всеми преимуществами ODBC *3.x* функции.  
  
 Атрибут SQL_ATTR_ODBC_VERSION окружения должно быть присвоено SQL_OV_ODBC2. Это позволит гарантировать, что драйвер ведет себя как ODBC *2.x* драйверов с учетом изменений, описанных в разделе [изменения в поведении](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Если приложение будет использовать любой из функций, описанных в разделе [новые функции](../../../odbc/reference/develop-app/new-features.md), условный код следует использовать для определения, является ли драйвер ODBC *3.x* или ODBC *2.x* драйвера. Приложение использует **SQLGetDiagField** и **SQLGetDiagRec** для получения ODBC *3.x* SQLSTATE во время выполнения произошла ошибка при обработке на эти фрагменты условный код. Следует учитывать следующие моменты, касающиеся новых функциональных возможностей:  
  
-   Приложение, повлияло изменение в поведении размер набора строк должно быть не следует вызывать **SQLFetch** Если размер массива больше 1. Эти приложения следует заменить вызовы **SQLExtendedFetch** с вызовами **SQLSetStmtAttr** установить атрибут инструкции SQL_ATTR_ARRAY_STATUS_PTR и **SQLFetchScroll**, чтобы они могли общим кодом, который работает с и ODBC *3.x* и ODBC *2.x* драйверы. Так как **SQLSetStmtAttr** с SQL_ATTR_ROW_ARRAY_SIZE будут сопоставлены с **SQLSetStmtAttr** с SQL_ROWSET_SIZE для ODBC *2.x* драйверы, приложения можно просто установить SQL _ATTR_ROW_ARRAY_SIZE функционирование многострочной fetch.  
  
-   Большинство приложений, обновления, изменения в кодах SQLSTATE фактически не затрагиваются. Для приложений, которые будут затронуты, они механические поиска и замены в большинстве случаев с помощью таблицы преобразования ошибки в разделе «Сопоставление SQLSTATE» для преобразования ODBC *3.x* описания кодов ошибок ODBC *2.x* коды. С момента ODBC *3.x* диспетчера драйверов будет выполнить сопоставление из ODBC *2.x* SQLSTATE для ODBC *3.x* SQLSTATE эти создатели приложений должны только проверка для ODBC  *3.x* SQLSTATE и не придется волноваться о ODBC, включая *2.x* SQLSTATE в условный код.  
  
-   Если приложение позволяет эффективно использовать дату, время и типы данных timestamp, приложение может объявить себя быть ODBC *2.x* приложения и используйте его существующий код вместо использования кондиционирования кода.  
  
 Обновления также должно включать следующие действия:  
  
-   Вызовите **SQLSetEnvAttr** перед выделением присвоить атрибуту окружения SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2 соединение.  
  
-   Замените все вызовы **SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt** с вызовами **SQLAllocHandle** с соответствующим *HandleType* аргумент SQL_HANDLE_ENV, установленным в значение sql_handle_stmt или значение SQL_HANDLE_STMT.  
  
-   Замените все вызовы **SQLFreeEnv** или **SQLFreeConnect** с вызовами **SQLFreeHandle** с соответствующим *HandleType* аргумент SQL_HANDLE_DBC или значение SQL_HANDLE_STMT.  
  
-   Замените все вызовы **SQLSetConnectOption** с вызовами **SQLSetConnectAttr**. Если задания атрибута, значение которого является строка, задайте *StringLength* аргумент соответствующим образом. Изменение *атрибут* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLGetConnectOption** с вызовами **SQLGetConnectAttr**. Если строки или двоичного атрибута, задайте *BufferLength* соответствующее значение и передать *StringLength* аргумент. Изменение *атрибут* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLSetStmtOption** с вызовами **SQLSetStmtAttr**. Если задания атрибута, значение которого является строка, задайте *StringLength* аргумент соответствующим образом. Изменение *атрибут* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLGetStmtOption** с вызовами **SQLGetStmtAttr**. Если строки или двоичного атрибута, задайте *BufferLength* соответствующее значение и передать *StringLength* аргумент. Изменение *атрибут* аргументов SQL_XXXX SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLTransact** с вызовами **SQLEndTran**. Если крайний правый допустимый дескриптор в **SQLTransact** вызов является дескриптор среды *HandleType* аргумент SQL_HANDLE_ENV должен использоваться в **SQLEndTran** вызов с соответствующий *обрабатывать* аргумент. Если крайний правый допустимый дескриптор в вашей **SQLTransact** вызов является дескриптор соединения *HandleType* аргумент SQL_HANDLE_DBC должен использоваться в **SQLEndTran** вызов с соответствующий *обрабатывать* аргумент.  
  
-   Замените все вызовы **SQLColAttributes** с вызовами **SQLColAttribute**. Если *FieldIdentifier* равно SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE или SQL_COLUMN_LENGTH, не изменяйте ничего, кроме имени функции. Если это не так, измените *FieldIdentifier* из SQL_COLUMN_XXXX для SQL_DESC_XXXX. Если *FieldIdentifier* является SQL_DESC_CONCISE_TYPE и тип данных типом данных datetime, измените соответствующий ODBC *3.x* тип данных.  
  
-   При использовании блочных курсоров и прокручиваемых курсоров, приложение выполняет следующие функции:  
  
    -   Задает размер набора строк, тип курсора и параллелизма курсора с помощью **SQLSetStmtAttr**.  
  
    -   Вызовы **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, чтобы он указывал на массив записей состояния.  
  
    -   Вызовы **SQLSetStmtAttr** присвоить SQL_ATTR_ROWS_FETCHED_PTR, чтобы он указывал SQLINTEGER.  
  
    -   Выполняет необходимые привязки и выполняет инструкцию SQL.  
  
    -   Вызовы **SQLFetchScroll** в цикле для выборки строк и перемещаться в результирующем наборе.  
  
    -   Если необходимо получить закладкой, приложение вызывает **SQLSetStmtAttr** присвоить переменную, которая будет содержать закладка для строки, которой необходимо получить и вызывает метод SQL_ATTR_FETCH_BOOKMARK_PTR **SQLFetchScroll** с *FetchOrientation* аргумент sql_fetch_bookmark аргумента.  
  
-   При использовании массивов параметров, приложение выполняет следующие функции:  
  
    -   Вызовы **SQLSetStmtAttr** к атрибуту SQL_ATTR_PARAMSET_SIZE до размера массива параметров.  
  
    -   Вызовы **SQLSetStmtAttr** присвоить SQL_ATTR_ROWS_PROCESSED_PTR указывал на внутреннюю переменную UDWORD.  
  
    -   Выполняется подготовка, привязку и выполнять операции, соответствующим образом.  
  
    -   Если выполнение прекращается по некоторым причинам (например, SQL_NEED_DATA), его можно найти «current» ряда параметров, проверяя расположении, указанном SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставление замещающих функций для обеспечения обратной совместимости приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Вызов SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Вызов SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Вызов SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Операции с библиотекой курсоров](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Сопоставление типов сведений атрибутов1 курсора](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
