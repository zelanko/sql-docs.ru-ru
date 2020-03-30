---
title: Учебник по R. Создание и сохранение модели
description: В этом учебнике демонстрируется, как создать языковую модель R, используемую для аналитики в базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4cb806c0a6286ec8a6608b346d12e666a8e9a09f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73724527"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Создание модели R и ее сохранение в SQL Server (пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

На этом шаге вы узнаете, как создать модель машинного обучения и сохранить ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После сохранения модели ее можно вызвать непосредственно из кода [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью системной хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) или [функции PREDICT (T-SQL)](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql).

## <a name="prerequisites"></a>Предварительные требования

Для этого этапа требуется продолжение сеанса R из предыдущих этапов этого пошагового руководства. В нем используются строки подключения и объекты источников данных, созданные на этих этапах. Для запуска скрипта используются следующие средства и пакеты.

+ Rgui.exe для выполнения команд R
+ Management Studio для выполнения T-SQL
+ Пакет ROCR
+ Пакет RODBC

### <a name="create-a-stored-procedure-to-save-models"></a>Создание хранимой процедуры для сохранения моделей

На этом шаге обученная модель сохраняется в SQL Server с помощью хранимой процедуры. Создание хранимой процедуры позволяет упростить выполнение этой задачи.

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
> Если возникла ошибка, убедитесь, что вашей учетной записи назначены разрешения на создание объектов. Чтобы явно предоставить разрешения на создание объектов, можно выполнить инструкцию T-SQL следующего вида: `exec sp_addrolemember 'db_owner', '<user_name>'`.

## <a name="create-a-classification-model-using-rxlogit"></a>Создание модели классификации с помощью rxLogit

Эта модель представляет собой двоичный классификатор, который прогнозирует, получит ли таксист чаевые за определенную поездку. Вы используете источник данных, созданный на предыдущем занятии, для обучения классификатора с помощью логистической регрессии.

1. Вызовите функцию [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) , входящую в пакет **RevoScaleR** , чтобы создать модель логистической регрессии. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    Вызов, который создает эту модель, заключен в функцию system.time. Это позволяет получить время, необходимое для построения модели.

2. После создания модели ее можно проверить с помощью функции `summary` и просмотреть коэффициенты.

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

1. Сначала используйте функцию [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata), чтобы определить объект источника данных для хранения результатов оценки.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Чтобы упростить этот пример, в качестве входных данных мы используем для модели логистической регрессии тот же источник данных (`sql_feature_ds`), который использовался для обучения модели.  Чаще всего для оценки применяются новые данные либо для тестирования и обучения используются разные данные.
  
    + Результаты прогнозирования будут сохраняться в таблице _taxiscoreOutput_. Обратите внимание, что при создании с использованием функции rxSqlServerData схема этой таблицы не определяется. В этом случае схема получается из выходных данных функции rxPredict.
  
    + Для создания таблицы, в которой будут храниться прогнозируемые значения, у имени входа SQL, с помощью которого выполняется функция данных rxSqlServer, должны быть права DDL в базе данных. Если имя входа не имеет права на создание таблиц, выполнение инструкции завершается сбоем.

2. Вызовите функцию [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) , чтобы создать результаты.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Выполнение инструкции может занимать некоторое время. После ее завершения вы можете открыть SQL Server Management Studio и убедиться, что таблица успешно создана и содержит столбец оценки, а также другие ожидаемые выходные данные.

## <a name="plot-model-accuracy"></a>Построение диаграммы точности модели

Чтобы получить представление о точности модели, можно воспользоваться функцией [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) для построения графика зависимости чувствительности от частоты ложно положительных заключений. Так как rxRoc — это одна из новых функций, входящих в состав пакета RevoScaleR и поддерживающих контексты удаленных вычислений, у вас есть два варианта:

+ Вы можете использовать функцию rxRoc для построения графика в контексте удаленных вычислений с последующим возвращением графика в локальный клиент.

+ Также можно импортировать данные на клиентский компьютер R и использовать другие функции построения диаграмм R для создания графика производительности.

В этом разделе вы поэкспериментируете с обоими приемами.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Построение диаграммы в удаленном контексте вычислений (SQL Server)

1. Вызовите функцию rxRoc, предоставив данные, определенные ранее в качестве входных.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    В результате этого вызова возвращаются значения, используемые при расчете графика зависимости чувствительности от частоты ложно положительных заключений. В качестве столбца меток выступает столбец _tipped_ (Чаевые), содержащий фактические результаты, которые вы пытаетесь спрогнозировать. Сам прогноз содержится в столбце _Score_ (Оценка).

2. Чтобы построить график, вы можете сохранить объект ROC и затем выполнить отрисовку с помощью функции plot. График строится в контексте удаленных вычислений, а затем возвращается в вашу среду R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Чтобы просмотреть его, откройте графическое устройство R или щелкните **окно графиков** в RStudio.

    ![График зависимости чувствительности от частоты ложно положительных заключений для модели](media/rsql-e2e-rocplot.png "График зависимости чувствительности от частоты ложно положительных заключений для модели")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Создание диаграмм в локальном контексте вычислений с помощью данных из SQL Server

Чтобы убедиться, что используется локальный контекст вычислений, выполните команду `rxGetComputeContext()` в командной строке. Она должна возвращать значение "RxLocalSeq Compute Context".

1. Для контекста локальных вычислений этот процесс во многом схож с описываемым. Используйте функцию [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) для переноса указанных данных в локальную среду R.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Используя данные в локальной памяти, вы загружаете пакет **ROCR** и используете реализованную в нем функцию прогнозирования для получения новых прогнозов.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Создайте локальный график на основе значений, сохраненных в выходной переменной `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Построение графика производительности модели с помощью R](media/rsql-e2e-performanceplot.png "Построение графика производительности модели с помощью R")

> [!NOTE]
> В зависимости от используемого количества точек данных ваши диаграммы могут выглядеть немного иначе.

## <a name="deploy-the-model"></a>Развертывание модели

После того как вы создали модель и проверили ее работу, вы можете развернуть ее на сайте, где ее смогут использовать, а также при необходимости периодически повторно выполнять ее обучение и калибровку другие пользователи или сотрудники вашей организации. Этот процесс иногда называют *эксплуатацией* модели. В SQL Server эксплуатация реализуется путем внедрения кода R в хранимую процедуру. Поскольку код размещается в процедуре, его можно вызывать из любого приложения, которое может подключаться к SQL Server.

Перед вызовом модели из внешнего приложения необходимо сохранить ее в базе данных, используемой в рабочей среде. Обученные модели хранятся в двоичной форме в одном столбце типа **varbinary(max)** .

Типовой рабочий процесс развертывания состоит из следующих шагов:

1. Сериализация модели в шестнадцатеричную строку
2. Передача сериализованного объекта в базу данных
3. Сохранение модели в столбце varbinary(max)

В этом разделе вы узнаете, как использовать хранимую процедуру для сохранения модели, чтобы ее можно было использовать для получения прогнозов. В этом разделе используется хранимая процедура PersistModel. Определение процедуры PersistModel приводится в разделе [Предварительные требования](#prerequisites).

1. Если вы еще не используете локальную среду R, перейдите в нее, выполните сериализацию модели и сохраните ее в переменной.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Откройте подключение ODBC с помощью **RODBC**. Если этот пакет уже загружен, вызов RODBC можно опустить.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Вызовите хранимую процедуру PersistModel в SQL Server, чтобы передать сериализованный объект в базу данных и сохранить двоичное представление модели в столбце. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. С помощью Management Studio проверьте существование модели. В обозревателе объектов щелкните правой кнопкой мыши таблицу **nyc_taxi_models** и затем щелкните **Выбрать первые 1000 строк**. В столбце **models** (Модели) результатов должно отображаться двоичное представление.

Для сохранения модели в таблице требуется только инструкция INSERT. Тем не менее, для простоты в большинстве случаев можно выполнить упаковку в хранимую процедуру, например *PersistModel*.

## <a name="next-steps"></a>Дальнейшие действия

На следующем и заключительном занятии вы узнаете, как выполнять оценку на основе сохраненной модели с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!div class="nextstepaction"]
> [Развертывание модели R и ее использование в SQL](walkthrough-deploy-and-use-the-model.md)
