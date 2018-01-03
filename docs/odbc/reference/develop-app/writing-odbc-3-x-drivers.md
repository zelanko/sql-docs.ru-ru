---
title: "Написание драйверы ODBC 3.x | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b73a32d607bb2fc2c1cd2392ab4d1b436e7ed94d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="writing-odbc-3x-drivers"></a>Написание ODBC 3.x драйверы
В следующей таблице показаны функции поддержки в ODBC 3. *x* драйвер и приложение ODBC и сопоставления, предпринятые диспетчером драйверов при вызове функций для ODBC 3. *x* драйвера.  
  
|Компонент|Поддерживается<br /><br /> по<br /><br /> ODBC 3. *x*<br /><br /> драйвер?|Поддерживается<br /><br /> по<br /><br /> ODBC 3. *x*<br /><br /> приложения?|Сопоставленный поддерживается<br /><br /> в ODBC 3. *x*<br /><br /> Диспетчер драйверов для<br /><br /> ODBC 3. *x* драйвер?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|нет|Нет [1]|Да|  
|**SQLAllocEnv**|нет|Нет [1]|Да|  
|**SQLAllocHandle**|Да|Да|нет|  
|**SQLAllocStmt**|нет|Нет [1]|Да|  
|**SQLBindCol**|Да|Да|нет|  
|**SQLBindParam**|нет|Да [2]|Да|  
|**SQLBindParameter**|Да|Да|нет|  
|**SQLBrowseConnect**|Да|Да|нет|  
|**SQLBulkOperations**|Да|Да|нет|  
|**SQLCancel**|Да|Да|нет|  
|**SQLCloseCursor**|Да|Да|нет|  
|**SQLColAttribute**|Да|Да|нет|  
|**SQLColAttributes**|Нет [3]|нет|Да|  
|**SQLColumnPrivileges**|Да|Да|нет|  
|**SQLColumns**|Да|Да|нет|  
|**SQLConnect**|Да|Да|нет|  
|**SQLCopyDesc**|Да|Да|Да [4]|  
|**SQLDataSources**|нет|Да|Да|  
|**SQLDescribeCol**|Да|Да|нет|  
|**SQLDescribeParam**|Да|Да|нет|  
|**SQLDisconnect**|Да|Да|нет|  
|**SQLDriverConnect**|Да|Да|нет|  
|**SQLDrivers**|нет|Да|Да|  
|**SQLEndTran**|Да|Да|нет|  
|**SQLError**|нет|Нет [1]|Да|  
|**SQLExecDirect**|Да|Да|нет|  
|**SQLExecute**|Да|Да|нет|  
|**SQLExtendedFetch**|Да|нет|нет|  
|**SQLFetch**|Да|Да|нет|  
|**SQLFetchScroll**|Да|Да|нет|  
|**SQLForeignKeys**|Да|Да|нет|  
|**SQLFreeConnect**|нет|Да [1]|Да|  
|**SQLFreeEnv**|нет|Да [1]|Да|  
|**SQLFreeHandle**|Да|Да|нет|  
|**SQLFreeStmt**|Да|Да|нет|  
|**SQLGetConnectAttr**|Да|Да|нет|  
|**SQLGetConnectOption**|Нет [5]|Нет [1]|Да|  
|**SQLGetCursorName**|Да|Да|нет|  
|**SQLGetData**|Да|Да|нет|  
|**SQLGetDescField**|Да|Да|нет|  
|**SQLGetDescRec**|Да|Да|нет|  
|**SQLGetDiagField**|Да|Да|нет|  
|**SQLGetDiagRec**|Да|Да|нет|  
|**SQLGetEnvAttr**|Да|Да|нет|  
|**SQLGetFunctions**|Нет [6]|Да|Да|  
|**SQLGetInfo**|Да|Да|нет|  
|**SQLGetStmtAttr**|Да|Да|нет|  
|**SQLGetStmtOption**|Нет [5]|Нет [1]|Да|  
|**SQLGetTypeInfo**|Да|Да|нет|  
|**SQLMoreResults**|Да|Да|нет|  
|**SQLNativeSql**|Да|Да|нет|  
|**SQLNumParams**|Да|Да|нет|  
|**SQLNumResultCols**|Да|Да|нет|  
|**SQLParamData**|Да|Да|нет|  
|**SQLParamOptions**|нет|нет|Да|  
|**SQLPrepare**|Да|Да|нет|  
|**SQLPrimaryKeys**|Да|Да|нет|  
|**SQLProcedureColumns**|Да|Да|нет|  
|**SQLProcedures**|Да|Да|нет|  
|**SQLPutData**|Да|Да|нет|  
|**SQLRowCount**|Да|Да|нет|  
|**SQLSetConnectAttr**|Да|Да|нет|  
|**SQLSetConnectOption**|Нет [5]|Нет [1]|Да|  
|**SQLSetCursorName**|Да|Да|нет|  
|**SQLSetDescField**|Да|Да|нет|  
|**SQLSetDescRec**|Да|Да|нет|  
|**SQLSetEnvAttr**|Да|Да|нет|  
|**SQLSetPos**|Да|Да|нет|  
|**SQLSetParam**|нет|нет|Да|  
|**SQLSetScrollOption**|Да|Да|нет|  
|**SQLSetStmtAttr**|Да|Да|нет|  
|**SQLSetStmtOption**|Нет [5]|Нет [1]|Да|  
|**SQLSpecialColumns**|Да|Да|нет|  
|**SQLStatistics**|Да|Да|нет|  
|**SQLTablePrivileges**|Да|Да|нет|  
|**SQLTables**|Да|Да|нет|  
|**SQLTransact**|нет|Нет [1]|Да|  
  
 [1] Эта функция устарела в ODBC 3. *x*. ODBC 3. *x* приложения не должны использовать эту функцию. Однако на Open Group или приложение, совместимое с ISO CLI можно вызвать эту функцию.  
  
 [2] ODBC 3. *x* приложения должны использовать **SQLBindParameter** вместо **SQLBindParam**. Однако на Open Group или приложение, совместимое с ISO CLI можно вызвать эту функцию.  
  
 [3] записи драйвер следует отметить, что ODBC 2. *x* SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE и SQL_COLUMN_LENGTH должен обеспечивать поддержку и атрибуты столбцов **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** частично реализуется диспетчером драйверов, когда дескриптор копируется по подключениям, принадлежащих различными драйверами. Необходимые драйверы для поддержки **SQLCopyDesc** в двух собственные подключения. Функции, такие как **SQLDrivers**, реализованные исключительно диспетчером драйверов, не отображаются в этом списке.  
  
 [5] при определенных обстоятельствах драйверы должны поддерживать эту функцию. Дополнительные сведения см. в разделе справочной странице этой функции.  
  
 [6] можно выбрать поддержку драйвер **SQLGetFunctions** Если набор функций, поддерживаемых драйвером зависит от подключения для соединения.
