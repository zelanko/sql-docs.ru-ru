---
description: Соответствие функции
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
ms.openlocfilehash: 2ff61c62b18f531eaad7cc822f99c7065fcba129
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465796"
---
# <a name="function-conformance"></a>Соответствие функции
В следующей таблице указан уровень соответствия для каждой функции ODBC, где это хорошо определено.  
  
|Функция|Уровень согласованности|  
|--------------|-----------------------|  
|**Функцию SQLAllocHandle**|Основные сведения|  
|**SQLBindCol**|Основные сведения|  
|**SQLBindParameter**|Ядро [1]|  
|**SQLBrowseConnect**|уровне 1|  
|**SQLBulkOperations**|уровне 1|  
|**SQLCancel**|Ядро [1]|  
|**SQLCloseCursor**|Основные сведения|  
|**SQLColAttribute**|Ядро [1]|  
|**SQLColumnPrivileges**|Уровень 2|  
|**SQLColumns**|Основные сведения|  
|**SQLConnect**|Основные сведения|  
|**склкопидеск**|Основные сведения|  
|**SQLDataSources**|Основные сведения|  
|**SQLDescribeCol**|Ядро [1]|  
|**SQLDescribeParam**|Уровень 2|  
|**SQLDisconnect**|Основные сведения|  
|**SQLDriverConnect**|Основные сведения|  
|**SQLDrivers**|Основные сведения|  
|**SQLEndTran**|Ядро [1]|  
|**SQLExecDirect**|Основные сведения|  
|**SQLExecute**|Основные сведения|  
|**SQLFetch**|Основные сведения|  
|**SQLFetchScroll**|Ядро [1]|  
|**SQLForeignKeys**|Уровень 2|  
|**SQLFreeHandle**|Основные сведения|  
|**Функция SQLFreeStmt**|Основные сведения|  
|**SQLGetConnectAttr**|Основные сведения|  
|**SQLGetCursorName**|Основные сведения|  
|**SQLGetData**|Основные сведения|  
|**SQLGetDescField**|Основные сведения|  
|**SQLGetDescRec**|Основные сведения|  
|**SQLGetDiagField**|Основные сведения|  
|**Функции SQLGetDiagRec**|Основные сведения|  
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
|**SQLSetConnectAttr**|Ядро [2]|  
|**SQLSetCursorName**|Основные сведения|  
|**SQLSetDescField**|Ядро [1]|  
|**SQLSetDescRec**|Основные сведения|  
|**SQLSetEnvAttr**|Ядро [2]|  
|**функция SQLSetPos;**|Уровень 1 [1]|  
|**SQLSetStmtAttr**|Ядро [2]|  
|**SQLSpecialColumns**|Ядро [1]|  
|**SQLStatistics**|Основные сведения|  
|**SQLTablePrivileges**|Уровень 2|  
|**SQLTables**|Основные сведения|  
  
 [1] существенные функции этой функции доступны только при более высоком уровне соответствия.  
  
 [2] Установка некоторых атрибутов в значения, не используемые по умолчанию, зависит от уровня соответствия. Дополнительные сведения см. в следующем разделе — [соответствие атрибутов](../../../odbc/reference/develop-app/attribute-conformance.md).
