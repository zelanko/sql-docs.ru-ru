---
title: Оценить новые данные (SQL и R глубокое погружение) | Документы Microsoft
ms.custom: ''
ms.date: 12/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 829129f62a93c55d01b2a6f39e810f14dad723d2
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="score-new-data-sql-and-r-deep-dive"></a>Оценить новые данные (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом шаге используется модель логистической регрессии, созданный ранее, чтобы создавать оценки для другой набор данных, который использует же независимых переменных в качестве входных данных.

> [!NOTE]
> Для некоторых из этих шагов необходимы права администратора DDL.

## <a name="generate-and-save-scores"></a>Создайте и сохраните оценок
  
1. Обновление источника данных, которую вы настроили ранее, `sqlScoreDS`, чтобы добавить необходимые сведения.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Чтобы убедиться в том, что результаты не исчезнут, создайте объект источника данных. Затем, используйте объект источника данных для заполнения новой таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    К этому моменту таблица не была создана. Эта инструкция просто определяет контейнер для данных.
     
3. Проверьте текущий контекст вычисления и при необходимости задайте серверный контекст.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Перед выполнением функции прогнозирования, создающей результаты, необходимо проверить наличие таблицы выходных данных. В противном случае будет сообщение об ошибке при попытке записи в новую таблицу.
  
    Для этого вызовите функции **rxSqlServerTableExists** и **rxSqlServerDropTable**, передав имя таблицы в качестве входных данных.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    -  Функция **rxSqlServerTableExists** запрашивает драйвер ODBC и возвращает значение TRUE, если таблица существует, или значение FALSE в противном случае.
    -  Функция **rxSqlServerDropTable** выполняет DDL и возвращает значение TRUE, если таблица является успешно удалены, значение FALSE в противном случае.
    - Ссылки для обеих функций можно найти здесь: [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)
  
5. Теперь вы готовы к использованию [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) для создания оценки и сохранить их в новой таблице, определенные в источнике данных `sqlScoreDS`.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Функция **RxPredict** является еще одной функцией, поддерживающей выполнение в удаленных контекстах вычисления. Функцию **rxPredict** можно использовать для создания оценок из моделей, сформированных с помощью [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)или [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - В этом случае параметру *writeModelVars* присвоено значение **TRUE** . Это означает, что переменные, которые использовались для оценки, будут включены в новую таблицу.
  
    - Параметр *predVarNames* определяет переменную, в которой будут храниться результаты. Здесь вы передаете новой переменной `ccFraudLogitScore`.
  
    - Параметр *type* функции **rxPredict** определяет способ вычисления прогнозов. Укажите ключевое слово **ответ** для формирования оценок, на основе масштаба переменную ответа. Также можно использовать ключевое слово **ссылку** для формирования оценок, на основе базового ссылку функции, в этом случае прогнозы создаются с помощью логистической шкалы.

6. Через некоторое время вы можете обновить список таблиц в среде Management Studio, чтобы увидеть новую таблицу и ее данные.

7. Чтобы добавить дополнительные переменные в результирующие прогнозы, используйте аргумент *extraVarsToWrite*.  Например, в следующем коде переменной `custID` добавляется из оценки таблицы данных в таблицу выходные данные прогнозов.
  
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

## <a name="display-scores-in-a-histogram"></a>Отображение оценок в гистограмму

После создания новой таблицы можно вычислять и отображать гистограммы 10 000 прогнозируемые оценки. Вычисление выполняется быстрее, если указать значения нижнего и верхнего, поэтому получить из базы данных и добавить их в работе данные.

1. Создать новый источник данных, `sqlMinMax`, который запрашивает базу данных для получения значения нижнего и верхнего.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     В этом примере можно увидеть, насколько просто использовать объекты источника данных **RxSqlServerData** для определения произвольных наборов данных на основе запросов SQL, функций или хранимых процедур, а затем использовать их в коде R. Переменная не хранит фактические значения, а только определение источника данных. Запрос выполняется для создания значений только при его использовании в функции наподобие **rxImport**.
      
2. Вызовите [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) функцию для размещения значений в кадре данных, который можно использовать совместно для контекстов вычислений.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **Результаты**
     
     *> minMaxVals*
     
     *[1] –23,970256   9,786345*
  
3. Теперь доступны, максимальное и минимальное значения, используйте значения для создания другого источника данных для созданного оценок.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Используйте объект источника данных `sqlOutScoreDS` для возврата результатов и вычисления и отображения гистограммы. При необходимости добавьте код для задания контекста вычисления.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Результаты**
  
    ![Сложная гистограмма, созданная с помощью R](media/rsql-sue-complex-histogram.png "Сложная гистограмма, созданная с помощью R")
  
## <a name="next-step"></a>Следующий шаг

[Преобразование данных с помощью языка R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание моделей](../../advanced-analytics/tutorials/deepdive-create-models.md)


