---
title: Прогнозирование возможных результатов с помощью моделей Python
description: Руководство, в котором показано, как эксплуатацию внедренный скрипт PYthon в хранимые процедуры SQL Server с помощью функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 275981cbd4543263507415b5e7ba783f1ecbd8e5
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345845"
---
# <a name="run-predictions-using-python-embedded-in-a-stored-procedure"></a>Выполнение прогнозов с помощью Python Embedded в хранимой процедуре
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья является частью руководства, [в базе данных Python Analytics для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы узнаете, как *эксплуатацию* модели, которые были обучены и сохранены на предыдущем шаге.

В этом сценарии эксплуатация означает развертывание модели в рабочей среде для оценки. Интеграция с SQL Server делает это довольно простым, поскольку код Python можно внедрять в хранимую процедуру. Чтобы получить прогнозы из модели на основе новых входных данных, просто вызовите хранимую процедуру из приложения и передайте новые данные.

На этом занятии показаны два метода создания прогнозов на основе модели Python: пакетная Оценка и Оценка по строкам.

- **Пакетная Оценка:** Чтобы предоставить несколько строк входных данных, передайте запрос SELECT в качестве аргумента хранимой процедуре. Результатом является таблица наблюдений, соответствующих входным вариантам.
- **Индивидуальная оценка:** Передайте набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.

Весь код Python, необходимый для оценки, предоставляется как часть хранимых процедур.

## <a name="batch-scoring"></a>Пакетная Оценка

Первые две хранимые процедуры иллюстрируют базовый синтаксис для упаковки прогнозирующих вызовов Python в хранимой процедуре. Для обеих хранимых процедур в качестве входных данных требуется таблица.

- Имя используемой модели указывается в качестве входного параметра для хранимой процедуры. Хранимая процедура загружает сериализованную модель из таблицы `nyc_taxi_models`базы данных. Table, используя инструкцию SELECT в хранимой процедуре.
- Сериализованная модель хранится в переменной `mod` Python для дальнейшей обработки с помощью Python.
- Новые варианты, которые необходимо оценить, получаются из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса, указанного в. `@input_data_1` По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`.
- Обе хранимые процедуры используют функции `sklearn` из для вычисления метрики точности, AUC (в области кривой). Метрики точности, такие как AUC, могут быть созданы только в том случае, если вы также предоставляете целевую метку _(столбец «_ несущественные»). Для прогнозов не требуется Целевая метка ( `y`переменная), но вычисляется метрика точности.

    Поэтому, если у вас нет целевых меток для данных, которые необходимо оценить, можно изменить хранимую процедуру, чтобы удалить AUC вычисления, и вернуть только вероятности Tip из функций (переменная `X` в хранимой процедуре).

### <a name="predicttipscikitpy"></a>предикттипсЦикитпи

Ррун следующие инструкции T-SQL для создания хранимых процедур. Для этой хранимой процедуры требуется модель на основе пакета scikit-учиться, так как в ней используются функции, относящиеся к этому пакету:

+ Кадр данных, содержащий входные данные, `predict_proba` `mod`передается в функцию модели логистической регрессии. Функция (`probArray = mod.predict_proba(X)`) возвращает значение **типа float** , представляющее вероятность того, что будет предоставлена подсказка (из любой суммы). `predict_proba`

```sql
DROP PROCEDURE IF EXISTS PredictTipSciKitPy;
GO

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

### <a name="predicttiprxpy"></a>предикттипркспи

Эта хранимая процедура использует те же самые входные данные и создает тот же тип оценки, что и Предыдущая хранимая процедура, но использует функции из пакета **revoscalepy** , предоставляемого в машинном обучении SQL Server.

```sql
DROP PROCEDURE IF EXISTS PredictTipRxPy;
GO

CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
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
probList = probArray["tipped_Pred"].values 

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

## <a name="run-batch-scoring-using-a-select-query"></a>Выполнение пакетной оценки с помощью запроса SELECT

Хранимым процедурам **предикттипсЦикитпи** и **предикттипркспи** требуются два входных параметра: 

- Запрос, извлекающий данные для оценки
- Имя обученной модели

Передавая эти аргументы в хранимую процедуру, можно выбрать конкретную модель или изменить данные, используемые для оценки.

1. Чтобы использовать модель **scikit-учиться** для оценки, вызовите хранимую процедуру **предикттипсЦикитпи**, передав имя модели и строку запроса в качестве входных данных.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    Хранимая процедура возвращает прогнозируемые вероятности для каждого поездки, переданного в составе входного запроса. 
    
    Если для выполнения запросов используется среда SSMS (SQL Server Management Studio), вероятности будут отображаться в виде таблицы на панели **результатов** . На панели **сообщения** выводится метрика точности (AUC или область под кривой) со значением около 0,56.

2. Чтобы использовать модель **revoscalepy** для оценки, вызовите хранимую процедуру **предикттипркспи**, передав имя модели и строку запроса в качестве входных данных.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Оценка одной строки

Иногда вместо пакетной оценки может потребоваться передать один вариант, получить значения из приложения и возвратить один результат на основе этих значений. Например, можно настроить лист Excel, веб-приложение или отчет для вызова хранимой процедуры и передачи входных или выбранных пользователем данных.

В этом разделе вы узнаете, как создавать отдельные прогнозы путем вызова двух хранимых процедур:

+ [ПредикттипсинглемодесЦикитпи](#predicttipsinglemodescikitpy) предназначен для оценки одной строки с помощью модели scikit-учиться.
+ [Предикттипсинглемодеркспи](#predicttipsinglemoderxpy) предназначен для оценки одной строки с использованием модели revoscalepy.
+ Если вы еще не обучили модель, вернитесь к [шагу 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

Обе модели принимают в качестве входных данных ряд отдельных значений, таких как число пассажиров, расстояние поездок и т. д. Функция, возвращающая табличное значение, `fnEngineerFeatures`используется для преобразования значений широты и долготы из входных данных в новый компонент, прямое расстояние. [Занятие 4](sqldev-py4-create-data-features-using-t-sql.md) содержит описание этой возвращающей табличное значение функции.

Обе хранимые процедуры создают оценку на основе модели Python.

> [!NOTE]
> 
> Важно обеспечить все функции ввода, необходимые для модели Python при вызове хранимой процедуры из внешнего приложения. Чтобы избежать ошибок, может потребоваться привести или преобразовать входные данные в тип данных Python, а также проверить тип данных и длину данных.

### <a name="predicttipsinglemodescikitpy"></a>предикттипсинглемодесЦикитпи

Ознакомьтесь с кодом хранимой процедуры, которая выполняет оценку с помощью модели **scikit-учиться** , в течение минуты.

```sql
DROP PROCEDURE IF EXISTS PredictTipSingleModeSciKitPy;
GO

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
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
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

### <a name="predicttipsinglemoderxpy"></a>предикттипсинглемодеркспи

Следующая хранимая процедура выполняет оценку с помощью модели **revoscalepy** .

```sql
DROP PROCEDURE IF EXISTS PredictTipSingleModeRxPy;
GO

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
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
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
probList = probArray["tipped_Pred"].values

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

### <a name="generate-scores-from-models"></a>Создание оценок на основе моделей

После создания хранимых процедур можно легко создать оценку на основе любой модели. Просто откройте новое окно **запроса** и введите или вставьте параметры для каждого из столбцов компонента. Семь обязательных значений для этих столбцов функций по порядку:
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Чтобы создать прогноз с помощью модели **revoscalepy** , выполните следующую инструкцию:
  
    ```sql
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Чтобы создать оценку с помощью модели **scikit-учиться** , выполните следующую инструкцию:

    ```sql
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'SciKit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

Выходные данные обеих процедур являются вероятностью, выплачиваемой для поездки на такси с указанными параметрами или функциями.

## <a name="conclusions"></a>Заключение

В этом руководстве вы узнали, как работать с кодом Python, внедренным в хранимые процедуры. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] упрощает развертывание моделей Python для прогнозирования и включение повторного обучения модели в рамках рабочего процесса корпоративных данных.

## <a name="previous-step"></a>Предыдущий шаг

[Обучение и сохранение модели Python](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>См. также

[Расширение Python в SQL Server](../concepts/extension-python.md)
