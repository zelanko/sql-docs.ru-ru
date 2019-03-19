---
title: Оценка с помощью sp_rxPredict хранимой процедуры - службы машинного обучения SQL Server в реальном времени
description: Создание прогнозов с помощью sp_rxPredict, оценка входных данных к предварительно обученной модели, написанные на языке R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ed1fbe8be63cd184fd49b1e76f94583bd50cf380
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161521"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Оценка с sp_rxPredict в SQL Server машинного обучения в реальном времени
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Оценка использования в реальном времени [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) системные хранимые процедуры и возможности расширения CLR в SQL Server для высокой производительности прогнозов или оценки в прогнозирования рабочих нагрузок. Оценки в реальном времени от языка и выполняется без зависимостей на R или Python, запусков:. Если модель создана и обучена с использованием функций Microsoft, а затем сериализуются в двоичный формат, в SQL Server, можно использовать оценки в реальном времени для создания прогнозируемых выходных данных на новых входных данных на экземплярах SQL Server, у которых нет надстройки R или Python установлен.

## <a name="how-real-time-scoring-works"></a>Как оценка в реальном времени работает

Оценки в реальном времени поддерживается в SQL Server 2017 и SQL Server 2016 к конкретным типам моделей основаны на функциях RevoScaleR или MicrosoftML, такие как [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)[rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Собственные библиотеки C++ используется для формирования оценок, на основе ввода пользователя, для машинного обучения модели, сохраненной в специальных двоичном формате.

Поскольку обученной модели можно использовать для оценки без вызова внешней языковой среды выполнения, сокращается объем работ нескольких процессов. Это поддерживает значительно повысить производительность прогнозирования для оценки сценариев рабочей среды. Так как данные никогда не покидает SQL Server, результаты можно создается и вставляется в таблицу без преобразования любых данных между R и SQL.

Оценки в реальном времени — это многоэтапный процесс:

1. Хранимая процедура, выполняющий оценки необходимо включить на основе каждой базы данных.
2. Загрузите предварительно обученной модели в двоичном формате.
3. Вы предоставить новые входные данные для оценки, табличном, так и для одной строки, в качестве входных данных в модели.
4. Для формирования оценок, вызовите [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) хранимой процедуры.

> [!TIP]
> Пример оценки в реальном времени в действии, см. в разделе [сквозное окончания ссуды списания кредита прогноза построен с помощью Azure HDInsight кластеров Spark и служба SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="prerequisites"></a>предварительные требования

+ [Включение интеграции со средой CLR для SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Включить оценки в реальном времени](#bkmk_enableRtScoring).

+ Обучение модели должен быть на основе заранее с помощью одного из поддерживаемых **rx** алгоритмы. Для R, в реальном времени, оценки при помощи `sp_rxPredict` работает с [RevoScaleR и MicrosoftML поддерживаются алгоритмы](#bkmk_rt_supported_algos). Для Python, см. в разделе [revoscalepy и microsoftml Поддерживаемые алгоритмы](#bkmk_py_supported_algos)

+ Сериализация модели с использованием [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R, и [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрого оценки.

+ Сохраните модель в экземпляр ядра базы данных, из которого необходимо вызвать его. Этот экземпляр не требуется расширение среды выполнения R или Python.

> [!Note]
> Оценки в реальном времени, в настоящее время оптимизирован для быстрого прогнозирования на основе небольших наборов данных, от небольшое количество строк до сотен тысяч строк. На больших наборах данных, с помощью [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) могут выполняться быстрее.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

### <a name="python-algorithms-using-real-time-scoring"></a>Python алгоритмы, с помощью оценки в реальном времени

+ revoscalepy моделей

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) \*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) \*
  
  Модели, отмеченные \* также поддерживают собственной оценки с помощью функции PREDICT.

+ microsoftml моделей

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Преобразования, предоставляемые microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [Concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>Алгоритмы R с помощью оценки в реальном времени

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

Оценки в реальном времени не использует интерпретатор; Таким образом любые функции, которые могут потребовать интерпретатора не поддерживается на этапе оценки.  Они могут включать:

  + Моделирует использование `rxGlm` или `rxNaiveBayes` алгоритмы не поддерживаются.

  + Модели с помощью функции преобразования или формула, содержащая преобразования, такие как <code>A ~ log(B)</code> не поддерживаются в оценки в реальном времени. Чтобы использовать модель этого типа, рекомендуется выполнить преобразование входных данных перед их передачей для оценки в реальном времени.


## <a name="example-sprxpredict"></a>Пример: sp_rxPredict

В этом разделе описываются шаги, необходимые для настройки **в режиме реального времени** прогноза, а также приводятся примеры на языке R того, как вызвать функцию из T-SQL.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Шаг 1. Включить процесс оценки в режиме реального времени

Необходимо включить эту функцию для каждой базы данных, который вы хотите использовать для оценки. Администратор сервера должен запустить служебную программу командной строки RegisterRExt.exe, входящий в состав пакета RevoScaleR.

> [!NOTE]
> В порядке для оценки в реальном времени для работы функции SQL CLR необходимо включить в экземпляре; Кроме того база данных должна быть помечена заслуживающая доверия. При выполнении сценарий, эти действия выполняются автоматически. Тем не менее рассмотрите влияние на дополнительную безопасность, прежде чем сделать это!

1. Откройте командную строку с повышенными правами и перейдите к папке, где находится RegisterRExt.exe. При установке по умолчанию можно использовать следующий путь:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Выполните следующую команду, подставив имя своего экземпляра и целевой базы данных, где вы хотите включить расширенные хранимые процедуры:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Например чтобы добавить расширенную хранимую процедуру CLRPredict базы данных на экземпляре по умолчанию, введите следующую команду:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Имя экземпляра является необязательным, если база данных находится на экземпляре по умолчанию. Если вы используете именованный экземпляр, укажите имя экземпляра.

3. RegisterRExt.exe создает следующие объекты:

    + Доверенных сборок
    + Хранимая процедура `sp_rxPredict`
    + Роль базы данных, `rxpredict_users`. Администратор базы данных позволяют этой роли разрешение для пользователей, которые используют функции оценки в режиме реального времени.

4. Добавить всех пользователей, которым необходимо запустить `sp_rxPredict` в новую роль.

> [!NOTE]
> 
> В SQL Server 2017 дополнительные меры безопасности, чтобы избежать возникновения неполадок в интеграции со средой CLR. Эти меры налагаются дополнительные ограничения на использование этой хранимой процедуры. 

### <a name="step-2-prepare-and-save-the-model"></a>Шаг 2. Подготовка и сохранение модели

Двоичный формат, требуемый sp\_rxPredict совпадает со значением в формат, необходимый для использования функции PREDICT. Таким образом, в коде R включают вызов [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)и не забудьте указать `realtimeScoringOnly = TRUE`, как показано в этом примере:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Шаг 3. Вызов sp_rxPredict

Вы вызываете sp\_rxPredict, как вы и другие хранимой процедуры. В текущем выпуске, хранимая процедура принимает только два параметра:  _\@модели_ для модели в двоичном формате и  _\@inputData_ для данных, используемыми при оценке, определяется как допустимый SQL-запрос.

Так как двоичный формат имеет те же данные, используется функция PREDICT, можно использовать в таблице моделей и данных из предыдущего примера.

```sql
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> Вызов sp\_rxPredict завершается неудачей, если входные данные для оценки не входят столбцы, которые соответствуют требованиям модели. В настоящее время поддерживаются только следующие типы данных .NET: double, float, short, ushort, long, ulong и строка.
> 
> Таким образом может потребоваться отфильтровать неподдерживаемые типы входных данных перед его использованием для оценки в реальном времени.
> 
> Сведения о соответствующих типов SQL, см. в разделе [сопоставления типов SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [сопоставление данных параметров CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Отключить оценки в реальном времени

Чтобы отключить функцию в режиме реального времени оценки, откройте командную строку с повышенными привилегиями и выполните следующую команду: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Следующие шаги

Пример того, как rxPredict может использоваться для оценки, см. в разделе [сквозное окончания ссуды списания кредита прогноза построен с помощью Azure HDInsight кластеров Spark и служба SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/).

Дополнительные сведения об оценке в SQL Server см. в разделе [как для создания прогнозов машинного обучения SQL Server](r/how-to-do-realtime-scoring.md).
