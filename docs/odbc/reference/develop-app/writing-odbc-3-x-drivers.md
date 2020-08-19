---
description: Написание драйверов ODBC 3.x
title: Создание драйверов ODBC 3. x | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c5fec9b94dbcf60868c44e49d92bddb4bb73e9cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421348"
---
# <a name="writing-odbc-3x-drivers"></a>Написание драйверов ODBC 3.x
В следующей таблице показана поддержка функций в ODBC 3. драйвер *x* и приложение ODBC, а также сопоставление, выполняемое диспетчером драйверов при вызове функций для ODBC 3. драйвер *x* .  
  
|Функция|Поддерживается<br /><br /> с помощью<br /><br /> ODBC 3. *x*<br /><br /> аудиодрайвера?|Поддерживается<br /><br /> с помощью<br /><br /> ODBC 3. *x*<br /><br /> приклад?|Сопоставлено/поддерживается<br /><br /> по ODBC 3. *x*<br /><br /> Диспетчер драйверов для<br /><br /> ODBC 3. драйвер *x* ?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|Нет|Нет [1]|Да|  
|**SQLAllocEnv**|Нет|Нет [1]|Да|  
|**Функцию SQLAllocHandle**|Да|Да|Нет|  
|**SQLAllocStmt**|Нет|Нет [1]|Да|  
|**SQLBindCol**|Да|Да|Нет|  
|**склбиндпарам**|Нет|Да [2]|Да|  
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
|**склкопидеск**|Да|Да|Да [4]|  
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
|**Функция SQLFreeStmt**|Да|Да|Нет|  
|**SQLGetConnectAttr**|Да|Да|Нет|  
|**SQLGetConnectOption**|Нет [5]|Нет [1]|Да|  
|**SQLGetCursorName**|Да|Да|Нет|  
|**SQLGetData**|Да|Да|Нет|  
|**SQLGetDescField**|Да|Да|Нет|  
|**SQLGetDescRec**|Да|Да|Нет|  
|**SQLGetDiagField**|Да|Да|Нет|  
|**Функции SQLGetDiagRec**|Да|Да|Нет|  
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
|**функция SQLSetPos;**|Да|Да|Нет|  
|**SQLSetParam**|Нет|Нет|Да|  
|**склсетскроллоптион**|Да|Да|Нет|  
|**SQLSetStmtAttr**|Да|Да|Нет|  
|**SQLSetStmtOption**|Нет [5]|Нет [1]|Да|  
|**SQLSpecialColumns**|Да|Да|Нет|  
|**SQLStatistics**|Да|Да|Нет|  
|**SQLTablePrivileges**|Да|Да|Нет|  
|**SQLTables**|Да|Да|Нет|  
|**SQLTransact**|Нет|Нет [1]|Да|  
  
 [1] Эта функция является устаревшей в ODBC 3. *x*. ODBC 3. приложения *x* не должны использовать эту функцию. Однако можно вызвать эту функцию с помощью открытой группы или приложения, совместимого с CLI ISO.  
  
 [2] ODBC 3. приложения *x* должны использовать **SQLBindParameter** вместо **склбиндпарам**. Однако можно вызвать эту функцию с помощью открытой группы или приложения, совместимого с CLI ISO.  
  
 [3] модули записи драйверов должны заметить, что ODBC 2. атрибуты столбца *x* SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE и SQL_COLUMN_LENGTH должны поддерживаться с помощью **SQLColAttribute**.  
  
 [4]   **склкопидеск** частично реализуется диспетчером драйверов при копировании дескриптора между соединениями, относящимися к разным драйверам. Драйверы необходимы для поддержки **склкопидеск** в двух своих подключениях. Такие функции, как **SQLDrivers**, реализованные только диспетчером драйверов, не отображаются в этом списке.  
  
 [5] при определенных обстоятельствах может потребоваться поддержка этой функции драйверами. Дополнительные сведения см. на странице справки этой функции.  
  
 [6] Драйвер может поддерживать **SQLGetFunctions** , если набор функций, поддерживаемых драйвером, отличается от подключения к подключению.
