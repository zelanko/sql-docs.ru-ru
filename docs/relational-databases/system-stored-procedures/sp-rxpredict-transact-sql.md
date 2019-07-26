---
title: sp_rxPredict | Документация Майкрософт
ms.date: 07/24/2019
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
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9cd9bb481ec54f9d99c80aba54241827c2a118cf
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471070"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Создает прогнозируемое значение для заданного ввода, состоящего из модели машинного обучения, хранящейся в двоичном формате в базе данных SQL Server.

Обеспечивает оценку моделей машинного обучения R и Python практически в реальном времени. `sp_rxPredict``rxPredict` — это хранимая процедура, предоставляемая как оболочка для функции R в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package), а также функция [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) Python в [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Она написана на C++ языке и оптимизирована специально для операций оценки.

Несмотря на то, что модель должна быть создана с помощью R или Python, после ее сериализации и сохранения в двоичном формате в целевом экземпляре ядра СУБД его можно использовать в экземпляре ядра СУБД, даже если интеграция R или Python не установлена. Дополнительные сведения см. [в статье Оценка в реальном времени с помощью sp_rxPredict](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

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

Чтобы создать и обучить модель, используйте один из поддерживаемых алгоритмов для R или Python, предоставляемый [службами SQL Server 2016 r](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services?view=sql-server-2017), [SQL Server 2016 r Server (изолированный)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016), [SQL Server 2017 службы машинного обучения (R или Python)](https://docs.microsoft.com//sql/advanced-analytics/what-is-sql-server-machine-learning?view=sql-server-2017)или [SQL Server 2017. Сервер (изолированный) (R или Python)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2017).

#### <a name="r-revoscaler-models"></a>CЕРВЕРНЫЙ Модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [рксбтрис](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>CЕРВЕРНЫЙ Модели MicrosoftML

  + [рксфасттрис](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [рксфастфорест](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [ркслогистикрегрессион](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [ркснеуралнет](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [рксфастлинеар](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>CЕРВЕРНЫЙ Преобразования, предоставляемые MicrosoftML

  + [феатуризетекст](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [сцеплен](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [категорикалхаш](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [селектфеатурес](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

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

#### <a name="python-transformations-supplied-by-microsoftml"></a>Языке Преобразования, предоставляемые microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [сцеплен](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Неподдерживаемые типы моделей

Следующие типы моделей не поддерживаются:

+ Модели, `rxGlm` использующие алгоритмы или `rxNaiveBayes` в RevoScaleR
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

В дополнение к допустимому SQL-запросу входные данные *@inputData* должны включать столбцы, совместимые со столбцами в хранимой модели.

`sp_rxPredict`поддерживает только следующие типы столбцов .NET: Double, float, Short, ushort, Long, ulong и String. Может потребоваться отфильтровать неподдерживаемые типы во входных данных, прежде чем использовать их для оценки в реальном времени. 

  Сведения о соответствующих типах SQL см. в разделе [Сопоставление типов SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [сопоставление данных параметров CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

