---
title: Сопоставление нерекомендуемых функций | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b59d2604dd9d4b7c3166027c1917dea096b331d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818376"
---
# <a name="mapping-deprecated-functions"></a>Сопоставление нерекомендуемых функций
В этом разделе описывается, как устаревшие функции сопоставляются по ODBC 3 *.x* диспетчера драйверов для обеспечения обратной совместимости ODBC 3 *.x* драйверы, которые используются с ODBC 2. *x* приложений. Диспетчер драйверов выполняет это сопоставление, независимо от версии приложения. Так как каждый из ODBC 2. *x* функции в следующем списке сопоставляется с соответствующей ODBC 3 *.x* функции при вызове в ODBC 3 *.x* драйвера ODBC 3 *.x*драйвер должен реализовывать ODBC 2. *x* функции.  
  
 Сопоставление в списке активируется в том случае, когда драйвер ODBC 3 *.x* драйвер и драйвер не поддерживает функцию, с которым выполняется сопоставление.  
  
 В следующей таблице перечислены все повторяющиеся функциональность, которая была введена в ODBC 3 *.x*.  
  
|ODBC 2. *x* функции|ODBC 3 *.x* функции|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** с *параметр* из SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**SQLSetScrollOption**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] несмотря на то что эта функция не существует в ODBC 2 *.x*, он находится в стандартах Open Group и ISO.  
  
 [2] это функция ODBC 1.0.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставление SQLAllocConnect](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [Сопоставление SQLAllocEnv](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [Сопоставление SQLAllocStmt](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [Сопоставление SQLBindParam](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [Сопоставление SQLColAttributes](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [Сопоставление SQLError](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [Сопоставление SQLFreeConnect](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [Сопоставление SQLFreeEnv](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [Сопоставление SQLFreeStmt](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [Функция SQLGetConnectOption](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [Сопоставление SQLGetStmtOption](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [Сопоставление SQLInstallTranslator](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [Сопоставление SQLParamOptions](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [Сопоставление SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [Сопоставление SQLSetParam](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [Сопоставление SQLSetScrollOptions](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [Сопоставление SQLSetStmtOption](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [Сопоставление SQLTransact](../../../odbc/reference/appendixes/sqltransact-mapping.md)
