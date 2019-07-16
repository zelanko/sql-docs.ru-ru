---
title: Выполнение фрагментирующего анализа с помощью rxDataStep RevoScaleR - машинного обучения SQL Server
description: Пошагового руководства по блокам данных для распределенных анализа, с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6ccc64c98f0519b33b6ba9da180c01e4478492f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962206"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Выполнение фрагментирующего анализа с помощью rxDataStep (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии вы использовать **rxDataStep** функцию для обработки данных в виде фрагментов, не требуя что весь набор данных будет загружен в память и обрабатывать одновременно, как и в традиционных системах R. **RxDataStep** функции считывает данные в блоке, применяет функции R для каждого блока данных, в свою очередь и затем сохраняет сводные результаты для каждого фрагмента данных в общий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных. После считывания всех данных, результаты объединяются.

> [!TIP]
> На этом занятии с помощью вычисления таблицы сопряженности **таблицы** функции в R. Этот пример предназначен только для обучения. 
> 
> Если требуется внести наборы реальных данных, мы рекомендуем использовать **rxCrossTabs** или **rxCube** функции в **RevoScaleR**, оптимизированные для этого рода операция.

## <a name="partition-data-by-values"></a>Секционирование данных по значениям

1. Создайте пользовательскую функцию R, который вызывает R **таблицы** функции для каждого блока данных и назовите новую функцию **ProcessChunk**.
  
    ```R
    ProcessChunk <- function( dataList) {
    # Convert the input list to a data frame and compute contingency table
    chunkTable <- table(as.data.frame(dataList))
  
    # Convert table output to a data frame with a single row
    varNames <- names(chunkTable)
    varValues <- as.vector(chunkTable)
    dim(varValues) <- c(1, length(varNames))
    chunkDF <- as.data.frame(varValues)
    names(chunkDF) <- varNames
  
    # Return the data frame, which has a single row
    return( chunkDF )
    }
    ```

2. В качестве контекста вычисления задайте сервер.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
3. Определение источника данных SQL Server для хранения обрабатываемых данных. Для начала назначьте переменной SQL-запрос. Затем используйте эту переменную в *sqlQuery* аргумент новый источник данных SQL Server.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. При необходимости можно запустить **rxGetVarInfo** в этом источнике данных. На этом этапе он содержит один столбец: *Var 1: DayOfWeek, тип: коэффициент, нет доступных уровней фактора*
     
5. Прежде чем применять эту переменную-признак к исходным данным, создайте отдельную таблицу для хранения промежуточных результатов. Опять же, просто используйте **RxSqlServerData** функции для определения данных, обязательно удалите все имеющиеся таблицы с тем же именем.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Вызовите эту пользовательскую функцию **ProcessChunk** для преобразования данных, как считывать, используя его как *transformFunc* аргумент **rxDataStep** функции.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Чтобы просмотреть промежуточные результаты из **ProcessChunk**, назначьте результаты **rxImport** переменной, а затем выведите результаты на консоль.
  
    ```R
    iroResults <- rxImport(iroDataSource)
    iroResults
    ```

    **Частичные результаты**

    |      |    1  |   2   |  3   |  4   |  5  |   6   |  7 |
    | --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
    | 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
    | 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |

9. Чтобы вычислить окончательные результаты по всем фрагментам, просуммируйте столбцы и отобразите результаты на консоли.

    ```R
    finalResults <- colSums(iroResults)
    finalResults
    ```

    **Результаты**

    1  |   2  |   3  |   4  |   5  |   6  |   7
    ---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
    97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. Чтобы удалить таблицу промежуточных результатов, сделать вызов к **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)