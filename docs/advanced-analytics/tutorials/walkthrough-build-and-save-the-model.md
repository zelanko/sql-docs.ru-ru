---
title: Создание модели R и сохранение в SQL Server (пошаговое руководство)
description: Учебник, показывающий, как создать языковую модель R, используемую для SQL Server аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af2b1bf8f619800737863ff955011b011f4819d0
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715392"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Создание модели R и сохранение в SQL Server (пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

На этом шаге вы узнаете, как создать модель машинного обучения и сохранить ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сохранив модель, вы можете вызывать ее непосредственно из [!INCLUDE[tsql](../../includes/tsql-md.md)] кода с помощью системной хранимой процедуры, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) или [функции Predict (T-SQL)](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql).

## <a name="prerequisites"></a>предварительные требования

Этот шаг предполагает выполнение текущего сеанса R на основе предыдущих шагов этого пошагового руководства. В нем используются строки подключения и объекты источников данных, созданные в этих шагах. Для запуска скрипта используются следующие средства и пакеты.

+ RGUI. exe для выполнения команд R
+ Management Studio для выполнения T-SQL
+ Пакет РОКР
+ Пакет RODBC

### <a name="create-a-stored-procedure-to-save-models"></a>Создание хранимой процедуры для сохранения моделей

На этом шаге используется хранимая процедура для сохранения обученной модели в SQL Server. Создание хранимой процедуры для выполнения этой операции упрощает задачу.

Выполните следующий код T-SQL в окнах запроса в Management Studio, чтобы создать хранимую процедуру.

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
> Если возникает ошибка, убедитесь, что у вашего имени входа есть разрешение на создание объектов. Вы можете предоставить явные разрешения на создание объектов, выполнив инструкцию T-SQL следующим образом `exec sp_addrolemember 'db_owner', '<user_name>'`:.

## <a name="create-a-classification-model-using-rxlogit"></a>Создание модели классификации с помощью rxLogit

Модель является двоичным классификатором, который прогнозирует, может ли драйвер такси получить совет по определенному переопределению. Вы будете использовать источник данных, созданный на предыдущем занятии, для обучения классификатора TIP с помощью логистической регрессии.

1. Вызовите функцию [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) , входящую в пакет **RevoScaleR** , чтобы создать модель логистической регрессии. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    Вызов, который создает эту модель, заключен в функцию system.time. Это позволяет получить время, необходимое для построения модели.

2. После построения модели ее можно проверить с помощью `summary` функции и просмотреть коэффициенты.

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

1. Сначала используйте функцию [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) , чтобы определить объект источника данных для хранения результата оценки.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Чтобы упростить этот пример, входные данные модели логистической регрессии — это тот же источник данных компонентов (`sql_feature_ds`), который использовался для обучения модели.  Чаще всего для оценки применяются новые данные либо для тестирования и обучения используются разные данные.
  
    + Результаты прогноза будут сохранены в таблице _таксискореаутпут_. Обратите внимание, что схема для этой таблицы не определена при ее создании с помощью rxSqlServerData. Схема получается из выходных данных rxPredict.
  
    + Чтобы создать таблицу, в которой хранятся прогнозируемые значения, имя входа SQL, выполняющее функцию данных rxSqlServer, должно иметь права DDL в базе данных. Если имя входа не может создавать таблицы, инструкция завершается ошибкой.

2. Вызовите функцию [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) , чтобы создать результаты.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Если инструкция выполнена, выполнение может занять некоторое время. По завершении можно открыть SQL Server Management Studio и убедиться, что таблица была создана и содержит столбец Score и другие ожидаемые выходные данные.

## <a name="plot-model-accuracy"></a>Точность построения модели

Чтобы получить представление о точности модели, можно использовать функцию [рксрок](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) для построения графика работы приемника. Поскольку Рксрок — одна из новых функций, предоставляемых пакетом RevoScaleR, который поддерживает удаленные контексты вычислений, у вас есть два варианта:

+ Вы можете использовать функцию Рксрок для выполнения графика в удаленном контексте вычислений, а затем вернуть график к локальному клиенту.

+ Также можно импортировать данные на клиентский компьютер R и использовать другие функции построения диаграмм R для создания графика производительности.

В этом разделе вы поэкспериментируем с обоими методами.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Построение диаграммы в удаленном контексте вычислений (SQL Server)

1. Вызовите функцию Рксрок и укажите данные, определенные ранее в качестве входных данных.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Этот вызов возвращает значения, используемые при вычислении диаграммы ROC. Столбец метка имеет _неограниченный_результат, в котором есть фактические результаты, которые вы пытаетесь спрогнозировать, а в столбце _Оценка_ — прогноз.

2. Для фактического построения диаграммы можно сохранить объект ROC и затем нарисовать его с помощью функции графика. Граф создается в удаленном контексте вычислений и возвращается в среду R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Для просмотра графа откройте графическое устройство R или щелкните окно графиков в RStudio.

    ![Построение ROC для модели](media/rsql-e2e-rocplot.png "Построение ROC для модели")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Создание диаграмм в локальном контексте вычислений с помощью данных из SQL Server

Вы можете проверить, что контекст вычислений является локальным `rxGetComputeContext()` , выполнив команду в командной строке. Возвращаемое значение должно быть "Ркслокалсекным контекстом вычислений".

1. Для локального контекста вычислений процесс во многом аналогичен. Используйте функцию [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) для переноса указанных данных в локальную среду R.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Используя данные в локальной памяти, вы загружаете пакет **рокр** и используете функцию прогнозирования из этого пакета для создания новых прогнозов.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Создайте локальную графику на основе значений, хранящихся в выходной переменной `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Построение графиков производительности модели с помощью R](media/rsql-e2e-performanceplot.png "Построение графиков производительности модели с помощью R")

> [!NOTE]
> Диаграммы могут выглядеть иначе, в зависимости от количества используемых точек данных.

## <a name="deploy-the-model"></a>Развертывание модели

После создания модели и проверки ее правильности вы, вероятно, захотите развернуть ее на сайте, где пользователи или сотрудники вашей организации могут использовать модель, или, возможно, переучить и рекалибровать модель на регулярной основе. Этот процесс иногда называют *эксплуатацию* моделью. В SQL Server операция по внедрению достигается путем внедрения кода R в хранимую процедуру. Поскольку код находится в процедуре, он может быть вызван из любого приложения, которое может подключаться к SQL Server.

Прежде чем можно будет вызвать модель из внешнего приложения, необходимо сохранить модель в базе данных, используемой для рабочей среды. Обученные модели хранятся в двоичном виде в одном столбце типа **varbinary (max)** .

Типичный рабочий процесс развертывания состоит из следующих этапов.

1. Сериализация модели в шестнадцатеричную строку
2. Передача сериализованного объекта в базу данных
3. Сохранение модели в столбце varbinary (max)

В этом разделе описано, как использовать хранимую процедуру для сохранения модели и сделать ее доступной для прогнозов. Хранимая процедура, используемая в этом разделе, — PersistModel. Определение PersistModel находится в предварительных [требованиях](#prerequisites).

1. Переключитесь обратно в локальную среду R, если она еще не используется, выполните сериализацию модели и сохраните ее в переменной.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Откройте подключение ODBC с помощью **RODBC**. Если пакет уже загружен, можно опустить вызов RODBC.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Вызовите хранимую процедуру PersistModel на SQL Server, чтобы передать сериализованный объект в базу данных и сохранить двоичное представление модели в столбце. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Для проверки существования модели используйте Management Studio. В обозревателе объектов щелкните правой кнопкой мыши таблицу **nyc_taxi_models** и выберите пункт **выбрать первые 1000 строк**. В результате в столбце Models ( **модели** ) должно отобразиться двоичное представление.

Для сохранения модели в таблице требуется только инструкция INSERT. Однако часто бывает проще при заключении в хранимую процедуру, например *PersistModel*.

## <a name="next-steps"></a>Следующие шаги

На следующем и заключительном занятии вы узнаете, как выполнить оценку для сохраненной [!INCLUDE[tsql](../../includes/tsql-md.md)]модели с помощью.

> [!div class="nextstepaction"]
> [Развертывание модели R и использование в SQL](walkthrough-deploy-and-use-the-model.md)
