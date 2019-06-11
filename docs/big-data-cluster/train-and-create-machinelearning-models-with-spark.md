---
title: Моделей машинного Обучения Train/Create с помощью Spark
titleSuffix: SQL Server big data clusters
description: Используйте PySpark для обучения и создания моделей машинного обучения с помощью Spark в кластерах больших данных SQL Server (Предварительная версия).
author: lgongmsft
ms.author: lgong
ms.manager: craigg
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 348749b038b97138c4a6c85fd2f56b45b85c5d60
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822921"
---
# <a name="train-and-create-machine-learning-models-with-spark"></a>Обучение и создание моделей машинного обучения Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Spark в кластере SQL Server больших данных позволяет искусственного Интеллекта и машинного обучения. В примере показано, как для обучения модели машинного обучения с помощью Python в Spark (PySpark) с помощью данных, хранимых в HDFS. 

Пример — Пошаговое руководство по с помощью фрагментов кода, которые могут быть использованы из книжки Studio данных Azure и каждой ячейки выполнения сразу за раз. Дополнительные сведения о подключении с помощью Spark в записной книжке [здесь](notebooks-guidance.md)

В примере:

1. Начните с **понимание данных и прогнозирования требуемого**
2. **Отправка данных в HDFS и подготовить данные** для создания модели
3. **Выберите компоненты для использования**
4. **Разбиение данных как обучающую и тестовую выборки**
5. Собрали **конвейер машинного обучения и построения модели**
6. Используйте созданный модель для **прогнозирования**
7. На последнем этапе **сохранения созданной модели для дальнейшей**.

E2E машинного обучения включает в себя несколько дополнительных действий, просмотр данных, анализ функций, выделения и субъект-компонент, например Выбор модели. Многие из этих действий учитываются здесь для краткости.

## <a name="step-1---understanding-the-data-and-prediction-desired"></a>Шаг 1 - основные сведения о данных и прогнозирования требуемого

В этом примере используется данных adult census income из [здесь]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv ). В `AdultCensusIncome.csv`, каждая строка представляет дохода и другие характеристики, такие как возраст, часов в неделю, для образовательных учреждений, род занятий и т.д. для заданного материалы для взрослых. Построить модель, которую можно использовать для прогнозирования Если дохода. Модели принимает возраст и часов в неделю как компоненты и спрогнозировать если доход для клиента > 50 тысяч или < 50 КБ. 

## <a name="step-2---upload-the-data-to-hdfs-and-basic-explorations-on-data"></a>Шаг 2 - отправке данных в HDFS и основные просмотров данных
Из Azure Data Studio подключения к шлюзу HDFS/Spark и создайте каталог с именем `spark_ml` в HDFS. Скачайте [AdultCensusIncome.csv]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv ) на локальном компьютере и отправить в HDFS. Отправка `AdultCensusIncome.csv` к созданной папке.


Теперь можно напишите код. Можно скопировать приведенный ниже код и вставьте его в отдельных ячейках записной книжки в студии данных Azure. 

Приведенный ниже код считывает CSV-файл в кадр данных Spark. Рамками, он подсчитывает количество строк и столбцов и отобразить загруженных данных.

```python
datafile = "/spark_ml/AdultCensusIncome.csv"

#Read the data to a spark data frame.
data_all = spark.read.format('csv').options(header='true', inferSchema='true', ignoreLeadingWhiteSpace='true', ignoreTrailingWhiteSpace='true').load(datafile)
print("Number of rows: {},  Number of coulumns : {}".format(data_all.count(), len(data_all.columns)))

#Replace "-" with "_" in column names
columns_new = [col.replace("-", "_") for col in data_all.columns]
data_all = data_all.toDF(*columns_new)

#Print Schema and show top 5 row
data_all.printSchema() 
data_all.show(5)
```

## <a name="step-3---select-features-to-use"></a>Шаг 3 - Выбор компонентов для использования

На этом шаге используйте следующие два условия
1. `Label`    — Указывает значение для прогнозирования. Она представлена в виде столбца в данных.  
2. `Features` — Относится к характеристикам данных для прогнозирования. Также называется некоторое время как `predictors` 

В этом примере `Label`, является **доход** столбца. Для простоты выберите **возраст** и **hours_per_week** как `Features`. На самом деле функции выбираются, применив некоторые методы корреляции для понимания того, что лучше всего описать прогнозирующих метки.

```python
# Choose feature columns and the label column.
label = "income"
xvars = ["age", "hours_per_week"] #all numeric

print("label = {}".format(label))
print("features = {}".format(xvars))

select_cols = xvars
select_cols.append(label)
data = data_all.select(select_cols)

```

## <a name="step-4---split-as-training-and-test-set"></a>Шаг 4 - разбиение как обучающую и тестовую выборки

Для обучения модели, а остальные 25% для оценки модели используйте 75% строк. Кроме того сохраняются обучения и тестовых наборов данных для хранилища HDFS. Шаг не является обязательным, но для демонстрации показано сохранение и загрузка в формате ORC. Другие форматы, например, `Parquet` также может использоваться.

Опубликовать этот шаг, вы увидите два каталоги, созданные с именем AdultCensusIncomeTrain и AdultCensusIncomeTest

```python

# Split data into train and test.
train, test = data.randomSplit([0.75, 0.25], seed=123)

print("train ({}, {})".format(train.count(), len(train.columns)))
print("test ({}, {})".format(test.count(), len(test.columns)))

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train.write.mode('overwrite').orc(train_data_path)
test.write.mode('overwrite').orc(test_data_path)
print("train and test datasets saved to {} and {}".format(train_data_path, test_data_path))

```

## <a name="step-5---put-together-a-pipeline-and-build-a-model"></a>Шаг 5 - собрали конвейера и построить модель
[Конвейер машинного Обучения Spark](https://spark.apache.org/docs/2.3.1/ml-pipeline.html) последовательности все шаги как рабочий процесс и облегчают поэкспериментировать с различными алгоритмами и их параметрами. Следующий код сначала создает этапы и помещает эти этапы друг с другом в конвейер машинного обучения.  LogisticRegression используется для создания модели.

```python
from pyspark.ml import Pipeline, PipelineModel
from pyspark.ml.feature import OneHotEncoder, StringIndexer, VectorAssembler
from pyspark.ml.classification import LogisticRegression

reg = 0.1
print("Using LogisticRegression model with Regularization Rate of {}.".format(reg))

# create a new Logistic Regression model.
lr = LogisticRegression(regParam=reg)

dtypes = dict(train.dtypes)
dtypes.pop(label)

si_xvars = []
ohe_xvars = []
featureCols = []
for idx,key in enumerate(dtypes):
    if dtypes[key] == "string":
        featureCol = "-".join([key, "encoded"])
        featureCols.append(featureCol)
        
        tmpCol = "-".join([key, "tmp"])
        si_xvars.append(StringIndexer(inputCol=key, outputCol=tmpCol, handleInvalid="skip")) #, handleInvalid="keep"
        ohe_xvars.append(OneHotEncoder(inputCol=tmpCol, outputCol=featureCol))
    else:
        featureCols.append(key)

# string-index the label column into a column named "label"
si_label = StringIndexer(inputCol=label, outputCol='label')

# assemble the encoded feature columns in to a column named "features"
assembler = VectorAssembler(inputCols=featureCols, outputCol="features")

```

Теперь собрали конвейера. 

```python
# put together the pipeline
stages = []
stages.extend(si_xvars)
stages.extend(ohe_xvars)
stages.append(si_label)
stages.append(assembler)
stages.append(lr)
pipe = Pipeline(stages=stages)
print("Pipeline Created")

```

После создания конвейера, необходимо используйте для обучения модели.

```python
# train the model
model = pipe.fit(train)
print("Model Trained")
print("Model is ", model)
print("Model Stages", model.stages)

```

## <a name="step-6---predict-using-the-model-and-evaluate-the-model-accuracy"></a>Шаг 6 - прогнозирование при помощи модели и оценки точности модели
Приведенный ниже код использует проверочного набора данных для прогнозирования результата, используя модель, созданная на предыдущем шаге. Измеряется точность модели с `areaUnderROC` и `areaUnderPR` метрики.

```python
from pyspark.ml.evaluation import BinaryClassificationEvaluator
# make prediction
pred = model.transform(test)

# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```


## <a name="step-7---persist-the-models-to-hdfs"></a>Шаг 7 - сохранения модели в HDFS
Наконец сохранить модель в HDFS для последующего использования. Опубликовать этот шаг, созданная модель сохраняются как /spark_ml/AdultCensus.mml

```python
##NOTE: by default the model is saved to and loaded from path

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

model.write().overwrite().save(model_fs)
print("saved model to {}".format(model_fs))

# load the model file (from dbfs)
model2 = PipelineModel.load(model_fs)
assert str(model2) == str(model)
print("loaded model from {}".format(model_fs))
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о том, как приступить к работе с записные книжки PySpark, см. в разделе [использованию записных книжек](notebooks-guidance.md).