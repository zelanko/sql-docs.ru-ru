---
title: Неявные преобразования курсора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60fabee858409f65a73bb03749a64b532e79d66b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422333"
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
  
  
