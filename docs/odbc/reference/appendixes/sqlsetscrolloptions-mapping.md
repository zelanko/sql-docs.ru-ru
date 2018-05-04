---
title: Сопоставление SQLSetScrollOptions | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetScrollOptions
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a34db1972437578b2f38e9c42ecec8afcbb9d69
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-mapping"></a>Сопоставление SQLSetScrollOptions
Если приложение вызывает **SQLSetScrollOptions** через ODBC 3 *.x* драйвер и драйвер не поддерживает **SQLSetScrollOptions**, вызов  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 приведет к следующим образом:  
  
-   Вызов  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     с *свойство* аргументу присвоено одно из значений в таблице ниже, в зависимости от значения *KeysetSize* аргумент в **SQLSetScrollOptions**.  
  
    |*Аргумент KeysetSize*|*Свойство аргумента*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Значение, большее, чем *RowsetSize* аргумент|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Если значение *KeysetSize* аргумент не указан в таблице выше вызов **SQLSetScrollOptions** возвращает SQLSTATE S1107 (строк значение вне допустимого диапазона) и нет ни одной из следующих действий выполнить.  
  
     Диспетчер драйверов затем проверяет, установлен ли соответствующий бит **InfoValuePtr* значение, возвращаемое вызовом **SQLGetInfo**, согласно значению *параллелизма* аргумент в **SQLSetScrollOptions**.  
  
    |*Параллелизм* аргумент|*Свойство* параметр|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Если *параллелизма* аргумент не является одним из значений в таблице выше вызов **SQLSetScrollOptions** возвращает SQLSTATE S1108 (параметр параллелизма вне допустимого диапазона) и нет ни одной из следующих действий выполнить. Если соответствующий бит (как указано в таблице выше) не включен в **InfoValuePtr* одно из значений, соответствующих *параллелизма* аргументов, вызов  **SQLSetScrollOptions** возвращает SQLSTATE S1C00 (драйверы, не поддерживающих) и выполняются ни одно из следующих действий.  
  
-   Вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     с  *\*ValuePtr* присвоено одно из значений в следующей таблице, в соответствии со значением *KeysetSize* аргумент в **SQLSetScrollOptions**.  
  
    |*KeysetSize* аргумент|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Значение, большее, чем *RowsetSize* аргумент|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     с  *\*ValuePtr* значение *параллелизма* аргумент в **SQLSetScrollOptions**.  
  
-   Если *KeysetSize* аргумента в вызове **SQLSetScrollOptions** положительное, вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     с  *\*ValuePtr* значение *KeysetSize* аргумент в **SQLSetScrollOptions**.  
  
-   Вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     с  *\*ValuePtr* значение *RowsetSize* аргумент в **SQLSetScrollOptions**.  
  
    > [!NOTE]  
    >  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работа с ODBC 3 *.x* драйвер, который не поддерживает **SQLSetScrollOptions**, драйвер Диспетчер задает параметр инструкции SQL_ROWSET_SIZE атрибут не SQL_ATTR_ROW_ARRAY_SIZE инструкции к *RowsetSize* аргумент в **SQLSetScrollOption**. В результате **SQLSetScrollOptions** не может использоваться приложением при их получении нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Он может использоваться только в том случае, если извлечение нескольких строк путем вызова **SQLExtendedFetch**.
