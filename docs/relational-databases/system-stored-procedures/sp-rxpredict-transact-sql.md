---
title: sp_rxPredict | Документация Майкрософт
ms.date: 03/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning-services
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: b3f6ee7c1f0b1dc1ccbcd4db260621dc5bda3168
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750464"
---
# <a name="sp_rxpredict"></a>sp_rxPredict  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly.md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Создает прогнозируемое значение для заданного ввода, состоящего из модели машинного обучения, хранящейся в двоичном формате в базе данных SQL Server.

Обеспечивает оценку моделей машинного обучения R и Python практически в реальном времени. `sp_rxPredict`— это хранимая процедура, предоставляемая как оболочка для `rxPredict` функции R в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package), а также функция [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) Python в [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Она написана на языке C++ и оптимизирована специально для операций оценки.

Несмотря на то, что модель должна быть создана с помощью R или Python, после ее сериализации и сохранения в двоичном формате в целевом экземпляре ядра СУБД его можно использовать в экземпляре ядра СУБД, даже если интеграция R или Python не установлена. Дополнительные сведения см. [в статье Оценка в реальном времени с помощью sp_rxPredict](https://docs.microsoft.com/sql/machine-learning/real-time-scoring).

## <a name="syntax"></a>Синтаксис

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Аргументы

**model**

Предварительно обученная модель в поддерживаемом формате. 

**input**

Допустимый SQL-запрос

### <a name="return-values"></a>Возвращаемые значения

Возвращается столбец оценки, а также все передаваемые столбцы из источника входных данных.
Дополнительные столбцы оценки, например доверительный интервал, могут быть возвращены, если алгоритм поддерживает создание таких значений.

## <a name="remarks"></a>Примечания

Чтобы включить использование хранимой процедуры, в экземпляре необходимо включить SQLCLR.

> [!NOTE]
> Для енабинг этого параметра существуют последствия безопасности. Используйте альтернативную реализацию, например функцию [прогнозирования Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017) , если на сервере невозможно включить SQLCLR.

Пользователю требуется `EXECUTE` разрешение на базу данных.

### <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

Чтобы создать и обучить модель, используйте один из поддерживаемых алгоритмов для R или Python, предоставляемый [SQL Server службы машинного обучения (R или Python)](https://docs.microsoft.com/sql/machine-learning/sql-server-machine-learning-services), [SQL Server 2016 r Services](https://docs.microsoft.com/sql/machine-learning/r/sql-server-r-services), [SQL Server Machine Learning Server (автономный) (r или Python)](https://docs.microsoft.com/sql/machine-learning/r/r-server-standalone)или [SQL Server 2016 R Server (изолированный)](https://docs.microsoft.com/sql/machine-learning/r/r-server-standalone?view=sql-server-2016).

#### <a name="r-revoscaler-models"></a>R: модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R: модели MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R: преобразования, предоставляемые MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: модели revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>Python: модели microsoftml

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python: преобразования, предоставляемые microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Неподдерживаемые типы моделей

Следующие типы моделей не поддерживаются:

+ Модели, использующие `rxGlm` `rxNaiveBayes` алгоритмы или в RevoScaleR
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

В дополнение к допустимому SQL-запросу входные данные в * \@ inputData* должны включать столбцы, совместимые со столбцами в хранимой модели.

`sp_rxPredict`поддерживает только следующие типы столбцов .NET: Double, float, Short, ushort, Long, ulong и String. Может потребоваться отфильтровать неподдерживаемые типы во входных данных, прежде чем использовать их для оценки в реальном времени. 

  Сведения о соответствующих типах SQL см. в статье [Сопоставление типов SQL и CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [Сопоставление данных о параметрах CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

