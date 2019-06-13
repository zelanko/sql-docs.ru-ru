---
title: Краткое руководство по работе с входных и выходных данных в Python - машинного обучения SQL Server
description: В этом кратком руководстве для скрипта Python в SQL Server Узнайте, как структурировать входных и выходных данных для системной хранимой процедуры sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fe60197671e40317f56a62ad98ea364a238df174
ms.sourcegitcommit: c3de32efeee3095fcea0d3faebb8f2ff1b56d229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033382"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>Краткое руководство. Обрабатывать входные и выходные данные с помощью Python в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве показано, как для обработки входных данных и выводит при использовании Python в службах машинного обучения SQL Server.

По умолчанию [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) принимает один входной набор данных, которая обычно предоставляется в виде допустимый SQL-запрос.

Другие виды входные данные могут передаваться как переменные SQL: например, можно передать обученной модели как переменную, например с помощью функции сериализации [pickle](https://docs.python.org/3.0/library/pickle.html) или [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для записи модели двоичный формат.

Хранимая процедура возвращает один Python [pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) кадр данных в качестве выходных данных, но можно также выводить скалярных величин и модели как переменные. Например можно выходные данные обученной модели в качестве двоичной переменной и передать его в инструкцию T-SQL INSERT для записи в таблицу модели. Можно также создавать графики (в двоичном формате) или скаляры (отдельных значений, таких как дата и время, затраченное время для обучения модели и так далее).

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте Python в SQL Server существует](quickstart-python-verify.md), сведения и ссылки по настройке среды Python, необходимые для этого краткого руководства.

## <a name="create-the-source-data"></a>Создание исходных данных

Создайте небольшую таблицу тестовых данных, выполнив следующую инструкцию T-SQL:

```sql
CREATE TABLE PythonTestData (col1 INT NOT NULL)
INSERT INTO PythonTestData VALUES (1);
INSERT INTO PythonTestData VALUES (10);
INSERT INTO PythonTestData VALUES (100);
GO
```

После создания таблицы используйте следующую инструкцию, чтобы выполнить запрос к ней:
  
```sql
SELECT * FROM PythonTestData
```

**Результаты**

![Содержимое таблицы PythonTestData](./media/select-pythontestdata.png)

## <a name="inputs-and-outputs"></a>Входы и выходы

Давайте взглянем на значение по умолчанию входных и выходных переменных sp_execute_external_script: `InputDataSet` и `OutputDataSet`.

1. Могут получать данные из таблицы в качестве входных данных для скрипта Python. Выполните приведенную ниже инструкцию. Он получает данные из таблицы, циклическом прохождении через среду выполнения Python и возвращает значения с именем столбца *NewColName*.

    Данные, возвращаемые в запросе передается в среду выполнения Python, который возвращает данные в базу данных SQL как кадр данных pandas. В предложении WITH RESULT SETS определяет схему таблицы возвращаемых данных для базы данных SQL.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные сценария Python, который возвращает данные из таблицы](./media/python-output-pythontestdata.png)

2. Давайте изменим имя входных или выходных переменных. Приведенный выше сценарий по умолчанию входные данные и данные имени переменной, _InputDataSet_ и _OutputDataSet_. Чтобы определить входные данные, связанные с _InputDataSet_, использовании *@input_data_1* переменной.

    В этом скрипте, чтобы были изменены имена входных и выходных переменных для хранимой процедуры *SQL_out* и *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Регистр входных и выходных переменных в `@input_data_1_name` и `@output_data_1_name` нужно учитывать регистр из них в коде Python в `@script`, как Python — с учетом регистра.

    В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Тем не менее можно вызывать другие наборы данных из кода Python, и может возвращать выходные данные других типов в дополнение к набору данных. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами. 

    `WITH RESULT SETS` Инструкция определяет схему для данных, который используется в SQL Server. Необходимо указать совместимые типы данных SQL для каждого столбца, возвращаемого из Python. Определение схемы можно использовать для предоставления новые имена столбцов слишком необходимо использовать имена столбцов из Python data.frame.

3. Вы можете также создать значения с помощью скрипта Python и оставить строку ввода запроса в _@input_data_1_ пустым.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'Python'
    , @script = N'
    import pandas as pd
    mytextvariable = pandas.Series(["hello", " ", "world"]);
    OutputDataSet = pd.DataFrame(mytextvariable);'
    , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Результаты**

    ![Результаты запроса с помощью @script как входные данные](./media/python-data-generated-output.png)

## <a name="next-steps"></a>Следующие шаги

Изучите некоторые проблемы, которые могут возникнуть при передаче табличных данных между Python и SQL Server.

> [!div class="nextstepaction"]
> [Краткое руководство. Структуры данных Python в SQL Server](quickstart-python-data-structures.md)
