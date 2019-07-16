---
title: Оценка новых данных с помощью RevoScaleR и rxPredict - машинного обучения SQL Server
description: Руководство о том, как для оценки данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 386daeb62262182d40ea0b15cca3eb9714c23d64
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962199"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Оценка новых данных (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом шаге используется модель логистической регрессии, созданную на предыдущем занятии, для оценки еще одного набора данных, который использует теми же независимыми переменными в качестве входных данных.

> [!div class="checklist"]
> * Оценка новых данных
> * Создание гистограммы оценок

> [!NOTE]
> Для некоторых из этих действий требуются права администратора DDL.

## <a name="generate-and-save-scores"></a>Создайте и сохраните оценок
  
1. Обновление источника данных sqlScoreDS (созданных в [урок два](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)) использовать сведения о столбцах, созданные на предыдущем занятии.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Чтобы убедиться в том, что не потерять результаты, создайте объект источника данных. Затем используйте новый объект источника данных для заполнения новой таблицы в базе данных RevoDeepDive.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    К этому моменту таблица не была создана. Эта инструкция просто определяет контейнер для данных.
     
3. Проверьте текущий контекст вычислений с помощью **rxGetComputeContext()** и настройки контекста вычислений на сервере, при необходимости.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. В качестве меры предосторожности Проверьте наличие таблицы выходных данных. Если одно уже существует с тем же именем, вы получите ошибку при попытке записи в новую таблицу.
  
    Для этого вызовите функции [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) и [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable), передав имя таблицы в качестве входных данных.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** запрашивает драйвер ODBC и возвращает TRUE, если таблица существует, или FALSE в противном случае.
    + **rxSqlServerDropTable** выполняет DDL и возвращает значение TRUE, если таблица успешно удалена, или FALSE в противном случае.

5. Выполнение [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) для создания оценок и сохранить их в новой таблице, определенной в sqlScoreDS источника данных.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Функция **RxPredict** является еще одной функцией, поддерживающей выполнение в удаленных контекстах вычисления. Можно использовать **rxPredict** функцию для создания оценок из моделей на основе [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit), или [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - В этом случае параметру *writeModelVars* присвоено значение **TRUE** . Это означает, что переменные, которые использовались для оценки, будут включены в новую таблицу.
  
    - Параметр *predVarNames* определяет переменную, в которой будут храниться результаты. Здесь вы передаете переменную, `ccFraudLogitScore`.
  
    - Параметр *type* функции **rxPredict** определяет способ вычисления прогнозов. Укажите ключевое слово **ответ** для формирования оценок на основе шкалы зависимой переменной. Также можно использовать ключевое слово **ссылку** для формирования оценок в зависимости от базовой функции связи, в этом случае создаются прогнозы с помощью логистической шкале.

6. Через некоторое время вы можете обновить список таблиц в среде Management Studio, чтобы увидеть новую таблицу и ее данные.

7. Чтобы добавить дополнительные переменные в результирующие прогнозы, используйте аргумент *extraVarsToWrite*.  Например, в следующем коде переменная *custID* добавляется из таблицы данных для оценки в выходную таблицу прогнозов.
  
    ```R
    rxPredict(modelObject = logitObj,
            data = sqlScoreDS,
            outData = sqlServerOutDS,
            predVarNames = "ccFraudLogitScore",
              type = "link",
            writeModelVars = TRUE,
            extraVarsToWrite = "custID",
            overwrite = TRUE)
    ```

## <a name="display-scores-in-a-histogram"></a>Отображение оценок на гистограмме

После создания новой таблицы, вычисление и отображение гистограммы с 10 000 прогнозируемых оценок. Вычисление выполняется быстрее, если указать нижнее и верхнее значения, поэтому получены из базы данных и добавить их в рабочие данные.

1. Создайте новый источник данных, sqlMinMax, который запрашивает базу данных для получения нижнего и верхнего значений.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     В этом примере можно увидеть, насколько просто использовать объекты источника данных **RxSqlServerData** для определения произвольных наборов данных на основе запросов SQL, функций или хранимых процедур, а затем использовать их в коде R. Переменная не хранит фактические значения, а только определение источника данных. Запрос выполняется для создания значений только при его использовании в функции наподобие **rxImport**.
      
2. Вызовите [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) функции, чтобы поместить значения в кадр данных, который может использоваться совместно в разных контекстах вычисления.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Результаты**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Теперь, когда максимальное и минимальное значения доступны, используйте значения для создания другого источника данных для созданных оценок.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Используйте sqlOutScoreDS объекта источника данных для получения оценок и вычисления и отображения гистограммы. При необходимости добавьте код для задания контекста вычисления.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Результаты**
  
    ![Сложная гистограмма, созданная с помощью R](media/rsql-sue-complex-histogram.png "Сложная гистограмма, созданная с помощью R")
  
## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Преобразование данных с помощью языка R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)