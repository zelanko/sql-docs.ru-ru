---
title: Функция Sqlgetconnectoption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8504709cb2cedb36c62bb9be74ffc8d12a4c811d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188787"
---
# <a name="sqlgetconnectoption-mapping"></a>Сопоставление SQLGetConnectOption
Если приложение вызывает **SQLGetConnectOption** через ODBC 3 *.x* драйвера, вызов метода  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 сопоставлено следующим образом:  
  
-   Если *fOption* указывает параметр соединения, определенных для ODBC, который возвращает строку, вызовы диспетчера драйверов  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *fOption* указывает параметр подключения, определенных для ODBC, который возвращает значение 32-разрядное целое число, вызовы диспетчера драйверов  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *fOption* указывает параметр инструкции, определяемым драйвером, вызовы диспетчера драйверов  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В указанных выше трех случаях *ConnectionHandle* аргумент присвоено значение в *hdbc*, *атрибут* аргумент присвоено значение в *fOption* и *ValuePtr* аргумент имеет значение совпадает со значением *pvParam*.  
  
 Для параметров соединения ODBC, определяемое, устанавливает диспетчер драйверов *BufferLength* аргумента в вызове **SQLGetConnectAttr** предопределенные максимальной длины (SQL_MAX_OPTION_STRING_LENGTH); параметра подключения нестроковые *BufferLength* имеет значение 0.  
  
 Для ODBC 3 *.x* драйвера, диспетчер драйверов не проверяет *параметр* символах SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX — или больше, чем SQL_CONNECT_OPT_DRVR_START. Драйвер должен проверить допустимость значений параметров.
