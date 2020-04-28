---
title: Вызов SQLSetPos | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46cfbb4e2e6b60f620cd7e38272bf9308ece91bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306245"
---
# <a name="calling-sqlsetpos"></a>Вызов SQLSetPos
В ODBC *2. x*указатель на массив состояния строки был аргументом для **SQLExtendedFetch**. Впоследствии массив состояния строк был обновлен с помощью вызова функции **SQLSetPos**. Некоторые драйверы полагаться на тот факт, что этот массив не меняется между **SQLExtendedFetch** и **SQLSetPos**. В ODBC *3. x*указатель на массив состояния является полем дескриптора, поэтому приложение может легко изменить его, чтобы оно указывало на другой массив. Это может быть проблемой, когда приложение ODBC *3. x* работает с драйвером ODBC *2. x* , но вызывает **SQLSetStmtAttr** для установки указателя состояния массива и вызова **SQLFetchScroll** для выборки данных. Диспетчер драйверов сопоставляет его как последовательность вызовов **SQLExtendedFetch**. В следующем коде ошибка обычно возникает, когда диспетчер драйверов сопоставляет второй вызов **SQLSetStmtAttr** при работе с драйвером ODBC *2. x* :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Эта ошибка возникает, если невозможно изменить указатель состояния строки в ODBC *2. x* между вызовами **SQLExtendedFetch**. Вместо этого диспетчер драйверов выполняет следующие действия при работе с драйвером ODBC *2. x* :  
  
1.  Инициализирует внутренний флаг диспетчера драйверов *фсетпосеррор* в значение true.  
  
2.  Когда приложение вызывает **SQLFetchScroll**, диспетчер драйверов устанавливает *фсетпосеррор* в значение false.  
  
3.  Когда приложение вызывает **SQLSetStmtAttr** для установки SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов устанавливает *Фсетпосеррор* равным тотруе.  
  
4.  Когда приложение вызывает функцию **SQLSetPos**с параметром *фсетпосеррор* , равным true, диспетчер драйверов создает SQL_ERROR с параметром SQLSTATE HY011 (атрибут не может быть установлен сейчас), чтобы указать, что приложение попыталось вызвать функцию **SQLSetPos** после изменения указателя состояния строки, но до вызова **SQLFetchScroll**.
