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
ms.openlocfilehash: ccfebb99d6f98f1c6c2e5eea4650e1433e536d97
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792453"
---
# <a name="sqlgetconnectoption-mapping"></a>Сопоставление SQLGetConnectOption
Если приложение вызывает **SQLGetConnectOption** через ODBC *3.x* драйвера, вызов метода  
  
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
  
 Для ODBC *3.x* драйвера, диспетчер драйверов не проверяет *параметр* символах SQL_CONN_OPT_MIN и SQL_CONN_OPT_MAX — или больше, чем SQL_CONNECT_OPT_DRVR_START. Драйвер должен проверить допустимость значений параметров.
