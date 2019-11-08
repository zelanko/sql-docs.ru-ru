---
title: Использование курсоров (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 16124d582d5651462e0ba0fda657fe66097b9a63
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73781625"
---
# <a name="use-cursors-odbc"></a>Использование курсоров (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-use-cursors"></a>Использование курсоров  
  
1.  Вызовите функцию [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md), чтобы задать нужные атрибуты курсора:  
  
     Задайте атрибуты SQL_ATTR_CURSOR_TYPE и SQL_ATTR_CONCURRENCY (этот параметр предпочтителен).  
  
     или  
  
     Задайте атрибуты SQL_CURSOR_SCROLLABLE и SQL_CURSOR_SENSITIVITY.  
  
2.  Вызовите метод [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) для установки размера набора строк с помощью атрибута SQL_ATTR_ROW_ARRAY_SIZE.  
  
3.  По желанию можно вызвать функцию [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) для задания имени курсора, если позиционированные обновления предполагается проводить с помощью предложения WHERE CURRENT OF.  
  
4.  Выполните инструкцию SQL.  
  
5.  По желанию можно вызвать функцию [SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) для получения имени курсора, если позиционированные обновления предполагается проводить с помощью предложения WHERE CURRENT OF, а имя курсора не было задано с помощью функции [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) на шаге 3.  
  
6.  Вызовите функцию [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) для получения числа столбцов (C) в наборе строк.  
  
     Используйте привязку по столбцам.  
  
     \- или -  
  
     Используйте привязку на уровне строки.  
  
7.  Получайте наборы строк из курсора по мере необходимости.  
  
8.  Вызовите функцию [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md), чтобы определить, доступен ли другой результирующий набор.  
  
    -   Если вернулось значение SQL_SUCCESS, то доступен другой результирующий набор.  
  
    -   Если вернулось значение SQL_NO_DATA, то больше нет результирующих наборов.  
  
    -   Если вернулось значение SQL_SUCCESS_WITH_INFO или SQL_ERROR, вызовом функции [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) определите, есть ли выходные данные от инструкции PRINT или RAISERROR.  
  
     Если в качестве выходных параметров используются привязанные параметры инструкции или возвращаемое значение хранимой процедуры, используйте данные, имеющиеся в буферах привязанного параметра.  
  
     При использовании привязки параметров каждый вызов метода [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) или [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) выполнит инструкцию SQL S раз, где S — число элементов в массиве привязанных параметров. Это значит, что придется обработать S наборов результатов, каждый из которых содержит все результирующие наборы, выходные параметры и коды возврата, обычно возвращаемые при исполнении отдельной инструкции SQL.  
  
     Следует заметить, что, когда результирующий набор содержит вычисляемые строки, каждая вычисляемая строка представляется как отдельный результирующий набор. Эти вычисляемые результирующие наборы находятся среди обычных строк, разбивая их на несколько результирующих наборов.  
  
9. Можно также вызвать функцию [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с SQL_UNBIND, чтобы освободить все буферы связанных столбцов.  
  
10. Если есть еще один результирующий набор, перейдите к шагу 6.  
  
     На шаге 9 вызов функции [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) на частично обработанном результирующем наборе очистит оставшиеся результаты из набора. Другой способ очистки частично обработанного результирующего набора — вызов функции [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
     Типом курсора можно управлять, задавая параметры SQL_ATTR_CURSOR_TYPE и SQL_ATTR_CONCURRENCY либо SQL_ATTR_CURSOR_SENSITIVITY и SQL_ATTR_CURSOR_SCROLLABLE. Не следует смешивать два метода задания режима работы курсоров.  
  
## <a name="see-also"></a>См. также раздел  
 [Разделы &#40;руководства по использованию курсоров ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  
