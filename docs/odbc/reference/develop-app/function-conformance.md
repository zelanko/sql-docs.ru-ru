---
title: "Функция соответствия | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 48ed4bc9b52b6a905972e566870e7e2f86fc4734
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="function-conformance"></a>Функция соответствия
Следующая таблица указывает уровень соответствия каждой функции ODBC, в которой это является правильно определенным.  
  
|Функция|Уровень соответствия|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Основные сведения|  
|**SQLBindCol**|Основные сведения|  
|**SQLBindParameter**|Основные [1]|  
|**SQLBrowseConnect**|уровне 1|  
|**SQLBulkOperations**|уровне 1|  
|**SQLCancel**|Основные [1]|  
|**SQLCloseCursor**|Основные сведения|  
|**SQLColAttribute**|Основные [1]|  
|**SQLColumnPrivileges**|Уровень 2|  
|**SQLColumns**|Основные сведения|  
|**SQLConnect**|Основные сведения|  
|**SQLCopyDesc**|Основные сведения|  
|**SQLDataSources**|Основные сведения|  
|**SQLDescribeCol**|Основные [1]|  
|**SQLDescribeParam**|Уровень 2|  
|**SQLDisconnect**|Основные сведения|  
|**SQLDriverConnect**|Основные сведения|  
|**SQLDrivers**|Основные сведения|  
|**SQLEndTran**|Основные [1]|  
|**SQLExecDirect**|Основные сведения|  
|**SQLExecute**|Основные сведения|  
|**SQLFetch**|Основные сведения|  
|**SQLFetchScroll**|Основные [1]|  
|**SQLForeignKeys**|Уровень 2|  
|**SQLFreeHandle**|Основные сведения|  
|**SQLFreeStmt**|Основные сведения|  
|**SQLGetConnectAttr**|Основные сведения|  
|**SQLGetCursorName**|Основные сведения|  
|**SQLGetData**|Основные сведения|  
|**SQLGetDescField**|Основные сведения|  
|**SQLGetDescRec**|Основные сведения|  
|**SQLGetDiagField**|Основные сведения|  
|**SQLGetDiagRec**|Основные сведения|  
|**SQLGetEnvAttr**|Основные сведения|  
|**SQLGetFunctions**|Основные сведения|  
|**SQLGetInfo**|Основные сведения|  
|**SQLGetStmtAttr**|Основные сведения|  
|**SQLGetTypeInfo**|Основные сведения|  
|**SQLMoreResults**|уровне 1|  
|**SQLNativeSql**|Основные сведения|  
|**SQLNumParams**|Основные сведения|  
|**SQLNumResultCols**|Основные сведения|  
|**SQLParamData**|Основные сведения|  
|**SQLPrepare**|Основные сведения|  
|**SQLPrimaryKeys**|уровне 1|  
|**SQLProcedureColumns**|уровне 1|  
|**SQLProcedures**|уровне 1|  
|**SQLPutData**|Основные сведения|  
|**SQLRowCount**|Основные сведения|  
|**SQLSetConnectAttr**|Core [2]|  
|**SQLSetCursorName**|Основные сведения|  
|**SQLSetDescField**|Основные [1]|  
|**SQLSetDescRec**|Основные сведения|  
|**SQLSetEnvAttr**|Core [2]|  
|**SQLSetPos**|Уровень 1 [1]|  
|**SQLSetStmtAttr**|Core [2]|  
|**SQLSpecialColumns**|Основные [1]|  
|**SQLStatistics**|Основные сведения|  
|**SQLTablePrivileges**|Уровень 2|  
|**SQLTables**|Основные сведения|  
  
 [1] важных функций этой функции доступны только на более высоких уровнях совместимости.  
  
 [2] Задание определенные атрибуты нестандартные значения зависит от уровня совместимости. Дополнительные сведения см. следующий раздел, [соответствия атрибута](../../../odbc/reference/develop-app/attribute-conformance.md).

