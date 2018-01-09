---
title: "Использование языка R в базе данных Azure SQL | Документы Microsoft"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: e6376a5b03a272633e876b993c3a67467d7b4637
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-r-in-azure-sql-database"></a>Использование языка R в базе данных Azure SQL

В октябре 2017 г. группа разработчиков SQL Server объявила для поддержки выполнения R код в базе данных с помощью хранимых процедур, аналогично R Services в SQL Server 2016. 

Поддерживать актуальность на общедоступный выпуск расписания и события, в разделе [в блоге SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/) или [блог Microsoft R Server](https://blogs.msdn.microsoft.com/rserver/).

> [!IMPORTANT]
> В настоящее время Предварительный просмотр R поддержки доступен в базе данных SQL Azure в Западная центральной части США и функции будут ограничены по сравнению с функции для R и Python кода выполнения в SQL Server 2016 или 2017 г.

## <a name="whats-included"></a>Содержимое

Функции R в базе данных могут использоваться на следующих уровнях обслуживания базы данных и уровни производительности.
 
- Уровень обслуживания Premium — P1, P2, P4, P6, P11, P15
- PRS6 PRS2 PRS4, уровень — PRS1, службы Reporting Services Premium
- Для эластичного пула "премиум" — 125 число Edtu или выше
- Пул эластичных RS Premium — 125 число Edtu или выше

Предварительная версия включает эти пакеты:

+   Microsoft R Open с помощью R версии 3.3.3.
+   Являются предварительно установленные пакеты Base R и функции
+   Microsoft R Server 9.2, включая пакет RevoScaleR

В текущей предварительной версии можно выполнять следующие задачи:

+ Обучение моделей с помощью любые данные, которые помещаются в памяти
+   Оценки моделей с помощью любые данные, которые помещаются в памяти
+   Тривиальное параллелизма для выполнения скриптов R (с помощью @parallel параметр в sp_execute_external_script)
+   Потоковая передача выполнения для выполнения скриптов R (с помощью @r_RowsPerRead параметр в sp_execute_external_script)
+   За один раз выполнить один скрипт R


В предварительной версии R в базе данных SQL Azure не поддерживаются следующие задачи:

+ Невозможно включить выполнение сценариев R на конкретных баз данных.
+ Динамические административные представления, указанный для монитора ЦП и использование памяти скриптов R не доступны.
+ Можно установить нет пакетов сторонних разработчиков. Создание ВНЕШНЕЙ БИБЛИОТЕКИ инструкция не поддерживается.

## <a name="example"></a>Пример

В базе данных SQL Azure, все команды R запускаются из T-SQL, с помощью хранимой процедуры [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). 

Следующий пример демонстрирует опробовать функцию предварительного просмотра, с помощью набора данных iris, входящий в состав базового R.

### <a name="step-1-create-the-data-tables"></a>Шаг 1. Создание таблиц данных

Начните с создания двух таблиц: один для хранения исходных данных, извлеченных из R и для хранения обученной модели.

```sql
DROP TABLE IF EXISTS iris_data, iris_models;
GO
CREATE TABLE iris_data (
        id INT NOT NULL IDENTITY PRIMARY KEY
        , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
        , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
        , "Species" VARCHAR(100) NULL
);
CREATE TABLE iris_models (
    model_name VARCHAR(30) NOT NULL PRIMARY KEY,
    model VARBINARY(max) NOT NULL,
    native_model VARBINARY(MAX) NOT NULL
);
GO
```

### <a name="step-2-populate-table-with-data-from-the-iris-dataset"></a>Шаг 2. Заполнить таблицы данными из набора данных iris

После создания таблицы, выполните следующий код для вставки в таблице обучающих данных. Хранимая процедура sp_execute_external_script вызывает R и возвращает набор данных iris в виде блока данных с помощью схемы, указанной в инструкции INSERT INTO.

```sql
INSERT INTO iris_data
("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
EXEC sp_execute_external_script @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

### <a name="step-3-create-the-stored-procedure-that-generates-the-model"></a>Шаг 3. Создание хранимой процедуры, которая приводит к возникновению ошибки модели

Следующая хранимая процедура выполняет работу, фактического создания и обучения модели, могут быть сохранены в двух форматах двоичных.

```sql
CREATE PROCEDURE generate_iris_model
    @trained_model VARBINARY(MAX) OUTPUT, 
    @native_trained_model VARBINARY(MAX) OUTPUT
AS
BEGIN
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    iris_model <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris_rx_data);
    trained_model <- as.raw(serialize(iris_model, connection=NULL));
    native_trained_model <- rxSerializeModel(iris_model, realtimeScoringOnly = TRUE)
    '
  , @input_data_1 = N'SELECT "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@trained_model VARBINARY(MAX) OUTPUT, @native_trained_model VARBINARY(MAX) OUTPUT
    , @trained_model = @trained_model OUTPUT
    , @native_trained_model = @native_trained_model OUTPUT;
End
```

+ **ВЫВОДА** ключевое слово на входные параметры указывает, что передать значения и они будут использовать для вывода также.
+ Строка, начинающаяся с `iris_model` определяет модель дерева принятия решений для прогнозирования на основе атрибутов цветов вида.
+ Вызов `serialize` сохраняет модели в двоичном формате подходит для хранения данных в SQL Server. 
+ Кроме того, с моделями, основанными на алгоритмах RevoScaleR, можно использовать [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) функции, которая сохраняет модель в новый собственном двоичном формате. Модели, сохраненные в этом формате могут быть загружены для оценки с помощью функции ПРОГНОЗИРОВАНИЯ в SQL Server.

### <a name="step-4-train-and-save-the-model"></a>Шаг 4. Обучение и сохранить модель

После создания хранимой процедуры, вызовите для обработки входных данных и создать модель. Приведенный ниже код также сохраняет модель в таблицу **iris_models**, после чего вы можно использовать позже для прогнозирования указывает цветов.

```sql
DECLARE @model VARBINARY(MAX), @native_modelVARBINARY(MAX);
EXEC generate_iris_model @model OUTPUT, @native_model OUTPUT;
DELETE FROM iris_models WHERE model_name = 'iris.dtree';
INSERT INTO iris_models (model_name, model, native_model) VALUES('iris.dtree', @model, @native_model);
SELECT model_name, datalength(model)/1024. AS model_size_kb, datalength(native_model)/1024. AS native_model_size_kb FROM iris_models;
GO
```

### <a name="step-5-create-a-stored-procedure-for-scoring"></a>Шаг 5. Создание хранимой процедуры для оценки

Создайте хранимую процедуру для оценки. Эта хранимая процедура загружает указанную модель из таблицы и создает отчет на основе входных данных.

```sql
CREATE PROCEDURE predict_iris_species (@model varchar(100))
AS
BEGIN
  DECLARE @rx_model VARBINARY(MAX) = (SELECT model FROM iris_models WHERE model_name = @model);
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    irismodel<-unserialize(rx_model);
    OutputDataSet <-rxPredict(irismodel, iris_rx_data, extraVarsToWrite = c("Species", "id"));
      '
  , @input_data_1 = N'SELECT "id", "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@rx_model varbinary(max)'
  , @rx_model = @rx_model
  WITH RESULT SETS ( ("setosa_Pred" FLOAT, "versicolor_Pred" FLOAT, "virginica_Pred" FLOAT, "Species.Actual" VARCHAR(100), "id" INT));
END;
GO
```

Эта хранимая процедура использует [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) функции, но может также использовать внутреннюю функцию ПРОГНОЗИРОВАНИЯ в T-SQL как показано [здесь](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-general-availability-of-native-scoring-using-predict-function-in-azure-sql-database/). Использование функции ПРОГНОЗИРОВАНИЯ требует использования [ **rx** модель](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) и сохранить модель с помощью [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel).

### <a name="step-6-use-the-stored-procedure-to-generate-predictions"></a>Шаг 6. Используйте хранимую процедуру для создания прогнозов

Чтобы формировать оценки на основе модели, выполните хранимую процедуру. Можно вставлять значения в таблицу или возвращать прогнозы для вызывающего приложения.

```sql
EXEC predict_iris_species 'iris.dtree';
GO
```

## <a name="related-resources"></a>Связанные ресурсы

В Azure Marketplace также предоставляет несколько виртуальных машин, которые включают 2017 г. SQL Server:

+ [Подготовьте виртуальную машину для машинного обучения в Azure](provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

Также ознакомьтесь с этих виртуальных машинах, которые заранее с различными популярными машинного обучения средства:

+ [Виртуальная машина обработки и анализа данных](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)
+ [Углубленного обучения виртуальной машины](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)

