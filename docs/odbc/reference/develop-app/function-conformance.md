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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 45eb427b660496430334633b5d43ee8989211c0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069754"
---
# <a name="function-conformance"></a>Соответствие функции
В следующей таблице указан уровень соответствия для каждой функции ODBC, где это хорошо определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|**Функцию SQLAllocHandle**|Core|  
|**SQLBindCol**|Core|  
|**SQLBindParameter**|Ядро [1]|  
|**SQLBrowseConnect**|уровне 1|  
|**SQLBulkOperations**|уровне 1|  
|**SQLCancel**|Ядро [1]|  
|**SQLCloseCursor**|Core|  
|**SQLColAttribute**|Ядро [1]|  
|**SQLColumnPrivileges**|Уровень 2|  
|**SQLColumns**|Core|  
|**SQLConnect**|Core|  
|**склкопидеск**|Core|  
|**SQLDataSources**|Core|  
|**SQLDescribeCol**|Ядро [1]|  
|**SQLDescribeParam**|Уровень 2|  
|**SQLDisconnect**|Core|  
|**SQLDriverConnect**|Core|  
|**SQLDrivers**|Core|  
|**SQLEndTran**|Ядро [1]|  
|**SQLExecDirect**|Core|  
|**SQLExecute**|Core|  
|**SQLFetch**|Core|  
|**SQLFetchScroll**|Ядро [1]|  
|**SQLForeignKeys**|Уровень 2|  
|**SQLFreeHandle**|Core|  
|**Функция SQLFreeStmt**|Core|  
|**SQLGetConnectAttr**|Core|  
|**SQLGetCursorName**|Core|  
|**SQLGetData**|Core|  
|**SQLGetDescField**|Core|  
|**SQLGetDescRec**|Core|  
|**SQLGetDiagField**|Core|  
|**Функции SQLGetDiagRec**|Core|  
|**SQLGetEnvAttr**|Core|  
|**SQLGetFunctions**|Core|  
|**SQLGetInfo**|Core|  
|**SQLGetStmtAttr**|Core|  
|**SQLGetTypeInfo**|Core|  
|**SQLMoreResults**|уровне 1|  
|**SQLNativeSql**|Core|  
|**SQLNumParams**|Core|  
|**SQLNumResultCols**|Core|  
|**SQLParamData**|Core|  
|**SQLPrepare**|Core|  
|**SQLPrimaryKeys**|уровне 1|  
|**SQLProcedureColumns**|уровне 1|  
|**SQLProcedures**|уровне 1|  
|**SQLPutData**|Core|  
|**SQLRowCount**|Core|  
|**SQLSetConnectAttr**|Ядро [2]|  
|**SQLSetCursorName**|Core|  
|**SQLSetDescField**|Ядро [1]|  
|**SQLSetDescRec**|Core|  
|**SQLSetEnvAttr**|Ядро [2]|  
|**функция SQLSetPos;**|Уровень 1 [1]|  
|**SQLSetStmtAttr**|Ядро [2]|  
|**SQLSpecialColumns**|Ядро [1]|  
|**SQLStatistics**|Core|  
|**SQLTablePrivileges**|Уровень 2|  
|**SQLTables**|Core|  
  
 [1] существенные функции этой функции доступны только при более высоком уровне соответствия.  
  
 [2] Установка некоторых атрибутов в значения, не используемые по умолчанию, зависит от уровня соответствия. Дополнительные сведения см. в следующем разделе — [соответствие атрибутов](../../../odbc/reference/develop-app/attribute-conformance.md).
