---
title: Набор демонстрационных данных IRI для учебников по Python и R
Description: Создайте базу данных, содержащую набор данных IRI, и таблицу для хранения моделей. Этот набор данных используется в упражнениях, демонстрирующих создание оболочки языка R или кода Python в SQL Server хранимой процедуре.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9e5fb470e9045060e6cf2423470c2e4e1ee14f30
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469647"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Демонстрационные данные IRI для учебников по Python и R в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом упражнении вы создадите базу данных SQL Server для хранения данных из [набора данных IRI цветок](https://en.wikipedia.org/wiki/Iris_flower_data_set) и моделей на основе одних и тех же данных. Данные IRI включены в дистрибутивы R и Python, установленные SQL Server, и используются в руководствах по машинному обучению для SQL Server. 

Для выполнения этого упражнения необходимо иметь [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) или другое средство, которое может выполнять запросы T-SQL.

Ниже приведены руководства и краткие руководства, в которых используется этот набор данных.

+  [QuickStart Создание, обучение и использование модели Python с хранимыми процедурами в SQL Server](quickstart-python-train-score-in-tsql.md)

## <a name="create-the-database"></a>Создайте базу данных

1. Запустите SQL Server Management Studio и откройте новое окно **запроса** .  

2. Создайте новую базу данных для этого проекта и измените контекст окна **запроса** , чтобы она использовала новую базу данных.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Если вы не знакомы с SQL Server или работаете на сервере, которому вы владеете, то распространенной ошибкой является вход в систему и начало работы, не указывая, что вы находитесь в базе данных **master** . Чтобы убедиться, что используется правильная база данных, всегда указывайте контекст с помощью `USE <database name>` инструкции (например, `use irissql`).

3. Добавьте пустые таблицы: одну для хранения данных и одну для хранения обученных моделей. Таблица **iris_models** используется для хранения сериализованных моделей, созданных в других упражнениях.

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
    > Если вы не знакомы с T-SQL, то запомните `DROP...IF` инструкцию. При попытке создать таблицу, которая уже существует, SQL Server возвращает ошибку: "В базе данных уже имеется объект с именем" iris_data ". Одним из способов избежать таких ошибок является удаление существующих таблиц или других объектов в рамках кода.

4. Выполните следующий код, чтобы создать таблицу, используемую для хранения обученной модели. Чтобы сохранить модели Python (или R) в SQL Server, они должны быть сериализованы и сохранены в столбце типа **varbinary (max)** . 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    В дополнение к содержимому модели, как правило, также добавляются столбцы для других полезных метаданных, например имя модели, Дата обучения, исходный алгоритм и параметры, исходные данные и т. д. Теперь мы будем просто использовать только имя модели.

## <a name="populate-the-table"></a>Заполнение таблицы

Вы можете получать встроенные данные IRI из R или Python. Можно использовать Python или R для загрузки данных в кадр данных, а затем вставить их в таблицу базы данных. Перемещение обучающих данных из внешнего сеанса в SQL Serverную таблицу является многошаговым процессом.

+ Создайте хранимую процедуру, которая получает нужные данные.
+ Для фактического получения данных выполните хранимую процедуру.
+ Создайте инструкцию INSERT, чтобы указать, куда должны быть сохранены извлеченные данные.

1. В системах с интеграцией Python создайте следующую хранимую процедуру, которая использует код Python для загрузки данных.

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

    При выполнении этого кода должно появиться сообщение "успешно завершенные команды". Все это означает, что хранимая процедура была создана в соответствии со спецификациями.

2. Кроме того, в системах с интеграцией R Создайте процедуру, использующую R.

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

3. Для фактического заполнения таблицы выполните хранимую процедуру и укажите таблицу, в которую должны быть записаны данные. При запуске хранимая процедура выполняет код Python или R, который загружает встроенный набор данных IRI, а затем вставляет данные в таблицу **iris_data** .

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Если вы не знакомы с T-SQL, имейте в виду, что инструкция INSERT добавляет только новые данные. Он не проверяет наличие существующих данных, а также удаляет и перестраивает таблицу. Чтобы избежать получения нескольких копий одних и тех же данных в таблице, можно сначала выполнить эту инструкцию `TRUNCATE TABLE iris_data`:. Инструкция T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) удаляет существующие данные, но сохраняет структуру таблицы в неизменном виде.

    > [!TIP]
    > Чтобы изменить хранимую процедуру позже, не нужно удалять и повторно создавать ее. Используйте инструкцию [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) . 


## <a name="query-the-data"></a>Запрос данных

В качестве шага проверки выполните запрос для подтверждения передачи данных.

1. В обозревателе объектов в разделе базы данных щелкните правой кнопкой мыши базу данных **ирисскл** и запустите новый запрос.

2. Выполните некоторые простые запросы:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Следующие шаги

В следующем кратком руководстве мы создадим модель машинного обучения и сохраняем ее в таблице, а затем используем эту модель для создания прогнозируемых результатов.

+ [QuickStart Создание, обучение и использование модели Python с хранимыми процедурами в SQL Server](quickstart-python-train-score-in-tsql.md)
