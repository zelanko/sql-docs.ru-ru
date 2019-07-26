---
title: Выполнение анализа фрагментирования с помощью RevoScaleR rxDataStep
description: Пошаговое руководство по блокам данных для распределенного анализа с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3aa0b42c9806e8d8972f31c69b1b33b222c43287
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469704"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Выполнение анализа фрагментирования с помощью rxDataStep (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии вы используете функцию **rxDataStep** для обработки данных в блоках, не требуя, чтобы весь набор данных загружался в память и обрабатывался в один момент времени, как в традиционном языке R. Функции **rxDataStep** считывают данные в блоке, применяют функции R к каждому блоку данных в свою очередь, а затем сохраняют сводные результаты для каждого фрагмента в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] общем источнике данных. При считывании всех данных результаты объединяются.

> [!TIP]
> На этом занятии вы Вычислите таблицу с непредвиденными обстоятельствами с помощью **табличной** функции в R. Этот пример предназначен только для инструкций. 
> 
> Если необходимо табличировать реальные наборы данных, мы рекомендуем использовать функции **ркскросстабс** или **rxCube** в **RevoScaleR**, которые оптимизированы для этой операции.

## <a name="partition-data-by-values"></a>Секционирование данных по значениям

1. Создайте пользовательскую функцию R, которая вызывает функцию **таблицы** r для каждого фрагмента данных, и назовите новую функцию **ProcessChunk**.
  
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
  
3. Определите SQL Server источник данных для хранения обрабатываемых данных. Для начала назначьте переменной SQL-запрос. Затем используйте эту переменную в аргументе *sqlQuery* нового источника данных SQL Server.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. При необходимости можно запустить **функцию rxgetvarinfo** для этого источника данных. На этом этапе он содержит один столбец: *Var 1: DayOfWeek, Type: Factor, недоступность уровней коэффициента*
     
5. Прежде чем применять эту переменную-признак к исходным данным, создайте отдельную таблицу для хранения промежуточных результатов. Опять же, вы просто используете функцию **RxSqlServerData** , чтобы определить данные, и обязательно удалите все существующие таблицы с одним и тем же именем.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Вызовите пользовательскую функцию **ProcessChunk** для преобразования данных по мере их считывания, используя ее в качестве аргумента *transformFunc* функции **rxDataStep** .
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Чтобы просмотреть промежуточные результаты **ProcessChunk**, назначьте результаты **rxImport** переменной, а затем выводите результаты на консоль.
  
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

10. Чтобы удалить таблицу промежуточных результатов, выполните вызов **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)