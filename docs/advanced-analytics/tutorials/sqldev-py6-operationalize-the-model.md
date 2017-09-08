---
title: "Шаг 6: Ввода в эксплуатацию модели | Документы Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b33f3876f054d7e7150a18967d5cfa37dd2d82bf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="step-6-operationalize-the-model"></a>Шаг 6. Ввод модели в эксплуатацию

На этом шаге вы научитесь *ввода в эксплуатацию* модели, обучение и сохранен в предыдущем шаге. Ввода в эксплуатацию в данном случае означает «развернуть модель в рабочей среде для оценки». Это легко сделать, если в хранимой процедуре содержится коде Python. Затем можно вызвать хранимую процедуру из приложений для создания прогнозов на новый наблюдения.

Вы узнаете двумя методами для вызова модели Python из хранимой процедуры:

- **Режим пакетной оценки**. Используйте запрос SELECT, чтобы предоставить несколько строк данных. Хранимая процедура возвращает таблицу наблюдений, соответствующую входным вариантам.
- **Режим индивидуальной оценки**. Передайте набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.

## <a name="scoring-using-the-scikit-learn-model"></a>Оценки с помощью scikit-модель

Хранимая процедура _PredictTipSciKitPy_ использует scikit-модель. Эта хранимая процедура показан основной синтаксис для упаковки вызова прогноза Python в хранимой процедуре.

- Имя модели для использования предоставляется как входной параметр хранимой процедуры. 
- Хранимая процедура затем будет загрузить сериализованный модель из таблицы базы данных `nyc_taxi_models`.table, с помощью инструкции SELECT в хранимой процедуре.
- Сериализованный модель сохраняется в переменной Python `mod` для дальнейшей обработки с помощью Python.
- Будут получены новые случаи, которые должны быть рассчитаны с [!INCLUDE[tsql](../../includes/tsql-md.md)] запрос, указанный в `@input_data_1`. По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`.
- Этот кадр данных передается `predict_proba` функции модели логистической регрессии, `mod`, которой был создан с помощью scikit-модель. 
- `predict_proba` Функции (`probArray = mod.predict_proba(X)`) возвращает **float** , представляет вероятность того, предоставляемую совет (сумма).
- Хранимая процедура также вычисляет точность метрики, AUC (площадь под кривой). Точность метрик, таких как AUC возможно только при указании целевой метки (т. е. скошенные столбец). Прогнозы не обязательно целевой метке (переменной `y`), но не метрики расчета точности.

  Таким образом, если у вас нет целевого метки данных для оценки, можно изменить хранимую процедуру для удаления вычисления AUC и просто возвращают вероятности совет от возможностей (переменная `X` в хранимой процедуре).

```SQL
CREATE PROCEDURE [dbo].[PredictTipSciKitPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
  EXEC sp_execute_external_script
    @language = N'Python',
    @script = N'
        import pickle;
        import numpy;
        import pandas;
        from sklearn import metrics
        
        mod = pickle.loads(lmodel2)
        
        X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
        y = numpy.ravel(InputDataSet[["tipped"]])
        
        probArray = mod.predict_proba(X)
        probList = []
        for i in range(len(probArray)):
          probList.append((probArray[i])[1])
        
        probArray = numpy.asarray(probList)
        fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
        aucResult = metrics.auc(fpr, tpr)
        print ("AUC on testing data is: " + str(aucResult))
        
        OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
        ',  
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="scoring-using-the-revoscalepy-model"></a>Оценки с использованием модели revoscalepy

Хранимая процедура _PredictTipRxPy_ использует модель, которая была создана с помощью **revoscalepy** библиотеки. Он работает так же, как _PredictTipSciKitPy_ процедуры, но с определенными изменениями для **revoscalepy** функции.

```SQL
CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict_ex(mod, X)
      probList = []
      for i in range(len(probArray._results["tipped_Pred"])):
        probList.append((probArray._results["tipped_Pred"][i]))
      
      probArray = numpy.asarray(probList)
      fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
      aucResult = metrics.auc(fpr, tpr)
      print ("AUC on testing data is: " + str(aucResult))
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',    
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="batch-scoring-using-a-select-query"></a>Пакетная оценка с помощью запроса SELECT

Хранимые процедуры **PredictTipSciKitPy** и **PredictTipRxPy** требуется два входных параметра: 

- Запрос, получающий данные для оценки
- Имя обученной модели

В этом разделе вы узнаете, как передавать эти аргументы в хранимую процедуру, чтобы легко изменить модели и данные, используемые для оценки.

1. Определение входных данных и вызывать хранимые процедуры для оценки следующим образом. В этом примере используется хранимая процедура PredictTipSciKitPy для оценки, а также передает имя модели и строки запроса.

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    Хранимая процедура возвращает прогнозируемые значения вероятности для каждого маршрута, переданные как часть входного запроса. При использовании среды SSMS (SQL Server Management Studio) для выполнения запросов вероятности будет отображаться в виде таблицы **результатов** области. **Сообщений** области выводит метрики точности (AUC или площадь под кривой) со значением около 0.56.

2. Для использования **revoscalepy** модель для оценки, вызовите хранимую процедуру **PredictTipRxPy**, передавая модели имя и о строке запроса.

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="score-individual-rows-using-scikit-learn-model"></a>Оценка отдельные строки, с помощью scikit-модель

В некоторых случаях вместо массовой оценки, может объект необходимо передать в одном корпусе получать значения из приложения и получения одного результата на основе их значений. Например, можно настроить лист Excel, веб-приложение или отчет служб Reporting Services так, чтобы они вызывали хранимую процедуру, передавая в нее входные значения, введенные или выбранные пользователями.

В этом разделе вы узнаете, как создать единичные прогнозы путем вызова хранимой процедуры.

1. Внимательно просмотрите код хранимых процедур [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) и [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy), которые являются частью загрузки. Эти хранимые процедуры используют scikit-Дополнительные сведения и revoscalepy модели и выполнять количественную оценку следующим образом:

  - Имя модели и несколько значений одного предоставляются в виде входных данных. Эти входные данные включают пассажира count, расстояние маршрута и так далее.
  - Табличная функция `fnEngineerFeatures`, принимает входные значения и преобразует виде широт и долгот для направления расстояние. [Занятие 4](sqldev-py4-create-data-features-using-t-sql.md) содержится описание этой функции, возвращающие табличные значения.
  - Если хранимая процедура вызывается из внешнего приложения, убедитесь, что входные данные соответствует требуемые входные функции модели Python. Сюда могут относиться приведения или преобразования входных данных в тип данных Python, или проверка типа данных и длины данных.
  - Хранимая процедура создает оценку на основе хранимых модели Python.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Вот определение хранимой процедуры, которая выполняет вычисления с помощью **scikit-узнать** модели.

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeSciKitPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
  SELECT * FROM [dbo].[fnEngineerFeatures]( 
    @passenger_count,
    @trip_distance,
    @trip_time_in_secs,
    @pickup_latitude,
    @pickup_longitude,
    @dropoff_latitude,
    @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      probList = []
      probList.append((mod.predict_proba(X)[0])[1])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
    ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

### <a name="predicttipsinglemoderxpy"></a>PredictTipSingleModeRxPy

Вот определение хранимой процедуры, которая выполняет вычисления с помощью **revoscalepy** модели.

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures]( 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict_ex(mod, X)
      
      probList = []
      probList.append(probArray._results["tipped_Pred"])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

2.  Опробуйте его, откройте новый **запроса** окна, а вызов хранимой процедуры, задать для каждого из столбцов признаков.

    ```SQL
    -- Call stored procedure PredictTipSingleModeSciKitPy to score using SciKit-Learn model
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    -- Call stored procedure PredictTipSingleModeRxPy to score using revoscalepy model
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```
    
    Для этих столбцов компонентов, в порядке, семи значений:
    
    -   *passenger_count*
    -   *trip_distance*
    -   *trip_time_in_secs*
    -   *pickup_latitude*
    -   *pickup_longitude*
    -   *dropoff_latitude*
    -   *dropoff_longitude*

3. Выходные данные обе процедуры — вероятность совета оплачиваемой для маршрута такси выше параметров или функции.

## <a name="conclusions"></a>Заключение

В этом учебнике вы узнали, как работать с кода Python, встроенные в хранимых процедурах. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] упрощает развертывание Python моделей для прогнозирования и включения переподготовки модели в рамках корпоративных данных рабочего процесса.

## <a name="previous-step"></a>Предыдущий шаг
[Шаг 6. Ввод модели в эксплуатацию](sqldev-py6-operationalize-the-model.md)

## <a name="see-also"></a>См. также:

[Машинного обучения служб с Python](../python/sql-server-python-services.md)

