---
title: "Шаг 6: Ввода в эксплуатацию модели Python, с помощью SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 56a0ae3bab6e8a60221f34c954adc661d2d0ddca
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="step-6-operationalize-the-python-model-using-sql-server"></a>Шаг 6: Ввода в эксплуатацию модели Python, с помощью SQL Server

В этой статье является частью учебника [analytics Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы научитесь *ввода в эксплуатацию* модели, обучение и сохранен в предыдущем шаге.

В этом сценарии ввода в эксплуатацию означает развертывание модели в рабочей среде для оценки. Интеграция с SQL Server делает это довольно просто, так как код Python можно внедрять в хранимой процедуре. Для получения прогнозов из модели, основанной на новые входные данные, вызовите хранимую процедуру из приложения и передаются новые данные.

На этом занятии показано два способа для создания прогнозов на основе модели Python: пакетной обработки оценки и оценки по строкам.

- **Массовая оценка:** для предоставления нескольких строк входных данных, передать запрос SELECT в качестве аргумента хранимой процедуры. Результатом является таблица наблюдений, соответствующий входных вариантов.
- **Отдельные оценки:** передать набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.

Весь код Python, необходимый для оценки предоставляется как часть хранимой процедуры.

| Имя хранимой процедуры | Пакет или один | Источник модели|
|----|----|----|
|PredictTipRxPy|пакет (1)| revoscalepy модели|
|PredictTipSciKitPy|пакет (1) |scikit-модель|
|PredictTipSingleModeRxPy|одна строка| revoscalepy модели|
|PredictTipSingleModeSciKitPy|одна строка| scikit-модель|

## <a name="batch-scoring"></a>Массовая оценка

Первые две хранимые процедуры иллюстрируют базовый синтаксис для упаковки вызова прогноза Python в хранимой процедуре. Оба вызова хранимых процедур необходимо таблицу данных в качестве входных данных.

- Имя точную модель для использования предоставляется как входной параметр хранимой процедуры. Хранимая процедура загружает сериализованной модели из таблицы базы данных `nyc_taxi_models`.table, с помощью инструкции SELECT в хранимой процедуре.
- Сериализованный модель сохраняется в переменной Python `mod` для дальнейшей обработки с помощью Python.
- Будут получены новые случаи, которые должны быть рассчитаны с [!INCLUDE[tsql](../../includes/tsql-md.md)] запрос, указанный в `@input_data_1`. По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`.
- Оба хранимой процедуры используйте функции из `sklearn` для расчета показателя точности, AUC (площадь под кривой). Точность метрик, таких как AUC возможно только при указании целевой метке ( _чаевых оставил зависимости_ столбца). Прогнозы не обязательно целевой метке (переменной `y`), но не метрики расчета точности.

    Таким образом, при отсутствии целевой метки данных для оценки можно изменить хранимую процедуру, чтобы удалить AUC вычисления и возвращают только вероятности совет от возможностей (переменная `X` в хранимой процедуре).

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

Хранимая процедура должна уже были созданы для вас. Если не удается найти его, выполните следующие инструкции T-SQL для создания хранимых процедур.

Эта хранимая процедура требует модель, основанную на scikit-узнать пакета, так как оно использует функции, относящиеся к этому пакету:

+ Передаваемый кадра данных, содержащий входные данные `predict_proba` функции модели логистической регрессии, `mod`. `predict_proba` Функции (`probArray = mod.predict_proba(X)`) возвращает **float** , представляет вероятность того, предоставляемую совет (сумма).

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

### <a name="predicttiprxpy"></a>PredictTipRxPy

Эта хранимая процедура использует такими же входными и тот же тип оценки как предыдущие хранимая процедура создается, но использует функции из **revoscalepy** пакет, в состав SQL Server машинного обучения.

> [!NOTE] 
> Между предыдущих версиях и RTM-версии, чтобы отразить изменения в пакете revoscalepy слегка измененного кода для этой хранимой процедуры. В разделе [изменения](#changes) таблица содержит дополнительные сведения.

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
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict(mod, X)
      prob_list = prob_array["tipped_Pred"].values 
      
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

## <a name="run-batch-scoring-using-a-select-query"></a>Выполнения массовой оценки с помощью запроса SELECT

Хранимые процедуры **PredictTipSciKitPy** и **PredictTipRxPy** требуется два входных параметра: 

- Запрос, получающий данные для оценки
- Имя обученной модели

Передавая эти аргументы в хранимую процедуру, можно выбрать конкретной модели или изменить данные, используемые для оценки.

1. Для использования **scikit-Узнайте** модель для оценки, вызовите хранимую процедуру **PredictTipSciKitPy**, передав имя модели и строку запроса в качестве входных данных.

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    Хранимая процедура возвращает прогнозируемые значения вероятности для каждого маршрута, переданные как часть входного запроса. 
    
    При использовании среды SSMS (SQL Server Management Studio) для выполнения запросов вероятности будет отображаться в виде таблицы **результатов** области. **Сообщений** области выводит метрики точности (AUC или площадь под кривой) со значением около 0.56.

2. Для использования **revoscalepy** модель для оценки, вызовите хранимую процедуру **PredictTipRxPy**, передав имя модели и строку запроса в качестве входных данных.

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Оценки одной строки

В некоторых случаях вместо оценки пакета может потребоваться для передачи в одном случае извлечение значений из приложения и возвращение одного результата на основе их значений. Например можно настроить Excel лист, веб-приложения или отчета для вызова хранимой процедуры и передайте ему входные данные, типизированные или выбранных пользователей.

В этом разделе вы узнаете, как создать единичные прогнозы путем вызова две хранимые процедуры:

+ [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) предназначен для оценки одной строки с помощью scikit-модель.
+ [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy) предназначен для оценки одной строки с помощью модели revoscalepy.
+ Если модель не обучена еще, вернуться к [шаг 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

Обе модели принимают ряд одного значения, такие как count пассажира, расстояние маршрута и так далее. Табличная функция `fnEngineerFeatures`, используется для преобразования значения широты и долготы из входных данных в новую функцию, прямой расстояние. [Занятие 4](sqldev-py4-create-data-features-using-t-sql.md) содержится описание этой функции, возвращающие табличные значения.

Обе хранимой процедуры создать оценку на основе модели Python.

> [!NOTE]
> 
> Важно предоставить входных признаков, необходимые для модели Python при вызове хранимой процедуры из внешнего приложения. Чтобы избежать ошибок, может потребоваться привести или преобразовать входные данные с типом данных Python, помимо проверка типа данных и длины данных.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Внимательно просмотрите код, выполняющий оценки с помощью хранимой процедуры **scikit-узнать** модели.

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

Следующая хранимая процедура выполняет вычисления с помощью **revoscalepy** модели.

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
      from revoscalepy.functions.RxPredict import rx_predict;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict(mod, X)
      
      probList = []
      prob_list = prob_array["tipped_Pred"].values
      
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

### <a name="generate-scores-from-models"></a>Формировать оценки на основе моделей

После создания хранимой процедуры можно легко для создания оценки на основе либо модели. Просто откройте новый **запроса** окно и введите или вставьте параметров для каждого из столбцов признаков. Семь необходимых значений для этих столбцов компонентов, в порядке:
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Для создания прогноза с помощью **revoscalepy** модели, выполните следующую инструкцию:
  
    ```SQL
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Для создания оценки с помощью **scikit-узнать** модели, выполните следующую инструкцию:

    ```SQL
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

Выходные данные обе процедуры — вероятность совета оплачиваемой для маршрута такси с указанными параметрами и компонентами.

### <a name="changes"></a>Изменения

В этом разделе перечислены изменения в код, используемый в этом учебнике. Эти изменения были внесены в соответствии с последней **revoscalepy** версии. Дополнительные сведения о API см [Python функции Справочник по библиотеке](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference).

| Изменить сведения о | Примечания|
| ----|----|
| Удалить `import pandas` всех выборок| pandas теперь загрузки по умолчанию|
| функция `rx_predict_ex` изменено на`rx_predict`| Требуется RTM и предварительных версий`rx_predict_ex`|
| функция `rx_logit_ex` изменено на`rx_logit`| Требуется RTM и предварительных версий`rx_logit_ex`|
| ` probList.append(probArray._results["tipped_Pred"])`изменено на`prob_list = prob_array["tipped_Pred"].values`| обновления для API|

Если вы установили службы Python, с помощью предварительной версии SQL Server 2017 г., рекомендуется обновить. Можно также обновить только компоненты Python и R с помощью последний выпуск сервера Machine обучения. Дополнительные сведения см. в разделе [с использованием привязки для обновления экземпляра SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="conclusions"></a>Заключение

В этом учебнике вы узнали, как работать с кода Python, встроенные в хранимых процедурах. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] упрощает развертывание Python моделей для прогнозирования и включения переподготовки модели в рамках корпоративных данных рабочего процесса.

## <a name="previous-step"></a>Предыдущий шаг

[Шаг 5: Обучение и сохранить модель Python](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>См. также раздел

[Машинного обучения служб с Python](../python/sql-server-python-services.md)
