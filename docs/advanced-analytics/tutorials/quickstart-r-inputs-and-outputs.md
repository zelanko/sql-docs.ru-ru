---
title: Краткое руководство по работе с входными и выходными данными в R
description: В этом кратком руководстве по скрипту R в SQL Server содержатся сведения о структурировании входных и выходных данных в системную хранимую процедуру sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 4e9e7efe6143d35e627abef4272281aad4b5b184
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469160"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Краткое руководство. Обработку входных и выходных данных с помощью R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве показано, как выполнять обработку входных и выходных данных при использовании R в SQL Server Службы машинного обучения или службах R.

Если вы хотите выполнить код R в SQL Server, необходимо заключить скрипт R в хранимую процедуру. Можно записать один или передать скрипт R в [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Эта системная хранимая процедура используется для запуска среды выполнения R в контексте SQL Server, который передает данные в R, безопасно управляет сеансами пользователей R и возвращает результаты клиенту.

По умолчанию [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) принимает один входной набор данных, который обычно предоставляется в виде допустимого SQL-запроса. Другие типы входных данных могут передаваться как переменные SQL.

Хранимая процедура возвращает один кадр данных R в качестве выходных данных, но вы также можете выводить скаляры и модели в виде переменных. Например, можно вывести обученную модель как двоичную переменную и передать ее в инструкцию T-SQL INSERT, чтобы записать эту модель в таблицу. Можно также создавать графики (в двоичном формате) или скаляры (отдельные значения, такие как Дата и время, время, затраченное на обучение модели, и т. д.).

## <a name="prerequisites"></a>Предварительные требования

Предыдущее краткое руководство, [Проверка наличия R в SQL Server](quickstart-r-verify.md), содержит сведения и ссылки для настройки среды R, необходимой для этого краткого руководства.

## <a name="create-the-source-data"></a>Создание исходных данных

Создайте маленькую таблицу тестовых данных, выполнив следующую инструкцию T-SQL:

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

Рассмотрим входные и выходные переменные по умолчанию sp_execute_external_script: `InputDataSet` и. `OutputDataSet`

1. Данные из таблицы можно получить в качестве входных данных для скрипта R. Выполните приведенную ниже инструкцию. Он получает данные из таблицы, выполняет цикл обработки в среде выполнения R и возвращает значения с именем столбца *невколнаме*.

    Данные, возвращаемые запросом, передаются в среду выполнения R, которая возвращает данные в базу данных SQL в виде кадра данных. Предложение WITH RESULTSET SETS определяет схему возвращаемой таблицы данных для базы данных SQL.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные скрипта R, возвращающие данные из таблицы](./media/r-output-rtestdata.png)

2. Давайте изменим имена входных и выходных переменных. В приведенном выше скрипте использовались имена входных и выходных переменных по умолчанию, _InputDataSet_ и _OutputDataSet_. Чтобы определить входные данные, связанные с _инпутдатсет_, используйте *@input_data_1* переменную.

    В этом скрипте имена выходных и входных переменных для хранимой процедуры были изменены на *SQL_out* и *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'R'
      , @script = N' SQL_out <- SQL_in;'
      , @input_data_1 = N'SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Обратите внимание, что в языке r учитывается регистр, поэтому регистр входных и выходных `@input_data_1_name` переменных `@output_data_1_name` в и должен соответствовать именам в коде R в `@script`. 

    В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако вы можете вызывать другие наборы данных из кода R, а в дополнение к набору данных могут возвращаться выходные данные других типов. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами. 

    `WITH RESULT SETS` Инструкция определяет схему для данных, которые используются в SQL Server. Необходимо предоставить совместимые с SQL типы данных для каждого столбца, возвращаемого из R. Определение схемы можно использовать для предоставления новых имен столбцов, так как не нужно использовать имена столбцов из фрейма данных R.

3. Можно также формировать значения с помощью скрипта R и оставлять строку _@input_data_1_ входного запроса пустой.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N' mytextvariable <- c("hello", " ", "world");
            OutputDataSet <- as.data.frame(mytextvariable);'
        , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Результаты**

    ![Результаты запроса, @script использующие в качестве входных данных](./media/r-data-generated-output.png)

## <a name="next-steps"></a>Следующие шаги

Изучите некоторые проблемы, которые могут возникнуть при передаче данных между R и SQL Server, например неявные преобразования и различия в табличных данных между R и SQL.

> [!div class="nextstepaction"]
> [QuickStart Обработку типов данных и объектов](quickstart-r-data-types-and-objects.md)