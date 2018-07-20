---
title: Использование модели Python в SQL для обучения и оценки | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 02ffd5a25c076ef5a65a6e3a998aae485e37d982
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085026"
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>Использование модели Python в SQL для обучения и оценки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В [предыдущее занятие](wrap-python-in-tsql-stored-procedure.md), вы узнали общий шаблон для с помощью Python вместе с SQL. Вы узнали, что Python код должен выходных данных одного четко определенный кадр данных и при необходимости можно выводить несколько переменных скалярные или binary. Вы узнали, что хранимая процедура SQL должны разрабатываться для передачи подходящего типа данных в Python и обработки результатов.

В этом разделе описано используйте этот же шаблон для обучения модели данных, добавленные в SQL Server и сохраните модель в таблицу SQL Server:

+ Создании хранимой процедуры, которая вызывает Python функцию машинного обучения.
+ Хранимая процедура требует данные от SQL Server для использования в обучении модели.
+ Хранимая процедура выходные данные обученной модели, что двоичной переменной. 
+ Сохраните обученную модель путем вставки в таблицу модели переменной. 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>Создайте хранимую процедуру и выполните Обучение модели Python

1. Выполните следующий код в SQL Server Management Studio для создания хранимой процедуры, для построения модели.

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

2. Если эта команда выполняется без ошибок, новую хранимую процедуру создается и добавляется в базу данных. Хранимые процедуры можно найти в среде Management Studio **обозревателя объектов**в разделе **программирования**.

3. Теперь запустите хранимую процедуру.

    ```sql
    EXEC generate_iris_model
    ```

    Должно появиться сообщение об ошибке, так как вы не указали, что требует входных данных хранимой процедуры.

    «Процедура или функция «generate_iris_model» ожидает параметр "\@trained_model", который не был указан.»

4. Чтобы создать модель с необходимые входные данные и сохранить его в таблицу требует некоторых дополнительных инструкций:

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. Теперь попробуйте еще раз выполнение кода создания модели. 

    Вы должны получить сообщение: «нарушение ограничения ПЕРВИЧНОГО ключа невозможно вставить повторяющийся ключ в объект «dbo.iris_models». Повторяющееся значение ключа является (упрощенного алгоритма Байеса)».

    Это, так как имя модели была проведена, вручную введя «Упрощенный алгоритм Байеса» как часть инструкции INSERT. Предположим, что вы планируете создать множество моделей, с помощью различных параметров и различных алгоритмов при каждом запуске, необходимо учесть настройку схему метаданных, чтобы автоматически, можно присвоить имя модели и более легко идентифицировать их.

6. Чтобы обойти эту ошибку, можно внести небольшие изменения в оболочку SQL. Этот пример создает имя уникальным модели путем добавления текущую дату и время:

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes ' + CAST(GETDATE()as varchar)
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    ```

7. Для просмотра моделей, выполните простой инструкции SELECT.

    ```sql
    SELECT * FROM iris_models;
    GO
    ```

    **Результаты**

    |MODEL_NAME | model |
    |------|------|
    | упрощенный алгоритм Байеса | 0x800363736B6C656172... |
    | Упрощенный алгоритм Байеса Jan 01 2018 9:39:00 | 0x800363736B6C656172... |
    | Упрощенный алгоритм Байеса Feb 01 2018 10:51 по | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>Формировать оценки на основе модели

Наконец Загрузите этой модели из таблицы в переменную и передать его обратно в Python для формирования оценок.

1. Запустите следующий код, чтобы создать хранимую процедуру, которая выполняет оценки. 

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

    Хранимая процедура получает из таблицы модели упрощенного алгоритма Байеса и использует функции, связанные с моделью для формирования оценок. В этом примере хранимая процедура получает модель из таблицы, использующей имя модели. Тем не менее в зависимости от того, какого рода метаданные сохраняются в модели, также можно получить самые последние модель или модель с наивысшими показателями точности.

2. Запустите следующие строки, чтобы передать имя модели «Упрощенный алгоритм Байеса» хранимой процедуры, которая выполняет код оценки. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    При выполнении хранимой процедуры, она возвращает Python data.frame. Эта строка T-SQL указывает схему для возвращенных результатов: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    Можно вставлять результаты в новую таблицу, или возвращать их в приложение.

    В этом примере стала простой, используя данные из набора данных iris Python для оценки. (См. в строке `iris_data[[1,2,3,4]])`.) Однако чаще всего вы бы выполнить SQL-запрос для получения новых данных и передавать, Python в качестве `InputDataSet`. 

### <a name="remarks"></a>Примечания

Если вы привыкли работать на языке Python, вы, возможно, привыкли загрузки данных, создание некоторых сводок и диаграмм, а затем обучения модели и создание некоторые показатели в одинаковых 250 строк кода.

Тем не менее если ваша цель — для ввода в эксплуатацию процесса (Создание модели оценки, и т.д.) в SQL Server, необходимо иметь в виду способами, что процесс можно разделить на повторяемые действия, которые могут быть изменены с помощью параметров. Насколько возможно, требуется код Python, который применяется в хранимую процедуру, чтобы были четко определенные входные и выходные данные, которые сопоставляются хранимой процедуры входные и выходные данные.

Кроме того как правило может повысить производительность, разделив их процесса просмотра данных в процессе обучения модели или вычисление оценок. 

Счет и процессов обучения можно часто оптимизировать за счет использования функции SQL Server, например параллельная обработка, или с помощью алгоритмов в [revoscalepy](../python/what-is-revoscalepy.md) или [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , поддержка потоковой передачи и параллельного выполнения, а не с помощью стандартных библиотек Python. 

## <a name="next-lesson"></a>Следующее занятие

В рамках заключительного занятия выполнять код Python из удаленного клиента, используя SQL Server в качестве контекста вычисления. Этот шаг необязателен, если у клиента Python или не планируется запускать Python вне хранимой процедуры.

+ [Создание модели revoscalepy от клиента Python](use-python-revoscalepy-to-create-model.md)
