---
title: Выполнить анализ фрагментации, с помощью rxDataStep (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5db0acfb90c200442489cd7c3ec464223195eec6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31204426"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-and-r-deep-dive"></a>Выполнение анализа фрагментации, с помощью rxDataStep (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии использовать **rxDataStep** функции для обработки данных в виде фрагментов, а не требуется, весь набор данных будет загружен в память и обрабатывать одновременно, как и традиционные R. **RxDataStep** функции считывает данные в блоке, применяет функций R каждый фрагмент данных, в свою очередь и сохраняет сводки результатов для каждого блока общего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных. При считывании данных все результаты объединяются.

> [!TIP]
> Для этого занятия на непредвиденные случаи таблицы вычислений с помощью `table` функции в R. Этот пример предназначен для только в целях ознакомления. 
> 
> Если требуется подсчитать реальных наборов данных, мы рекомендуем использовать **rxCrossTabs** или **rxCube** функции в **RevoScaleR**, которые оптимизируются для данного сортировку операция.

## <a name="partition-data-by-values"></a>Секционировать данные по значениям

1. Создание пользовательской функции R, который вызывает R `table` каждого фрагмента данных и назовите новую функцию `ProcessChunk`.
  
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
  
3. Определите источник данных SQL Server для хранения данных, который обработка. Для начала назначьте переменной SQL-запрос. Затем с помощью этой переменной в *sqlQuery* новый аргумент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных.
  
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
4. При необходимости можно запустить **rxGetVarInfo** в этом источнике данных. На этом этапе он содержит один столбец: *Var 1: DayOfWeek, тип: коэффициент нет доступных уровней коэффициент*
     
5. Прежде чем применять эту переменную-признак к исходным данным, создайте отдельную таблицу для хранения промежуточных результатов. Опять же просто используйте функцию RxSqlServerData для определения данных, makign, удалите все существующие таблицы с таким же именем.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Вызывать пользовательскую функцию `ProcessChunk` для преобразования данных по мере считывания, используя его как *transformFunc* аргумент **rxDataStep** функции.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Для просмотра промежуточных результатов `ProcessChunk`, присвойте результаты **rxImport** переменной и вывод результатов на консоль.
  
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

10. Удалить таблицу промежуточные результаты, вызвать **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-step"></a>Следующий шаг

[Анализ данных в локальном контексте вычисления](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание таблицы SQL Server с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
