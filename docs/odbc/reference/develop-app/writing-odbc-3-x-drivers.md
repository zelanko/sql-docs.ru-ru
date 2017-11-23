---
title: "Написание драйверы ODBC 3.x | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
ms.openlocfilehash: 5ea639a8bde008d657cff558183220d7e68fe568
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="writing-odbc-3x-drivers"></a>Написание ODBC 3.x драйверы
В следующей таблице показаны функции поддержки в ODBC 3. *x* драйвер и приложение ODBC и сопоставления, предпринятые диспетчером драйверов при вызове функций для ODBC 3. *x* драйвера.  
  
|Функция|Поддерживается<br /><br /> по<br /><br /> ODBC 3. *x*<br /><br /> драйвер?|Поддерживается<br /><br /> по<br /><br /> ODBC 3. *x*<br /><br /> приложения?|Сопоставленный поддерживается<br /><br /> в ODBC 3. *x*<br /><br /> Диспетчер драйверов для<br /><br /> ODBC 3. *x* драйвер?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|Нет|Нет [1]|Да|  
|**SQLAllocEnv**|Нет|Нет [1]|Да|  
|**SQLAllocHandle**|Да|Да|Нет|  
|**SQLAllocStmt**|Нет|Нет [1]|Да|  
|**SQLBindCol**|Да|Да|Нет|  
|**SQLBindParam**|Нет|Да [2]|Да|  
|**SQLBindParameter**|Да|Да|Нет|  
|**SQLBrowseConnect**|Да|Да|Нет|  
|**SQLBulkOperations**|Да|Да|Нет|  
|**SQLCancel**|Да|Да|Нет|  
|**SQLCloseCursor**|Да|Да|Нет|  
|**SQLColAttribute**|Да|Да|Нет|  
|**SQLColAttributes**|Нет [3]|Нет|Да|  
|**SQLColumnPrivileges**|Да|Да|Нет|  
|**SQLColumns**|Да|Да|Нет|  
|**SQLConnect**|Да|Да|Нет|  
|**SQLCopyDesc**|Да|Да|Да [4]|  
|**SQLDataSources**|Нет|Да|Да|  
|**SQLDescribeCol**|Да|Да|Нет|  
|**SQLDescribeParam**|Да|Да|Нет|  
|**SQLDisconnect**|Да|Да|Нет|  
|**SQLDriverConnect**|Да|Да|Нет|  
|**SQLDrivers**|Нет|Да|Да|  
|**SQLEndTran**|Да|Да|Нет|  
|**SQLError**|Нет|Нет [1]|Да|  
|**SQLExecDirect**|Да|Да|Нет|  
|**SQLExecute**|Да|Да|Нет|  
|**SQLExtendedFetch**|Да|Нет|Нет|  
|**SQLFetch**|Да|Да|Нет|  
|**SQLFetchScroll**|Да|Да|Нет|  
|**SQLForeignKeys**|Да|Да|Нет|  
|**SQLFreeConnect**|Нет|Да [1]|Да|  
|**SQLFreeEnv**|Нет|Да [1]|Да|  
|**SQLFreeHandle**|Да|Да|Нет|  
|**SQLFreeStmt**|Да|Да|Нет|  
|**SQLGetConnectAttr**|Да|Да|Нет|  
|**SQLGetConnectOption**|Нет [5]|Нет [1]|Да|  
|**SQLGetCursorName**|Да|Да|Нет|  
|**SQLGetData**|Да|Да|Нет|  
|**SQLGetDescField**|Да|Да|Нет|  
|**SQLGetDescRec**|Да|Да|Нет|  
|**SQLGetDiagField**|Да|Да|Нет|  
|**SQLGetDiagRec**|Да|Да|Нет|  
|**SQLGetEnvAttr**|Да|Да|Нет|  
|**SQLGetFunctions**|Нет [6]|Да|Да|  
|**SQLGetInfo**|Да|Да|Нет|  
|**SQLGetStmtAttr**|Да|Да|Нет|  
|**SQLGetStmtOption**|Нет [5]|Нет [1]|Да|  
|**SQLGetTypeInfo**|Да|Да|Нет|  
|**SQLMoreResults**|Да|Да|Нет|  
|**SQLNativeSql**|Да|Да|Нет|  
|**SQLNumParams**|Да|Да|Нет|  
|**SQLNumResultCols**|Да|Да|Нет|  
|**SQLParamData**|Да|Да|Нет|  
|**SQLParamOptions**|Нет|Нет|Да|  
|**SQLPrepare**|Да|Да|Нет|  
|**SQLPrimaryKeys**|Да|Да|Нет|  
|**SQLProcedureColumns**|Да|Да|Нет|  
|**SQLProcedures**|Да|Да|Нет|  
|**SQLPutData**|Да|Да|Нет|  
|**SQLRowCount**|Да|Да|Нет|  
|**SQLSetConnectAttr**|Да|Да|Нет|  
|**SQLSetConnectOption**|Нет [5]|Нет [1]|Да|  
|**SQLSetCursorName**|Да|Да|Нет|  
|**SQLSetDescField**|Да|Да|Нет|  
|**SQLSetDescRec**|Да|Да|Нет|  
|**SQLSetEnvAttr**|Да|Да|Нет|  
|**SQLSetPos**|Да|Да|Нет|  
|**SQLSetParam**|Нет|Нет|Да|  
|**SQLSetScrollOption**|Да|Да|Нет|  
|**SQLSetStmtAttr**|Да|Да|Нет|  
|**SQLSetStmtOption**|Нет [5]|Нет [1]|Да|  
|**SQLSpecialColumns**|Да|Да|Нет|  
|**SQLStatistics**|Да|Да|Нет|  
|**SQLTablePrivileges**|Да|Да|Нет|  
|**SQLTables**|Да|Да|Нет|  
|**SQLTransact**|Нет|Нет [1]|Да|  
  
 [1] Эта функция устарела в ODBC 3. *x*. ODBC 3. *x* приложения не должны использовать эту функцию. Однако на Open Group или приложение, совместимое с ISO CLI можно вызвать эту функцию.  
  
 [2] ODBC 3. *x* приложения должны использовать **SQLBindParameter** вместо **SQLBindParam**. Однако на Open Group или приложение, совместимое с ISO CLI можно вызвать эту функцию.  
  
 [3] записи драйвер следует отметить, что ODBC 2. *x* SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE и SQL_COLUMN_LENGTH должен обеспечивать поддержку и атрибуты столбцов **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** частично реализуется диспетчером драйверов, когда дескриптор копируется по подключениям, принадлежащих различными драйверами. Необходимые драйверы для поддержки **SQLCopyDesc** в двух собственные подключения. Функции, такие как **SQLDrivers**, реализованные исключительно диспетчером драйверов, не отображаются в этом списке.  
  
 [5] при определенных обстоятельствах драйверы должны поддерживать эту функцию. Дополнительные сведения см. в разделе справочной странице этой функции.  
  
 [6] можно выбрать поддержку драйвер **SQLGetFunctions** Если набор функций, поддерживаемых драйвером зависит от подключения для соединения.
