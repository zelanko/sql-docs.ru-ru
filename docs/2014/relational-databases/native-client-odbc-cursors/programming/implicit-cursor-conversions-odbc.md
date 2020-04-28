---
title: Неявные преобразования курсора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 300ce02538a59ef043424d866ad4ce49267fcfa4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62711572"
---
# <a name="implicit-cursor-conversions-odbc"></a>Неявные преобразования курсора (ODBC)
  Приложения могут запрашивать тип курсора через [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , а затем выполнять инструкцию SQL, которая не поддерживается серверными курсорами запрошенного типа. Вызов **SQLExecute** или **SQLExecDirect** возвращает SQL_SUCCESS_WITH_INFO и **SQLGetDiagRec** возвращает:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Приложение может определить, какой тип курсора теперь используется, вызвав **SQLGetStmtOption** в значение SQL_CURSOR_TYPE. Преобразование типа курсора применяется только к одной инструкции. Следующие **SQLExecDirect** или **SQLExecute** будут выполняться с использованием параметров курсора исходной инструкции.  
  
## <a name="see-also"></a>См. также  
 [Сведения о программировании курсора &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
