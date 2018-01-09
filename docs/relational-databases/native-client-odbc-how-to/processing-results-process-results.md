---
title: "Обработка результатов (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7217f631a0409f89fd8db0dfc4cf440ecda855f1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="processing-results---process-results"></a>Результаты обработки - обработка результатов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

Обработка результатов в приложении ODBC необходимо вначале Определение характеристик результирующего набора, а затем данные считываются в программные переменные с помощью [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) или [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md).  
  
### <a name="to-process-results"></a>Обработка результатов  
  
1.  Получите сведения о результирующем наборе.  
  
2.  Если используются привязанные столбцы, вызовите функцию [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) для каждого столбца, чтобы привязать буфер программы к столбцу.  
  
3.  Для каждой строки в результирующем наборе сделайте следующее.  
  
    -   Вызовите функцию [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401), чтобы получить следующую строку.  
  
    -   Если используются привязанные столбцы, используйте данные, теперь доступные в привязанных буферах столбцов.  
  
    -   Если используются непривязанные столбцы, вызовите функцию [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) один или несколько раз, чтобы получить данные для непривязанных столбцов после последнего привязанного столбца. Вызовы функции **SQLGetData** должны следовать по возрастанию номера столбца.  
  
    -   Получение данных из столбца типа text или image производится многократным вызовом функции **SQLGetData**.  
  
4.  Когда функция [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) указывает конец результирующего набора, возвращая SQL_NO_DATA, вызовите функцию [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md), чтобы определить, доступен ли другой результирующий набор.  
  
    -   Если вернулось значение SQL_SUCCESS, то доступен другой результирующий набор.  
  
    -   Если вернулось значение SQL_NO_DATA, то больше нет результирующих наборов.  
  
    -   Если вернулось значение SQL_SUCCESS_WITH_INFO или SQL_ERROR, вызовом функции [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) определите, есть ли выходные данные от инструкции PRINT или RAISERROR.  
  
         Если в качестве выходных параметров используются привязанные параметры инструкции или возвращаемое значение хранимой процедуры, используйте данные, имеющиеся в буферах привязанного параметра. Кроме того, если используются привязанные параметры, при каждом вызове функции [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) или [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) инструкция SQL будет выполняться *S* раз, где *S* — количество элементов в массиве привязанных параметров. Это значит, что придется обработать *S* наборов результатов, каждый из которых содержит все результирующие наборы, выходные параметры и коды возврата, обычно возвращаемые при исполнении отдельной инструкции SQL.  
  
    > [!NOTE]  
    >  Если результирующий набор содержит вычисляемые строки, каждая вычисляемая строка доступна как отдельный результирующий набор. Эти вычисляемые результирующие наборы находятся среди обычных строк, разбивая их на несколько результирующих наборов.  
  
5.  Можно также вызвать функцию [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с SQL_UNBIND, чтобы освободить все буферы связанных столбцов.  
  
6.  Если есть еще один результирующий набор, перейдите к шагу 1.  
  
> [!NOTE]  
>  Чтобы отменить обработку результирующего набора прежде, чем функция [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) вернет значение SQL_NO_DATA, вызовите функцию [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>См. также:  
[Получить сведения о результирующем наборе &#40; ODBC &#41;](../../relational-databases/native-client-odbc-how-to/processing-results-retrieve-result-set-information.md)   
  
  
