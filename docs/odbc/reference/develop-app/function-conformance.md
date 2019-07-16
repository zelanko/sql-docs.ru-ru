---
title: Функция соответствия | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 45eb427b660496430334633b5d43ee8989211c0f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069754"
---
# <a name="function-conformance"></a>Соответствие функции
Следующая таблица указывает уровень соответствия каждой функции ODBC, в которой это является правильно определенным.  
  
|Компонент|Уровень соответствия|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Основные сведения|  
|**SQLBindCol**|Основные сведения|  
|**SQLBindParameter**|Core [1]|  
|**SQLBrowseConnect**|уровне 1|  
|**SQLBulkOperations**|уровне 1|  
|**SQLCancel**|Core [1]|  
|**SQLCloseCursor**|Основные сведения|  
|**SQLColAttribute**|Core [1]|  
|**SQLColumnPrivileges**|Уровень 2|  
|**SQLColumns**|Основные сведения|  
|**SQLConnect**|Основные сведения|  
|**SQLCopyDesc**|Основные сведения|  
|**SQLDataSources**|Основные сведения|  
|**SQLDescribeCol**|Core [1]|  
|**SQLDescribeParam**|Уровень 2|  
|**SQLDisconnect**|Основные сведения|  
|**SQLDriverConnect**|Основные сведения|  
|**SQLDrivers**|Основные сведения|  
|**SQLEndTran**|Core [1]|  
|**SQLExecDirect**|Основные сведения|  
|**SQLExecute**|Основные сведения|  
|**SQLFetch**|Основные сведения|  
|**SQLFetchScroll**|Core [1]|  
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
|**SQLSetDescField**|Core [1]|  
|**SQLSetDescRec**|Основные сведения|  
|**SQLSetEnvAttr**|Core [2]|  
|**SQLSetPos**|Уровень 1 [1]|  
|**SQLSetStmtAttr**|Core [2]|  
|**SQLSpecialColumns**|Core [1]|  
|**SQLStatistics**|Основные сведения|  
|**SQLTablePrivileges**|Уровень 2|  
|**SQLTables**|Основные сведения|  
  
 [1] несколько важных функций этой функции доступны только на более высоких уровнях совместимости.  
  
 [2] задания определенных атрибутов нестандартные значения зависит от уровня совместимости. Дополнительные сведения см. следующий раздел, [соответствие атрибутов](../../../odbc/reference/develop-app/attribute-conformance.md).
