---
title: Оценки в реальном времени в SQL Server машинного обучения | Документация Майкрософт
description: Создание прогнозов с помощью sp_rxPredict, количественная оценка входных данных dta к предварительно обученной модели, написанные на языке R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d5a3d0318f925918ef98ae18744e4287d6b81108
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2018
ms.locfileid: "40394377"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Оценка с sp_rxPredict в SQL Server машинного обучения в реальном времени
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, каким образом оценки в реальном времени работает для реляционных данных SQL Server, с помощью машинного обучения моделей написаны в R. 

> [!Note]
> Собственная Оценка — это специальные реализация оценки в реальном времени, использующего функции ПРОГНОЗИРОВАНИЯ T-SQL в машинном коде для оценки очень быстро. Дополнительные сведения и доступности, см. в разделе [собственной оценки](sql-native-scoring.md).

## <a name="how-real-time-scoring-works"></a>Как оценка в реальном времени работает

Оценки в реальном времени поддерживается в SQL Server 2017 и SQL Server 2016 к конкретным типам моделей основаны на функциях RevoScaleR или MicrosoftML, такие как [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) или [rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Собственные библиотеки C++ используется для формирования оценок, на основе ввода пользователя, для машинного обучения модели, сохраненной в специальных двоичном формате.

Поскольку обученной модели можно использовать для оценки без вызова внешней языковой среды выполнения, сокращается объем работ нескольких процессов. Это поддерживает значительно повысить производительность прогнозирования для оценки сценариев рабочей среды. Так как данные никогда не покидает SQL Server, результаты можно создается и вставляется в таблицу без преобразования любых данных между R и SQL.

Оценки в реальном времени — это многоэтапный процесс:

1. Хранимая процедура, выполняющий оценки необходимо включить на основе каждой базы данных.
2. Загрузите предварительно обученной модели в двоичном формате.
3. Укажите новые входные данные, табличном, так и для одной строки, в качестве входных данных в модели.
4. Для формирования оценок sp_rxPredict вызовите хранимую процедуру.

## <a name="get-started"></a>Начало работы

Примеры кода и инструкции, см. в разделе [выполнении собственной оценки или оценки в реальном времени](r/how-to-do-realtime-scoring.md).

Пример того, как rxPredict может использоваться для оценки, см. в разделе [сквозное окончания ссуды списания кредита прогноза построен с помощью Azure HDInsight кластеров Spark и служба SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Если вы работаете исключительно в коде R, можно также использовать [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) функции для быстрой оценки.

## <a name="requirements"></a>Требования

Оценки в реальном времени поддерживается на следующих платформах:

+ Службы машинного обучения SQL Server 2017
+ SQL Server R Services 2016, и обновить компоненты R 9.1.0 или более поздней версии

На сервере SQL Server необходимо включить функцию в режиме реального времени оценки заранее добавить библиотеки основанных на среде CLR для SQL Server.

Сведения о оценки в реальном времени в распределенной среде на основе Microsoft R Server см. [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) функции в [пакет mrsDeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), который поддерживает Публикация моделей для оценки в реальном времени как новую веб-службы, работающей на сервере R.

### <a name="restrictions"></a>Ограничения

+ Обучение модели должен быть на основе заранее с помощью одного из поддерживаемых **rx** алгоритмы. Дополнительные сведения см. в разделе [Поддерживаемые алгоритмы](#bkmk_rt_supported_algos). Оценки в реальном времени с `sp_rxPredict` поддерживает алгоритмов RevoScaleR и MicrosoftML.

+ Модель должна быть сохранена с помощью новых функций сериализации: [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R, и [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрого оценки.

+ Оценки в реальном времени не использует интерпретатор; Таким образом любые функции, которые могут потребовать интерпретатора не поддерживается на этапе оценки.  Они могут включать:

  + Моделирует использование `rxGlm` или `rxNaiveBayes` алгоритмы в настоящее время не поддерживаются

  + RevoScaleR моделей, которые используют функции преобразования R или формулу, которая содержит преобразования, такие как <code>A ~ log(B)</code> не поддерживаются в оценки в реальном времени. Чтобы использовать модель этого типа, рекомендуется выполнять преобразование на входные данные перед их передачей для оценки в реальном времени.

+ Оценки в реальном времени, в настоящее время оптимизирован для быстрого прогнозирования на основе небольших наборов данных, от небольшое количество строк до сотен тысяч строк. На больших наборах данных, с помощью [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) могут выполняться быстрее.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-real-time-scoring"></a><a name="bkmk_rt_supported_algos">Алгоритмы, поддерживающие оценки в реальном времени

+ RevoScaleR моделей

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Модели, отмеченные \* также поддерживают собственной оценки с помощью функции PREDICT.

+ MicrosoftML моделей

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Преобразования, предоставляемые MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [Concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Типы модели не поддерживается

Оценки в реальном времени не поддерживается для преобразования R, отличного от перечисленных явным образом в предыдущем разделе. 

Для разработчиков, привыкших к работе с RevoScaleR и другие библиотеки R характерные для Майкрософт, включают неподдерживаемых функций `rxGlm` или `rxNaiveBayes` алгоритмы в RevoScaleR, модели PMML и других моделей, созданных с помощью других библиотек R из CRAN или Другие репозитории.

### <a name="known-issues"></a>Известные проблемы

+ `sp_rxPredict` Возвращает сообщение неточные при передается значение NULL в качестве модели: «System.Data.SqlTypes.SqlNullValueException:Data в Null».

## <a name="next-steps"></a>Следующие шаги

[Как сделать оценки в реальном времени](r/how-to-do-realtime-scoring.md)
