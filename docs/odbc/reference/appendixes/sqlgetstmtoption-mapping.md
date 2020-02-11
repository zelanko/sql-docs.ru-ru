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
ms.openlocfilehash: 2973455ff4ee7e8dc51b2cd07a6423c9b1c36346
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073815"
---
# <a name="sqlgetstmtoption-mapping"></a>Сопоставление SQLGetStmtOption
Когда приложение вызывает **SQLGetStmtOption** для драйвера ODBC *3. x* , который не поддерживает его, вызов метода  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 результат будет следующим:  
  
-   Если *параметром fOption* указывает параметр инструкции, определяемый ODBC, который возвращает строку, диспетчер драйверов вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *параметром fOption* указывает параметр инструкции ODBC, возвращающий значение 32-разрядного целого числа, диспетчер драйверов вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *параметром fOption* указывает параметр инструкции, определяемый драйвером, диспетчер драйверов вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В предыдущих трех случаях аргументу *статеменсандле* присваивается значение в *хстмт*, аргументу *атрибута* присваивается значение в *параметром fOption*, а аргументу *ValuePtr* присваивается то же значение, что и *пвпарам*.  
  
 Для параметров соединения, определенных ODBC, диспетчер драйверов устанавливает аргумент *BufferLength* в вызове **SQLGetConnectAttr** до предопределенной максимальной длины (SQL_MAX_OPTION_STRING_LENGTH); для параметра соединения, не предназначенного для строки, *BufferLength* имеет значение 0.  
  
 Параметр инструкции SQL_GET_BOOKMARK является устаревшим в ODBC *3. x*. Для работы драйвера ODBC *3. x* с приложениями ODBC *2. x* , использующими SQL_GET_BOOKMARK, он должен поддерживать SQL_GET_BOOKMARK. Чтобы драйвер ODBC *3. x* работал с приложениями ODBC *2. x* , он должен поддерживать настройку SQL_USE_BOOKMARKS для SQL_UB_ON и предоставлять закладки фиксированной длины. Если драйвер ODBC *3. x* поддерживает только закладки с переменной длиной, а не только закладки с фиксированной длиной, он должен возвращать значение SQLSTATE HYC00 (дополнительная функция не реализована), если приложение ODBC *2. x* пытается установить SQL_USE_BOOKMARKS SQL_UB_ON.  
  
 Для драйвера ODBC *3. x* диспетчер драйверов больше не проверяет, находится ли *параметр* между SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX или больше SQL_CONNECT_OPT_DRVR_START. Драйвер должен проверить это.
