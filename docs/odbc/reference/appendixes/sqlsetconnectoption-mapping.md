---
title: "Сопоставление SQLSetConnectOption | Документы Microsoft"
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
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e531888390bbe4f625d308ad983059634e84ba2b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-mapping"></a>Сопоставление SQLSetConnectOption
Когда ODBC 2. *x* приложение вызывает **SQLSetConnectOption** через ODBC 3*.x* драйвера, вызов  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 приведет к следующим образом:  
  
-   Если *fOption* указывает атрибут соединения, определенных для ODBC, необходима строка, диспетчер драйверов вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *fOption* указывает атрибут соединения, определенных для ODBC, возвращающее значение 32-разрядное целое число, диспетчер драйверов вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Если *fOption* указывает атрибут соединения, определяемым драйвером, диспетчер драйверов вызывает  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 В предыдущем трех случаях *ConnectionHandle* аргументу присвоено значение в *hdbc*, *атрибута* аргументу присвоено значение в *fOption* и *ValuePtr* аргумент имеет значение совпадает со значением *vParam*.  
  
 Поскольку диспетчер драйверов не знает, определяемым драйвером соединения атрибут, который должен быть строка или 32-разрядное целое значение, он должен передать в допустимое значение для *BufferLength* аргумент **SQLSetConnectAttr**. Если драйвер определяет специальную семантику для определенных драйвером подключения атрибуты и должен быть вызван с помощью **SQLSetConnectOption**, он должен поддерживать **SQLSetConnectOption**.  
  
 Если ODBC 2. *x* приложение вызывает **SQLSetConnectOption** задание параметра инструкции драйвера в ODBC 3*.x* драйвер и параметр был определен в ODBC 2. *x* версии драйвера, новая константа манифеста должен быть определен для параметра в ODBC 3*.x* драйвера. При использовании старых константы манифеста в вызове **SQLSetConnectOption**, диспетчер драйверов вызывает **SQLSetConnectAttr** с **StringLength** аргумент присвоено значение 0.  
  
 Для ODBC 3*.x* драйвера, диспетчер драйверов больше не проверяет *fOption* — между SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX или больше, чем SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Установка параметров инструкции на уровне соединения  
 В ODBC 2. *x*, приложение может вызвать **SQLSetConnectOption** задание параметра инструкции. После этого драйвер устанавливает параметр инструкции по умолчанию для инструкций позже, выделенных для этого подключения. Драйвер определяется ли драйвер задает параметр инструкции для любой существующей операторы, связанные с заданным подключением.  
  
 Эта возможность рекомендуется к использованию в ODBC 3*.x*. ODBC 3*.x* драйверы должен поддерживать только параметр ODBC 2. *x* атрибуты инструкции на уровне соединения, если для работы с ODBC 2. *x* приложений, которые. ODBC 3*.x* приложения никогда не следует устанавливать атрибуты инструкции на уровне соединения. ODBC 3*.x* на уровне соединения, за исключением SQL_ATTR_METADATA_ID и атрибуту SQL_ATTR_ASYNC_ENABLE атрибуты, которые атрибуты соединения и атрибуты инструкции и может быть невозможно задать атрибуты инструкции Задайте на уровне соединения или на уровне инструкции.

