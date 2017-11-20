---
title: "Сопоставление SQLGetStmtOption | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 503af3ea0dbac61cee506b932f79eccab5dedcf8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetstmtoption-mapping"></a>Сопоставление SQLGetStmtOption
Если приложение вызывает **SQLGetStmtOption** ODBC 3*.x* драйвер, который не поддерживает это вызов метода  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 приведет к следующим образом:  
  
-   Если *fOption* указывает параметр инструкции, определенных для ODBC, который возвращает строку, диспетчер драйверов вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *fOption* указывает параметр инструкции, определенных для ODBC, который возвращает значение 32-разрядное целое число, диспетчер драйверов вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *fOption* указывает параметр инструкции, определяемым драйвером, диспетчер драйверов вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В предыдущем трех случаях *StatementHandle* аргументу присвоено значение в *hstmt*, *атрибута* аргументу присвоено значение в *fOption* и *ValuePtr* аргумент имеет значение совпадает со значением *pvParam*.  
  
 Для параметров соединения строкой, определяемой ODBC задает диспетчер драйверов *BufferLength* аргумента в вызове **SQLGetConnectAttr** в стандартных максимальную длину (SQL_MAX_OPTION_STRING_LENGTH); параметра соединения нестроковые *BufferLength* имеет значение 0.  
  
 Параметр инструкции SQL_GET_BOOKMARK рекомендуется к использованию в ODBC 3*.x*. Для ODBC 3*.x* драйвер для работы с ODBC 2. *x* приложений, использующих SQL_GET_BOOKMARK, он должен поддерживать SQL_GET_BOOKMARK. Для ODBC 3*.x* драйвер для работы с ODBC 2. *x* приложений, он должен поддерживать значение SQL_USE_BOOKMARKS SQL_UB_ON и должны предоставлять закладки фиксированной длины. Если ODBC 3*.x* драйвер поддерживает только закладки переменной длины, но закладки не фиксированной длины, она должна вернуть SQLSTATE HYC00 (дополнительная возможность не реализована) Если ODBC 2. *x* приложения пытается установить SQL_USE_BOOKMARKS для SQL_UB_ON.  
  
 Для ODBC 3*.x* драйвера, диспетчер драйверов больше не проверяет, является ли *параметр* — между SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX или больше, чем SQL_CONNECT_OPT_DRVR_START. Драйвер должен установите этот флажок.

