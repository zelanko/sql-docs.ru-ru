---
title: sp_rxPredict Документы Майкрософт
ms.date: 03/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
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
monikerRange: '>=sql-server-2016||>= sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 86b9cd8a9327eb8afaf9945ca09629362062011f
ms.sourcegitcommit: 2426a5e1abf6ecf35b1e0c062dc1e1225494cbb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2020
ms.locfileid: "80517456"
---
# <a name="sp_rxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Генерирует прогнозируемое значение для данного ввода, состоящего из модели машинного обучения, хранящейся в двоичном формате в базе данных S'L Server.

Обеспечивает скоринг на r и Python моделей машинного обучения в почти в режиме реального времени. `sp_rxPredict`является сохраненной процедурой, предоставляемой `rxPredict` в качестве обертки для функции R в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML,](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)а также функции [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) Python в [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml.](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) Она написана в СЗ и оптимизирована специально для скоринговых операций.

Хотя модель должна быть создана с помощью R или Python, как только она сериализуется и хранится в двоичном формате на экземпляре движка целевой базы данных, она может быть использована из этого экземпляра движка базы данных даже тогда, когда интеграция R или Python не установлена. Для получения дополнительной информации, смотрите [в режиме реального времени забил с sp_rxPredict](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="syntax"></a>Синтаксис

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Аргументы

**model**

Предподготовленная модель в поддерживаемом формате. 

**input**

Действительный запрос S'L

### <a name="return-values"></a>Возвращаемые значения

Возвращается столбец оценки, а также любые сквозные столбцы из источника входных данных.
Дополнительные столбцы оценки, такие как доверительный интервал, могут быть возвращены, если алгоритм поддерживает генерацию таких значений.

## <a name="remarks"></a>Remarks

Для обеспечения использования сохраненной процедуры в экземпляре необходимо включить S'LCLR.

> [!NOTE]
> Есть последствия для безопасности, чтобы enabing этот вариант. Используйте альтернативную реализацию, например функцию [Transact-S'L PREDICT,](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017) если на вашем сервере не может быть включена функция S'LCLR.

Пользователю `EXECUTE` требуется разрешение в базе данных.

### <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

Для создания и обучения модели используйте один из поддерживаемых алгоритмов для R или Python, предоставляемый [сервисами обучения S'L Server 2Machine (R или Python),](https://docs.microsoft.com/sql/advanced-analytics/what-is-sql-server-machine-learning) [S'L Server 2016 R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services), [сервером s'L Server Machine Learning Server (Standalone) (Standalone) ,](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone)или [Сервером S'L 2016 R Server (Standalone).](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016)

#### <a name="r-revoscaler-models"></a>R: Модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdЛесно](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R: Модели MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R: Преобразования, поставляемые MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: revoscalepy модели

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

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python: Преобразования, поставляемые microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Неподдерживаемые типы моделей

Следующие типы моделей не поддерживаются:

+ Модели с `rxGlm` `rxNaiveBayes` использованием или алгоритмов в RevoScaleR
+ Модели PMML в R
+ Модели, созданные с использованием других сторонних библиотек 

## <a name="examples"></a>Примеры

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Помимо того, что данные по вхвошне * \@ввхотятывой* информации во вхотульских данных должны включать столбцы, совместимые с столбцоввого доносом в сохраненной модели.

`sp_rxPredict`поддерживает только следующие типы столбцов .NET: двойной, плавающий, короткий, ushort, длинный, ulong и строка. Возможно, вам придется отфильтровать неподдерживаемые типы в входных данных, прежде чем использовать их для подсчета очков в режиме реального времени. 

  Сведения о соответствующих типах SQL см. в статье [Сопоставление типов SQL и CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [Сопоставление данных о параметрах CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

