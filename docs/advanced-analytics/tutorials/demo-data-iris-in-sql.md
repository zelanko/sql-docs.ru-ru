---
title: Набор данных IRIS Демонстрация учебники Python и R в SQL Server | Документация Майкрософт
Description: Create a database containing the Iris dataset and a table for storing models. This dataset is used in exercises showing how to wrap R language or Python code in a SQL Server stored procedure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2fbe5915f7b135882bbbefbb83b572d2cd640837
ms.sourcegitcommit: 12779bddd056a203d466d83c4a510a97348fe9d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216688"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Демонстрационных данных IRIS учебники Python и R в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом упражнении, создание базы данных SQL Server для хранения данных из [набора данных Iris цветок](https://en.wikipedia.org/wiki/Iris_flower_data_set) и моделей, основанных на тех же данных. Данных IRIS включается в дистрибутивах R и Python, устанавливаемые с SQL Server и используется в учебники по машинному обучению для SQL Server. 

Для этого упражнения вам понадобится [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) или другого средства, которые могут выполнять запросы T-SQL.

Учебники и примеры использования, с помощью этого набора данных включают следующее:

+  [Использовать модели Python в SQL Server для обучения и оценки](train-score-using-python-in-tsql.md)

## <a name="create-the-database"></a>Создайте базу данных

1. Запустите SQL Server Management Studio, а затем открыть новое **запроса** окна.  

2. Создать новую базу данных для этого проекта и изменить контекст на **запроса** окна для работы с новой базы данных.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Если вы еще не знакомы с SQL Server, или при работе с сервером, вы являетесь владельцем, распространенная ошибка — для входа и начать работу, не замечая, вы находитесь в **master** базы данных. Чтобы убедиться, что вы используете правильную базу данных, всегда указывайте контекста с помощью `USE <database name>` инструкции (например, `use irissql`).

3. Добавить пустой таблицы: один для хранения данных, а второй — для хранения обученных моделей. **Iris_models** таблица используется для хранения сериализованного модели, созданные в других упражнениях.

    Следующий код создает таблицу для обучающих данных.

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

    > [!TIP] 
    > Если вы не знакомы с T-SQL, имеет смысл запоминать `DROP...IF` инструкции. При попытке создать таблицу, уже существует, SQL Server возвращает ошибку: «Уже существует объект с именем «iris_data» в базе данных.» Чтобы избежать подобных ошибок рекомендуется удалить все имеющиеся таблицы или другие объекты как часть вашего кода.

4. Запустите следующий код, чтобы создать таблицу, используемую для хранения обученной модели. Для сохранения моделей (R или Python) в SQL Server, они должно быть сериализовано и хранятся в столбце типа **varbinary(max)**. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Дополнение к содержимому модели как правило, вы бы также добавьте столбцы для другие полезные метаданные, такие как имени модели, она была обучение, дата источника алгоритма и параметров, исходные данные и так далее. Сейчас мы пойдем по простому и используйте имя модели.

## <a name="populate-the-table"></a>Заполнение таблицы

Встроенные данных Iris можно получить из R или Python. Можно использовать для загрузки данных в кадр данных R или Python и затем вставить в таблицу в базе данных. Перемещение данных для обучения из внешнего сеанса в таблицу SQL Server — это многоэтапный процесс:

+ Создайте хранимую процедуру, которая получает нужные данные.
+ Выполните хранимую процедуру, чтобы получить данные.
+ Создайте инструкции INSERT, чтобы указать, где следует сохранить извлеченные данные.

1. В системах с интеграцией Python создайте следующую хранимую процедуру, использующий код Python для загрузки данных.

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

    При выполнении этого кода, вы должны получить сообщение «Команд успешно завершено.» Все это означает, что является создания хранимой процедуры в соответствии с вашими характеристиками.

2. Кроме того в системах, где интеграция R, создайте процедуру, которая использует R для этого.

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

3. Фактически заполнение таблицы, выполните хранимую процедуру и укажите таблицу, где данные должны быть записаны. При запуске, хранимая процедура выполняется код Python или R, который загружает встроенный набор данных Iris, а затем вставляет данные в **iris_data** таблицы.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Если вы не знакомы с T-SQL, имейте в виду, что инструкция INSERT добавляет только новые данные; он не будет проверить существующие данные, или удалить и перестроить таблицы. Чтобы избежать получения нескольких копий тех же данных в таблице, можно запустить Эта инструкция сначала: `TRUNCATE TABLE iris_data`. T-SQL, [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) инструкция удаляет существующие данные, но сохраняет структуру таблицы без изменений.

    > [!TIP]
    > Изменение хранимой процедуры позже, не нужно удалить и создать его повторно. Используйте [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) инструкции. 


## <a name="query-the-data"></a>Запрос данных

В качестве шага проверки выполните запрос, чтобы убедиться, что данные были отправлены.

1. В обозревателе объектов в базах данных, щелкните правой кнопкой мыши **irissql** базы данных, а затем запустите новый запрос.

2. Выполните некоторые простые запросы:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Следующие шаги

На следующем занятии будет создать модель машинного обучения и сохраните его в таблицу и затем использовать модели для создания прогнозируемых выходных данных.

+ [Использовать модели Python в SQL Server для обучения и оценки](train-score-using-python-in-tsql.md)
