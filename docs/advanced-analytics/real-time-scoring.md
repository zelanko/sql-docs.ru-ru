---
title: "В реальном времени оценки | Документы Microsoft"
ms.custom: 
ms.date: 11/03/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 3fce545d18876014e577b1f4e67800d4940881f3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="realtime-scoring"></a>Оценки в реальном времени

В этом разделе рассматриваются функции, доступные в SQL Server 2016 и 2017 г. SQL Server, поддерживает оценки моделей машинного обучения в почти в реальном времени.

> [!TIP]
> Оценки собственного — специальные реализация оценки, в реальном времени использует собственную функцию ПРОГНОЗИРОВАНИЯ T-SQL для оценки очень быстро и доступна только в 2017 г. SQL Server. Дополнительные сведения см. в разделе [оценки собственного](sql-native-scoring.md).

## <a name="how-realtime-scoring-works"></a>Как работает в режиме реального времени оценки

В реальном времени оценки поддерживается в 2017 г. SQL Server и SQL Server 2016 на типах моделей, созданных с помощью алгоритмов RevoScaleR или MicrosoftML оценочных (). Он использует собственные библиотеки C++ для формирования оценок, на основе ввода пользователя для машинного обучения модели, хранящихся в специальных двоичном формате.

Поскольку обученной модели можно использовать для оценки без вызова внешних CLR-среда, сокращаются издержки, связанные с несколькими процессами. Это обеспечивает поддержку значительно повысить производительность прогноза для оценки сценарии производства. Поскольку данные никогда не покидает SQL Server, результаты могут возникать и вставить в новую таблицу без преобразования любых данных между R и SQL Server.

Оценки в реальном времени представляет собой многоэтапный процесс.

1. Хранимая процедура, выполняющий оценки необходимо включить отдельно для каждой базы данных.
2. Можно загрузить предварительно обученной модели в двоичном формате.
3. Укажите новые входные данные, табличные или одной строки, в качестве входного для модели.
4. Для формирования оценок sp_rxPredict вызовите хранимую процедуру.

## <a name="get-started"></a>Начало работы

Примеры кода и инструкции см. в разделе [способы выполнения собственного оценки или оценки в реальном времени](r/how-to-do-realtime-scoring.md).

Примером как rxPredict можно использовать для оценки, см. в разделе [начала до окончания кредитов ChargeOff прогноза построен с использованием Azure HDInsight Spark кластеров и службы R SQL Server 2016](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Если вы работаете исключительно в коде R, можно также использовать [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) функции для быстрой оценки.

## <a name="requirements"></a>Требования

В реальном времени оценки поддерживается на этих платформах:

+ Службы машинного обучения SQL Server 2017
+ SQL Server R Services 2016 при обновлении экземпляра служб R на сервере Microsoft R 9.1.0 или более поздней версии
+ Сервер машинного обучения (автономный)

На сервере SQL Server необходимо включить в реальном времени, заранее оценки компонентов. Это происходит потому данной функции требуется установка библиотек среды CLR в SQL Server.

Сведения, касающиеся в реальном времени оценки в распределенной среде, в зависимости от Microsoft R Server можно найти [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) функции в [mrsDeploy пакета](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), который поддерживает Публикация модели для оценки в качестве новой веб-службы, запущенные на сервере R в реальном времени.

### <a name="restrictions"></a>Ограничения

+ Модель должна обучена заранее с помощью одного из поддерживаемых **rx** алгоритмы. Дополнительные сведения см. в разделе [поддерживается алгоритмы](#bkmk_rt_supported_algos). В реальном времени оценки с `sp_rxPredict` поддерживает алгоритмы RevoScaleR и MicrosoftML.

+ Модель должна быть сохранена с помощью новых функций сериализации: [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R, и [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации были оптимизированы для поддержки быстрой оценки.

+ В реальном времени оценки не использует интерпретатор интерпретатор; Таким образом любые функции, которые могут потребовать интерпретатор не поддерживается на этапе оценки.  Они могут включать:

  + Модели с помощью `rxGlm` или `rxNaiveBayes` алгоритмы в настоящее время не поддерживаются

  + RevoScaleR моделей, использующих функцию преобразования R или формулу, которая содержит преобразования, например <code>A ~ log(B)</code> не поддерживаются в режиме реального времени оценки. При использовании этого типа модели, рекомендуется выполнять преобразование на для ввода данных перед их передачей в реальном времени оценки.

+ В настоящее время оценки в реальном времени оптимизирован для быстрого прогнозов на небольшие наборы данных, от нескольких строк до сотен тысяч строк. В очень больших наборов данных, с помощью [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) могут выполняться быстрее.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-realtime-scoring"></a><a name="bkmk_rt_supported_algos">Алгоритмы, поддерживающие оценки в реальном времени

+ RevoScaleR моделей

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)\*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)\*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)\*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Модели, отмеченные \* также поддерживает собственный оценки с помощью функции ПРОГНОЗА.

+ MicrosoftML моделей

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Преобразования, предоставляемый MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Типы моделей не поддерживается

Приведенные ниже типы моделей не поддерживаются:

+ Моделей, которые содержат другие неподдерживаемые типы преобразований R
+ Модели с помощью `rxGlm` или `rxNaiveBayes` алгоритмы в RevoScaleR
+ PMML модели
+ Модели, созданные с помощью других библиотек R из CRAN или другие репозитории
+ Моделей, которые содержат любого другого вида преобразования R, отличного от перечисленных здесь

### <a name="known-issues"></a>Известные проблемы

+ `sp_rxPredict`Возвращает сообщение неточными при передаче значения NULL в качестве модели: «System.Data.SqlTypes.SqlNullValueException:Data в Null».

## <a name="next-steps"></a>Следующие шаги

[Как сделать оценки в реальном времени](r/how-to-do-realtime-scoring.md)
