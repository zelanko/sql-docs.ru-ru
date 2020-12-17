---
description: Демонстрационные данные ирисов Фишера для учебников по Python и R при использовании со Службой машинного обучения SQL Server
title: Демонстрационный набор данных Iris для учебников
titleSuffix: SQL machine learning
Description: Создание базы данных, содержащей набор данных Iris и прогнозных моделей. Этот набор данных используется в руководствах по Python и R для Служб машинного обучения SQL.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 05/26/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current'
ms.openlocfilehash: 76e746701aa331cf1720ea56befd5956fd65cfd4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470465"
---
# <a name="iris-demo-data-for-python-and-r-tutorials-with-sql-machine-learning"></a>Демонстрационные данные ирисов Фишера для учебников по Python и R при использовании со Службой машинного обучения SQL Server
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

В этом упражнении вы создадите базу данных для хранения данных из [набора ирисов Фишера](https://en.wikipedia.org/wiki/Iris_flower_data_set) и созданных на их основе моделей. Данные ирисов Фишера входят в дистрибутивы R и Python и используются в рамках учебников по машинному обучению для SQL.

Для выполнения этого упражнения вам потребуется [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) или другое средство, поддерживающее выполнение запросов T-SQL.

Этот набор данных используется в следующих учебниках и кратких руководствах:

+ [Краткое руководство. Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md)

## <a name="create-the-database"></a>Создание базы данных

1. Запустите SQL Server Management Studio и откройте новое окно **Запрос**.  

2. Создайте новую базу данных для этого проекта и измените контекст окна **Запрос**, чтобы использовать эту базу.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

3. Добавьте пустые таблицы: одну для хранения данных, а другую — для хранения обученных моделей. Таблица **iris_models** используется для хранения сериализованных моделей, создаваемых в рамках других упражнений.

    В следующем коде создается таблица для обучающих данных.

    ```sql
    DROP TABLE IF EXISTS iris_data;
    GO
    CREATE TABLE iris_data (
      id INT NOT NULL IDENTITY PRIMARY KEY
      , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
      , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
      , "Species" VARCHAR(100) NOT NULL, "SpeciesId" INT NOT NULL
    );
    ```

4. Выполните следующий код, чтобы создать таблицу для хранения обученной модели. Сохраняемые модели Python (или R) в SQL Server необходимо сериализовать и поместить в столбец типа **varbinary(max)** .

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO

    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Помимо содержимого модели, как правило, следует добавить столбцы для других полезных метаданных, таких как имя модели, дата обучения, исходные алгоритм и параметры, исходные данные и т. д. Для большего удобства пока мы будем использовать только имя модели.

## <a name="populate-the-table"></a>Заполнение таблицы

Вы можете получить данные встроенного набора Iris как из R так и из Python. Вы можете загрузить данные в кадр данных с помощью Python или R и затем вставить его в таблицу в базе данных. Перемещение обучающих данных из внешнего сеанса в таблицу выполняется в несколько шагов:

+ Создайте хранимую процедуру, которая получает нужные данные.
+ Выполните хранимую процедуру, чтобы получить данные.
+ Создайте инструкцию INSERT, чтобы указать, где требуется сохранить извлеченные данные.

1. В системах с интеграцией с Python создайте следующую хранимую процедуру, которая использует код Python для загрузки данных.

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    from sklearn import datasets
    iris = datasets.load_iris()
    iris_data = pandas.DataFrame(iris.data)
    iris_data["Species"] = pandas.Categorical.from_codes(iris.target, iris.target_names)
    iris_data["SpeciesId"] = iris.target
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

    При выполнении этого кода должно появиться сообщение "Выполнение команд успешно завершено". Это означает, что соответствующая вашим требованиям хранимая процедура была успешно создана.

2. В системах с интеграцией с R вместо нее следует создать процедуру, использующую R.

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'R', 
    @script = N'
    library(RevoScaleR)
    data(iris)
    iris$SpeciesID <- c(unclass(iris$Species))
    iris_data <- iris
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

3. Чтобы заполнить таблицу, выполните хранимую процедуру и укажите таблицу, в которую требуется записать данные. После запуска эта хранимая процедура выполняет код Python или R, который загружает встроенный набор данных Iris и затем вставляет данные в таблицу **iris_data**.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Если вы не знакомы с T-SQL, учтите, что инструкция INSERT только добавляет новые данные. Она не проверяет существующие данные и не выполняет удаление или перестроение таблицы. Чтобы исключить многократное копирование одних и тех же данных в таблицу, можно сначала выполнить следующую инструкцию: `TRUNCATE TABLE iris_data`. Инструкция T-SQL [TRUNCATE TABLE](../../t-sql/statements/truncate-table-transact-sql.md) удаляет существующие данные, сохраняя при этом структуру таблицы в неизменном виде.

## <a name="query-the-data"></a>Запрос данных

Для проверки выполните запрос и убедитесь, что данные были отправлены.

1. В разделе "Базы данных" обозревателя объектов щелкните правой кнопкой мыши базу **irissql** и запустите новый запрос.

2. Выполните несколько простых запросов:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Дальнейшие действия

В следующем кратком руководстве вы создадите модель машинного обучения и сохраните ее в таблице, после чего получите результаты прогноза на ее основе.

+ [Краткое руководство. Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md)