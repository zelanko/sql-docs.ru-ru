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
ms.openlocfilehash: 06b6b0f982b5c8d864e5024c8544f1f8e9af75ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091699"
---
# <a name="sqlsetscrolloptions-mapping"></a>Сопоставление SQLSetScrollOptions
Когда приложение вызывает **SQLSetScrollOptions** через драйвер ODBC *3. x* , а драйвер не поддерживает **SQLSetScrollOptions**, вызов  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 результат будет следующим:  
  
-   Вызов метода  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     Если для аргумента *инфотипе* задано одно из значений, приведенных в следующей таблице, в зависимости от значения аргумента *кэйсетсизе* в **SQLSetScrollOptions**.  
  
    |*Кэйсетсизе, аргумент*|*Инфотипе, аргумент*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Значение, большее, чем аргумент *ровсетсизе*|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Если значение аргумента *кэйсетсизе* не указано в приведенной выше таблице, вызов **SQLSETSCROLLOPTIONS** возвращает значение SQLSTATE S1107 (строка находится за пределами диапазона) и не выполняется ни одно из следующих действий.  
  
     Затем Диспетчер драйверов проверяет, задан ли соответствующий бит в значении **инфовалуептр* , возвращаемом вызовом **SQLGetInfo**, в соответствии со значением аргумента *Concurrency* в **SQLSetScrollOptions**.  
  
    |Аргумент *Concurrency*|Параметр *инфотипе*|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Если аргумент *параллелизма* не является одним из значений в предыдущей таблице, вызов **SQLSETSCROLLOPTIONS** возвращает значение SQLSTATE S1108 (параметр параллелизма выходит за пределы диапазона) и ни один из следующих действий не выполняется. Если соответствующий бит (как указано в предыдущей таблице) не установлен в **инфовалуептр* в одно из значений, соответствующих аргументу *Concurrency* , вызов **SQLSetScrollOptions** возвращает SQLSTATE S1C00 (драйвер не поддерживается), и ни один из следующих действий не выполняется.  
  
-   Вызов метода  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     Если для * \*ValuePtr* задано одно из значений, приведенных в следующей таблице, в соответствии со значением аргумента *кэйсетсизе* в **SQLSetScrollOptions**.  
  
    |*Кэйсетсизе* , аргумент|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Значение, большее, чем аргумент *ровсетсизе*|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Вызов метода  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     Если для * \*ValuePtr* задан аргумент *Concurrency* в **SQLSetScrollOptions**.  
  
-   Если аргумент *кэйсетсизе* в вызове **SQLSetScrollOptions** является положительным, вызывается метод  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     Если для * \*ValuePtr* задан аргумент *кэйсетсизе* в **SQLSetScrollOptions**.  
  
-   Вызов метода  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     Если для * \*ValuePtr* задан аргумент *ровсетсизе* в **SQLSetScrollOptions**.  
  
    > [!NOTE]  
    >  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работающего с драйвером ODBC *3. x* , который не поддерживает **SQLSetScrollOptions**, диспетчер драйверов устанавливает параметр инструкции SQL_ROWSET_SIZE, а не атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции, в аргумент *ровсетсизе* в **склсетскроллоптион**. В результате **SQLSetScrollOptions** не может использоваться приложением при выборке нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Его можно использовать только при выборке нескольких строк путем вызова **SQLExtendedFetch**.
