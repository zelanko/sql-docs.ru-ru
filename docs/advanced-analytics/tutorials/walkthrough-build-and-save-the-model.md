---
title: "Построение модели R и сохранить в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: "21"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d10d27aa32125bd85e4694741c8dc765ff5c123e
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="build-an-r-model-and-save-to-sql-server"></a>Построение модели R и сохранить в SQL Server

На этом шаге вы узнаете, как для создания модели машинного обучения и сохраните модель в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="create-a-classification-model-using-rxlogit"></a>Создать модель классификации с помощью rxLogit

Модель, создаваемые — двоичный классификатор, который прогнозирует ли драйвер такси шансов получить совет по определенной расстояния или нет. Будет использоваться источник данных, созданного на предыдущем занятии, для обучения классификатора подсказки с помощью логистической регрессии.

1. Вызовите функцию [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) , входящую в пакет **RevoScaleR** , чтобы создать модель логистической регрессии. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = sql_feature_ds));
    ```

    Вызов, который создает эту модель, заключен в функцию system.time. Это позволяет получить время, необходимое для построения модели.

2. После построения модели, можно проверить с помощью `summary` функции, а также просматривать коэффициенты.

    ```R
    summary(logitObj);
    ```

     *Результаты*

     *Алгоритм логистической регрессии результаты: чаевых оставил зависимости ~ passenger_count + trip_distance + trip_time_in_secs +*
     <br/>*direct_distance*
     <br/>*Данные: featureDataSource (RxSqlServerData источник данных)*
     <br/>*Dependent variable(s): чаевых оставил зависимости*
     <br/>*Общее число независимых переменных: 5*
     <br/>*Число допустимых наблюдений: 17068*
     <br/>*Число отсутствующих наблюдений: 0*
     <br/>*-2\*LogLikelihood: 23540.0602 (остаточные отклонение на 17063 степеней свободы)*
     <br/>*Коэффициенты:*
     <br/>*Значение z оценки средней квадратической Значение ошибки z Pr (> | z |)*
     <br/>*(Перехват) - 2.509e-03 3.223e-02-0.078 0.93793*
     <br/>*passenger_count-5.753e-02 1.088e-02-5.289 1.23E-07\*\*\**
     <br/>*trip_distance-3.896e-02 1.466e-02-2.658 0.00786\*\**
     <br/>*trip_time_in_secs 2.115e-04 4.336e-05 4.878 1.07e-06\*\*\**
     <br/>*direct_distance 6.156e-02 2.076e-02 2.966 0.00302\*\**
     <br/>*---*
     <br/>*Коды значимости:  0 "\*\*\*" 0,001 "\*\*" 0,01 "\*" 0,05 "." 0.1 ‘ ’ 1*
     <br/>*Условие номер окончательной дисперсию Ковариация матрицы: 48.3933*
     <br/>*Число итераций: 4*

## <a name="use-the-logistic-regression-model-for-scoring"></a>Использование модели логистической регрессии для оценки

Теперь, когда модель создана, ее можно использовать для прогнозирования того, получит ли таксист чаевые за определенную поездку.

1. Во-первых, используйте [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) для определения объекта источника данных для хранения оценки resul

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Чтобы упростить этот пример входных данных для модели логистической регрессии является один и тот же источник данных компонентов (`sql_feature_ds`), используемые для обучения модели.  Чаще всего для оценки применяются новые данные либо для тестирования и обучения используются разные данные.
  
    + В таблице, будут сохранены результаты прогноза _taxiscoreOutput_. Обратите внимание, что схема для этой таблицы не определены при создании с помощью rxSqlServerData. Схемы получаются из rxPredict выходные данные.
  
    + Чтобы создать таблицу, которая хранит прогнозируемые значения, имя входа SQL, выполнение функции данных rxSqlServer требуются привилегии DDL в базе данных. Если имя входа не может создать таблицы, инструкция завершится ошибкой.

2. Вызовите функцию [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) , чтобы создать результаты.

    ```R
    rxPredict(modelObject = logitObj,
        data = sql_feature_ds,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Если инструкция выполняется успешно, он займет некоторое время для запуска. После завершения можно открыть SQL Server Management Studio и убедитесь, что таблица была создана, и что он содержит столбец оценки и другие ожидаемый результат.

## <a name="plot-model-accuracy"></a>Точность модели построения

Чтобы получить представление о точности модели, можно использовать [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) функции для построения кривой операционной получателя. Поскольку rxRoc является одним из новых функций, предоставляемых пакета RevoScaleR с поддержкой контекстах удаленных вычислений, у вас есть два варианта:

+ Функция rxRoc графика, выполняются в контексте удаленных вычислений и возвращать графика на локальный клиентский компьютер.

+ Также можно импортировать данные на клиентский компьютер R и использовать другие функции построения диаграмм R для создания графика производительности.

В этом разделе экспериментов с обоих методов.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Построение диаграммы в удаленном контексте вычислений (SQL Server)

1. Вызовите функцию rxRoc и предоставляют данные, определенные ранее в качестве входных данных.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Этот вызов возвращает значения, используемые при вычислении ROC диаграммы. Столбец меток отличается _чаевых оставил зависимости_, содержит фактические результаты, вы пытаетесь прогнозирования, пока _Оценка_ столбец содержит прогноз.

2. На самом деле построения диаграммы, можно сохранить объект ROC и создайте его с `plot` функции. Граф создается в контексте удаленного вычислений и возвращается к среде R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Просмотр графика, открыв графического устройства R или щелкнув **построения** окна в RStudio.

    ![Построение ROC для модели](media/rsql-e2e-rocplot.png "Построение ROC для модели")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Создание диаграмм в локальном контексте вычислений с помощью данных из SQL Server

1. Локальный Контекст вычислений происходит так же. Вы используете [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) функцию для приведения в локальной среде R указанных данных.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Используя данные в локальной памяти, загрузить **ROCR** пакета и использовать для создания некоторых новых прогнозов прогнозирующую функцию из этого пакета.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Создание локального построения, на основе значений, хранящихся в выходной переменной `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Построение графиков производительности модели с помощью R](media/rsql-e2e-performanceplot.png "Построение графиков производительности модели с помощью R")

> [!NOTE]
> Диаграммы могут отличаться от этого, в зависимости от количества точек данных, который использовался.

## <a name="deploy-the-model"></a>Развертывание модели

После построения модели и возможно установить, что оно работает хорошо, может потребоваться развернуть ее на узле, где пользователи или пользователи в вашей организации можно сделать при использовании модели, или может быть обучение и повторной калибровки модели на регулярной основе. Этот процесс иногда называется *ввод в эксплуатацию* модели.

Поскольку [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяет вызывать модели R с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимой процедуры можно легко использовать R в клиентском приложении.

Однако перед вызовом модели из внешнего приложения необходимо сохранить ее в базе данных, используемой в рабочей среде. В службах [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]модели обучения хранятся в двоичной форме в одном столбце типа **varbinary(max)**.

Таким образом, для перемещения модели обучения из среды R в SQL Server необходимо выполнить следующие действия:

+ сериализовать модель в шестнадцатеричную строку;

+ передать сериализованный объект в базу данных;

+ сохранить модель в столбце varbinary(max).

В этом разделе вы узнаете, как сохранить модели и способа вызова для создания прогнозов.

1. Переключение обратно в локальной среде R, если вы не уже используете ее, сериализует модель и сохранить его в переменной.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Открытие соединения ODBC с помощью **RODBC**.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

    Вызов RODBC можно опустить, если уже загружен пакет.

3. Вызовите хранимую процедуру, созданные сценария PowerShell, чтобы сохранить двоичное представление модели в столбце в базе данных.

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

    Для сохранения модели в таблице требуется только инструкция INSERT. Однако это проще, когда в оболочку в хранимой процедуре, такие как _PersistModel_.

    > [!NOTE]
    > Если возникает ошибка, например, «разрешение на выполнение запрещен в объекте PersistModel», убедитесь, что имя входа имеет разрешение. Можно предоставить явные разрешения на только что хранимую процедуру, выполнив инструкцию T-SQL, следующим образом:`GRANT EXECUTE ON [dbo].[PersistModel] TO <user_name>`

4. После создания модели и хранится в базе данных, ее можно было вызывать напрямую из [!INCLUDE[tsql](../../includes/tsql-md.md)] кода, с помощью системной хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    Тем не менее с помощью любой модели часто позволяет упростить входного запроса и вызова для модели, а также другие параметры в пользовательской хранимой процедуры.

    Ниже приведен полный код один такой хранимой процедуры. Рекомендуется создать хранимую процедуру, подобные данному, чтобы упростить управление и обновление моделей R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

    ```tsql
    CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)
    AS
    BEGIN
      SET NOCOUNT ON;
      INSERT INTO nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
    END
    ```

  > [!NOTE]
  > Используйте **SET NOCOUNT ON** задает предложение, чтобы предотвратить дополнительные результирующие вмешивалась в инструкции SELECT.


В разделе Далее и последней вы узнаете, как проводить оценку сохраненную модель с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="next-lesson"></a>Следующее занятие

[Развертывание модели R и использовать в SQL](walkthrough-deploy-and-use-the-model.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Создание компонентов данных, с помощью R и SQL](walkthrough-create-data-features.md)

