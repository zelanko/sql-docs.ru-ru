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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f94b1191815f37728a2d8de8fc1175113644bc5a
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793888"
---
# <a name="calling-sqlsetpos"></a>Вызов SQLSetPos
В ODBC *2.x*, указатель на массив статусов строк был аргумента **SQLExtendedFetch**. Массив статусов строк позже была обновлена с помощью вызова **SQLSetPos**. Некоторые драйверы полагались на тот факт, что этот массив не меняется между **SQLExtendedFetch** и **SQLSetPos**. В ODBC *3.x*, поле дескриптора является указатель на массив состояний, и поэтому приложения можно легко изменить его в другой массив. Это может стать проблемой при ODBC *3.x* при работе с ODBC *2.x* драйвер, но вызывает **SQLSetStmtAttr** задать указатель состояния массива и вызывает  **SQLFetchScroll** для выборки данных. Диспетчер драйверов сопоставляет ее как последовательность вызовов **SQLExtendedFetch**. В следующем коде ошибка обычно должно порождаться при диспетчера драйверов сопоставляет второй **SQLSetStmtAttr** вызывать при работе с ODBC *2.x* драйвера:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Ошибка возникнет при наличии невозможно изменить указатель состояния строк в ODBC *2.x* между вызовами **SQLExtendedFetch**. Вместо этого диспетчер драйверов выполняет следующие шаги при работе с ODBC *2.x* драйвера:  
  
1.  Инициализирует внутренний флаг диспетчера драйверов *fSetPosError* значение true.  
  
2.  Если приложение вызывает **SQLFetchScroll**, диспетчер драйверов задает *fSetPosError* значение false.  
  
3.  Когда приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, задает диспетчера драйверов *fSetPosError* равно toTRUE.  
  
4.  Когда приложение вызывает **SQLSetPos**, с помощью *fSetPosError* , равным TRUE, диспетчер драйверов вызывает ошибку SQL_ERROR с SQLSTATE HY011 (атрибут нельзя установить сейчас) указывает, что приложение Предпринята попытка вызвать **SQLSetPos** после изменения указатель строки состояния, но до вызова метода **SQLFetchScroll**.
