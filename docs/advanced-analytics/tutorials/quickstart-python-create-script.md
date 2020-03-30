---
title: Краткое руководство. Выполнение скриптов Python
description: Сведения о выполнении простых скриптов Python с помощью Служб машинного обучения SQL Server Вы узнаете, как применить хранимую процедуру sp_execute_external_script для выполнения скрипта в экземпляре SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8c1347d58f0b8a4014a51a220b6ecded5a343082
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "76831914"
---
# <a name="quickstart-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>Краткое руководство. Выполнение простых скриптов Python с помощью Служб машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы запустите ряд простых скриптов Python, используя [Службы машинного обучения SQL Server](../what-is-sql-server-machine-learning.md). Также вы узнаете, как применить хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для выполнения скрипта в экземпляре SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server со [службами машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) и с установленным языком Python.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих сценарии Python. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, которые могут подключаться к экземпляру SQL Server и выполнять запросы T-SQL или хранимые процедуры. В этом кратком руководстве используется среда [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Выполнение простого сценария

Чтобы выполнить сценарий Python, необходимо передать его в качестве аргумента в системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Эта системная хранимая процедура запускает среду выполнения Python в контексте SQL Server, передает данные в Python, безопасно управляет пользовательскими сеансами в Python и возвращает результаты на клиент.

Далее вы будете выполните этот пример сценария Python в своем экземпляре SQL Server.

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. Откройте новое окно запроса в среде **SQL Server Management Studio**, подключенной к вашему экземпляру SQL Server.

1. Передайте весь сценарий Python в хранимую процедуру `sp_execute_external_script`.

   Сценарий передается с помощью аргумента `@script`. Все, что находится внутри аргумента `@script`, должно быть допустимым кодом Python.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

1. Далее вычисляется правильный результат, и функция Python `print` возвращает результат в окне **Сообщения**.

   Он должен выглядеть примерно так.

    **Результаты**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Выполнение сценария Hello World

Типичный пример — сценарий, который просто выводит строку "Hello World". Выполните следующую команду.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

В хранимую процедуру `sp_execute_external_script` передаются следующие входные данные.

| | |
|-|-|
| @language | Определяет вызываемое расширение языка (в данном случае Python). |
| @script | Определяет команды, которые передаются в среду выполнения Python.<br>Весь скрипт Python должен быть включен в этот аргумент в виде текста в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее. |
| @input_data_1 | Данные, возвращаемые запросом, передаются в среду выполнения Python, которая возвращает эти данные в SQL Server в виде кадра данных. |
|WITH RESULT SETS | Это предложение определяет схему возвращаемой таблицы данных для SQL Server. В данном случае добавляется "Hello World" в качестве имени столбца и **int** в качестве типа данных. |

Эта команда выводит следующий текст:

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Использование входных и выходных данных

По умолчанию процедура `sp_execute_external_script` принимает в качестве входных данных один набор данных, обычно предоставляемый в виде допустимого SQL-запроса. Затем она возвращает один кадр данных Python в качестве выходных данных.

Сейчас мы будем использовать заданные по умолчанию входные и выходные переменные процедуры `sp_execute_external_script`: **InputDataSet** и **OutputDataSet**.

1. Создайте небольшую таблицу тестовых данных.

    ```sql
    CREATE TABLE PythonTestData (col1 INT NOT NULL)
    
    INSERT INTO PythonTestData
    VALUES (1);
    
    INSERT INTO PythonTestData
    VALUES (10);
    
    INSERT INTO PythonTestData
    VALUES (100);
    GO
    ```

1. Используйте инструкцию `SELECT` для запроса в эту таблицу.
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **Результаты**

    ![Содержимое таблицы PythonTestData](./media/select-pythontestdata.png)

1. Выполните следующий скрипт Python. Он получает данные из таблицы с помощью инструкции `SELECT`, передает их через среду выполнения Python и возвращает результаты в виде кадра данных. Предложение `WITH RESULT SETS` определяет схему таблицы возвращаемых данных для SQL Server, добавляя имя столбца *NewColName*.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Результат скрипта Python, возвращающий данные из таблицы](./media/python-output-pythontestdata.png)

1. Теперь измените имена входных и выходных переменных. Имена входных и выходных переменных по умолчанию°— **InputDataSet** и **OutputDataSet**. Следующий сценарий изменяет их на **SQL_in** и **SQL_out**.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Обратите внимание, что в Python учитывается регистр. Входные и выходные переменные, используемые в сценарии Python (**SQL_out**, **SQL_in**), должны соответствовать именам, определенным в аргументах `@input_data_1_name` и `@output_data_1_name`, включая регистр.

   > [!TIP]
   > В качестве параметра может быть передан только один входной набор данных, и можно возвращать только один набор данных. Однако вы можете вызывать из кода Python другие наборы данных, а также возвращать выходные данные других типов в дополнение к этому набору данных. Вы также можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами.

1. Можно также формировать значения только с помощью сценария Python, без каких-либо входных данных (в аргументе `@input_data_1` задано пустое значение).

   Следующий сценарий выводит текст "hello" и "world".

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   mytextvariable = pandas.Series(["hello", " ", "world"]);
   OutputDataSet = pd.DataFrame(mytextvariable);
   '
       , @input_data_1 = N''
   WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
   ```

   **Результаты**

   ![Результаты запроса с использованием @script в качестве входных данных](./media/python-data-generated-output.png)

> [!NOTE]
> В Python начальные пробелы используются для группирования инструкций. Поэтому когда внедренный сценарий Python разделяется на несколько строк, как в предыдущем примере, не пытайтесь выровнять команды Python по одной линии с командами SQL. Например, следующий сценарий выдаст ошибку.

  ```text
  EXECUTE sp_execute_external_script @language = N'Python'
      , @script = N'
      import pandas as pd
      mytextvariable = pandas.Series(["hello", " ", "world"]);
      OutputDataSet = pd.DataFrame(mytextvariable);
      '
      , @input_data_1 = N''
  WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
  ```

## <a name="check-python-version"></a>Проверка версии Python

Если вы хотите узнать, какая версия Python установлена в вашем экземпляре SQL Server, выполните следующий сценарий.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Функция Python `print` возвращает версию в окне **Сообщения**. В приведенном ниже примере можно видеть, что в данном случае установлен Python версии 3.5.2.

**Результаты**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>Список пакетов Python

Майкрософт предоставляет ряд пакетов Python, которые предустанавливаются со службами машинного обучения SQL Server в вашем экземпляре SQL Server.

Чтобы просмотреть список установленных пакетов Python вместе с их версиями, выполните следующий сценарий.

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pkg_resources
import pandas
dists = [str(d) for d in pkg_resources.working_set]
OutputDataSet = pandas.DataFrame(dists)
'
WITH RESULT SETS(([Package] NVARCHAR(max)))
GO
```

Список возвращается из `pkg_resources.working_set` в Python в формате кадра данных.

**Результаты**

:::image type="content" source="media/python-package-list.png" alt-text="Просмотр всех установленных пакетов Python":::

## <a name="next-steps"></a>Дальнейшие действия

О том, как использовать структуры данных при использовании Python в службах машинного обучения SQL Server, см. в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Краткое руководство. Работа с типами данных и объектами при использовании Python в службах машинного обучения SQL Server](quickstart-python-data-structures.md)

Дополнительные сведения об использовании Python в службах машинного обучения SQL Server см. в следующих статьях:

- [Написание расширенных функций Python с использованием служб машинного обучения SQL Server](quickstart-python-functions.md)
- [Создание и оценка модели прогнозов в Python с помощью служб машинного обучения SQL Server](quickstart-python-train-score-model.md)
- [Что такое службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
