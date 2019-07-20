---
title: Краткое руководство по работе с входными и выходными данными в Python
description: В этом кратком руководстве по скрипту Python в SQL Server сведения о структурировании входных и выходных данных в системную хранимую процедуру sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: a23896f5242e0f1182b2864e426bbb20aeda763f
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344805"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>Краткое руководство. Обработку входных и выходных данных с помощью Python в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве показано, как выполнять обработку входных и выходных данных при использовании Python в SQL Server Службы машинного обучения.

По умолчанию [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) принимает один входной набор данных, который обычно предоставляется в виде допустимого SQL-запроса.

Другие типы входных данных могут передаваться как переменные SQL. Например, обученную модель можно передать как переменную с помощью функции сериализации, такой как поле [выбора](https://docs.python.org/3.0/library/pickle.html) или [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) , для записи модели в двоичном формате.

Хранимая процедура возвращает один кадр данных Python [Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) в качестве выходных данных, но можно также выводить скаляры и модели в виде переменных. Например, можно вывести обученную модель как двоичную переменную и передать ее в инструкцию T-SQL INSERT, чтобы записать эту модель в таблицу. Можно также создавать графики (в двоичном формате) или скаляры (отдельные значения, такие как Дата и время, время, затраченное на обучение модели, и т. д.).

## <a name="prerequisites"></a>предварительные требования

Предыдущее краткое руководство. [Проверка наличия Python в SQL Server](quickstart-python-verify.md)содержит сведения и ссылки для настройки среды Python, необходимой для этого краткого руководства.

## <a name="create-the-source-data"></a>Создание исходных данных

Создайте маленькую таблицу тестовых данных, выполнив следующую инструкцию T-SQL:

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

![Содержимое таблицы Писонтестдата](./media/select-pythontestdata.png)

## <a name="inputs-and-outputs"></a>Входы и выходы

Рассмотрим входные и выходные переменные по умолчанию sp_execute_external_script: `InputDataSet` и. `OutputDataSet`

1. Данные из таблицы можно получить в качестве входных данных для скрипта Python. Выполните приведенную ниже инструкцию. Он получает данные из таблицы, выполняет цикл обработки в среде выполнения Python и возвращает значения с именем столбца *невколнаме*.

    Данные, возвращаемые запросом, передаются в среду выполнения Python, которая возвращает данные в базу данных SQL в виде Pandas. Предложение WITH RESULTSET SETS определяет схему возвращаемой таблицы данных для базы данных SQL.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные скрипта Python, возвращающие данные из таблицы](./media/python-output-pythontestdata.png)

2. Давайте изменим имена входных и выходных переменных. В приведенном выше скрипте использовались имена входных и выходных переменных по умолчанию, _InputDataSet_ и _OutputDataSet_. Чтобы определить входные данные, связанные с _InputDataSet_, используйте *@input_data_1* переменную.

    В этом скрипте имена выходных и входных переменных для хранимой процедуры были изменены на *SQL_out* и *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Регистр входных и выходных переменных в `@input_data_1_name` и `@output_data_1_name` должен соответствовать регистру в коде Python в `@script`, так как в Python учитывается регистр.

    В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако можно вызвать другие наборы данных из кода Python, а также можно вернуть выходные данные других типов в дополнение к набору данных. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами. 

    `WITH RESULT SETS` Инструкция определяет схему для данных, которые используются в SQL Server. Для каждого столбца, возвращаемого из Python, необходимо предоставить совместимые с SQL типы данных. Определение схемы можно использовать для предоставления новых имен столбцов, так как не нужно использовать имена столбцов из файла Python Data. Frame.

3. Можно также формировать значения с помощью скрипта Python и оставлять строку _@input_data_1_ входного запроса пустой.

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

    ![Результаты запроса, @script использующие в качестве входных данных](./media/python-data-generated-output.png)

## <a name="next-steps"></a>Следующие шаги

Изучите некоторые проблемы, которые могут возникнуть при передаче табличных данных между Python и SQL Server.

> [!div class="nextstepaction"]
> [QuickStart Структуры данных Python в SQL Server](quickstart-python-data-structures.md)
