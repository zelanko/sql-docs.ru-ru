---
title: Создание и выполнение простых скриптов Python
titleSuffix: SQL Server Machine Learning Services
description: Создавайте и запускайте простые скрипты Python в экземпляре SQL Server с SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ecf99f1ae70cf44b32955ae164dbe3017bdf5f24
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006115"
---
# <a name="quickstart-create-and-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>Краткое руководство. Создание и выполнение простых скриптов Python с помощью SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы создадите и выполните набор простых скриптов Python с помощью [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md). Вы узнаете, как заключить правильно сформированный сценарий Python в хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) и выполнить скрипт в SQL Serverном экземпляре.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server с [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) с установленным языком Python.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих скрипты Python. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, если они могут подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Выполнение простого скрипта

Чтобы выполнить сценарий Python, необходимо передать его в качестве аргумента в системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Эта системная хранимая процедура запускает среду выполнения Python в контексте SQL Server, передает данные в Python, безопасно управляет сеансами пользователей Python и возвращает результаты клиенту.

В следующих шагах вы выполните этот пример скрипта Python в экземпляре SQL Server:

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. Откройте новое окно запроса в **SQL Server Management Studio** , подключенном к экземпляру SQL Server.

1. Передайте полный сценарий Python в хранимую процедуру `sp_execute_external_script`.

   Скрипт передается через аргумент `@script`. Все, что находится внутри аргумента `@script`, должно быть допустимым кодом Python.

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

1. Вычисляется правильный результат, и функция Python `print` возвращает результат в окно **сообщений** .

   Он должен выглядеть примерно так.

    **Результаты**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Выполнение скрипта Hello World

Типичный пример сценария — это тот, который просто выводит строку "Hello World". Выполните следующую команду.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Входные данные для хранимой процедуры `sp_execute_external_script` включают:

| | |
|-|-|
| @language | Определяет расширение языка для вызова, в данном случае Python |
| @script | Определение команд, передаваемых в среду выполнения Python<br>Весь сценарий Python должен быть заключен в этот аргумент как текст в Юникоде. Можно также добавить текст в переменную типа **nvarchar** , а затем вызвать переменную |
| @input_data_1 | данные, возвращаемые запросом, переданные в среду выполнения Python, которая возвращает данные для SQL Server в виде кадра данных |
|WITH RESULT SETS | Определяет схему возвращаемой таблицы данных для SQL Server, в данном случае добавляет "Hello World" в качестве имени столбца и **int** для типа данных. |

Команда выводит следующий текст:

| Всем привет |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Использование входных и выходных данных

По умолчанию `sp_execute_external_script` принимает один набор данных в качестве входных, что обычно предоставляется в виде допустимого SQL-запроса. Затем он возвращает один кадр данных Python в качестве выходных данных.

Сейчас давайте будем использовать входные и выходные переменные по умолчанию `sp_execute_external_script`: **InputDataSet** и **OutputDataSet**.

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

1. Используйте инструкцию `SELECT` для запроса таблицы.
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **Результаты**

    ![Содержимое таблицы Писонтестдата](./media/select-pythontestdata.png)

1. Выполните следующий скрипт Python. Он получает данные из таблицы с помощью оператора `SELECT`, передает их через среду выполнения Python и возвращает данные в виде кадра данных. Предложение `WITH RESULT SETS` определяет схему возвращаемой таблицы данных для SQL, добавляя имя столбца *невколнаме*.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные скрипта Python, возвращающие данные из таблицы](./media/python-output-pythontestdata.png)

1. Теперь измените имена входных и выходных переменных. Имена входных и выходных переменных по умолчанию — **InputDataSet** и **OutputDataSet**, следующий сценарий изменяет имена на **SQL_in** и **SQL_out**:

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Обратите внимание, что в Python учитывается регистр. Входные и выходные переменные, используемые в скрипте Python (**SQL_out**, **SQL_in**), должны соответствовать именам, определенным в `@input_data_1_name` и `@output_data_1_name`, включая регистр.

   > [!TIP]
   > В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако можно вызвать другие наборы данных из кода Python, а также можно вернуть выходные данные других типов в дополнение к набору данных. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами.

1. Можно также формировать значения только с помощью скрипта Python без входных данных (`@input_data_1` установлен в пустое значение).

   Следующий скрипт выводит текст "Hello" и "World".

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
> Python использует начальные пробелы для группирования операторов. Таким образом, когда сценарий Python с невнедренным фрагментом охватывает несколько строк, как в предыдущем сценарии, не пытайтесь понизить уровень команд Python, чтобы они были в строке с командами SQL. Например, этот скрипт выдаст ошибку:

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

Если вы хотите узнать, какая версия Python установлена в экземпляре SQL Server, выполните следующий скрипт.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Функция Python `print` возвращает версию в окно **сообщений** . В приведенном ниже примере выходных данных видно, что в этом случае устанавливается Python версии 3.5.2.

**Результаты**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>Вывод списка пакетов Python

Корпорация Майкрософт предоставляет ряд пакетов Python, предварительно устанавливаемых с SQL Server Службы машинного обучения в экземпляре SQL Server.

Чтобы просмотреть список установленных пакетов Python, включая версию, выполните следующий скрипт.

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pip
for i in pip.get_installed_distributions():
    print(i)
'
GO
```

Выходные данные изменяются `pip.get_installed_distributions()` в Python и возвращаются как сообщения `STDOUT`.

**Результаты**

```text
STDOUT message(s) from external script:
xlwt 1.2.0
XlsxWriter 0.9.6
xlrd 1.0.0
win-unicode-console 0.5
widgetsnbextension 2.0.0
wheel 0.29.0
Werkzeug 0.12.1
wcwidth 0.1.7
unicodecsv 0.14.1
traitlets 4.3.2
tornado 4.4.2
toolz 0.8.2
. . .
```

## <a name="next-steps"></a>Следующие шаги

Чтобы узнать, как использовать структуры данных при использовании Python в SQL Server Службы машинного обучения, следуйте указаниям в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Работа с типами данных и объектами с помощью Python в SQL Server Службы машинного обучения](quickstart-python-data-structures.md)

Дополнительные сведения об использовании Python в SQL Server Службы машинного обучения см. в следующих статьях:

- [Создавайте дополнительные функции Python с помощью SQL Server Службы машинного обучения](quickstart-python-functions.md)
- [Создание и оценка прогнозной модели в Python с помощью SQL Server Службы машинного обучения](quickstart-python-train-score-model.md)
- [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
