---
title: Функциональное соответствие Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305595"
---
# <a name="function-conformance"></a>Соответствие функции
В следующей таблице указывается уровень соответствия каждой функции ODBC, где это четко определено.  
  
|Компонент|Уровень согласованности|  
|--------------|-----------------------|  
|**СЗЛАллокХэндл**|Основные сведения|  
|**SQLBindCol**|Основные сведения|  
|**SQLBindParameter**|Ядро|  
|**SQLBrowseConnect**|уровне 1|  
|**СЗЛБалКОперации**|уровне 1|  
|**SQLCancel**|Ядро|  
|**SQLCloseCursor**|Основные сведения|  
|**SQLColAttribute**|Ядро|  
|**SQLColumnPrivileges**|Уровень 2|  
|**SQLColumns**|Основные сведения|  
|**SQLConnect**|Основные сведения|  
|**СЗЛКопиДеск**|Основные сведения|  
|**Источники данных S'LData**|Основные сведения|  
|**SQLDescribeCol**|Ядро|  
|**SQLDescribeParam**|Уровень 2|  
|**СЗЛДИСКоннект**|Основные сведения|  
|**SQLDriverConnect**|Основные сведения|  
|**SQLDrivers**|Основные сведения|  
|**SQLEndTran**|Ядро|  
|**SQLExecDirect**|Основные сведения|  
|**SQLExecute**|Основные сведения|  
|**SQLFetch**|Основные сведения|  
|**SQLFetchScroll**|Ядро|  
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
|**СЗЛГетЕнвТтр**|Основные сведения|  
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
|**SQLSetConnectAttr**|Ядро|  
|**СЗЛСетКурсОрНамейм**|Основные сведения|  
|**SQLSetDescField**|Ядро|  
|**SQLSetDescRec**|Основные сведения|  
|**SQLSetEnvAttr**|Ядро|  
|**функция SQLSetPos;**|Уровень 1|  
|**SQLSetStmtAttr**|Ядро|  
|**SQLSpecialColumns**|Ядро|  
|**SQLStatistics**|Основные сведения|  
|**SQLTablePrivileges**|Уровень 2|  
|**SQLTables**|Основные сведения|  
  
 Значительные функции этой функции доступны только на более высоких уровнях соответствия.  
  
 Установка определенных атрибутов на значения недефолтного значения зависит от уровня соответствия. Для получения дополнительной информации смотрите следующий [раздел, Атрибут соответствия](../../../odbc/reference/develop-app/attribute-conformance.md).
