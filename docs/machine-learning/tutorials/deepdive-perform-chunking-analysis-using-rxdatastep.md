---
title: Фрагментирующий анализ в RevoScaleR
description: Учебник по RevoScaleR, часть 12. Сведения о фрагментировании данных для распределенного анализа с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0ad082c3a21292b782d5888b48b698c986c0b5b2
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116807"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Выполнение фрагментирующего анализа с помощью rxDataStep (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта часть 12 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике вы примените функцию **rxDataStep** для обработки данных блоками, вместо того чтобы загружать в память и сразу обрабатывать весь набор данных, как в традиционных системах R. Функции **rxDataStep** считывают данные блоками, а функции R используются для последовательной обработки каждого блока данных. Затем сводные результаты для каждого блока сохраняются в единый источник данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После считывания всех данных результаты объединяются.

> [!TIP]
> В этом учебнике вы вычислите таблицу сопряженности с помощью функции **table** в R. Этот пример предназначен только для обучения. 
> 
> Если требуется внести в таблицу наборы реальных неструктурированных данных, рекомендуется использовать функции **rxCrossTabs** или **rxCube** в **RevoScaleR** — они оптимизированы для решения подобных задач.

## <a name="partition-data-by-values"></a>Секционирование данных по значениям

1. Создайте пользовательскую функцию R, которая вызывает функцию **table** для каждого блока данных, и назовите ее **ProcessChunk**.
  
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
  
3. Определите источник данных SQL Server для хранения обрабатываемых данных. Для начала назначьте переменной SQL-запрос. Используйте эту переменную в аргументе *sqlQuery* нового источника данных SQL Server.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. При необходимости можно запустить **rxGetVarInfo** для этого источника данных. На этом этапе он содержит один столбец. *Var 1: DayOfWeek, Type: factor, no factor levels available* (Переменная 1: день недели, тип: признак, уровни признаков недоступны)
     
5. Прежде чем применять эту переменную-признак к исходным данным, создайте отдельную таблицу для хранения промежуточных результатов. Используйте функцию **RxSqlServerData** для определения данных и обязательно удалите все имеющиеся таблицы с тем же именем.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Вызовите пользовательскую функцию **ProcessChunk**, чтобы преобразовывать данные во время чтения. Эта функция будет использоваться в качестве аргумента *transformFunc* для функции **rxDataStep**.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Чтобы просмотреть промежуточные результаты функции **ProcessChunk**, назначьте результаты **rxImport** переменной, а затем выведите результаты на консоль.
  
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

10. Чтобы удалить таблицу с промежуточными результатами, вызовите функцию **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)