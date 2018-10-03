---
title: Сопоставление SQLSetScrollOptions | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetScrollOptions
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5520554b509b0c25d62e4a191e16ad3524a02652
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651449"
---
# <a name="sqlsetscrolloptions-mapping"></a>Сопоставление SQLSetScrollOptions
Если приложение вызывает **SQLSetScrollOptions** через ODBC 3 *.x* драйвер, но драйвер не поддерживает **SQLSetScrollOptions**, вызов  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 приведет к следующим образом:  
  
-   Вызов  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     с помощью *InfoType* аргументу присвоено одно из значений в следующей таблице, в зависимости от значения *KeysetSize* аргумента в **SQLSetScrollOptions**.  
  
    |*Аргумент KeysetSize*|*Свойство аргумент*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Значение, большее, чем *RowsetSize* аргумент|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Если значение *KeysetSize* аргумент не указан в приведенной выше таблице вызов **SQLSetScrollOptions** возвращает SQLSTATE S1107 (строка значение вне допустимого диапазона) и ни один из следующих шагов выполнить.  
  
     Диспетчер драйверов, затем проверяет, задано ли соответствующий бит **InfoValuePtr* значение, возвращаемое вызовом **SQLGetInfo**, согласно заданному значению *параллелизма* аргумента в **SQLSetScrollOptions**.  
  
    |*Параллелизм* аргумент|*Свойство* параметр|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Если *параллелизма* аргумент не является ни одно из значений в таблице выше, вызов **SQLSetScrollOptions** возвращает SQLSTATE S1108 (параметр параллелизма вне допустимого диапазона) и ни один из следующих шагов выполнить. Если соответствующий бит (как указано в таблице выше) не задано **InfoValuePtr* одно из значений, соответствующий *параллелизма* аргументов, вызов  **SQLSetScrollOptions** возвращает SQLSTATE S1C00 (драйвер для не поддерживающих) и ни один из следующих шагов выполняются.  
  
-   Вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     с помощью  *\*ValuePtr* присвоено одно из значений в следующей таблице, согласно заданному значению *KeysetSize* аргумента в **SQLSetScrollOptions**.  
  
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
  
     с помощью  *\*ValuePtr* присвоено *параллелизма* аргумента в **SQLSetScrollOptions**.  
  
-   Если *KeysetSize* аргумента в вызове **SQLSetScrollOptions** положительно, вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     с помощью  *\*ValuePtr* присвоено *KeysetSize* аргумента в **SQLSetScrollOptions**.  
  
-   Вызов  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     с помощью  *\*ValuePtr* присвоено *RowsetSize* аргумента в **SQLSetScrollOptions**.  
  
    > [!NOTE]  
    >  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работа с ODBC 3 *.x* драйвер, который не поддерживает **SQLSetScrollOptions**, драйвер Диспетчер задает параметр инструкции SQL_ROWSET_SIZE, атрибут не SQL_ATTR_ROW_ARRAY_SIZE инструкции к *RowsetSize* аргумента в **SQLSetScrollOption**. В результате **SQLSetScrollOptions** не может использоваться приложением, при получении нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Он может использоваться только в том случае, если получение несколько строк с помощью вызова **SQLExtendedFetch**.
