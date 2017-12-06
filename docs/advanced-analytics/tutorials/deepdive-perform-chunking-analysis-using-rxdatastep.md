---
title: "Выполнять анализ фрагментации, с помощью rxDataStep | Документы Microsoft"
ms.custom: 
ms.date: 05/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 245bf9cf48b833a87b96666f1c050ca8fc1b4dbc
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="perform-chunking-analysis-using-rxdatastep"></a>Выполнение фрагментирующего анализа с помощью rxDataStep

Функцию **rxDataStep** можно использовать для обработки данных фрагментами, вместо того чтобы загружать в память и сразу обрабатывать весь набор данных, как в традиционных системах R. В данном случае данные считываются фрагментами, а функции R используются для последовательной обработки каждого фрагмента данных. Затем сводные результаты для каждого фрагмента записываются в единый источник данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

На этом занятии вы научитесь этот метод с помощью `table` функции в R, чтобы вычислить таблицу на непредвиденные случаи.

> [!TIP]
> Этот пример предназначен только для обучения. Если требуется подсчитать реальных наборов данных, мы рекомендуем использовать **rxCrossTabs** или **rxCube** функции в **RevoScaleR**, которые оптимизируются для данного сортировку операция.

## <a name="partition-data-by-values"></a>Секционирование данных по значениям

1. Создайте пользовательскую функцию R, которая вызывает *таблицы* каждого фрагмента данных и назовите ее `ProcessChunk`.
  
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
    rxSetComputeContext( sqlCompute )
    ```
  
3. Будет определен источник данных SQL Server для хранения обрабатываемых данных. Для начала назначьте переменной SQL-запрос.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    ```

4. Включите эту переменную в аргумент *sqlQuery* нового источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
     При обработке функцией *rxGetVarInfo* этого источника данных вы увидите, что имеется всего один столбец: *Var 1: DayOfWeek, Type: factor, no factor levels available*(Переменная 1: DayOfWeek, тип: признак, уровни признаков недоступны).
     
5. Прежде чем применять эту переменную-признак к исходным данным, создайте отдельную таблицу для хранения промежуточных результатов. Опять же просто используйте функцию RxSqlServerData для определения данных и удалить все существующие таблицы с таким же именем.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Теперь будет вызывать пользовательскую функцию `ProcessChunk` для преобразования данных по мере считывания, используя его как *transformFunc* аргумент функции rxDataStep.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Для просмотра промежуточных результатов `ProcessChunk`присвоить переменной результаты rxImport и вывод результатов на консоль.
  
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

10. Чтобы удалить таблицу промежуточных результатов, выполнение другого вызова rxSqlServerDropTable.
  
    ```R
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)
    ```

## <a name="next-step"></a>Следующий шаг

[Анализ данных в локальном контексте;](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание новой таблицы SQL Server, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)


