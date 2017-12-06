---
title: "Оценка новых данных | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83beab637e3740dc41706c34ccfacffe985f2957
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="score-new-data"></a>Оценка новых данных

Теперь, когда у вас есть модель, которую можно использовать для прогнозирования, вы внесете в нее данные из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для получения ряда прогнозов.

Вы будете использовать модель логистической регрессии *logitObj*для формирования оценок для еще одного набора данных с теми же независимыми переменными в качестве входных данных.

> [!NOTE]
> Для выполнения некоторых действий потребуются права администратора DDL.

## <a name="generate-and-save-scores"></a>Создайте и сохраните оценок
  
1. Обновите ранее настроенный источник данных *sqlScoreDS*, добавив сведения о необходимых столбцах.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Чтобы не потерять результаты, вы создадите новый объект источника данных и с его помощью заполните новую таблицу в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
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
  
    -  Функция rxSqlServerTableExists запрашивает драйвер ODBC и возвращает TRUE, если таблица существует, или FALSE в противном случае.
    -  Функция rxSqlServerDropTable функция выполняет DDL и возвращает TRUE, если таблица успешно удалена, FALSE в противном случае.
  
5. Теперь вы готовы использовать функцию **rxPredict** для создания оценок и их сохранения в новой таблице, определенной в источнике данных *sqlScoreDS*.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Функция rxPredict является другую функцию, которая поддерживает работу в контекстах удаленных вычислений. Функция rxPredict позволяет создавать оценки из моделей, созданных с помощью rxLinMod, rxLogit или rxGlm.
  
    - В этом случае параметру *writeModelVars* присвоено значение **TRUE** . Это означает, что переменные, которые использовались для оценки, будут включены в новую таблицу.
  
    - Параметр *predVarNames* определяет переменную, в которой будут храниться результаты. В этом случае передается новая переменная *ccFraudLogitScore*.
  
    - *Тип* параметр rxPredict определяет способ расчета прогнозов. Укажите ключевое слов **response** , чтобы оценки формировались на основе шкалы зависимой переменной, или используйте ключевое слово **link** , чтобы оценки формировались с помощью базовой функции связи, в которой ситуационные прогнозы основываются на логистической шкале.

6. Через некоторое время вы можете обновить список таблиц в среде Management Studio, чтобы увидеть новую таблицу и ее данные.

7. Чтобы добавить дополнительные переменные в результирующие прогнозы, можно использовать аргумент *extraVarsToWrite* .  Например, в следующем коде переменная *custID* добавляется из таблицы данных для оценки в выходную таблицу прогнозов.
  
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

После создания новой таблицы производится вычисление и отображение гистограммы с 10 000 прогнозируемых оценок. Вычисления будут производиться быстрее, если указать нижнее и верхнее значения, поэтому они будут получены из базы данных и добавлены в рабочие данные.

1. Создайте источник данных *sqlMinMax*, который выполняет запрос к базе данных для получения нижнего и верхнего значений.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Из этого примера можно увидеть, насколько просто использовать объекты источников данных RxSqlServerData определять произвольные наборы данных на основе запросов SQL, функции или хранимые процедуры и затем использовать их в коде R. Переменная не сохраняет фактические значения только определение источника данных; для создания значений только при использовании в такой функции, как rxImport выполняется запрос.
      
2. Вызовите функцию rxImport для размещения значений в кадре данных, который можно использовать совместно для контекстов вычислений.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **Результаты**
     
     *> minMaxVals*
     
     *[1] –23,970256   9,786345*
  
3. Теперь, когда доступны максимальное и минимальное значения, используйте значения для создания источника данных оценки.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. И наконец, используйте объект источника данных для получения данных оценки и вычисления и отображения гистограммы. При необходимости добавьте код для задания контекста вычисления.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Результаты**
  
    ![Сложная гистограмма, созданная с помощью R](media/rsql-sue-complex-histogram.png "Сложная гистограмма, созданная с помощью R")
  
## <a name="next-step"></a>Следующий шаг

[Преобразование данных с помощью R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание моделей](../../advanced-analytics/tutorials/deepdive-create-models.md)


