---
title: Вызов S'LSetPos (англ.) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306245"
---
# <a name="calling-sqlsetpos"></a>Вызов SQLSetPos
В ODBC *2.x*указатель на массив состояния строки был аргументом в **пользу S'LExtendedFetch.** Позже массив статуса строки был обновлен вызовом в **S'LSetPos.** Некоторые драйверы полагаются на тот факт, что этот массив не изменяется между **S'LExtendedFetch** и **S'LSetPos**. В ODBC *3.x*указатель на массив состояния является полем дескриптора, и поэтому приложение может легко изменить его, чтобы указать на другой массив. Это может быть проблемой, когда приложение ODBC *3.x* работает с драйвером ODBC *2.x,* но вызывает **s'LSetStmtAttr,** чтобы установить указатель статуса массива, и вызывает **S'LFetchScroll** для получения данных. Менеджер драйверов отображает его как последовательность вызовов на **S'LExtendedFetch.** В следующем коде ошибка обычно возникает при составлении карты менеджера драйверов на втором вызове **S'LSetStmtAttr** при работе с драйвером ODBC *2.x:*  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Ошибка была бы поднята, если бы не было возможности изменить указатель статуса строки в ODBC *2.x* между вызовами на **S'LExtendedFetch.** Вместо этого менеджер драйвера выполняет следующие действия при работе с драйвером ODBC *2.x:*  
  
1.  Инициализирует внутренний флаг менеджера драйверов *fSetPosError* к TRUE.  
  
2.  Когда приложение вызывает **S'LFetchScroll,** менеджер драйвера устанавливает *fSetPosError* на FALSE.  
  
3.  Когда приложение вызывает **S'LSetStmtAttr** для установки SQL_ATTR_ROW_STATUS_PTR, менеджер драйверов устанавливает *fSetPosError,* равный TRUE.  
  
4.  Когда приложение вызывает **S'LSetPos**, с *fSetPosError,* равным TRUE, менеджер драйвера поднимает SQL_ERROR с S'Lstate HY011 (атрибут не может быть установлен сейчас), чтобы указать, что приложение попыталось вызвать **s'LSetPos** после изменения указателя статуса строки, но до вызова **S'LFetchScroll.**
