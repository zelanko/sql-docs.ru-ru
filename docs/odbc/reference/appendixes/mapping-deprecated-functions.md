---
title: Сопоставление устаревших функций | Документация Майкрософт
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
ms.openlocfilehash: 307f0f54434fdcb4ebb19c38256a7a04f4a5c46d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990710"
---
# <a name="mapping-deprecated-functions"></a>Сопоставление нерекомендуемых функций
В этом разделе описывается, как устаревшие функции сопоставляются диспетчером драйверов ODBC *3. x* для обеспечения обратной СОВМЕСТИМОСТИ драйверов ODBC *3. x* , используемых с приложениями ODBC *2. x* . Диспетчер драйверов выполняет это сопоставление независимо от версии приложения. Поскольку каждая из функций ODBC *2. x* в следующем списке сопоставляется с соответствующей функцией ODBC *3. x* при вызове в драйвере ODBC *3. x* , драйверу ODBC *3. x* не требуется реализовывать функции ODBC *2. x* .  
  
 Сопоставление в списке активируется, если драйвер является драйвером ODBC *3. x* , а драйвер не поддерживает сопоставляемую функцию.  
  
 В следующей таблице перечислены все повторные функциональные возможности, появившиеся в ODBC *3. x*.  
  
|Функция ODBC *2. x*|ODBC *3. x,* функция|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**Функцию SQLAllocHandle**|  
|**SQLAllocEnv**|**Функцию SQLAllocHandle**|  
|**SQLAllocStmt**|**Функцию SQLAllocHandle**|  
|**Склбиндпарам**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**Функции SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** с *возможностью* SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**склсетскроллоптион**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] Несмотря на то, что эта функция не существовала в ODBC *2. x*, она имеет стандарты Open Group и ISO.  
  
 [2] это функция ODBC 1,0.  
  
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
  
-   [Сопоставление SQLGetConnectOption](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [Сопоставление SQLGetStmtOption](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [Сопоставление SQLInstallTranslator](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [Сопоставление SQLParamOptions](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [Сопоставление SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [Сопоставление SQLSetParam](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [Сопоставление SQLSetScrollOptions](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [Сопоставление SQLSetStmtOption](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [Сопоставление SQLTransact](../../../odbc/reference/appendixes/sqltransact-mapping.md)
