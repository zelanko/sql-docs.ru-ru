---
title: Руководство по развертыванию прогнозной модели на языке R
titleSuffix: SQL machine learning
description: В заключительной части этого цикла учебников, состоящего из четырех частей, вы развернете прогнозную модель в R с помощью машинного обучения SQL.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/04/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f13efaa9181521a40d6f3ba9a5cdeef7da3d2afc
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606987"
---
# <a name="tutorial-deploy-a-predictive-model-in-r-with-sql-machine-learning"></a>Руководство по развертыванию прогнозной модели в R с помощью машинного обучения SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В заключительной части этого цикла учебников, состоящего из четырех частей, вы развернете модель машинного обучения, разработанную в R, в SQL Server с помощью Служб машинного обучения.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В заключительной части этого цикла учебников, состоящего из четырех частей, вы развернете модель машинного обучения, разработанную в R, в SQL Server с помощью Служб машинного обучения.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
В заключительной части этого цикла учебников, состоящего из четырех частей, вы развернете модель машинного обучения, разработанную в R, в SQL Server с помощью служб SQL Server R Services.
::: moniker-end

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]

> * Создание хранимой процедуры, которая формирует модель машинного обучения
> * Сохранение модели в таблице базы данных
> * Создание хранимой процедуры, которая делает прогнозы с помощью модели
> * Выполнение модели с новыми данными

В [первой части](r-predictive-model-introduction.md) вы узнали, как восстановить учебную базу данных.

Во [второй части](r-predictive-model-prepare-data.md) вы узнали, как импортировать пример базы данных, а затем подготовить данные, которые будут использоваться для обучения прогнозной модели на языке R.

В [третьей части](r-predictive-model-train.md) вы узнали, как создать и обучить несколько моделей машинного обучения на языке R, а затем выбрать наиболее точную.

## <a name="prerequisites"></a>Предварительные требования

В четвертой части этого цикла учебников предполагается, что вы уже выполнили предварительные требования из [**первой части**](r-predictive-model-introduction.md), а также действия, указанные во [**второй**](r-predictive-model-prepare-data.md) и [**третьей**](r-predictive-model-train.md) частях.

## <a name="create-a-stored-procedure-that-generates-the-model"></a>Создание хранимой процедуры, которая формирует модель

В третьей части этого цикла учебников вы решили, что модель дерева принятия решений (dtree) была самой точной. Теперь с помощью разработанных вами сценариев R создайте хранимую процедуру (`generate_rental_model`), которая обучает и создает модель dtree с использованием rpart из пакета R.

Выполните приведенные ниже команды в Azure Data Studio.

```sql
USE [TutorialDB]
DROP PROCEDURE IF EXISTS generate_rental_model;
GO
CREATE PROCEDURE generate_rental_model (@trained_model VARBINARY(max) OUTPUT)
AS
BEGIN
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
rental_train_data$Holiday <- factor(rental_train_data$Holiday);
rental_train_data$Snow    <- factor(rental_train_data$Snow);
rental_train_data$WeekDay <- factor(rental_train_data$WeekDay);

#Create a dtree model and train it using the training data set
model_dtree <- rpart(RentalCount ~ Month + Day + WeekDay + Snow + Holiday, data = rental_train_data);
#Serialize the model before saving it to the database table
trained_model <- as.raw(serialize(model_dtree, connection=NULL));
'
        , @input_data_1 = N'
            SELECT RentalCount
                 , Year
                 , Month
                 , Day
                 , WeekDay
                 , Snow
                 , Holiday
            FROM dbo.rental_data
            WHERE Year < 2015
            '
        , @input_data_1_name = N'rental_train_data'
        , @params = N'@trained_model varbinary(max) OUTPUT'
        , @trained_model = @trained_model OUTPUT;
END;
GO
```

## <a name="store-the-model-in-a-database-table"></a>Сохранение модели в таблице базы данных

Создайте таблицу в базе данных TutorialDB, а затем сохраните модель в таблице.

1. Создайте таблицу (`rental_models`) для хранения модели.

    ```sql
    USE TutorialDB;
    DROP TABLE IF EXISTS rental_models;
    GO
    CREATE TABLE rental_models (
          model_name VARCHAR(30) NOT NULL DEFAULT('default model') PRIMARY KEY
        , model VARBINARY(MAX) NOT NULL
        );
    GO
    ```

1. Сохраните модель в таблицу как двоичный объект с именем модели "DTree".

    ```sql
    -- Save model to table
    TRUNCATE TABLE rental_models;
    
    DECLARE @model VARBINARY(MAX);
    
    EXECUTE generate_rental_model @model OUTPUT;
    
    INSERT INTO rental_models (
          model_name
        , model
        )
    VALUES (
         'DTree'
        , @model
        );
    
    SELECT *
    FROM rental_models;
    ```

## <a name="create-a-stored-procedure-that-makes-predictions"></a>Создание хранимой процедуры, которая делает прогнозы

Создайте хранимую процедуру (`predict_rentalcount_new`), которая создает прогнозы с использованием обученной модели и набора новых данных.

```sql
-- Stored procedure that takes model name and new data as input parameters and predicts the rental count for the new data
USE [TutorialDB]
DROP PROCEDURE IF EXISTS predict_rentalcount_new;
GO
CREATE PROCEDURE predict_rentalcount_new (
      @model_name VARCHAR(100)
    , @input_query NVARCHAR(MAX)
    )
AS
BEGIN
    DECLARE @model VARBINARY(MAX) = (
            SELECT model
            FROM rental_models
            WHERE model_name = @model_name
            );

    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
#Convert types to factors
rentals$Holiday <- factor(rentals$Holiday);
rentals$Snow    <- factor(rentals$Snow);
rentals$WeekDay <- factor(rentals$WeekDay);

#Before using the model to predict, we need to unserialize it
rental_model <- unserialize(model);

#Call prediction function
rental_predictions <- predict(rental_model, rentals);
rental_predictions <- data.frame(rental_predictions);
'
        , @input_data_1 = @input_query
        , @input_data_1_name = N'rentals'
        , @output_data_1_name = N'rental_predictions'
        , @params = N'@model varbinary(max)'
        , @model = @model
    WITH RESULT SETS(("RentalCount_Predicted" FLOAT));
END;
GO
```

## <a name="execute-the-model-with-new-data"></a>Выполнение модели с новыми данными

Теперь вы можете использовать хранимую процедуру `predict_rentalcount_new` для прогнозирования аренды на основе новых данных.

```sql
-- Use the predict_rentalcount_new stored procedure with the model name and a set of features to predict the rental count
EXECUTE dbo.predict_rentalcount_new @model_name = 'DTree'
    , @input_query = '
        SELECT CONVERT(INT,  3) AS Month
             , CONVERT(INT, 24) AS Day
             , CONVERT(INT,  4) AS WeekDay
             , CONVERT(INT,  1) AS Snow
             , CONVERT(INT,  1) AS Holiday
        ';
GO
```

Отобразится результат, аналогичный приведенному ниже.

```results
RentalCount_Predicted
332.571428571429
```

Вы успешно создали, обучили и развернули модель в базе данных SQL. Затем вы использовали ее в хранимой процедуре для прогнозирования значений на основе новых данных.


## <a name="clean-up-resources"></a>Очистка ресурсов

После использования базы данных TutorialDB удалите ее с сервера SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

В четвертой части этого цикла учебников вы узнали, как выполнять следующие задачи:

* Создание хранимой процедуры, которая формирует модель машинного обучения
* Сохранение модели в таблице базы данных
* Создание хранимой процедуры, которая делает прогнозы с помощью модели
* Выполнение модели с новыми данными

Дополнительные сведения об использовании R в Службах машинного обучения:

* [Запуск простых скриптов R](quickstart-r-create-script.md)
* [Структуры данных, типы данных и объекты R](quickstart-r-data-types-and-objects.md)
* [Функции R](quickstart-r-functions.md)
