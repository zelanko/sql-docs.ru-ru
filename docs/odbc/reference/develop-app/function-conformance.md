---
title: Соответствие функции | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33cd0ad4269ed59e31c8ab343ddbb01806afce04
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305595"
---
# <a name="function-conformance"></a>Соответствие функции
В следующей таблице указан уровень соответствия для каждой функции ODBC, где это хорошо определено.  
  
|Функция|Уровень согласованности|  
|--------------|-----------------------|  
|**Функцию SQLAllocHandle**|Ядро|  
|**SQLBindCol**|Ядро|  
|**SQLBindParameter**|Ядро [1]|  
|**SQLBrowseConnect**|уровне 1|  
|**SQLBulkOperations**|уровне 1|  
|**SQLCancel**|Ядро [1]|  
|**SQLCloseCursor**|Ядро|  
|**SQLColAttribute**|Ядро [1]|  
|**SQLColumnPrivileges**|Уровень 2|  
|**SQLColumns**|Ядро|  
|**SQLConnect**|Ядро|  
|**склкопидеск**|Ядро|  
|**SQLDataSources**|Ядро|  
|**SQLDescribeCol**|Ядро [1]|  
|**SQLDescribeParam**|Уровень 2|  
|**SQLDisconnect**|Ядро|  
|**SQLDriverConnect**|Ядро|  
|**SQLDrivers**|Ядро|  
|**SQLEndTran**|Ядро [1]|  
|**SQLExecDirect**|Ядро|  
|**SQLExecute**|Ядро|  
|**SQLFetch**|Ядро|  
|**SQLFetchScroll**|Ядро [1]|  
|**SQLForeignKeys**|Уровень 2|  
|**SQLFreeHandle**|Ядро|  
|**Функция SQLFreeStmt**|Ядро|  
|**SQLGetConnectAttr**|Ядро|  
|**SQLGetCursorName**|Ядро|  
|**SQLGetData**|Ядро|  
|**SQLGetDescField**|Ядро|  
|**SQLGetDescRec**|Ядро|  
|**SQLGetDiagField**|Ядро|  
|**Функции SQLGetDiagRec**|Ядро|  
|**SQLGetEnvAttr**|Ядро|  
|**SQLGetFunctions**|Ядро|  
|**SQLGetInfo**|Ядро|  
|**SQLGetStmtAttr**|Ядро|  
|**SQLGetTypeInfo**|Ядро|  
|**SQLMoreResults**|уровне 1|  
|**SQLNativeSql**|Ядро|  
|**SQLNumParams**|Ядро|  
|**SQLNumResultCols**|Ядро|  
|**SQLParamData**|Ядро|  
|**SQLPrepare**|Ядро|  
|**SQLPrimaryKeys**|уровне 1|  
|**SQLProcedureColumns**|уровне 1|  
|**SQLProcedures**|уровне 1|  
|**SQLPutData**|Ядро|  
|**SQLRowCount**|Ядро|  
|**SQLSetConnectAttr**|Ядро [2]|  
|**SQLSetCursorName**|Ядро|  
|**SQLSetDescField**|Ядро [1]|  
|**SQLSetDescRec**|Ядро|  
|**SQLSetEnvAttr**|Ядро [2]|  
|**функция SQLSetPos;**|Уровень 1 [1]|  
|**SQLSetStmtAttr**|Ядро [2]|  
|**SQLSpecialColumns**|Ядро [1]|  
|**SQLStatistics**|Ядро|  
|**SQLTablePrivileges**|Уровень 2|  
|**SQLTables**|Ядро|  
  
 [1] существенные функции этой функции доступны только при более высоком уровне соответствия.  
  
 [2] Установка некоторых атрибутов в значения, не используемые по умолчанию, зависит от уровня соответствия. Дополнительные сведения см. в следующем разделе — [соответствие атрибутов](../../../odbc/reference/develop-app/attribute-conformance.md).
