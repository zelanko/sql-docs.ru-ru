---
title: Создание приложений ODBC 3. x | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081449"
---
# <a name="writing-odbc-3x-applications"></a>Написание приложений ODBC 3.x
Когда приложение ODBC *2. x* обновляется до ODBC *3. x*, оно должно быть написано таким, что оно работает с драйверами ODBC *2. x* и *3. x* . Приложение должно включать условный код, чтобы воспользоваться всеми преимуществами функций ODBC *3. x* .  
  
 Для атрибута среды SQL_ATTR_ODBC_VERSION должно быть задано значение SQL_OV_ODBC2. Это обеспечит работу драйвера как драйвер ODBC *2. x* в соответствии с изменениями, описанными в разделе [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Если приложение будет использовать любую из функций, описанных в разделе [новые функции](../../../odbc/reference/develop-app/new-features.md), следует использовать условный код, чтобы определить, является ли драйвер драйвером ODBC *3. x* или ODBC *2. x* . Приложение использует **SQLGetDiagField** и **SQLGETDIAGREC** для получения ODBC *3. x* SQLSTATE при обработке ошибок в этих фрагментах условного кода. Следует учитывать следующие моменты, связанные с новыми функциональными возможностями:  
  
-   Приложение, затронутое изменением поведения размера набора строк, должно быть внимательным, чтобы не вызывать **SQLFetch** , если размер массива больше 1. Эти приложения должны заменить вызовы **SQLExtendedFetch** вызовами **SQLSetStmtAttr** , чтобы задать атрибут инструкции SQL_ATTR_ARRAY_STATUS_PTR и **SQLFetchScroll**, чтобы они имели общий код, который работает с драйверами ODBC *3. x* и ODBC *2. x* . Так как **SQLSetStmtAttr** с SQL_ATTR_ROW_ARRAY_SIZE будет сопоставляться с **SQLSetStmtAttr** с SQL_ROWSET_SIZE для драйверов ODBC *2. x* , приложения могут просто установить SQL_ATTR_ROW_ARRAY_SIZE для своих операций многострочные FETCH.  
  
-   Большинство обновляемых приложений на самом деле не затрагиваются изменениями в кодах SQLSTATE. Для этих приложений они могут выполнить механические Поиск и заменить в большинстве случаев, используя таблицу преобразования ошибок в разделе "сопоставление SQLSTATE", чтобы преобразовать коды ошибок ODBC *3. x* в коды ODBC *2. x* . Так как диспетчер драйверов ODBC *3. x* будет выполнять сопоставление из ODBC *2. x* , SQLSTATE с SQLSTATE ODBC *3. x* , эти средства записи приложений должны только проверять наличие ODBC *3. x* SQLSTATE и не беспокоиться о включении ODBC *2. x* SQLSTATE в условном коде.  
  
-   Если приложение использует типы данных даты, времени и отметок времени, приложение может объявить себя как приложение ODBC *2. x* и использовать существующий код вместо использования условного кода.  
  
 Обновление должно также включать следующие шаги.  
  
-   Вызовите **SQLSetEnvAttr** перед выделением соединения, чтобы задать SQL_OV_ODBC2 атрибута среды SQL_ATTR_ODBC_VERSION.  
  
-   Замените все вызовы **SQLAllocEnv**, **SQLAllocConnect**или **SQLAllocStmt** на вызовы **функцию SQLAllocHandle** с соответствующим аргументом *параметром handletype* SQL_HANDLE_ENV, SQL_HANDLE_DBC или SQL_HANDLE_STMT.  
  
-   Замените все вызовы **SQLFreeEnv** или **SQLFreeConnect** вызовами **SQLFreeHandle** с помощью соответствующего аргумента *параметром handletype* SQL_HANDLE_DBC или SQL_HANDLE_STMT.  
  
-   Замените все вызовы **SQLSetConnectOption** на вызовы **SQLSetConnectAttr**. Если задан атрибут, значение которого является строкой, установите аргумент *StringLength* соответствующим образом. Измените аргумент *атрибута* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLGetConnectOption** на вызовы **SQLGetConnectAttr**. Если вы получаете строковый или двоичный атрибут, задайте для *BufferLength* соответствующее значение и передайте аргумент *StringLength* . Измените аргумент *атрибута* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLSetStmtOption** на вызовы **SQLSetStmtAttr**. Если задан атрибут, значение которого является строкой, установите аргумент *StringLength* соответствующим образом. Измените аргумент *атрибута* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLGetStmtOption** на вызовы **SQLGetStmtAttr**. Если вы получаете строковый или двоичный атрибут, задайте для *BufferLength* соответствующее значение и передайте аргумент *StringLength* . Измените аргумент *атрибута* с SQL_XXXX на SQL_ATTR_XXXX.  
  
-   Замените все вызовы **SQLTransact** на вызовы **SQLEndTran**. Если правый допустимый маркер в вызове **SQLTransact** является обработчиком среды, то в вызове **SQLEndTran** следует использовать SQL_HANDLE_ENV аргумент *параметром handletype* с соответствующим аргументом *Handle* . Если правый допустимый маркер в вызове **SQLTransact** является маркером соединения, то в вызове **SQLEndTran** следует использовать SQL_HANDLE_DBC аргумент *параметром handletype* с соответствующим аргументом *Handle* .  
  
-   Замените все вызовы **SQLColAttributes** на вызовы **SQLColAttribute**. Если аргумент *фиелдидентифиер* имеет значение SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE или SQL_COLUMN_LENGTH, не изменяйте ничего, кроме имени функции. В противном случае измените значение *фиелдидентифиер* с SQL_COLUMN_XXXX на SQL_DESC_XXXX. Если *фиелдидентифиер* имеет SQL_DESC_CONCISE_TYPE и тип данных имеет тип данных DateTime, измените соответствующий тип данных ODBC *3. x* .  
  
-   При использовании блочных курсоров, прокручиваемых курсоров или и того и другого, приложение выполняет следующие действия:  
  
    -   Задает размер набора строк, тип курсора и параллелизм курсора с помощью **SQLSetStmtAttr**.  
  
    -   Вызывает **SQLSetStmtAttr** , чтобы задать SQL_ATTR_ROW_STATUS_PTR, указывающий на массив записей состояния.  
  
    -   Вызывает **SQLSetStmtAttr** , чтобы задать SQL_ATTR_ROWS_FETCHED_PTR, указывающий на SQLINTEGER.  
  
    -   Выполняет необходимые привязки и выполняет инструкцию SQL.  
  
    -   Вызывает **SQLFetchScroll** в цикле для выборки строк и перемещения в результирующем наборе.  
  
    -   Если требуется получить по закладке, приложение вызывает **SQLSetStmtAttr** , чтобы задать SQL_ATTR_FETCH_BOOKMARK_PTR переменной, которая будет содержать закладку для строки, которую требуется получить, и вызывает **SQLFetchScroll** с аргументом *фетчориентатион* SQL_FETCH_BOOKMARK.  
  
-   При использовании массивов параметров приложение выполняет следующие действия:  
  
    -   Вызывает **SQLSetStmtAttr** , чтобы задать для атрибута SQL_ATTR_PARAMSET_SIZE размер массива параметров.  
  
    -   Вызывает **SQLSetStmtAttr** , чтобы задать SQL_ATTR_ROWS_PROCESSED_PTR, указывающий на внутреннюю переменную удворд.  
  
    -   Выполняет необходимые операции подготовки, привязки и выполнения.  
  
    -   Если выполнение останавливается по какой-либо причине (например, SQL_NEED_DATA), оно может найти "текущую" строку параметров путем проверки расположения, на которое указывает SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставление замещающих функций для обеспечения обратной совместимости приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Вызов SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Вызов SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Вызов SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Операции с библиотекой курсоров](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Сопоставление типов сведений атрибутов1 курсора](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
