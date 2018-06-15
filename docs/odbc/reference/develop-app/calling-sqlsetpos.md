---
title: Вызов SQLSetPos | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9e7eeeaa8e2268256b103095ef0077329c52cc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911819"
---
# <a name="calling-sqlsetpos"></a>Вызов SQLSetPos
В ODBC 2. *x*, указатель на массив состояния строк был аргумента **SQLExtendedFetch**. Массив состояния строк позднее был обновлен с помощью вызова **SQLSetPos**. Некоторые драйверы полагались на тот факт, что этот массив не меняется между **SQLExtendedFetch** и **SQLSetPos**. В ODBC 3. *x*, указатель на массив состояний поле дескриптора, поэтому приложения можно легко изменить его для указания в другой массив. Это может вызвать проблемы при ODBC 3. *x* при работе с ODBC 2. *x* драйвер, но вызывает **SQLSetStmtAttr** присвоить указатель состояния массива и вызывает **SQLFetchScroll** для выборки данных. Диспетчер драйверов сопоставляет ее как последовательность вызовов **SQLExtendedFetch**. В следующем коде ошибка обычно должно порождаться при диспетчера драйверов сопоставляет второй **SQLSetStmtAttr** вызывать при работе с ODBC 2 *.x* драйвера:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Ошибка возникнет, если бы изменить указатель строки состояния в ODBC 2. *x* между вызовами **SQLExtendedFetch**. Вместо этого диспетчер драйверов выполняет следующие шаги при работе с ODBC 2 *.x* драйвера:  
  
1.  Инициализирует внутренний флаг диспетчера драйверов *fSetPosError* значение TRUE.  
  
2.  Если приложение вызывает **SQLFetchScroll**, диспетчер драйверов задает *fSetPosError* значение FALSE.  
  
3.  Когда приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, задает диспетчер драйверов *fSetPosError* toTRUE равны.  
  
4.  Когда приложение вызывает **SQLSetPos**, с *fSetPosError* равно TRUE, диспетчер драйверов вызывает ошибку SQL_ERROR с SQLSTATE HY011 (атрибут нельзя установить сейчас) указывает, что приложение Предпринята попытка вызова **SQLSetPos** после изменения состояния строки указателя, но до вызова метода **SQLFetchScroll**.
