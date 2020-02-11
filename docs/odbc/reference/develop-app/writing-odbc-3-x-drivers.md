---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb403cef47f901cdb43bbb32c669ba68aa34913d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078898"
---
# <a name="writing-odbc-3x-drivers"></a>Написание драйверов ODBC 3.x
В следующей таблице показана поддержка функций в ODBC 3. драйвер *x* и приложение ODBC, а также сопоставление, выполняемое диспетчером драйверов при вызове функций для ODBC 3. драйвер *x* .  
  
|Компонент|Поддерживается<br /><br /> с помощью<br /><br /> ODBC 3. *x*<br /><br /> аудиодрайвера?|Поддерживается<br /><br /> с помощью<br /><br /> ODBC 3. *x*<br /><br /> приклад?|Сопоставлено/поддерживается<br /><br /> по ODBC 3. *x*<br /><br /> Диспетчер драйверов для<br /><br /> ODBC 3. драйвер *x* ?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|нет|Нет [1]|Да|  
|**SQLAllocEnv**|нет|Нет [1]|Да|  
|**Функцию SQLAllocHandle**|Да|Да|нет|  
|**SQLAllocStmt**|нет|Нет [1]|Да|  
|**SQLBindCol**|Да|Да|нет|  
|**склбиндпарам**|нет|Да [2]|Да|  
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
|**склкопидеск**|Да|Да|Да [4]|  
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
|**Функция SQLFreeStmt**|Да|Да|нет|  
|**SQLGetConnectAttr**|Да|Да|нет|  
|**SQLGetConnectOption**|Нет [5]|Нет [1]|Да|  
|**SQLGetCursorName**|Да|Да|нет|  
|**SQLGetData**|Да|Да|нет|  
|**SQLGetDescField**|Да|Да|нет|  
|**SQLGetDescRec**|Да|Да|нет|  
|**SQLGetDiagField**|Да|Да|нет|  
|**Функции SQLGetDiagRec**|Да|Да|нет|  
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
|**функция SQLSetPos;**|Да|Да|нет|  
|**SQLSetParam**|нет|нет|Да|  
|**склсетскроллоптион**|Да|Да|нет|  
|**SQLSetStmtAttr**|Да|Да|нет|  
|**SQLSetStmtOption**|Нет [5]|Нет [1]|Да|  
|**SQLSpecialColumns**|Да|Да|нет|  
|**SQLStatistics**|Да|Да|нет|  
|**SQLTablePrivileges**|Да|Да|нет|  
|**SQLTables**|Да|Да|нет|  
|**SQLTransact**|нет|Нет [1]|Да|  
  
 [1] Эта функция является устаревшей в ODBC 3. *x*. ODBC 3. приложения *x* не должны использовать эту функцию. Однако можно вызвать эту функцию с помощью открытой группы или приложения, совместимого с CLI ISO.  
  
 [2] ODBC 3. приложения *x* должны использовать **SQLBindParameter** вместо **склбиндпарам**. Однако можно вызвать эту функцию с помощью открытой группы или приложения, совместимого с CLI ISO.  
  
 [3] модули записи драйверов должны заметить, что ODBC 2. атрибуты столбца *x* SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE и SQL_COLUMN_LENGTH должны поддерживаться с помощью **SQLColAttribute**.  
  
 [4] **склкопидеск** частично реализуется диспетчером драйверов при копировании дескриптора между соединениями, относящимися к разным драйверам. Драйверы необходимы для поддержки **склкопидеск** в двух своих подключениях. Такие функции, как **SQLDrivers**, реализованные только диспетчером драйверов, не отображаются в этом списке.  
  
 [5] при определенных обстоятельствах может потребоваться поддержка этой функции драйверами. Дополнительные сведения см. на странице справки этой функции.  
  
 [6] Драйвер может поддерживать **SQLGetFunctions** , если набор функций, поддерживаемых драйвером, отличается от подключения к подключению.
