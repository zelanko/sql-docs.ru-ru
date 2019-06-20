---
title: Сопоставление SQLSetStmtOption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad53ba3fa02107d4902c43084beadda7a420e586
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735305"
---
# <a name="sqlsetstmtoption-mapping"></a>Сопоставление SQLSetStmtOption
Если приложение вызывает **SQLSetStmtOption** через ODBC 3 *.x* драйвера, вызов метода  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 приведет к следующим образом:  
  
-   Если *fOption* указывает атрибут инструкции, определенных для ODBC, который представляет собой строку, диспетчер драйверов вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *fOption* указывает атрибут инструкции, определенных для ODBC, возвращает значение 32-разрядное целое число, вызовы диспетчера драйверов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Если *fOption* указывает атрибут инструкции, определяемым драйвером, вызовы диспетчера драйверов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 В указанных выше трех случаях **StatementHandle** аргумент присвоено значение в *hstmt*, *атрибут* аргумент присвоено значение в *fOption* и *ValuePtr* аргумент присвоено значение в виде *vParam*.  
  
 Поскольку диспетчер драйверов не знает, должен ли атрибут инструкции, определяемым драйвером, строка или значение 32-разрядное целое число, он должен передать в допустимое значение для *StringLength* аргумент **SQLSetStmtAttr**. Если драйвер определила особой семантики для атрибуты инструкции, определяемым драйвером и должен вызываться с помощью **SQLSetStmtOption**, он должен поддерживать **SQLSetStmtOption**.  
  
 Если приложение вызывает **SQLSetStmtOption** Установка параметра инструкции специфические для драйвера в ODBC 3 *.x* драйвера и параметра был определен в ODBC 2. *x* версию драйвера, новая константа манифеста должен быть определен параметр в ODBC 3 *.x* драйвера. Если старый константа манифеста используется в вызове **SQLSetStmtOption**, диспетчер драйверов вызывает **SQLSetStmtAttr** с *StringLength* аргумент присвоено значение 0.  
  
 Если приложение вызывает **SQLSetStmtAttr** присвоить SQL_ATTR_USE_BOOKMARKS SQL_UB_ON в ODBC 3 *.x* драйвера, атрибут инструкции SQL_ATTR_USE_BOOKMARKS устанавливается SQL_UB_FIXED. SQL_UB_ON является той же константы как SQL_UB_FIXED. Диспетчер драйверов передает SQL_UB_FIXED через драйвер. SQL_UB_FIXED был объявлен устаревшим в ODBC 3 *.x*, но ODBC 3 *.x* драйвер должен реализовать его для работы с ODBC 2. *x* приложений, использующих закладки фиксированной длины.  
  
 Для ODBC 3 *.x* драйвера, диспетчер драйверов не проверяет *параметр* символах SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX — или больше, чем SQL_CONNECT_OPT_DRVR_START.
