---
title: "Сопоставление SQLGetConnectOption | Документы Microsoft"
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
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: faf67d9649911122b0b3fc19905c50e94af684ab
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetconnectoption-mapping"></a>Сопоставление SQLGetConnectOption
Если приложение вызывает **SQLGetConnectOption** через ODBC 3*.x* драйвера, вызов  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 сопоставлено следующим образом:  
  
-   Если *fOption* указывает параметр подключения, определенных для ODBC, который возвращает строку, диспетчер драйверов вызывает  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *fOption* указывает параметр подключения, определенных для ODBC, который возвращает значение 32-разрядное целое число, диспетчер драйверов вызывает  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *fOption* указывает параметр инструкции, определяемым драйвером, диспетчер драйверов вызывает  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В предыдущем трех случаях *ConnectionHandle* аргументу присвоено значение в *hdbc*, *атрибута* аргументу присвоено значение в *fOption* и *ValuePtr* аргумент имеет значение совпадает со значением *pvParam*.  
  
 Для параметров соединения строкой, определяемой ODBC задает диспетчер драйверов *BufferLength* аргумента в вызове **SQLGetConnectAttr** в стандартных максимальную длину (SQL_MAX_OPTION_STRING_LENGTH); параметра соединения нестроковые *BufferLength* имеет значение 0.  
  
 Для ODBC 3*.x* драйвера, диспетчер драйверов больше не проверяет *параметр* — между SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX или больше, чем SQL_CONNECT_OPT_DRVR_START. Драйвер должен проверять допустимость значений параметров.
