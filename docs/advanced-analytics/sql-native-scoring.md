---
title: Собственная Оценка в службе машинного обучения SQL Server | Документация Майкрософт
description: Создание прогнозов с помощью функции ПРОГНОЗИРОВАНИЯ T-SQL, количественная оценка входных данных dta к предварительно обученной модели на языке R или Python на сервере SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 372c81310fea86094543319f21e409142810de97
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713156"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Собственная Оценка с помощью функции ПРОГНОЗИРОВАНИЯ T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Собственный оценки использует [ПРОГНОЗИРОВАНИЯ T-SQL функция](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) и встроенные возможности расширения C++, в SQL Server 2017 для формирования прогноза значений или *оценок* для новых входных данных в режиме реального времени. Эту методику предлагает максимальной скорости обработки возможных прогнозирования и прогнозирования рабочих нагрузок, но поставляется с требованиями платформы и библиотеки: только функции RevoScaleR и revoscalepy имеют реализации C++.

Собственная Оценка необходимо иметь уже обученной модели. В SQL Server 2017 Windows или Linux, или в базе данных SQL Azure можно вызвать функции PREDICT в Transact-SQL для вызова собственного оценку на основе новых данных, указанных в качестве входного параметра. Функция PREDICT возвращает оценки через входные данные, указанные вами.

## <a name="how-native-scoring-works"></a>Как неуправляемый код оценки works

Использование собственного C++ библиотек с собственной оценкой от корпорации Майкрософт, который может читать уже обученную модель, которая ранее хранятся в специальном формате двоичных сохраняются на диске в виде потока необработанных байтов и формирования оценок для новых входных данных, которые вы указываете. Так как эта модель обучается, опубликованные и сохраненные, его можно использовать для оценки без вызова интерпретатора R или Python. Таким образом несколько взаимодействий процесс сокращается объем работ, в результате чего намного быстрее, производительность прогнозирования в рабочей среде на предприятии.

Для использования собственной оценки, вызов функции ПРОГНОЗИРОВАНИЯ T-SQL и передать следующие необходимые входные данные:

+ Совместимые модель на основе поддерживаемый алгоритм.
+ Входные данные, обычно определяется как SQL-запроса.

Функция возвращает прогнозы для входных данных, а также все столбцы исходных данных, который будет проходить через.

## <a name="prerequisites"></a>предварительные требования

ПРОГНОЗИРОВАНИЕ была доступна во всех выпусках ядра СУБД SQL Server 2017 и включена по умолчанию, в том числе служб SQL Server 2017 машинного обучения на Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) или базы данных SQL Azure. Необязательно для установки R, Python, или включить дополнительные функции.

+ Обучение модели должен быть на основе заранее с помощью одного из поддерживаемых **rx** алгоритмов, перечисленные ниже.

+ Сериализация модели с использованием [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R, и [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрого оценки.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

+ revoscalepy моделей

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ RevoScaleR моделей

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Если вам нужно использовать модели из MicrosoftML или microsoftml, используйте [оценки в реальном времени с sp_rxPredict](real-time-scoring.md).

Неподдерживаемые модели включают следующие типы:

+ Модели, содержащий другие преобразования
+ Моделирует использование `rxGlm` или `rxNaiveBayes` алгоритмы в RevoScaleR или revoscalepy эквиваленты
+ PMML модели
+ Модели, созданные с помощью других библиотек с открытым исходным кодом или сторонние

## <a name="example-predict-t-sql"></a>Пример: ПРОГНОЗИРОВАНИЯ (T-SQL)

В этом примере создания модели и затем вызвать в режиме реального времени прогнозирующую функцию из T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Шаг 1. Подготовка и сохранение модели

Выполните следующий код для создания образца базы данных и обязательными таблицами.

```SQL
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Используйте следующую инструкцию для заполнения таблицы данных с данными из **iris** набора данных.

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Теперь создайте таблицу для хранения моделей.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Следующий код создает модель на основе **iris** набора данных и сохраняет его в таблицу с именем **моделей**.

```SQL
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Обязательно используйте [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) функции RevoScaleR для сохранения модели. Стандартный R `serialize` функции не удается создать требуемый формат.

Можно выполнить инструкцию, такую как следующую команду, чтобы просмотреть сохраненную модель в двоичном формате:

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Шаг 2. Выполнение ПРОГНОЗ для модели

Следующая инструкция простой ПРОГНОЗ Возвращает классификацию из модели дерева принятия решений с помощью **собственной оценки** функции. Она предсказывает виды цветов ириса на основе атрибутов, которые вы предоставляете, длина лепестка и ширина.

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Если появится ошибка «произошла ошибка во время выполнения функции PREDICT. Модель повреждена», это обычно означает, что запрос не вернул модели. Проверьте ли правильно ввели имя модели, или если в таблице модели пуст.

> [!NOTE]
> Так как столбцы и значения, возвращенные **PREDICT** могут зависеть от типа модели, необходимо определить схему для возвращаемых данных с помощью **WITH** предложение.

## <a name="next-steps"></a>Следующие шаги

Для формирования комплексного решения, включающий собственной оценки см. в этих примерах от команды разработчиков SQL Server:

+ Развертывание скрипта машинного Обучения: [с помощью модели Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Развертывание скрипта машинного Обучения: [с помощью R-модели](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)