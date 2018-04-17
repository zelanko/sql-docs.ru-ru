---
title: Поместите код Python в хранимой процедуре | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b0c32ba91698345adea542ed5929a494b00059e5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="wrap-python-code-in-a-stored-procedure"></a>Поместите код Python в хранимой процедуре
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В [предыдущее занятие](run-python-using-t-sql.md), вы узнали, как сделать Python обращайтесь к SQL Server. На этом занятии вы узнаете, как внедрить код Python в хранимой процедуре, чтобы получать данные из наборов Python образец данных и запись данных в таблицу SQL Server.

Системная хранимая процедура [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) предоставляет оболочки, которое передает переменные SQL и наборы данных SQL в Python. Он также обрабатывает вывода результатов, Python и передает их в SQL Server в формате совместима с типами данных SQL.

Давайте посмотрим, как это работает.

## <a name="prepare-the-database-and-tables"></a>Подготовка базы данных и таблиц

Хотя допускается настройка удаленного клиента и выполнять код Python, с помощью кода Visual Studio, Visual Studio, PyCharm или другие средства, упрощающие сценарии, весь код в этом разделе следует выполнять как часть хранимой процедуры.

1. Запустите SQL Server Management Studio, а затем открыть новое **запроса** окна.  

2. Создать новую базу данных для этого проекта и изменить контекст на **запроса** окна для использования новой базы данных.

    ```sql
    CREATE DATABASE sqlpy;
    GO;
    USE sqlpy;
    GO;
    ```

    > [!TIP] 
    > Если вы не знакомы с SQL Server или работе на сервере, вы являетесь владельцем, распространенная ошибка заключается в том, для входа и начать работу без отметить, что вы являетесь **master** базы данных. Чтобы убедиться, что вы используете нужную базу данных, всегда указывать контекст с помощью `USE <database name>` инструкции.

3. Добавить некоторые пустые таблицы: один для хранения данных и один для хранения обучения моделей. Далее необходимо заполнить таблицы с помощью Python.

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

    Если вы не знакомы с T-SQL, имеет смысл запоминании `DROP...IF` инструкции. При попытке создать таблицу, уже существует, SQL Server возвращает ошибку: «Уже существует объект с именем «iris_data» в базе данных.» Один из способов избежать таких ошибок является удаление существующих таблиц или других объектов в рамках кода.

4. Выполните следующий код, чтобы создать таблицу, используемую для хранения обученной модели. Для сохранения моделей Python (или R) в SQL Server, они должно быть сериализовано и хранятся в столбце типа **varbinary(max)**. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Дополнение к содержимому модели обычно, также добавьте столбцы для других полезных метаданные, такие как имени модели, обучен, дата источника алгоритма и параметров, источник данных и так далее. Сейчас мы должен быть простым и используйте имя модели.

## <a name="populate-the-table"></a>Заполните таблицу

Переместить обучающие данные из Python в SQL Server таблицы состоит из нескольких шагов:

+ Создании хранимой процедуры, которая возвращает нужные данные.
+ Можно выполнить хранимую процедуру, чтобы получить данные.
+ Инструкция INSERT позволяет указать, где следует сохранить полученные данные.

1. Создайте следующую хранимую процедуру, которая включает код Python. 

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

    При выполнении этого кода должно появиться сообщение «Команд успешно завершено.» Это означает —, что хранимая процедура создана в соответствии с требованиями.

2. Фактически заполнение таблицы, выполните хранимую процедуру и указать таблицу, где должны записываться данные. При выполнении хранимой процедуры выполняется код Python, который загружает набор данных Iris из встроенного образца данных Python.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Если вы не знакомы с T-SQL, имейте в виду, что инструкция INSERT добавляет только новые данные; он не будет проверки существующих данных или удалите и перестройте таблицу. Чтобы избежать получения нескольких копий тех же данных в таблице, можно запустить эту инструкцию сначала: `TRUNCATE TABLE iris_data`. T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) инструкция удаляет существующие данные, но сохраняет структуру таблицы без изменений.

    > [!TIP]
    > Изменение хранимой процедуры более поздней версии, не нужно удалить и создать его заново. Используйте [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) инструкции. 

3. Чтобы проверить, правильно загрузить данные, можно запустить несколько простых запросов:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

В [занятию](../tutorials/train-score-using-python-in-tsql.md), создайте модель машинного обучения и сохраните его в таблицу.

### <a name="further-reading-about-stored-procedures"></a>Дополнительные сведения о хранимых процедурах

Если вы не знакомы с SQL Server, может оказаться сложным сначала хранимых процедур. Однако хранимая процедура — это мощный и гибкий интерфейс для передачи данных между приложением и сервером. С помощью хранимой процедуры, можно динамически определить входные данные, что упрощает для передачи в новых имен модели, новые параметры и новые данные, не изменяя код Python.

Общие сведения о работе хранимых процедур в разделе [хранимых процедур (ядро СУБД)](https://docs.microsoft.com/sql/relational-databases/stored-procedures/stored-procedures-database-engine), или этот учебник: [написание инструкций Transact-SQL](https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements).

Существуют также некоторые хорошо учебники на веб-узлам сообщества такие как [SQL Server Central](http://www.sqlservercentral.com/) или [команды SQL](http://www.sqlteam.com/).

Как вы думаете о том, как лучше всего инкапсулировать код Python в T-SQL, также рассмотреть возможность использования этих функций:

+ Определение значений по умолчанию для хранимой процедуры
+ С помощью ключевого слова OUTPUT для передачи данных через входные переменные
+ Создание определений схемы с помощью РЕЗУЛЬТАТОВ с помощью данных используется приложениями, имеет правильные данные типы и имена столбцов
+ Позволяет использовать подсказки для улучшения пакетной обработки
+ Олицетворение другого пользователя для тестирования кода, с помощью инструкции EXECUTE AS предложение

## <a name="next-lesson"></a>Следующее занятие

[Обучение модели Python и формирования оценок в SQL Server](../tutorials/train-score-using-python-in-tsql.md)