---
title: Создание модели R и сохранить в SQL Server (Пошаговое руководство) - машинного обучения SQL Server
description: Учебник, в котором показано, как создать модель языка R для анализа в базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b02b1e0298af6fbb96ba5ddd8d5a18dc8e154598
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645483"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Создание модели R и сохранить в SQL Server (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

На этом шаге вы научитесь создания модели машинного обучения и сохранить ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сохранив модель, можно вызвать непосредственно из [!INCLUDE[tsql](../../includes/tsql-md.md)] код, используя системную хранимую процедуру, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) или [функции PREDICT (T-SQL)](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql).

## <a name="prerequisites"></a>предварительные требования

Этот шаг предполагает выполняющимся R сеансом, в зависимости от предыдущего шага в этом пошаговом руководстве. Он использует соединение строк и данных источника объекты, созданные в этих шагах. Для запуска сценария используются следующие средства и пакеты.

+ RGUI.exe для выполнения команд R
+ Management Studio для выполнения T-SQL
+ Пакет ROCR
+ Пакет RODBC

### <a name="create-a-stored-procedure-to-save-models"></a>Создание хранимой процедуры для сохранения моделей

Этот шаг использует хранимую процедуру для сохранения обученной модели в SQL Server. Создание хранимой процедуры для выполнения этой операции упрощает задачу.

Выполните следующий код T-SQL в окон запросов в среде Management Studio для создания хранимой процедуры.

```sql
USE [NYCTaxi_Sample]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PersistModel')
  DROP PROCEDURE PersistModel
GO

CREATE PROCEDURE [dbo].[PersistModel] @m nvarchar(max)
AS
BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;
    insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
END
GO
```

> [!NOTE]
> Если отобразится сообщение об ошибке, убедитесь, что имя входа имеет разрешение на создание объектов. Вы можете предоставить явные разрешения для создания объектов, выполнив инструкцию T-SQL следующим образом: `exec sp_addrolemember 'db_owner', '<user_name>'`.

## <a name="create-a-classification-model-using-rxlogit"></a>Создание модели классификации с помощью rxLogit

Модель представляет собой двоичный классификатор, которая прогнозирует, является ли драйвер такси вероятность получения чаевых за определенной поездке, или нет. Вы используете источник данных, созданную на предыдущем занятии, для обучения классификатора с помощью логистической регрессии.

1. Вызовите функцию [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) , входящую в пакет **RevoScaleR** , чтобы создать модель логистической регрессии. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    Вызов, который создает эту модель, заключен в функцию system.time. Это позволяет получить время, необходимое для построения модели.

2. После построения модели, вы можете проверить его с помощью `summary` функции и просмотреть коэффициенты.

    ```R
    summary(logitObj);
    ```

    **Результаты**
    
    ```R
     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*
     direct_distance* 
     *Data: featureDataSource (RxSqlServerData Data Source)*
     *Dependent variable(s): tipped*
     *Total independent variables: 5*
     *Number of valid observations: 17068*
     *Number of missing observations: 0*
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*
     *Coefficients:*
     *Estimate Std. Error z value Pr(>|z|)*
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**
     *---*
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*
     *Condition number of final variance-covariance matrix: 48.3933*
     *Number of iterations: 4*
   ```

## <a name="use-the-logistic-regression-model-for-scoring"></a>Использование модели логистической регрессии для оценки

Теперь, когда модель создана, ее можно использовать для прогнозирования того, получит ли таксист чаевые за определенную поездку.

1. Во-первых, используйте [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) функции для определения объекта источника данных для сохранения результатов оценки.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Чтобы упростить этот пример входных данных для модели логистической регрессии является один и тот же источник данных компонентов (`sql_feature_ds`) вы использовали для обучения модели.  Чаще всего для оценки применяются новые данные либо для тестирования и обучения используются разные данные.
  
    + Результаты прогнозирования будут сохранены в таблице, _taxiscoreOutput_. Обратите внимание на то, что схема для этой таблицы не определено при ее создании с помощью функции rxSqlServerData. Чтобы получить схему, из выходных данных rxPredict.
  
    + Чтобы создать таблицу, которая хранит прогнозируемые значения, имя входа SQL, выполнением функции данных rxSqlServer требуются права DDL в базе данных. Если имя входа не удается создать таблицы, инструкция завершается неудачно.

2. Вызовите функцию [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) , чтобы создать результаты.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Если инструкция выполняется успешно, он займет некоторое время для выполнения. По завершении можно открыть SQL Server Management Studio и убедитесь, что она была создана, и что он содержит столбец оценки и другие ожидаемый результат.

## <a name="plot-model-accuracy"></a>Диаграмма точности модели

Чтобы получить представление о точности модели, можно использовать [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) функции для построения графика заключений. Поскольку rxRoc является одним из новых функций, предоставляемые пакетом RevoScaleR, поддерживающих удаленные контексты вычисления, у вас есть два варианта:

+ Можно использовать функцию rxRoc графика, выполняются в контексте удаленных вычислений и последующим возвращением графика в локальный клиент.

+ Также можно импортировать данные на клиентский компьютер R и использовать другие функции построения диаграмм R для создания графика производительности.

В этом разделе вы будете работать с помощью обоих методов.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Построение диаграммы в удаленном контексте вычислений (SQL Server)

1. Вызовите функцию rxRoc и предоставляют данные, определенные ранее в качестве входных данных.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Этот вызов возвращает значения, используемые при вычислении ROC диаграммы. Столбец меток отличается _tipped_, который содержит фактические результаты, вы пытаетесь спрогнозировать, хотя _Оценка_ столбец содержит прогноз.

2. На самом деле построения диаграммы, можно сохранить объект ROC и нарисуйте его с помощью функции построения. Граф создается на удаленном контексте вычисления и возвращается в вашу среду R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Просмотрите график, открыв графическое устройство R или щелкнув **построения** окно в RStudio.

    ![Построение ROC для модели](media/rsql-e2e-rocplot.png "Построение ROC для модели")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Создание диаграмм в локальном контексте вычислений с помощью данных из SQL Server

Можно проверить контекст вычислений является локальным, выполнив `rxGetComputeContext()` в командной строке. Возвращаемое значение должно быть «Контекст вычислений RxLocalSeq».

1. Для локального контекста вычислений процесс очень похоже на. Использовании [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) функцию для переноса указанных данных в локальной среде R.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Используя данные в локальной памяти, вы загружаете **ROCR** упаковывать и использовать прогнозирующую функцию из этого пакета для создания некоторых новых прогнозов.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Создание локального построения, исходя из значений, хранящихся в выходной переменной `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Построение графиков производительности модели с помощью R](media/rsql-e2e-performanceplot.png "Построение графиков производительности модели с помощью R")

> [!NOTE]
> Диаграммы могут отличаться от этого, в зависимости от того, сколько точек данных, которые вы использовали.

## <a name="deploy-the-model"></a>Развертывание модели

После построения модели и действительно подтвердила, что оно работает хорошо, может потребоваться развернуть его на сайт, где пользователям или сотрудникам организации можно сделать при использовании модели, или возможно повторное обучение и повторной калибровки модели на регулярной основе. Этот процесс иногда называется *ввод в эксплуатацию* модели. В SQL Server ввод в эксплуатацию достигается путем внедрения кода R в хранимой процедуре. Поскольку код находится в процедуре, он может вызываться из любого приложения, который может подключиться к SQL Server.

Перед вызовом модели из внешнего приложения, вам необходимо сохранить ее в базу данных, используемой в рабочей среде. Модели обучения хранятся в двоичной форме, в одном столбце типа **varbinary(max)**.

Типичное развертывание рабочего процесса состоит из следующих действий:

1. Сериализует модель в шестнадцатеричную строку
2. Передачи сериализованного объекта к базе данных
3. Сохранить модель в столбце varbinary(max)

В этом разделе вы научитесь использовать хранимую процедуру для сохранения модели и сделать его доступным для создания прогнозов. Хранимая процедура, используемая в этом разделе — PersistModel. Определение PersistModel состоит из [предварительные требования](#prerequisites).

1. Переключитесь обратно в локальную среду R, если вы уже не используете его, сериализует модель и сохраните его в переменной.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Откройте подключение ODBC с помощью **RODBC**. Можно опустить вызов RODBC, если у вас уже есть пакет загружен.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Вызовите процедуру PersistModel хранятся на сервере SQL Server для transmite сериализованного объекта к базе данных и сохранить двоичное представление модели в столбце. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Существует уточнить сведения о модели с помощью Management Studio. В обозревателе объектов щелкните правой кнопкой мыши **nyc_taxi_models** таблицы и нажмите кнопку **выделить 1000 верхних строк**. В результатах вы увидите в двоичное представление **моделей** столбца.

Для сохранения модели в таблице требуется только инструкция INSERT. Тем не менее, часто бывает проще, когда в оболочку в хранимой процедуре, такие как *PersistModel*.

## <a name="next-steps"></a>Следующие шаги

На последнем занятии Узнайте, как выполнять оценку на основе сохраненной модели с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!div class="nextstepaction"]
> [Развертывание модели R и использовать в SQL](walkthrough-deploy-and-use-the-model.md)
