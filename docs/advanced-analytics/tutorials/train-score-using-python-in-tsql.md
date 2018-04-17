---
title: Использовать модель Python в SQL для обучения и оценки | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b7f5883356ff6878f869ee10f915bcb93a2dba17
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>Использовать модель Python в SQL для обучения и оценки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В [предыдущее занятие](wrap-python-in-tsql-stored-procedure.md), вы узнали общий шаблон для использования Python вместе с SQL. Вы узнали, Python, ваш код должен вывода одного четко определенные data.frame и при необходимости можно выводить несколько переменных скалярные или binary. Вы узнали, что хранимая процедура SQL должны разрабатываться передать подходящего типа данных в Python, и обрабатывать результаты.

В этом разделе использовать этот же шаблон для обучения модели на данные, которые вы добавили в SQL Server и сохраните модель в таблицу SQL Server:

+ Создании хранимой процедуры, которая вызывает Python функцию машинного обучения.
+ Хранимая процедура требует данные от SQL Server для использования в обучении модели.
+ Хранимая процедура выводит обученной модели как двоичные переменной. 
+ Сохранить обученную модель, вставка переменной модели в таблицу. 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>Создайте хранимую процедуру и выполните Обучение модели Python

1. Выполните следующий код в SQL Server Management Studio, чтобы создать хранимую процедуру, которая строит модель.

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

2. Если эта команда выполняется без ошибок, новой хранимой процедуры создается и добавляется в базу данных. Хранимые процедуры можно найти в среде Management Studio **обозревателя объектов**в разделе **программирование**.

3. Теперь запустите хранимую процедуру.

    ```sql
    EXEC generate_iris_model
    ```

    Должно появиться ошибку, так как вы не указали, что требует ввода хранимой процедуры.

    «Процедура или функция «generate_iris_model» ожидает параметр "@trained_model", который не был предоставлен.»

4. Для создания модели, входные данные, необходимые и сохранить в таблицу требуются некоторые дополнительные инструкции:

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. Попробуйте еще раз выполнить код создания модели. 

    Вы должны получить сообщение: «нарушение ограничения ПЕРВИЧНОГО ключа невозможно вставить повторяющийся ключ в объект «dbo.iris_models». Повторяющееся значение ключа является (упрощенного алгоритма Байеса)».

    Это так, как указано имя модели, вручную введя в «Упрощенный алгоритм Байеса» как часть инструкции INSERT. Предположим, что вы планируете создать большое количество моделей, используя другие параметры или различных алгоритмов при каждом запуске, параметр следует рассматривать схему метаданные, чтобы автоматически, можно присвоить имя модели и более легко идентифицировать их.

6. Чтобы обойти эту ошибку, можно внести некоторые небольшие изменения SQL программу-оболочку. Этот пример создает имя уникальным модели путем добавления текущую дату и время:

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes ' + CAST(GETDATE()as varchar)
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    ```

7. Для просмотра моделей, запустите простой инструкции SELECT.

    ```sql
    SELECT * FROM iris_models;
    GO
    ```

    **Результаты**

    |MODEL_NAME | model |
    |------|------|
    | упрощенный алгоритм Байеса | 0x800363736B6C656172... |
    | Упрощенный алгоритм Байеса 2018 01 янв 9:39:00 | 0x800363736B6C656172... |
    | Упрощенный алгоритм Байеса 01 фев 2018 10:51 по | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>Формировать оценки на основе модели

Наконец давайте загрузить эту модель из таблицы в переменную и передать его Python для формирования оценок.

1. Выполните следующий код для создания хранимой процедуры, которая выполняет оценки. 

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
    OutputDataSet = iris_data.query( ''PredictedSpecies != SpeciesId'' )[[0, 5, 6]]
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

    Хранимая процедура возвращает из таблицы модели упрощенного алгоритма Байеса и использует функции, связанные с моделью для формирования оценок. В этом примере хранимая процедура возвращает модель из таблицы, используя имя модели. Тем не менее в зависимости от того, какие метаданные сохраняются в модели, можно также получить самые последние модели или модели с высокой степени точности.

2. Запустите следующие строки, чтобы передать имя модели «Упрощенный алгоритм Байеса» хранимой процедуры, которая выполняет код, оценки. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    При выполнении хранимой процедуры, она возвращает Python data.frame. Эта строка T-SQL указывает схему для возвращаемых результатов: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    Можно вставлять результаты в новую таблицу или возврат их в приложение.

    В этом примере были приложены простой, используя данные из набора данных iris Python для оценки. (См. в строке `iris_data[[1,2,3,4]])`.) Однако более обычно выполнить SQL-запрос для получения новых данных и передачи, в Python как `InputDataSet`. 

### <a name="remarks"></a>Замечания

Если вы привыкли работать в Python, может быть привычно загрузка данных, создание некоторых сводки и диаграмм, а затем Обучение модели и создание некоторые показатели в 250 одной строки кода.

Однако если вашей целью является ввода в эксплуатацию процесса (Создание моделей, оценки, т. д.) в SQL Server, необходимо принять во внимание способами, что процесс можно разделить на повторяемые действия, которые могут быть изменены с помощью параметров. Возможно, требуется код Python при запуске в хранимой процедуре, имеют четко определенные входные и выходные данные, сопоставленные хранимой процедуры входы и выходы.

Кроме того обычно можно улучшить производительность путем разделения процесса просмотра данных в процессе обучения модели или формировать оценки. 

Счет и процессы обучения можно часто оптимизировать за счет использования функции SQL Server, например параллельная обработка или с помощью алгоритмов в [revoscalepy](../python/what-is-revoscalepy.md) или [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , поддержка потоковой передачи и параллельного выполнения, а не с помощью стандартных библиотек Python. 

## <a name="next-lesson"></a>Следующее занятие

Окончательный занятия выполнять код Python из удаленного клиента, с помощью SQL Server в контексте. Этот шаг необязателен, если нет клиента Python или не будет выполнен Python, извне хранимой процедуры.

+ [Создать модель revoscalepy от клиента Python](use-python-revoscalepy-to-create-model.md)
