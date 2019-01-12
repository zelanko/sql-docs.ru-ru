---
title: Экспорт моделей машинного Обучения Spark с MLeap
titleSuffix: SQL Server 2019 big data clusters
description: Узнайте, как экспортировать машинного обучения моделей с MLeap Spark.
author: lgongmsft
ms.author: shivprashant
ms.reviewer: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ee858f66c99ff7b85e2e6c456ad509ec7deb0a6e
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2019
ms.locfileid: "54242135"
---
# <a name="export-spark-machine-learning-models-with-mleap"></a>Экспорт машинного обучения моделей с MLeap Spark

Сценарий обычно машинного обучения включает в себя обучение в Spark и оценка модели за пределами Spark. Экспортируйте модели в формате PDF, таким образом, он может использоваться за пределами Spark. [MLeap](https://github.com/combust/mleap) – один такой формат обмена модели. Он позволяет Spark конвейеры машинного обучения и модели, экспортируемых в качестве переносимого форматов и использовать их в любой системе на основе виртуальной машины Java с `Mleap` среды выполнения.

В этом руководстве показано, как можно экспортировать с помощью Mleap моделей spark. Действия представлены ниже и углубляться в код в следующем разделе.

1. Начните с создания модели Spark. Для этого используйте **обучения, а также создание машинного обучения модели с помощью Spark [здесь.](train-and-create-machinelearning-models-with-spark.md)**
2. В качестве следующего шага мы будем **импортировать training\test данных и модели**
3. **Экспорт модели как `Mleap` пакета**. Теперь этот экспортированный пакет можно использовать для оценки за пределами spark.
4. Чтобы проверить, мы импортируем `Mleap` снова объединить назад и использовать его для оценки в Spark.

## <a name="step-1---start-by-creating-a-spark-model"></a>Шаг 1 - начните с создания модели Spark
Запустите [обучения, а также создание машинного обучения модели с помощью Spark](train-and-create-machinelearning-models-with-spark.md) для создания наборов обучения и тестирования и модель и сохранить в хранилище HDFS. Модели должно быть экспортировано как `AdultCensus.mml` под `spark_ml` каталога.

## <a name="step-2---import-the-trainingtest-data-and-the-model"></a>Шаг 2 - Импорт training\test данных и модели

Шаг 1 создан `AdultCensus.mml`, который представляет собой модель spark. 

На этом этапе импорта модели ее spark.

```python
import mleap.pyspark
from mleap.pyspark.spark_support import SimpleSparkSerializer
from pyspark.ml import PipelineModel

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

print("load pyspark model from hbfs")
model = PipelineModel.load(model_fs)
print("Model is " , model)
print("Model stages", model.stages)
```

## <a name="step-3---export-the-model-as-mleap-bundle"></a>Шаг 3 — экспортировать модель в качестве `Mleap` пакета

Экспорт модели Spark как переносимом `Mleap` моделировать и сохранить его в локальном хранилище. Опубликовать этот шаг, она доступна в переносимом `Mleap` форматирования и может использоваться за пределами Spark.

```python
import os

#Get the train and test datasets

# Write the train and test data sets to intermediate storage

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train = spark.read.orc(train_data_path)
test = spark.read.orc(test_data_path)

print("train: ({}, {})".format(train.count(), len(train.columns)))
train.printSchema()

print("test: ({}, {})".format(test.count(), len(test.columns)))
test.printSchema()

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# remove an old model file, if needed.
try:
    os.remove(model_file)
except OSError:
    pass

model_file_path = "jar:file:{}".format(model_file)
model.serializeToBundle(model_file_path, model.transform(train))

```

Сохранение `Mleap` пакет с локального компьютера в hdfs

```python
print("persist the mleap bundle from local to hdfs")
from subprocess import Popen, PIPE
proc = Popen(["hadoop", "fs", "-put", "-f", model_file, os.path.join("/spark_ml", model_name_export)], stdout=PIPE, stderr=PIPE)
s_output, s_err = proc.communicate()
if(s_err):
    print("Error when storing to HDFS")
```

## <a name="step-3---validate-by-importing-the-mleap-bundle-and-scoring-in-spark"></a>Шаг 3 - Проверьте, Импорт `Mleap` пакета и счет в Spark
На шаге 2, мы уже экспорта модели в переносимом `Mleap` формат, который может использоваться за пределами Spark. На этом шаге мы импортируем `Mleap` сериализован в Spark и использовать его в Spark для оценки в тестовом наборе.
   
```python
model_deserialized = PipelineModel.deserializeFromBundle(model_file_path)
print("The deserialized model is ", model_deserialized)
print("The deserialized model stages are", model_deserialized.stages)

from pyspark.ml.evaluation import BinaryClassificationEvaluator

# make prediction
pred = model_deserialized.transform(test)


# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Results of using the model score test set")
print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```

## <a name="references"></a>Ссылки

* [Приступая к работе с записные книжки PySpark](notebooks-guidance.md)
* [Обучение и создание модели машинного обучения с помощью Spark](train-and-create-machinelearning-models-with-spark.md)
