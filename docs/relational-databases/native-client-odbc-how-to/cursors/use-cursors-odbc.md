---
title: "Использование курсоров (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5116bd61887153c546b021d9db2553a4f9563480
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="use-cursors-odbc"></a>Использование курсоров (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-cursors"></a>Использование курсоров  
  
1.  Вызовите функцию [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md), чтобы задать нужные атрибуты курсора:  
  
     Задайте атрибуты SQL_ATTR_CURSOR_TYPE и SQL_ATTR_CONCURRENCY (этот параметр предпочтителен).  
  
     либо  
  
     Задайте атрибуты SQL_CURSOR_SCROLLABLE и SQL_CURSOR_SENSITIVITY.  
  
2.  Вызовите метод [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) для установки размера набора строк с помощью атрибута SQL_ATTR_ROW_ARRAY_SIZE.  
  
3.  По желанию можно вызвать функцию [SQLSetCursorName](http://go.microsoft.com/fwlink/?LinkId=58406) для задания имени курсора, если позиционированные обновления предполагается проводить с помощью предложения WHERE CURRENT OF.  
  
4.  Выполните инструкцию SQL.  
  
5.  По желанию можно вызвать функцию [SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) для получения имени курсора, если позиционированные обновления предполагается проводить с помощью предложения WHERE CURRENT OF, а имя курсора не было задано с помощью функции [SQLSetCursorName](http://go.microsoft.com/fwlink/?LinkId=58406) на шаге 3.  
  
6.  Вызовите функцию [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) для получения числа столбцов (C) в наборе строк.  
  
     Используйте привязку по столбцам.  
  
     \- или -  
  
     Используйте привязку на уровне строки.  
  
7.  Получайте наборы строк из курсора по мере необходимости.  
  
8.  Вызовите функцию [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md), чтобы определить, доступен ли другой результирующий набор.  
  
    -   Если вернулось значение SQL_SUCCESS, то доступен другой результирующий набор.  
  
    -   Если вернулось значение SQL_NO_DATA, то больше нет результирующих наборов.  
  
    -   Если вернулось значение SQL_SUCCESS_WITH_INFO или SQL_ERROR, вызовом функции [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) определите, есть ли выходные данные от инструкции PRINT или RAISERROR.  
  
     Если в качестве выходных параметров используются привязанные параметры инструкции или возвращаемое значение хранимой процедуры, используйте данные, имеющиеся в буферах привязанного параметра.  
  
     При использовании привязки параметров каждый вызов метода [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) или [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) выполнит инструкцию SQL S раз, где S — число элементов в массиве привязанных параметров. Это значит, что придется обработать S наборов результатов, каждый из которых содержит все результирующие наборы, выходные параметры и коды возврата, обычно возвращаемые при исполнении отдельной инструкции SQL.  
  
     Следует заметить, что, когда результирующий набор содержит вычисляемые строки, каждая вычисляемая строка представляется как отдельный результирующий набор. Эти вычисляемые результирующие наборы находятся среди обычных строк, разбивая их на несколько результирующих наборов.  
  
9. Можно также вызвать функцию [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с SQL_UNBIND, чтобы освободить все буферы связанных столбцов.  
  
10. Если есть еще один результирующий набор, перейдите к шагу 6.  
  
     На шаге 9 вызов функции [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) на частично обработанном результирующем наборе очистит оставшиеся результаты из набора. Другой способ очистки частично обработанного результирующего набора — вызов функции [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
     Типом курсора можно управлять, задавая параметры SQL_ATTR_CURSOR_TYPE и SQL_ATTR_CONCURRENCY либо SQL_ATTR_CURSOR_SENSITIVITY и SQL_ATTR_CURSOR_SCROLLABLE. Не следует смешивать два метода задания режима работы курсоров.  
  
## <a name="see-also"></a>См. также:  
 [С помощью инструкций по курсорам &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  
