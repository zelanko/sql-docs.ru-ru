---
title: Сопоставление SQLSetConnectOption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b512a795c3b9e2d1c6aa1c7c9e92fbc42a8c7862
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125592"
---
# <a name="sqlsetconnectoption-mapping"></a>Сопоставление SQLSetConnectOption
Когда ODBC 2. *x* приложение вызывает **SQLSetConnectOption** через ODBC 3 *.x* драйвера, вызов метода  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 приведет к следующим образом:  
  
-   Если *fOption* указывает атрибут соединения, определенных для ODBC, необходима строка, вызовы диспетчера драйверов  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *fOption* указывает атрибут определяемые ODBC соединение, возвращающее значение 32-разрядное целое число, вызовы диспетчера драйверов  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Если *fOption* указывает атрибутом соединения, определяемым драйвером, вызовы диспетчера драйверов  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 В указанных выше трех случаях *ConnectionHandle* аргумент присвоено значение в *hdbc*, *атрибут* аргумент присвоено значение в *fOption* и *ValuePtr* аргумент имеет значение совпадает со значением *vParam*.  
  
 Поскольку диспетчер драйверов не знает, должен ли атрибут соединения, определяемым драйвером, строка или значение 32-разрядное целое число, он должен передать в допустимое значение для *BufferLength* аргумент **SQLSetConnectAttr**. Если драйвер имеет определенные особой семантики для определенное драйвером подключения атрибуты и должен вызываться с помощью **SQLSetConnectOption**, он должен поддерживать **SQLSetConnectOption**.  
  
 Если ODBC 2. *x* приложение вызывает **SQLSetConnectOption** Установка параметра инструкции специфические для драйвера в ODBC 3 *.x* драйвер и параметр был определен в ODBC 2. *x* версию драйвера, новая константа манифеста должен быть определен параметр в ODBC 3 *.x* драйвера. Если старый константа манифеста используется в вызове **SQLSetConnectOption**, диспетчер драйверов вызывает **SQLSetConnectAttr** с **StringLength** аргумент присвоено значение 0.  
  
 Для ODBC 3 *.x* драйвера, диспетчер драйверов не проверяет *fOption* символах SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX — или больше, чем SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Установка параметров инструкции на уровне соединения  
 В ODBC 2. *x*, приложение может вызвать **SQLSetConnectOption** для задания параметра инструкции. Когда это будет проделано, драйвер устанавливает параметр инструкции по умолчанию для любых операторов в более поздней версии, выделенных для этого подключения. Он является определяемым драйвером ли драйвер задает значение параметра инструкции для любого существующего операторы, связанные с указанным соединением.  
  
 Эта возможность является устаревшим в ODBC 3 *.x*. ODBC 3 *.x* драйверы должен поддерживать только параметр ODBC 2. *x* атрибуты инструкции на уровне соединения, если они хотят работать с ODBC 2. *x* приложений, сделать это. ODBC 3 *.x* приложения никогда не следует устанавливать атрибуты инструкции на уровне соединения. ODBC 3 *.x* атрибуты инструкции, которые нельзя установить на уровне соединения, за исключением SQL_ATTR_METADATA_ID и атрибуту SQL_ATTR_ASYNC_ENABLE атрибуты, которые атрибуты соединения и атрибуты инструкции, но может быть задать на уровне соединения или уровне инструкций.
