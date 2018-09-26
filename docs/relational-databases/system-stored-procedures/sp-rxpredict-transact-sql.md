---
title: sp_rxPredict | Документация Майкрософт
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a8b23fe592b7e7fc90f2e3229d71a805f7332f4d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713866"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Создает прогнозируемое значение для указанного входного, состоящий из машинного обучения модели, сохраненной в двоичном формате в базе данных SQL Server.

Предоставляет оценку на R и Python моделей машинного обучения в практически в реальном времени. `sp_rxPredict` Хранимая процедура, предоставленные как оболочка для `rxPredict` функции R в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)и [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) функции Python в [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Он создается на языке C++ и оптимизирован специально для оценки операций.

Несмотря на то, что модели должны создаваться с помощью R или Python, когда он сериализуется и сохраняется в двоичном формате на целевой экземпляр ядра СУБД, его можно будет использовать из этого экземпляра компонента database engine, даже в том случае, если не установлена интеграция R или Python. Дополнительные сведения см. в разделе [оценки в реальном времени с sp_rxPredict](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).


## <a name="syntax"></a>Синтаксис

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Аргументы

**model**

Предварительно обученной модели в поддерживаемом формате. 

**input**

Допустимый SQL-запрос

### <a name="return-values"></a>Возвращаемые значения

Возвращается столбец оценки, а также любой сквозные столбцы из источника входных данных.
Дополнительные столбцы, например доверительный интервал оценки, могут быть возвращены, если алгоритм поддерживает создание таких значений.

## <a name="remarks"></a>Примечания

Чтобы включить использование хранимой процедуры, необходимо включить SQLCLR в экземпляре.

> [!NOTE]
> Существуют проблемы безопасности, которые Включение этого параметра. Использовать альтернативную реализацию, такие как [ПРОГНОЗИРОВАНИЯ Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017) работать, если на сервере не включены SQLCLR.

Нужные пользователю `EXECUTE` разрешение в базе данных.


### <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

Для создания и обучения модели, используйте один из поддерживаемых алгоритмов для R или Python, предоставляемые [SQL Server 2016 R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services?view=sql-server-2017), [SQL Server 2016 R Server (изолированный)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016), [машины SQL Server 2017 Изучение служб (R или Python)](https://docs.microsoft.com//sql/advanced-analytics/what-is-sql-server-machine-learning?view=sql-server-2017), или [сервера SQL Server 2017 (изолированная версия) (R или Python)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2017).


#### <a name="r-revoscaler-models"></a>R: модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R: MicrosoftML моделей

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R: предоставляемые MicrosoftML преобразования

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [Concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: revoscalepy моделей

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>Python: microsoftml моделей

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python: Предоставляемые microsoftml преобразования

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [Concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-referencee/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Типы модели не поддерживается

Не поддерживаются следующие модели:

+ Моделирует использование `rxGlm` или `rxNaiveBayes` алгоритмы в RevoScaleR
+ Модели PMML в R
+ Модели, созданные с помощью других сторонних библиотек 

## <a name="examples"></a>Примеры

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Кроме того, что допустимый SQL-запрос, входные данные в *@inputData* должна включать столбцы, которые совместимы со столбцами в сохраненную модель.

`sp_rxPredict` поддерживает только следующие типы .NET столбца: double, float, short, ushort, long, ulong и строка. Может потребоваться отфильтровать неподдерживаемые типы входных данных перед его использованием для оценки в реальном времени. 

  Сведения о соответствующих типов SQL, см. в разделе [сопоставления типов SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [сопоставление данных параметров CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

