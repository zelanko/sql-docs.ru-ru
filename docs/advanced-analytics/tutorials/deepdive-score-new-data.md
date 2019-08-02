---
title: Оценка новых данных с помощью RevoScaleR и rxPredict
description: Пошаговое руководство по оценке данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff3782fb760e4d3dd1059103bc835b94d9c7581f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714837"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Оценка новых данных (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом шаге вы используете модель логистической регрессии, созданную на предыдущем занятии, для оценки другого набора данных, использующего те же независимые переменные, что и входные данные.

> [!div class="checklist"]
> * Оценка новых данных
> * Создание гистограммы оценок

> [!NOTE]
> Для выполнения некоторых из этих действий необходимы права администратора DDL.

## <a name="generate-and-save-scores"></a>Создание и сохранение оценок
  
1. Обновите источник данных sqlScoreDS (созданный на [занятии 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)), чтобы использовать сведения о столбцах, созданные на предыдущем занятии.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Чтобы убедиться, что результаты не потеряны, создайте новый объект источника данных. Затем используйте новый объект источника данных для заполнения новой таблицы в базе данных Реводипдиве.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    К этому моменту таблица не была создана. Эта инструкция просто определяет контейнер для данных.
     
3. Проверьте текущий контекст вычислений с помощью **рксжеткомпутеконтекст ()** и задайте для контекста вычислений сервер при необходимости.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. В качестве меры предосторожности проверьте наличие выходной таблицы. Если он уже существует с тем же именем, при попытке записи новой таблицы возникнет ошибка.
  
    Для этого вызовите функции [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) и [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable), передав имя таблицы в качестве входных данных.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** запрашивает драйвер ODBC и возвращает значение true, если таблица существует, и false в противном случае.
    + **rxSqlServerDropTable** выполняет DDL и возвращает значение true, если таблица успешно удалена, и false в противном случае.

5. Выполните [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) , чтобы создать оценки, и сохраните их в новой таблице, определенной в источнике данных sqlScoreDS.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Функция **RxPredict** является еще одной функцией, поддерживающей выполнение в удаленных контекстах вычисления. Для создания оценок на основе моделей, основанных на [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)или [RxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm), можно использовать функцию **rxPredict** .
  
    - В этом случае параметру *writeModelVars* присвоено значение **TRUE** . Это означает, что переменные, которые использовались для оценки, будут включены в новую таблицу.
  
    - Параметр *predVarNames* определяет переменную, в которой будут храниться результаты. Здесь вы передаете новую переменную `ccFraudLogitScore`,.
  
    - Параметр *type* функции **rxPredict** определяет способ вычисления прогнозов. Укажите **ответ** на ключевое слово для формирования оценок на основе масштаба переменной ответа. Или используйте **ссылку** на ключевое слово, чтобы создать оценки на основе базовой функции ссылки, в этом случае прогнозы создаются с помощью логистического масштаба.

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

## <a name="display-scores-in-a-histogram"></a>Отображение оценок в гистограмме

После создания новой таблицы Вычислите и отобразите гистограмму 10 000 прогнозируемых оценок. Вычисления выполняются быстрее, если заданы низкие и высокие значения, поэтому их можно получить из базы данных и добавить в рабочие данные.

1. Создайте новый источник данных Склминмакс, который запрашивает базу данных для получения минимальных и высоких значений.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     В этом примере можно увидеть, насколько просто использовать объекты источника данных **RxSqlServerData** для определения произвольных наборов данных на основе запросов SQL, функций или хранимых процедур, а затем использовать их в коде R. Переменная не хранит фактические значения, а только определение источника данных. Запрос выполняется для создания значений только при его использовании в функции наподобие **rxImport**.
      
2. Вызовите функцию [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) , чтобы разместить значения в кадре данных, который может совместно использоваться различными контекстами вычислений.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Результаты**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Теперь, когда максимальные и минимальные значения доступны, используйте значения для создания другого источника данных для созданных оценок.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Используйте объект источника данных Склаутскоредс для получения оценок, а также для вычисления и отображения гистограммы. При необходимости добавьте код для задания контекста вычисления.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Результаты**
  
    ![Сложная гистограмма, созданная с помощью R](media/rsql-sue-complex-histogram.png "Сложная гистограмма, созданная с помощью R")
  
## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Преобразование данных с помощью языка R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)