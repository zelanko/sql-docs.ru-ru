---
title: Краткое руководство по работе с входных и выходных данных в R - машинного обучения SQL Server
description: В этом кратком руководстве для скрипта R в SQL Server Узнайте, как структурировать входных и выходных данных для системной хранимой процедуры sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4df9e266e16e2cc37ce527c19ba7be483e43d50a
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582687"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Краткое руководство. Обрабатывать входные и выходные данные с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве показано, как для обработки входных данных и выводит при использовании R в службах машинного обучения SQL Server или R Services.

Если вы хотите запустить код R в SQL Server, нужно упаковать скрипт R в хранимой процедуре. Можно написать, или передать R-скрипте [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Эта система, хранимая процедура используется для запуска среды выполнения R в контексте SQL Server, который передает данные в R, безопасно управляет пользовательскими сеансами R и возвращает результаты клиенту.

По умолчанию [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) принимает один входной набор данных, которая обычно предоставляется в виде допустимый SQL-запрос. Другие виды входные данные могут передаваться как переменные SQL.

Хранимая процедура возвращает один кадр данных R как выходные данные, но можно также выводить скалярных величин и модели как переменные. Например можно выходные данные обученной модели в качестве двоичной переменной и передать его в инструкцию T-SQL INSERT для записи в таблицу модели. Можно также создавать графики (в двоичном формате) или скаляры (отдельных значений, таких как дата и время, затраченное время для обучения модели и так далее).

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте R в SQL Server существует](quickstart-r-verify.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

## <a name="create-the-source-data"></a>Создание исходных данных

Создайте небольшую таблицу тестовых данных, выполнив следующую инструкцию T-SQL:

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)
INSERT INTO RTestData VALUES (1);
INSERT INTO RTestData VALUES (10);
INSERT INTO RTestData VALUES (100);
GO
```

После создания таблицы используйте следующую инструкцию, чтобы выполнить запрос к ней:
  
```sql
SELECT * FROM RTestData
```

**Результаты**

![Содержимое таблицы RTestData](./media/select-rtestdata.png)

## <a name="inputs-and-outputs"></a>Входы и выходы

Давайте взглянем на значение по умолчанию входных и выходных переменных sp_execute_external_script: `InputDataSet` и `OutputDataSet`.

1. Могут получать данные из таблицы в качестве входных данных для R-скриптов. Выполните приведенную ниже инструкцию. Он получает данные из таблицы, циклическом прохождении через среду выполнения R и возвращает значения с именем столбца *NewColName*.

    Данные, возвращаемые в запросе передается в среду выполнения R, которая возвращает данные в базу данных SQL в формате кадра данных. В предложении WITH RESULT SETS определяет схему таблицы возвращаемых данных для базы данных SQL.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные сценария R, который возвращает данные из таблицы](./media/r-output-rtestdata.png)

2. Давайте изменим имя входных или выходных переменных. Приведенный выше сценарий по умолчанию входные данные и данные имени переменной, _InputDataSet_ и _OutputDataSet_. Чтобы определить входные данные, связанные с _InputDatSet_, использовании *@input_data_1* переменной.

    В этом скрипте, чтобы были изменены имена входных и выходных переменных для хранимой процедуры *SQL_out* и *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'R'
      , @script = N' SQL_out <- SQL_in;'
      , @input_data_1 = N'SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Обратите внимание, что R учитывает регистр, поэтому регистр входных и выходных переменных в `@input_data_1_name` и `@output_data_1_name` должны соответствовать именам в код R в `@script`. 

    В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако вы можете вызывать другие наборы данных из кода R, а в дополнение к набору данных могут возвращаться выходные данные других типов. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами. 

    `WITH RESULT SETS` Инструкция определяет схему для данных, который используется в SQL Server. Необходимо указать совместимые типы данных SQL для каждого столбца, возвращаемого из R. Определение схемы можно использовать для предоставления новые имена столбцов слишком необходимо использовать имена столбцов из кадра данных R.

3. Вы можете также создать значения с помощью скрипта R и оставить строку ввода запроса в _@input_data_1_ пустым.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N' mytextvariable <- c("hello", " ", "world");
            OutputDataSet <- as.data.frame(mytextvariable);'
        , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Результаты**

    ![Результаты запроса с помощью @script как входные данные](./media/r-data-generated-output.png)

## <a name="next-steps"></a>Следующие шаги

Изучите некоторые проблемы, которые могут возникнуть при передаче данных между R и SQL Server, таких как неявные преобразования и различия в табличных данных R и SQL.

> [!div class="nextstepaction"]
> [Краткое руководство. Обработка типов данных и объектов](quickstart-r-data-types-and-objects.md)