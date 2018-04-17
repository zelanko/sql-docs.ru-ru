---
title: Функция соответствия | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dc31fa21e9c3e8e5417f0560105e2b09691388c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
