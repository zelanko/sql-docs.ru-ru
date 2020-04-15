---
title: СЗЛСЕтСвитОпции Отображные Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77050df283b10abd17ba62a48bd366d6c1b3f601
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300504"
---
# <a name="sqlsetscrolloptions-mapping"></a>Сопоставление SQLSetScrollOptions
Когда приложение вызывает **S'LSetScrollOptions** через драйвер ODBC *3.x,* а драйвер не поддерживает **S'LSetScrollOptions,** вызов  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 приведет следующим образом:  
  
-   Звонок в  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     с аргументом *InfoType,* установленным на одно из значений в следующей таблице, в зависимости от значения аргумента *KeysetSize* в **S'LSetScrollOptions.**  
  
    |*Аргумент KeysetSize*|*Аргумент InfoType*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Значение, превышающее аргумент *RowsetSize*|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Если значение аргумента *KeysetSize* не указано в предыдущей таблице, вызов в **S'LSetScrollOptions** возвращает S'Lstate S1107 (значение строки вне диапазона) и ни один из следующих шагов не выполняется.  
  
     Затем менеджер драйвера проверяет, устанавливается ли соответствующий бит в значении*InfoValuePtr,* возвращенном по вызову в **S'LGetInfo,** в соответствии со значением аргумента *о параллели* в **S'LSetScrollOptions**.  
  
    |*Аргумент ы на параллелии*|*Настройка InfoType*|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Если аргумент *параллелизма* не является одним из значений в предыдущей таблице, вызов в **S'LSetScrollOptions** возвращает S'LSTATE S1108 (опцион на параллелизм вне диапазона), и ни один из следующих шагов не выполняется. Если подходящий бит (как указано в предыдущей таблице) не установлен в*infoValuePtr* к одному из значений, соответствующих аргументу *о параллели,* вызов в **S'LSetScrollOptions** возвращает S'LSTATE S1C00 (водитель не способен) и ни один из следующих шагов не выполняется.  
  
-   Звонок в  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     с * \*ValuePtr* установлен на одно из значений в следующей таблице, в соответствии со значением аргумента *KeysetSize* в **S'LSetScrollOptions**.  
  
    |*Аргумент KeysetSize*|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Значение, превышающее аргумент *RowsetSize*|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Звонок в  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     с * \*ValuePtr* установлен на *аргумент параллелизма* в **S'LSetScrollOptions**.  
  
-   Если аргумент *KeysetSize* в вызове к **S'LSetScrollOptions** является положительным,  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     с * \*ValuePtr* установлен на *KeysetSize* аргумент в **S'LSetScrollOptions**.  
  
-   Звонок в  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     с * \*ValuePtr* установлен на *аргумент RowsetSize* в **S'LSetScrollOptions**.  
  
    > [!NOTE]  
    >  Когда менеджер драйверов нанесет карты **для** приложения, работающего с драйвером ODBC *3.x,* не поддерживающим **S'LSetScrollOptions,** менеджер-водитель устанавливает опцию SQL_ROWSET_SIZE оператора, а не SQL_ATTR_ROW_ARRAY_SIZE атрибута, *аргументу RowsetSize* в **S'LSetScrollOption.** В результате этого приложение не может использовать сяритогевую опционы **slSetScrollOptions** при получении нескольких строк по вызову в **S'LFetch** или **S'LFetchScroll.** Он может быть использован только при получении нескольких строк по вызову в **S'LExtendedFetch.**
