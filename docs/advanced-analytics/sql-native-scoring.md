---
title: Собственная оценка с помощью PREDICT T-SQL
description: Формирование прогнозов с помощью функции PREDICT T-SQL путем оценки входных данных на основе предварительно обученной модели, написанной на языке R или Python, в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 766adecbc91f88ed0796e4214b7e4074fc564f01
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727283"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Собственная оценка с использованием функции PREDICT T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В рамках собственной оценки формируются прогнозируемые значения, или *оценки*, для новых входных данных практически в реальном времени с помощью [функции PREDICT T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) и возможностей собственного расширения C++ в SQL Server 2017. Эта методология обеспечивает максимально возможную скорость обработки прогнозов и рабочих нагрузок прогнозирования, но поставляется с требованиями к платформе и библиотеке: реализации на C++ есть только у функций из библиотек RevoScaleR и revoscalepy.

Для собственной оценки требуется уже обученная модель. В SQL Server 2017 в Windows или Linux или в Базе данных SQL Azure можно вызвать функцию PREDICT в Transact-SQL, чтобы выполнить собственную оценку для новых данных, указываемых в качестве входного параметра. Функция PREDICT возвращает оценки для предоставленных входных данных.

## <a name="how-native-scoring-works"></a>Как работает собственная оценка

Собственная оценка использует собственные C++ библиотеки от корпорации Майкрософт, которые могут прочесть уже обученную модель, ранее сохраненную в особом двоичном формате или сохраненную на диске в виде потока необработанных байтов, и сформировать оценки для новых вводимых данных. Поскольку модель обучена, опубликована и сохранена, ее можно использовать для оценки без вызова интерпретатора R или Python. Таким образом, затраты на взаимодействие нескольких процессов сокращаются, что приводит к значительному повышению производительности прогнозирования в корпоративных производственных сценариях.

Чтобы использовать собственную оценку, вызовите функцию PREDICT T-SQL и передайте следующие обязательные входные данные:

+ Совместимая модель, основанная на поддерживаемом алгоритме.
+ Входные данные, обычно определяемые в виде SQL-запроса.

Функция возвращает прогнозы для входных данных вместе со всеми столбцами исходных данных, которые необходимо передать.

## <a name="prerequisites"></a>Предварительные требования

Функция PREDICT доступна во всех выпусках ядра СУБД SQL Server 2017, в том числе в Службах машинного обучения SQL Server в Windows, SQL Server 2017 (в Windows), SQL Server 2017 (в Linux) и в Базе данных SQL Azure и включена по умолчанию. Вам не нужно устанавливать R, Python или включать дополнительные функции.

+ Модель должна быть заранее обучена с помощью одного из поддерживаемых алгоритмов **rx**, указанных ниже.

+ Сериализуйте модель с помощью [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R или [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрой оценки.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

+ Модели revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ Модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Если необходимо использовать модели из MicrosoftML или MicrosoftML, используйте [оценки в реальном времени с sp_rxPredict](real-time-scoring.md).

Поддерживаемые типы моделей включают следующие:

+ Модели, содержащие другие преобразования
+ Модели, использующие алгоритмы `rxGlm` или `rxNaiveBayes` в эквивалентах RevoScaleR или revoscalepy
+ Модели PMML
+ Модели, созданные с помощью других библиотек с открытым исходным кодом или библиотек сторонних разработчиков

## <a name="example-predict-t-sql"></a>Пример PREDICT (T-SQL)

В этом примере создается модель, а затем вызывается функция прогнозирования в реальном времени из T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Шаг 1. Подготовка и сохранение модели

Выполните следующий код, чтобы создать пример базы данных и необходимые таблицы.

```sql
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

Используйте следующую инструкцию, чтобы заполнить таблицу данных данными из набора данных **iris**.

```sql
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Теперь создайте таблицу для хранения моделей.

```sql
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Следующий код создает модель на основе набора данных **iris** и сохраняет его в таблицу **models**.

```sql
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
> Обязательно используйте функцию [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) из RevoScaleR для сохранения модели. Стандартная функция R `serialize` не может обеспечить необходимый формат сериализации.

Для просмотра сохраненной модели в двоичном формате можно выполнить следующую инструкцию:

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Шаг 2. Выполнение инструкции PREDICT для модели

Следующая простая инструкция PREDICT получает классификацию из модели дерева принятия решений с помощью функции **собственной оценки**. Она прогнозирует виды ирисов на основе указанных атрибутов: длины и ширины лепестка.

```sql
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

Если вы получили сообщение об ошибке "Ошибка при выполнении функции PREDICT. Модель повреждена или является недопустимой", обычно это означает, что запрос не возвратил модель. Проверьте, правильно ли указано название модели и пуста ли таблица модели.

> [!NOTE]
> Поскольку столбцы и значения, возвращаемые функцией **PREDICT**, могут зависеть от типа модели, необходимо определить схему возвращаемых данных с помощью предложения **WITH**.

## <a name="next-steps"></a>Дальнейшие действия

Полное решение, включающее собственную оценку, см. в следующих примерах от команды разработчиков SQL Server:

+ Развертывание сценария ML: [С помощью модели Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Развертывание сценария ML: [С помощью модели R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)