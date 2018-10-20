---
title: Использовать модели Python в SQL Server для обучения и прогнозы | Документация Майкрософт
description: Создайте и Обучите модель с помощью Python и классический набор данных Iris. Сохранить модель в SQL Server и затем использовать его для создания прогнозируемых выходных данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 839bcecdeaf7b5e2a7ea1297fe941353bffed20e
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461840"
---
# <a name="use-a-python-model-in-sql-server-for-training-and-scoring"></a>Использовать модели Python в SQL Server для обучения и оценки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом упражнении Python узнаете распространенный подход для создания, обучения и использование модели в SQL Server. Оно создает две хранимые процедуры. Первый из них создает модель упрощенного алгоритма Байеса для прогнозирования виды цветов ириса на основе характеристик цветок. Вторая процедура предназначена для оценки. Он вызывает модель, созданная в первой процедуре в выходной набор прогнозов. Путем пошагового выполнения этого упражнения, вы узнаете основные методы, которые основаны на выполнение кода Python на экземпляр ядра СУБД SQL Server.

Демонстрационные данные, используемые в этом упражнении [набор данных Iris](demo-data-iris-in-sql.md) в **irissql** базы данных.

## <a name="create-a-model-using-a-sproc"></a>Создание модели с помощью sproc

1. Откройте новое окно запроса в среде Management Studio, подключенных к **irissql** базы данных. 

    ```sql
    USE irissql
    GO
    ```

2. Выполните следующий код в новом окне запроса для создания хранимой процедуры, которая создает и обучает модель. Модели, сохраненные для повторного использования в SQL Server сериализуются в виде байтового потока и хранятся в столбце VARBINARY(MAX) в таблице базы данных. После создания модели квалификацию, сериализации и сохраняются в базе данных, он может вызываться другими процедурами или с помощью функции ПРОГНОЗИРОВАНИЯ T-SQL в оценки рабочих нагрузок.

   Этот код использует pickle для сериализации модели и scikit для предоставления упрощенный алгоритм Байеса. Модель будет обучена с использованием данных из столбцов от 0 до 4 **iris_data** таблицы. Параметры, вы увидите во второй части процедуры излагать входных данных и выходных данных модели. 

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]]))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

3. Убедитесь, что эта хранимая процедура существует. Если скрипт T-SQL на предыдущем шаге был выполнен без ошибок, новая хранимая процедура с именем **generate_iris_model** создается и добавляется к **irissql** базы данных. Хранимые процедуры можно найти в среде Management Studio **обозревателя объектов**в разделе **программирования**.

## <a name="execute-the-sproc-to-create-and-train-models"></a>Выполнение хранимой процедуры sproc для создания и обучения моделей

1. После создания хранимой процедуры, выполните следующий код ниже, чтобы выполнить его. Инструкции для выполнения хранимой процедуры — `EXEC` в пятой строке.

   Данном конкретном сценарии удаляет существующую модель с таким же именем («упрощенный алгоритм Байеса»), чтобы освободить место для новых, созданные путем повторного запуска ту же процедуру. Без удаления модели возникает ошибка о том, что объект уже существует. 

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes '
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Просмотрите результаты в области вывода. Этот скрипт содержит инструкцию SELECT, показывающий, что модель существует. Другой способ получения списка моделей — `SELECT * FROM iris_models` в **irissql**.

    **Результаты**

    |   | (отсутствует имя столбца |
    |---|-----------------|
    | 1 | упрощенный алгоритм Байеса     | 


## <a name="create-and-execute-a-sproc-for-generating-predictions"></a>Создание и выполнение sproc для создания прогнозов

Теперь, когда создания, обучения и сохранить модель, перейти к следующему шагу: Создание хранимой процедуры, которая создает прогнозы. Вы будете этого вызывающий sp_execute_external_script для запуска Python и затем передать в скрипт Python, который загружает сериализованную модель, созданной в предыдущем упражнении и передает ему входных данных для оценки.

1. Запустите следующий код, чтобы создать хранимую процедуру, которая выполняет оценки. Во время выполнения этой процедуры будет загрузить двоичная модель, используйте столбцы `[1,2,3,4]` на входе и указать столбцы `[0,5,6]` как выходные данные.

    ```sql
    CREATE PROCEDURE predict_species (@model varchar(100))
    AS
    BEGIN
    DECLARE @nb_model varbinary(max) = (SELECT model FROM iris_models WHERE model_name = @model);
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    import pickle
    irismodel = pickle.loads(nb_model)
    species_pred = irismodel.predict(iris_data[[1,2,3,4]])
    iris_data["PredictedSpecies"] = species_pred
    OutputDataSet = iris_data[[0,5,6]] 
    print(OutputDataSet)
    '
    , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@nb_model varbinary(max)'
    , @nb_model = @nb_model
    WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));
    END;
    GO
    ```

2. Выполните хранимую процедуру, предоставляя имя модели «Упрощенный алгоритм Байеса», чтобы процедура знал, какую модель для использования. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    При выполнении хранимой процедуры, она возвращает Python data.frame. Эта строка T-SQL указывает схему для возвращенных результатов: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Можно вставлять результаты в новую таблицу, или возвращать их в приложение.

    ![Результирующий набор из хранимой процедуры](media/train-score-using-python-NB-model-results.png)

    Результаты будут 150 прогнозы о виды цветов, используя цветочно характеристики в качестве входных данных. Для большинства наблюдений прогнозируемое указывает, следует соответствует фактическое виды цветов.

    В этом примере стала простой с помощью набора данных iris Python для обучения и оценки. Более типичный подход может быть связана с выполнением SQL-запрос для получения новых данных и передавать, Python в качестве `InputDataSet`. 

## <a name="conclusion"></a>Заключение

В этом упражнении вы узнали, как создавать хранимые процедуры для различных задач, где каждой хранимой процедуры используется системная хранимая процедура [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) запустить процесс Python. Входные данные для процесса Python передаются в сценарий sp_execute_external как параметры. Переменные данных в базе данных SQL Server и самого сценария Python, передаются как входные данные.

Если вы привыкли работать на языке Python, вы, возможно, привыкли загрузки данных, создание некоторых сводок и диаграмм, а затем обучения модели и создание некоторые показатели в одинаковых 250 строк кода. В этой статье отличается от традиционные подходы, объединяя операции в отдельные инструкции. Такой подход полезно на нескольких уровнях.

Одним из преимуществ является то, что можно отделить процессов в повторяемые действия, которые могут быть изменены с помощью параметров. Насколько возможно, требуется код Python, который применяется в хранимую процедуру, чтобы были четко определенные входные и выходные данные, которые сопоставляются входных данных хранимой процедуры и выходные данные, которые могут быть переданы в во время выполнения. В этом упражнении кода Python, который создает модель (с именем «Упрощенный алгоритм Байеса» в этом примере) передается в качестве входных данных вторая хранимая процедура, которая вызывает модель в процессе оценки.

Второе преимущество в том, что обучающие и оценки процессов можно оптимизировать за счет использования функций SQL Server, таких как параллельную обработку, управление ресурсами, или с помощью алгоритмов в [revoscalepy](../python/what-is-revoscalepy.md) или [MicrosoftML ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , поддерживают потоковую передачу и параллельное выполнение. Разделяя обучения и оценки, вы можете ориентироваться оптимизация для конкретных рабочих нагрузок.

## <a name="next-steps"></a>Следующие шаги

Предыдущих руководствах уделяется локального выполнения. Тем не менее можно выполнять также кода Python на клиентской рабочей станции, используя SQL Server в качестве контекста удаленных вычислений. Дополнительные сведения о настройке клиентской рабочей станции, который подключается к SQL Server, см. в разделе [настроить клиентские средства Python](../python/setup-python-client-tools-sql.md).

+ [Создание модели revoscalepy от клиента Python](use-python-revoscalepy-to-create-model.md)
