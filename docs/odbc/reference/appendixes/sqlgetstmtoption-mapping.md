---
title: Картирование S'LGetStmtOption (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68819269d41407f2ce9dee172c889f7d7f286793
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300604"
---
# <a name="sqlgetstmtoption-mapping"></a>Сопоставление SQLGetStmtOption
Когда приложение вызывает **s'LGetStmtOption** к драйверу ODBC *3.x,* который не поддерживает его,  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 приведет следующим образом:  
  
-   Если *fOption* указывает на опцию оператора, определяемую ODBC, которая возвращает строку, менеджер драйвера вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Если *fOption* указывает на опцию оператора, определяемую ODBC, которая возвращает 32-битное значение, менеджер драйвера вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Если *fOption* указывает на опцию оператора, определяемую драйвером, менеджер драйвера вызывает  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 В предыдущих трех случаях аргумент *StatementHandle* устанавливается к значению в *hstmt,* аргумент *attribute* установлен к значению в *fOption,* а аргумент *ValuePtr* устанавливается на то же значение, что и *pvParam.*  
  
 Для параметров подключения строк, определяемых ODBC, менеджер драйвера устанавливает аргумент *BufferLength* в вызове к **S'LGetConnectAttr** на заданную максимальную длину (SQL_MAX_OPTION_STRING_LENGTH); для опции неструнного *соединения, BufferLength* установлен на 0.  
  
 Вариант SQL_GET_BOOKMARK оператора был универслен в ODBC *3.x*. Для того, чтобы драйвер ODBC *3.x* работал с приложениями ODBC *2.x,* которые используют SQL_GET_BOOKMARK, он должен поддерживать SQL_GET_BOOKMARK. Для того, чтобы драйвер ODBC *3.x* работал с приложениями ODBC *2.x,* он должен поддерживать настройку SQL_USE_BOOKMARKS SQL_UB_ON и должен выставлять закладки с фиксированной длиной. Если драйвер ODBC *3.x* поддерживает только закладки с переменной длиной, а не закладки с фиксированной длиной, он должен вернуть S'LSTATE HYC00 (необязательная функция не реализована), если приложение ODBC *2.x* пытается установить SQL_USE_BOOKMARKS SQL_UB_ON.  
  
 Для драйвера ODBC *3.x* менеджер драйвера больше не проверяет, находится ли *опцион* между SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX, или больше, чем SQL_CONNECT_OPT_DRVR_START. Водитель должен проверить это.
