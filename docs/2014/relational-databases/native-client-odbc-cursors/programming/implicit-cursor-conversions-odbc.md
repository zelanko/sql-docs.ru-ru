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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62711572"
---
# <a name="implicit-cursor-conversions-odbc"></a>Неявные преобразования курсора (ODBC)
  Приложения могут запросить тип курсора с помощью [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) и затем выполнить инструкцию SQL, который не поддерживается серверными курсорами запрошенного типа. Вызов **SQLExecute** или **SQLExecDirect** возвращает SQL_SUCCESS_WITH_INFO и **SQLGetDiagRec** возвращает:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Приложение может определить, какой тип курсора теперь используется путем вызова **SQLGetStmtOption** со значением SQL_CURSOR_TYPE. Преобразование типа курсора применяется только к одной инструкции. Следующий **SQLExecDirect** или **SQLExecute** , выполняются с использованием первоначальных настроек курсора инструкции.  
  
## <a name="see-also"></a>См. также  
 [Подробные сведения о программировании курсоров &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
