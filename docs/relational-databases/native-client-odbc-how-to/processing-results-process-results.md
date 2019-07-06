---
title: Обработка результатов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b0848b254a331c08fc6b5afaf3eaf054b63c09c
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582587"
---
# <a name="processing-results---process-results"></a>Результаты обработки — обработка результатов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

Обработка результатов в приложении ODBC включает в себя сначала Определение характеристик результирующего набора, а затем данные считываются в программные переменные либо при помощи [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) или [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) .  
  
### <a name="to-process-results"></a>Обработка результатов  
  
1.  Получите сведения о результирующем наборе.  
  
2.  Если используются привязанные столбцы, вызовите функцию [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) для каждого столбца, чтобы привязать буфер программы к столбцу.  
  
3.  Для каждой строки в результирующем наборе сделайте следующее.  
  
    -   Вызовите функцию [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401), чтобы получить следующую строку.  
  
    -   Если используются привязанные столбцы, используйте данные, теперь доступные в привязанных буферах столбцов.  
  
    -   Если используются непривязанные столбцы, вызовите функцию [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) один или несколько раз, чтобы получить данные для непривязанных столбцов после последнего привязанного столбца. Вызовы функции **SQLGetData** должны следовать по возрастанию номера столбца.  
  
    -   Получение данных из столбца типа text или image производится многократным вызовом функции **SQLGetData**.  
  
4.  Когда функция [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) указывает конец результирующего набора, возвращая SQL_NO_DATA, вызовите функцию [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md), чтобы определить, доступен ли другой результирующий набор.  
  
    -   Если вернулось значение SQL_SUCCESS, то доступен другой результирующий набор.  
  
    -   Если вернулось значение SQL_NO_DATA, то больше нет результирующих наборов.  
  
    -   Если вернулось значение SQL_SUCCESS_WITH_INFO или SQL_ERROR, вызовом функции [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) определите, есть ли выходные данные от инструкции PRINT или RAISERROR.  
  
         Если в качестве выходных параметров используются привязанные параметры инструкции или возвращаемое значение хранимой процедуры, используйте данные, имеющиеся в буферах привязанного параметра. Кроме того, если используются привязанные параметры, при каждом вызове функции [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) или [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) инструкция SQL будет выполняться *S* раз, где *S* — количество элементов в массиве привязанных параметров. Это значит, что придется обработать *S* наборов результатов, каждый из которых содержит все результирующие наборы, выходные параметры и коды возврата, обычно возвращаемые при исполнении отдельной инструкции SQL.  
  
    > [!NOTE]  
    >  Если результирующий набор содержит вычисляемые строки, каждая вычисляемая строка доступна как отдельный результирующий набор. Эти вычисляемые результирующие наборы находятся среди обычных строк, разбивая их на несколько результирующих наборов.  
  
5.  Можно также вызвать функцию [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с SQL_UNBIND, чтобы освободить все буферы связанных столбцов.  
  
6.  Если есть еще один результирующий набор, перейдите к шагу 1.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

> [!NOTE]  
>  Чтобы отменить обработку результирующего набора прежде, чем функция [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) вернет значение SQL_NO_DATA, вызовите функцию [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>См. также  
[Получение сведений о результирующем наборе &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-retrieve-result-set-information.md)   
  
  
