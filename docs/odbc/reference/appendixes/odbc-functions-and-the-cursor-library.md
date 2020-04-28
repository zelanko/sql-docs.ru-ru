---
title: Функции ODBC и библиотека курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c609d0fb-787a-4b39-9673-332d411b3d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8293e9bc952fc1dffc5a8f796f5a066b91ae811
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304345"
---
# <a name="odbc-functions-and-the-cursor-library"></a>Функции ODBC и библиотека курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Если для соединения включена библиотека курсоров ODBC, диспетчер драйверов вызывает функции в библиотеке курсоров, а не в драйвере. Библиотека курсоров либо выполняет функцию, либо вызывает ее в указанном драйвере.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функции ODBC, выполняемые библиотекой курсоров](../../../odbc/reference/appendixes/odbc-functions-executed-by-the-cursor-library.md)  
  
-   [Функции ODBC, не выполняемые библиотекой курсоров](../../../odbc/reference/appendixes/odbc-functions-not-executed-by-the-cursor-library.md)  
  
-   [SQLBindCol (библиотека курсоров)](../../../odbc/reference/appendixes/sqlbindcol-cursor-library.md)  
  
-   [SQLBindParameter (библиотека курсоров)](../../../odbc/reference/appendixes/sqlbindparameter-cursor-library.md)  
  
-   [SQLBulkOperations (библиотека курсоров)](../../../odbc/reference/appendixes/sqlbulkoperations-and-the-cursor-library.md)  
  
-   [SQLCloseCursor (библиотека курсоров)](../../../odbc/reference/appendixes/sqlclosecursor-odbc.md)  
  
-   [SQLEndTran (библиотека курсоров)](../../../odbc/reference/appendixes/sqlendtran-cursor-library.md)  
  
-   [SQLExtendedFetch (библиотека курсоров)](../../../odbc/reference/appendixes/sqlextendedfetch-cursor-library.md)  
  
-   [SQLFetch (библиотека курсоров)](../../../odbc/reference/appendixes/sqlfetch-cursor-library.md)  
  
-   [SQLFetchScroll (библиотека курсоров)](../../../odbc/reference/appendixes/sqlfetchscroll-cursor-library.md)  
  
-   [SQLFreeStmt (библиотека курсоров)](../../../odbc/reference/appendixes/sqlfreestmt-cursor-library.md)  
  
-   [SQLGetData (библиотека курсоров)](../../../odbc/reference/appendixes/sqlgetdata-cursor-library.md)  
  
-   [SQLGetDescField и SQLGetDescRec (библиотека курсоров)](../../../odbc/reference/appendixes/sqlgetdescfield-and-sqlgetdescrec-cursor-library.md)  
  
-   [SQLGetFunctions (библиотека курсоров)](../../../odbc/reference/appendixes/sqlgetfunctions-cursor-library.md)  
  
-   [SQLGetInfo (библиотека курсоров)](../../../odbc/reference/appendixes/sqlgetinfo-cursor-library.md)  
  
-   [SQLGetStmtAttr (библиотека курсоров)](../../../odbc/reference/appendixes/sqlgetstmtattr-cursor-library.md)  
  
-   [SQLGetStmtOption (библиотека курсоров)](../../../odbc/reference/appendixes/sqlgetstmtoption-cursor-library.md)  
  
-   [SQLNativeSql (библиотека курсоров)](../../../odbc/reference/appendixes/sqlnativesql-cursor-library.md)  
  
-   [SQLRowCount (библиотека курсоров)](../../../odbc/reference/appendixes/sqlrowcount-cursor-library.md)  
  
-   [SQLSetConnectAttr (библиотека курсоров)](../../../odbc/reference/appendixes/sqlsetconnectattr-cursor-library.md)  
  
-   [SQLSetDescField и SQLSetDescRec (библиотека курсоров)](../../../odbc/reference/appendixes/sqlsetdescfield-and-sqlsetdescrec-cursor-library.md)  
  
-   [SQLSetEnvAttr (библиотека курсоров)](../../../odbc/reference/appendixes/sqlsetenvattr-and-the-cursor-library.md)  
  
-   [SQLSetPos (библиотека курсоров)](../../../odbc/reference/appendixes/sqlsetpos-cursor-library.md)  
  
-   [SQLSetScrollOptions (библиотека курсоров)](../../../odbc/reference/appendixes/sqlsetscrolloptions-cursor-library.md)  
  
-   [SQLSetStmtAttr (библиотека курсоров)](../../../odbc/reference/appendixes/sqlsetstmtattr-cursor-library.md)
