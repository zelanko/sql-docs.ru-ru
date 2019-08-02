---
title: Собственная оценка с использованием инструкции ПРОГНОЗИРОВАНИя T-SQL
description: Формирование прогнозов с помощью функции ПРОГНОЗИРОВАНИя T-SQL, вычисление выходных данных DTA для предварительно обученной модели, написанной на языке R или Python на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f84b799fa901f7461f448683cceffe78e1dddfd3
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714950"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Собственная оценка с использованием функции ПРОГНОЗИРОВАНИя T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В процессе оценки машинного кода используются [функции прогнозирования T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) и возможности собственного C++ расширения в SQL Server 2017 для создания прогнозных значений или *оценки* новых входных данных практически в реальном времени. Эта методология обеспечивает самую быструю возможную скорость обработки прогнозов и прогнозирования рабочих нагрузок, но поставляется с требованиями к платформе и библиотеке: только функции из RevoScaleR C++ и revoscalepy имеют реализации.

Для оценки машинного кода требуется уже обученная модель. В SQL Server 2017 Windows или Linux или в базе данных SQL Azure можно вызвать функцию PREDICT в Transact-SQL, чтобы вызвать собственную оценку по новым данным, предоставленным в качестве входного параметра. Функция PREDICT возвращает баллы за предоставленные вами входные данные.

## <a name="how-native-scoring-works"></a>Принцип работы машинной оценки

Собственная оценка использует собственные C++ библиотеки от корпорации Майкрософт, которые могут читать уже обученную модель, ранее сохраненную в особом двоичном формате или сохраненную на диске в виде потока необработанных байтов, и формировать оценки для новых вводимых данных. Поскольку модель обучена, опубликована и сохранена, ее можно использовать для оценки без вызова интерпретатора R или Python. Таким образом, затраты на взаимодействие нескольких процессов сокращаются, что приводит к значительному повышению производительности прогнозирования в корпоративных производственных сценариях.

Чтобы использовать собственную оценку, вызовите функцию ПРОГНОЗИРОВАНИя T-SQL и передайте следующие необходимые входные данные:

+ Совместимая модель, основанная на поддерживаемом алгоритме.
+ Входные данные, обычно определяемые как SQL-запрос.

Функция возвращает прогнозы для входных данных вместе со всеми столбцами исходных данных, которые необходимо передать.

## <a name="prerequisites"></a>предварительные требования

Прогноз доступен во всех выпусках ядра СУБД SQL Server 2017 и включен по умолчанию, включая SQL Server Службы машинного обучения в Windows, SQL Server 2017 (Windows), SQL Server 2017 (Linux) или базу данных SQL Azure. Вам не нужно устанавливать R, Python или включать дополнительные функции.

+ Модель должна заранее обучиться с помощью одного из поддерживаемых алгоритмов **RX** , перечисленных ниже.

+ Сериализация модели с помощью [ркссериализе](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) для R и [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для Python. Эти функции сериализации оптимизированы для поддержки быстрой оценки.

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

+ модели revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ Модели RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [рксбтрис](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Если необходимо использовать модели из MicrosoftML или MicrosoftML, используйте оценку [в режиме реального времени с sp_rxPredict](real-time-scoring.md).

Неподдерживаемые типы моделей включают следующие типы:

+ Модели, содержащие другие преобразования
+ Модели, `rxGlm` использующие алгоритмы или `rxNaiveBayes` в эквивалентах RevoScaleR или revoscalepy
+ Модели PMML
+ Модели, созданные с помощью других библиотек с открытым кодом или сторонними разработчиками

## <a name="example-predict-t-sql"></a>Пример PREDICT (T-SQL)

В этом примере создается модель, а затем вызывается функция прогнозирования в реальном времени из T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Шаг 1. Подготовка и сохранение модели

Выполните следующий код, чтобы создать образец базы данных и необходимые таблицы.

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

Используйте следующую инструкцию, чтобы заполнить таблицу данных данными из набора данных **IRI** .

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

Следующий код создает модель на основе набора данных **IRI** и сохраняет ее в таблицу с именем Models.

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
> Чтобы сохранить модель, обязательно используйте функцию [ркссериализемодел](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) из RevoScaleR. Стандартная функция R `serialize` не может создать требуемый формат.

Для просмотра хранимой модели в двоичном формате можно выполнить следующую инструкцию:

```sql
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Шаг 2. Выполнение ПРОГНОЗа для модели

Следующая простая инструкция PREDICT возвращает классификацию из модели дерева принятия решений с помощью **собственной функции оценки** . Он прогнозирует виды цветову IRI на основе предоставленных атрибутов, длины и ширины лепестка.

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

При возникновении ошибки "во время выполнения функции PREDICT произошла ошибка". Модель повреждена или недопустима ", обычно это означает, что запрос не вернул модель. Проверьте, правильно ли введено имя модели, или если таблица Models пуста.

> [!NOTE]
> Поскольку столбцы и значения, возвращаемые **прогнозом** , могут зависеть от типа модели, необходимо определить схему возвращаемых данных с помощью предложения **with** .

## <a name="next-steps"></a>Следующие шаги

Полное решение, которое включает в себя оценку машинного кода, см. в следующих примерах от команды разработчиков SQL Server.

+ Развертывание скрипта ML: [Использование модели Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Развертывание скрипта ML: [Использование модели R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)