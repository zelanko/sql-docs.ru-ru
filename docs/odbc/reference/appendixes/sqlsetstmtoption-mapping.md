---
title: Картирование S'LSetStmtOption (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91264cee0dfceeb7195e2bad40d1638a88e1e01a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304905"
---
# <a name="sqlsetstmtoption-mapping"></a>Сопоставление SQLSetStmtOption
Когда приложение вызывает **S'LSetStmtOption** через драйвер ODBC *3.x,*  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 приведет следующим образом:  
  
-   Если *fOption* указывает на атрибут оператора, определяемый ODBC, который является строкой, менеджер драйвера вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *fOption* указывает атрибут оператора, определяемого ODBC, который возвращает 32-битное значение, менеджер драйвера вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Если *fOption* указывает атрибут оператора, определяемого драйвером, менеджер драйвера вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 В предыдущих трех случаях аргумент **StatementHandle** устанавливается на значение в *hstmt,* аргумент *Attribute* установлен на значение в *fOption,* а аргумент *ValuePtr* устанавливается к значению *как vParam.*  
  
 Поскольку менеджер драйвера не знает, нуждается ли атрибут оператора, определяемый драйвером, в строке или 32-битном значении, он должен пройти в допустимом значении для аргумента *StringLength* **s'LSetStmtAttr.** Если драйвер определил специальную семантику для атрибутов оператора, определяемого драйвером, и должен быть вызван с помощью **S'LSetStmtOption,** он должен поддерживать **S'LSetStmtOption.**  
  
 Если приложение вызывает **S'LSetStmtOption,** чтобы установить опцию оператора для драйвера ODBC *3.x* и опция была определена в версии драйвера ODBC *2.x,* для драйвера ODBC *3.x* должна быть определена новая константа манифеста. Если старая константа манифеста используется при вызове в **S'LSetStmtOption,** менеджер драйвера вызовет **S'LSetStmtAttr** с аргументом *StringLength,* установленным на 0.  
  
 Когда приложение вызывает **S'LSetStmtAttr,** чтобы установить SQL_ATTR_USE_BOOKMARKS SQL_UB_ON в драйвере ODBC *3.x,* атрибут SQL_ATTR_USE_BOOKMARKS оператора настроен на SQL_UB_FIXED. SQL_UB_ON такая же постоянная, как и SQL_UB_FIXED. Менеджер водителя передает SQL_UB_FIXED к водителю. SQL_UB_FIXED был универслен в ODBC *3.x*, но водитель ODBC *3.x* должен реализовать его для работы с приложениями ODBC *2.x,* которые используют закладки с фиксированной длиной.  
  
 Для драйвера ODBC *3.x* менеджер драйвера больше не проверяет, находится ли *опцион* между SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX, или больше, чем SQL_CONNECT_OPT_DRVR_START.
