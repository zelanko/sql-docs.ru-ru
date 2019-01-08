---
title: Справочник по API ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: dllExport
ms.assetid: b7a49774-f458-44ce-9a04-a0457501405b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56d6068b842256bd450844c7b163727e5d35f3d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52525061"
---
# <a name="odbc-api-reference"></a>Справочник по API ODBC
В этом разделе описываются каждой функции ODBC в алфавитном порядке. Каждая функция определяется как C, функция языка программирования. Ниже приведены описания:  
  
-   Цель  
  
-   Версия ODBC  
  
-   Стандартный уровень соответствия интерфейса командной строки  
  
-   Синтаксис  
  
-   Аргументы  
  
-   Возвращаемые значения  
  
-   Диагностика  
  
-   Примечания об использовании и реализации  
  
-   Пример кода  
  
-   Ссылки на связанные функции  
  
 Стандартный уровень соответствия для интерфейса командной строки может принимать одно из следующих: ISO-92, откройте группу, ODBC, или устарели. Функция, отмечен как соответствующие стандарту ISO-92 также отображается в Open Group версии 1, из-за Open Group является чисто надмножеством ISO-92. Функции, как открыть группу с также появляется в ODBC 3. *x*, так как ODBC 3. *x* является чисто надмножеством Open Group версии 1. Функции, которые помечаются как совместимые с ODBC отображается ни одна из стандарта. С тегами как нерекомендуемые функции был объявлен устаревшим в ODBC 3. *x*.  
  
 Описывается обработка диагностических сведений в [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции. Текст, связанный со значениями SQLSTATE включено, чтобы указать описание условия, но не предназначен для задания определенного текста.  
  
> [!NOTE]  
>  Относящиеся к драйверу сведения о функции ODBC см. в разделе драйвер.  
  
 Этот раздел содержит разделы, посвященные следующие функции:  
  
-   [Функция SQLAllocConnect](../../../odbc/reference/syntax/sqlallocconnect-function.md)  
  
-   [Функция SQLAllocEnv](../../../odbc/reference/syntax/sqlallocenv-function.md)  
  
-   [Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [Функция SQLAllocStmt](../../../odbc/reference/syntax/sqlallocstmt-function.md)  
  
-   [Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)  
  
-   [Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)  
  
-   [Функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)  
  
-   [Функция SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)  
  
-   [Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [Функция SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)  
  
-   [Функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)  
  
-   [Функция SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)  
  
-   [Функция SQLColAttributes](../../../odbc/reference/syntax/sqlcolattributes-function.md)  
  
-   [Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)  
  
-   [Функция SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)  
  
-   [Функция SQLCompleteAsync](../../../odbc/reference/syntax/sqlcompleteasync-function.md)  
  
-   [Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)  
  
-   [Функция SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)  
  
-   [Функция SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [Функция SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)  
  
-   [Функция SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)  
  
-   [Функция SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)  
  
-   [Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
-   [Функция SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [Функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)  
  
-   [Функция SQLError](../../../odbc/reference/syntax/sqlerror-function.md)  
  
-   [Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)  
  
-   [Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)  
  
-   [Функция SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md)  
  
-   [Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)  
  
-   [Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)  
  
-   [Функция SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)  
  
-   [Функция SQLFreeConnect](../../../odbc/reference/syntax/sqlfreeconnect-function.md)  
  
-   [Функция SQLFreeEnv](../../../odbc/reference/syntax/sqlfreeenv-function.md)  
  
-   [Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
-   [Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)  
  
-   [Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [Функция SQLGetConnectOption](../../../odbc/reference/syntax/sqlgetconnectoption-function.md)  
  
-   [Функция SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)  
  
-   [Функция SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)  
  
-   [Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)  
  
-   [Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)  
  
-   [Функция SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [Функция SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [Функция SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [Функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [Функция SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
-   [Функция SQLGetStmtOption](../../../odbc/reference/syntax/sqlgetstmtoption-function.md)  
  
-   [Функция SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
-   [Функция SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)  
  
-   [Функция SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
-   [Функция SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)  
  
-   [Функция SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)  
  
-   [Функция SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)  
  
-   [Функция SQLParamOptions](../../../odbc/reference/syntax/sqlparamoptions-function.md)  
  
-   [Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)  
  
-   [Функция SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)  
  
-   [Функция SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)  
  
-   [Функция SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)  
  
-   [Функция SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)  
  
-   [Функция SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)  
  
-   [Функция SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   [Функция SQLSetConnectOption](../../../odbc/reference/syntax/sqlsetconnectoption-function.md)  
  
-   [Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)  
  
-   [Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
-   [Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)  
  
-   [Функция SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)  
  
-   [Функция SQLSetParam](../../../odbc/reference/syntax/sqlsetparam-function.md)  
  
-   [Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)  
  
-   [Функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)  
  
-   [Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
-   [Функция SQLSetStmtOption](../../../odbc/reference/syntax/sqlsetstmtoption-function.md)  
  
-   [Функция SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)  
  
-   [Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)  
  
-   [Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)  
  
-   [Функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md)  
  
-   [Функция SQLTransact](../../../odbc/reference/syntax/sqltransact-function.md)
