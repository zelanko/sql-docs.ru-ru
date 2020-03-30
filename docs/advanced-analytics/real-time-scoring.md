---
title: Оценка в реальном времени с помощью sp_rxPredict
description: Формирование прогнозов с помощью sp_rxPredict путем оценки входных данных на основе предварительно обученной модели, написанной на языке R, в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/26/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 746a9cadfca28aae3bd2781a3daf71aabb8d6e5b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727324"
---
# <a name="real-time-scoring-with-sp_rxpredict-in-sql-server-machine-learning"></a>Оценка в реальном времени с помощью sp_rxPredict в службе машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция оценки в реальном времени использует системную хранимую процедуру [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) и возможности расширения среды CLR в SQL Server для высокопроизводительного прогнозирования или оценки в рамках рабочих нагрузок прогнозирования. Оценка в реальном времени не зависит от языка и не имеет зависимости от среды выполнения R или Python. При условии, что модель создана и обучена с помощью функций Майкрософт, а затем сериализована в двоичный формат в SQL Server, вы можете использовать оценку в реальном времени для создания прогнозируемых результатов на основе новых входных данных в экземплярах SQL Server, в которых не установлена надстройка R или Python.

## <a name="how-real-time-scoring-works"></a>Принципы работы оценки в реальном времени

Оценка в реальном времени поддерживается для определенных типов моделей на основе функций RevoScaleR и MicrosoftML, таких как [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)[rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Она использует собственные библиотеки C++ для формирования оценок на основе данных, которые пользователь ввел в модель машинного обучения, хранящуюся в специальном двоичном формате.

Так как обученную модель можно использовать для оценки без вызова внешней среды выполнения языка, накладные расходы на несколько процессов сокращаются. Это обеспечивает гораздо более высокую производительность прогнозирования в рабочих сценариях оценки. Так как данные остаются в SQL Server, полученные результаты можно вставить в новую таблицу без преобразования из R в SQL, и наоборот.

Оценка в реальном времени — это многоэтапный процесс.

1. Необходимо включить хранимую процедуру, выполняющую оценку, для каждой базы данных.
2. Предварительно обученная модель загружается в двоичном формате.
3. В модель вводятся входные данные для оценки. Это могут быть таблицы или отдельные строки.
4. Для формирования оценок вызывается хранимая процедура [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql).

## <a name="prerequisites"></a>предварительные требования

+ [Включите интеграцию со средой CLR SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Включите оценку в реальном времени](#bkmk_enableRtScoring).

+ Модель должна быть заранее обучена с помощью одного из поддерживаемых алгоритмов **rx**. Для языка R оценка в реальном времени с помощью `sp_rxPredict` работает с [поддерживаемыми алгоритмами RevoScaleR и MicrosoftML](#bkmk_rt_supported_algos). Для языка Python см. [поддерживаемые алгоритмы revoscalepy и microsoftml](#bkmk_py_supported_algos)

+ Сериализуйте модель с помощью [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R или [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрой оценки.

+ Сохраните модель в экземпляре ядра СУБД, из которого она будет вызываться. В этом экземпляр не обязательно должно быть установлено расширение среды выполнения R или Python.

> [!Note]
> Оценка в реальном времени в настоящее время оптимизирована для быстрого прогнозирования на основе небольших наборов данных: от нескольких строк до сотен тысяч строк. Для больших наборов данных функция [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) может работать быстрее.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

### <a name="python-algorithms-using-real-time-scoring"></a>Алгоритмы Python, использующие оценку в реальном времени

+ Модели revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)\*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)\*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)\*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)\*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)\*
  
  Модели с пометкой \* также поддерживают собственную оценку с помощью функции PREDICT.

+ Модели microsoftml

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Преобразования, предоставляемые microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>Алгоритмы R, использующие оценку в реальном времени

+ Модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)\*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)\*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)\*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)\*
  
  Модели с пометкой \* также поддерживают собственную оценку с помощью функции PREDICT.

+ Модели MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Преобразования, предоставляемые MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Неподдерживаемые типы моделей

Для оценки в реальном времени не используется интерпретатор. Поэтому функции, которым может потребоваться интерпретатор, не поддерживаются на этапе оценки.  К ним могут относиться:

  + модели, использующие алгоритмы `rxGlm` и `rxNaiveBayes`;

  + модели, использующие функцию преобразования или формулу, содержащую преобразование, например <code>A ~ log(B)</code>. Чтобы использовать модель этого типа, рекомендуется выполнить преобразование входных данных перед их передачей в систему оценки в реальном времени.


## <a name="example-sp_rxpredict"></a>Пример: sp_rxPredict

В этом разделе описаны шаги, необходимые для настройки прогнозирования **в реальном времени**, а также приведен пример вызова функции из T-SQL на языке R.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Шаг 1. Включение процедуры оценки в реальном времени

Эту функцию необходимо включить для каждой базы данных, которая будет использоваться для оценки. Администратор сервера должен запустить программу командной строки RegisterRExt.exe, которая входит в состав пакета RevoScaleR.

> [!NOTE]
> Чтобы оценка в реальном времени работала, в экземпляре необходимо включить функциональность среды CLR SQL. Кроме того, базу данных необходимо пометить как заслуживающую доверия. При запуске скрипта эти действия выполняются автоматически. Однако, прежде чем делать это, обдумайте возможные последствия для безопасности.

1. Откройте командную строку с повышенными привилегиями и перейдите в папку, где находится программа RegisterRExt.exe. По умолчанию путь к ней следующий:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Выполните следующую команду, подставив имя своего экземпляра и целевую базу данных, в которой необходимо включить расширенные хранимые процедуры:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Например, чтобы включить расширенную хранимую процедуру в базе данных CLRPredict в экземпляре по умолчанию, введите следующую команду:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Имя экземпляра является необязательным, если база данных находится в экземпляре по умолчанию. Если используется именованный экземпляр, необходимо указать его имя.

3. Программа RegisterRExt.exe создает следующие объекты:

    + доверенные сборки;
    + хранимую процедуру `sp_rxPredict`;
    + новую роль базы данных `rxpredict_users`. Администратор базы данных может использовать эту роль для предоставления разрешения пользователям, которые используют функцию оценки в реальном времени.

4. Добавьте всех пользователей, которым требуется выполнять `sp_rxPredict`, в новую роль.

> [!NOTE]
> 
> В SQL Server 2017 для предотвращения проблем с интеграцией со средой CLR применяются дополнительные меры безопасности. Они накладывают дополнительные ограничения на использование этой хранимой процедуры. 

### <a name="step-2-prepare-and-save-the-model"></a>Шаг 2. Подготовка и сохранение модели

Двоичный формат, необходимый для sp\_rxPredict, аналогичен формату, требуемому для использования функции PREDICT. Поэтому в коде на языке R включите вызов [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) и укажите параметр `realtimeScoringOnly = TRUE`, как в следующем примере:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sp_rxpredict"></a>Шаг 3. Вызов sp_rxPredict

Процедура sp\_rxPredict вызывается так же, как и любая другая хранимая процедура. В текущем выпуске хранимая процедура принимает только два параметра: _\@model_ для модели в двоичном формате и _\@inputData_ для данных, используемых при оценке, которые определены в виде допустимого SQL-запроса.

Так как двоичный формат аналогичен тому, который используется функцией PREDICT, можно использовать модели и таблицу данных из предыдущего примера.

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
> Вызов sp\_rxPredict завершается ошибкой, если входные данные для оценки не включают в себя столбцы, соответствующие требованиям модели. В настоящее время поддерживаются только следующие типы данных .NET: double, float, short, ushort, long, ulong и string.
> 
> Поэтому может потребоваться отфильтровать неподдерживаемые типы во входных данных, прежде чем использовать их для оценки в реальном времени.
> 
> Сведения о соответствующих типах SQL см. в статье [Сопоставление типов SQL и CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [Сопоставление данных о параметрах CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Отключение оценки в реальном времени

Чтобы отключить функцию оценки в реальном времени, откройте командную строку с повышенными привилегиями и выполните следующую команду: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об оценке в SQL Server см. в статье [Создание прогнозов с помощью службы машинного обучения в SQL Server](r/how-to-do-realtime-scoring.md).
