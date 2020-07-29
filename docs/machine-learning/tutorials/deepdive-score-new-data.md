---
title: Оценка данных с помощью RevoScaleR
description: Учебник по RevoScaleR, часть 8. Оценка данных с помощью языка R в SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 58e58dcf3112566c09070cc6e522b29ffff6f3b9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757134"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Оценка новых данных (учебник по SQL Server и RevoScaleR)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта часть 8 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике вы будете использовать модель логистической регрессии, созданную в предыдущем учебнике, для оценки еще одного набора данных с теми же независимыми переменными в качестве входных данных.

> [!div class="checklist"]
> * Оценка новых данных
> * Создание гистограммы оценок

> [!NOTE]
> Для выполнения некоторых действий требуются права администратора DDL.

## <a name="generate-and-save-scores"></a>Создание и сохранение оценок
  
1. Обновите источник данных sqlScoreDS (созданный при работе со [вторым учебником](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)), чтобы использовать сведения о столбцах, созданных ранее.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Чтобы убедиться, что результаты не потеряны, создайте новый объект источника данных. Затем используйте новый объект источника данных для заполнения новой таблицы в базе данных RevoDeepDive.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    К этому моменту таблица не была создана. Эта инструкция просто определяет контейнер для данных.
     
3. Проверьте текущий контекст вычисления с помощью **rxGetComputeContext** и при необходимости задайте серверный контекст.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. В качестве меры предосторожности проверьте наличие выходной таблицы. Если она уже существует с тем же именем, при попытке записи новой таблицы возникнет ошибка.
  
    Для этого вызовите функции [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) и [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable), передав имя таблицы в качестве входных данных.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + Функция **rxSqlServerTableExists** запрашивает драйвер ODBC и возвращает значение TRUE, если таблица существует, или значение FALSE в противном случае.
    + Функция **rxSqlServerDropTable** выполняет DDL и возвращает значение TRUE, если таблица успешно удалена, или FALSE в противном случае.

5. Выполните функцию [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) для создания оценок и их сохранения в новой таблице, определенной в источнике данных sqlScoreDS.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Функция **RxPredict** является еще одной функцией, поддерживающей выполнение в удаленных контекстах вычисления. Функцию **rxPredict** можно использовать для создания оценок из моделей на основе [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) или [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - В этом случае параметру *writeModelVars* присвоено значение **TRUE** . Это означает, что переменные, которые использовались для оценки, будут включены в новую таблицу.
  
    - Параметр *predVarNames* определяет переменную, в которой будут храниться результаты. В этом случае передается новая переменная с именем `ccFraudLogitScore`.
  
    - Параметр *type* функции **rxPredict** определяет способ вычисления прогнозов. Укажите ключевое слово **response** для создания оценок на основе масштаба переменной ответа. Также можно использовать ключевое слово **link** для создания оценок на основе базовой функции link. В этом случае прогнозы создаются с помощью логистического масштаба.

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

После создания новой таблицы производится вычисление и отображение гистограммы с 10 000 прогнозируемых оценок. Вычисления будут производиться быстрее, если указать нижнее и верхнее значения, поэтому получите их из базы данных и добавьте в рабочие данные.

1. Создайте источник данных sqlMinMax, который выполняет запрос к базе данных для получения нижнего и верхнего значений.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     В этом примере можно увидеть, насколько просто использовать объекты источника данных **RxSqlServerData** для определения произвольных наборов данных на основе запросов SQL, функций или хранимых процедур, а затем использовать их в коде R. Переменная не хранит фактические значения, а только определение источника данных. Запрос выполняется для создания значений только при его использовании в функции наподобие **rxImport**.
      
2. Вызовите функцию [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport), чтобы поместить значения в кадр данных, который можно использовать совместно в разных контекстах вычисления.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Результаты**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Теперь, когда максимальное и минимальное значения доступны, используйте их для создания еще одного источника данных для сформированных оценок.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Используйте объект источника данных sqlOutScoreDS для получения оценки, а также вычисления и отображения гистограммы. При необходимости добавьте код для задания контекста вычисления.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Результаты**
  
    ![сложная гистограмма, созданная R](media/rsql-sue-complex-histogram.png "сложная гистограмма, созданная R")
  
## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Преобразование данных с помощью языка R](../../machine-learning/tutorials/deepdive-transform-data-using-r.md)