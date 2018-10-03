---
title: Сопоставление SQLGetStmtOption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2423d41b1e9c549b7202a68fb2a0e085e0a6e11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786608"
---
# <a name="sqlgetstmtoption-mapping"></a>Сопоставление SQLGetStmtOption
Если приложение вызывает **SQLGetStmtOption** ODBC 3 *.x* драйвер, который не поддерживает это, вызов  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 приведет к следующим образом:  
  
-   Если *fOption* указывает параметр инструкции, определенных для ODBC, который возвращает строку, вызовы диспетчера драйверов  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *fOption* указывает параметр инструкции, определенных для ODBC, который возвращает значение 32-разрядное целое число, вызовы диспетчера драйверов  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *fOption* указывает параметр инструкции, определяемым драйвером, вызовы диспетчера драйверов  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В указанных выше трех случаях *StatementHandle* аргумент присвоено значение в *hstmt*, *атрибут* аргумент присвоено значение в *fOption* и *ValuePtr* аргумент имеет значение совпадает со значением *pvParam*.  
  
 Для параметров соединения ODBC, определяемое, устанавливает диспетчер драйверов *BufferLength* аргумента в вызове **SQLGetConnectAttr** предопределенные максимальной длины (SQL_MAX_OPTION_STRING_LENGTH); параметра подключения нестроковые *BufferLength* имеет значение 0.  
  
 Параметр инструкции SQL_GET_BOOKMARK был объявлен устаревшим в ODBC 3 *.x*. Для ODBC 3 *.x* драйвера для работы с ODBC 2. *x* приложений, использующих SQL_GET_BOOKMARK, он должен поддерживать SQL_GET_BOOKMARK. Для ODBC 3 *.x* драйвера для работы с ODBC 2. *x* приложений, он должен поддерживать значение SQL_USE_BOOKMARKS SQL_UB_ON и должны предоставлять закладки фиксированной длины. Если ODBC 3 *.x* драйвер поддерживает только закладки переменной длины, но не закладки фиксированной длины, оно должно возвращать SQLSTATE HYC00 (дополнительная возможность не реализована) Если ODBC 2. *x* приложение пытается присвоить SQL_USE_BOOKMARKS SQL_UB_ON.  
  
 Для ODBC 3 *.x* драйвера, диспетчер драйверов не проверяет ли *параметр* символах SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX — или больше, чем SQL_CONNECT_OPT_DRVR_START. Драйвер необходимо проверить это.
