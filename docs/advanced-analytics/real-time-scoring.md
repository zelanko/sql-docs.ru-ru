---
title: Оценка в режиме реального времени с помощью хранимой процедуры sp_rxPredict
description: Формирование прогнозов с помощью sp_rxPredict, входных данных оценки для предварительно обученной модели, написанной на языке R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2e9c9353acdc0a2641203788c8e4883a9accb021
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345676"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Оценка в реальном времени с помощью sp_rxPredict в машинном обучении SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Оценка в режиме реального времени использует системную хранимую процедуру [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) и возможности расширения среды CLR в SQL Server для высокопроизводительных прогнозов или оценки рабочих нагрузок прогнозирования. Оценка в реальном времени не зависит от языка и выполняется без зависимостей от времени выполнения R или Python. Предполагая, что модель создана и обучена с помощью функций Майкрософт, а затем сериализована в двоичный формат в SQL Server, вы можете использовать оценку в реальном времени для создания прогнозируемых результатов для новых входных данных в экземплярах SQL Server, у которых нет надстройки R или Python. Установка.

## <a name="how-real-time-scoring-works"></a>Как работает Оценка в режиме реального времени

Оценка в реальном времени поддерживается как в SQL Server 2017, так SQL Server 2016, в конкретных типах моделей на основе таких функций RevoScaleR или MicrosoftML, как [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)[ркснеуралнет (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Он использует собственные C++ библиотеки для формирования оценок на основе введенных пользователем данных, предоставленных модели машинного обучения, хранящейся в специальном двоичном формате.

Так как обученную модель можно использовать для оценки без вызова внешней среды выполнения, затраты на несколько процессов сокращаются. Это обеспечивает гораздо более быструю производительность прогнозирования для сценариев оценки рабочей среды. Поскольку данные никогда не выходят SQL Server, их можно создать и вставить в новую таблицу без преобразования данных между R и SQL.

Оценка в режиме реального времени — это многоэтапный процесс:

1. Хранимая процедура, для которой выполняется оценка, должна быть включена для каждой базы данных.
2. Предварительно обученная модель загружается в двоичном формате.
3. Вы предоставляете в качестве входных данных новые входные данные для оценки, табличные или отдельные строки.
4. Чтобы создать оценки, вызовите хранимую процедуру [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) .

## <a name="prerequisites"></a>предварительные требования

+ [Включите интеграцию со средой CLR SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Включение оценки в режиме реального времени](#bkmk_enableRtScoring).

+ Модель должна заранее обучиться с помощью одного из поддерживаемых алгоритмов **приема** . Для R, оценка в режиме реального времени `sp_rxPredict` с помощью [поддерживаемых алгоритмов RevoScaleR и MicrosoftML](#bkmk_rt_supported_algos). Для Python см. раздел [Поддерживаемые алгоритмы revoscalepy и microsoftml](#bkmk_py_supported_algos) .

+ Сериализация модели с помощью [ркссериализе](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R и [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрой оценки.

+ Сохраните модель в экземпляре ядра СУБД, из которого его необходимо вызвать. Этот экземпляр не обязательно должен иметь расширение среды выполнения R или Python.

> [!Note]
> Оценка в реальном времени в настоящее время оптимизирована для быстрого прогнозирования на небольших наборах данных, от нескольких строк до сотен тысяч строк. В больших наборах данных использование [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) может выполняться быстрее.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

### <a name="python-algorithms-using-real-time-scoring"></a>Алгоритмы Python с оценкой в режиме реального времени

+ модели revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)\*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)\*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)\*
  
  Модели, помеченные \* также, поддерживают встроенную оценку с помощью функции Predict.

+ модели microsoftml

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Преобразования, предоставляемые microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [сцеплен](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>Алгоритмы R с использованием оценки в режиме реального времени

+ Модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)\*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)\*
  + [рксбтрис](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)\*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)\*
  
  Модели, помеченные \* также, поддерживают встроенную оценку с помощью функции Predict.

+ Модели MicrosoftML

  + [рксфасттрис](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [рксфастфорест](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [ркслогистикрегрессион](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [ркснеуралнет](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [рксфастлинеар](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Преобразования, предоставляемые MicrosoftML

  + [феатуризетекст](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [сцеплен](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [категориальные](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [категорикалхаш](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [селектфеатурес](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Неподдерживаемые типы моделей

В режиме оценки в реальном времени не используется интерпретатор. Таким образом, все функции, которые могут потребовать интерпретатор, не поддерживаются на этапе оценки.  К ним могут относиться следующие:

  + Модели, использующие `rxGlm` алгоритмы или `rxNaiveBayes` , не поддерживаются.

  + Модели, использующие функцию преобразования или формулу, содержащую преобразование, например <code>A ~ log(B)</code> , не поддерживаются в режиме оценки в реальном времени. Чтобы использовать модель этого типа, рекомендуется выполнить преобразование входных данных перед передачей данных в систему оценки в реальном времени.


## <a name="example-sprxpredict"></a>Пример: sp_rxPredict

В этом разделе описываются шаги, необходимые для настройки прогноза в **режиме реального времени** , а также пример в языке R для вызова функции из T-SQL.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Шаг 1. Включение процедуры оценки в режиме реального времени

Эту функцию необходимо включить для каждой базы данных, которая будет использоваться для оценки. Администратор сервера должен запустить программу командной строки RegisterRExt. exe, которая входит в состав пакета RevoScaleR.

> [!NOTE]
> Чтобы оценка в реальном времени работала, в экземпляре необходимо включить функциональность SQL CLR. Кроме того, база данных должна быть помечена как заслуживающая доверия. При выполнении скрипта эти действия выполняются самостоятельно. Однако прежде чем это сделать, примите во внимание дополнительные последствия для безопасности!

1. Откройте командную строку с повышенными привилегиями и перейдите в папку, где находится RegisterRExt. exe. Следующий путь можно использовать в установке по умолчанию:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Выполните следующую команду, подставив имя экземпляра и целевую базу данных, в которой необходимо включить расширенные хранимые процедуры:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Например, чтобы добавить расширенную хранимую процедуру в базу данных Клрпредикт на экземпляре по умолчанию, введите:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Имя экземпляра является необязательным, если база данных находится в экземпляре по умолчанию. Если используется именованный экземпляр, необходимо указать имя экземпляра.

3. RegisterRExt. exe создает следующие объекты:

    + Доверенные сборки
    + Хранимая процедура`sp_rxPredict`
    + Новая роль `rxpredict_users`базы данных. Администратор базы данных может использовать эту роль для предоставления разрешений пользователям, которые используют функцию оценки в режиме реального времени.

4. Добавьте всех пользователей, которым требуется выполнить `sp_rxPredict` команду для новой роли.

> [!NOTE]
> 
> В SQL Server 2017 для предотвращения проблем с интеграцией со средой CLR применяются дополнительные меры безопасности. Эти меры также накладывают дополнительные ограничения на использование этой хранимой процедуры. 

### <a name="step-2-prepare-and-save-the-model"></a>Шаг 2. Подготовка и сохранение модели

Двоичный формат, необходимый для\_SP rxPredict, совпадает с форматом, необходимым для использования функции Predict. Поэтому в коде R включите вызов [ркссериализемодел](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)и обязательно укажите `realtimeScoringOnly = TRUE`, как в следующем примере:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Шаг 3. Вызов sp_rxPredict

Метод SP\_rxPredict вызывается так же, как и любая другая хранимая процедура. В текущем выпуске хранимая процедура принимает только два параметра:  _\@модель_ для модели в двоичном формате и  _\@inputData_ для использования данных в оценке, определенных как допустимый SQL-запрос.

Так как двоичный формат используется в функции PREDICT, можно использовать модели и таблицу данных из предыдущего примера.

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
> Вызов SP\_rxPredict завершается ошибкой, если входные данные для оценки не включают столбцы, соответствующие требованиям модели. В настоящее время поддерживаются только следующие типы данных .NET: Double, float, Short, ushort, Long, ulong и String.
> 
> Поэтому может потребоваться отфильтровать неподдерживаемые типы во входных данных, прежде чем использовать их для оценки в реальном времени.
> 
> Сведения о соответствующих типах SQL см. в разделе [Сопоставление типов SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [сопоставление данных параметров CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Отключение оценки в режиме реального времени

Чтобы отключить функцию оценки в режиме реального времени, откройте командную строку с повышенными привилегиями и выполните следующую команду:`RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об оценке в SQL Server см. в статье [Создание прогнозов в SQL Server машинного обучения](r/how-to-do-realtime-scoring.md).
