---
title: Создание и выполнение простых сценариев R
titleSuffix: SQL Server Machine Learning Services
description: Создавайте и запускайте простые скрипты R в экземпляре SQL Server с SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d723fa9b90659eb31e96626a3a85c1299c17fa2f
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150317"
---
# <a name="quickstart-create-and-run-simple-r-scripts-with-sql-server-machine-learning-services"></a>Краткое руководство. Создание и выполнение простых скриптов R с помощью SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы создадите и запустите набор простых скриптов R с помощью [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md). Вы узнаете, как заключить правильно сформированный скрипт R в хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) и выполнить скрипт в SQL Serverном экземпляре.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server с [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) с установленным языком R.

  Ваш экземпляр SQL Server может находиться на виртуальной машине Azure или в локальной среде. Просто имейте в виду, что функция внешних скриптов по умолчанию отключена, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **Служба панель запуска SQL Server** запущена перед началом работы.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих скрипты R. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, если они могут подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Выполнение простого скрипта

Чтобы запустить скрипт R, вы передадите его в качестве аргумента системной хранимой процедуре [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Эта системная хранимая процедура запускает среду выполнения R в контексте SQL Server, передает данные в R, безопасно управляет сеансами пользователей R и возвращает результаты клиенту.

В следующих шагах вы выполните этот пример скрипта R в своем экземпляре SQL Server:

```r
a <- 1
b <- 2
c <- a/b
d <- a*b
print(c(c, d))
```

1. Откройте **SQL Server Management Studio** и подключитесь к экземпляру SQL Server.

1. Передайте полный скрипт `sp_execute_external_script` R в хранимую процедуру.

   Скрипт передается через `@script` аргумент. Все, что `@script` находится внутри аргумента, должно быть допустимым кодом R.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

1. Вычисляется правильный результат, и функция R `print` возвращает результат в окно **сообщения** .

   Он должен выглядеть примерно так.

    **Результаты**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Выполнение скрипта Hello World

Типичный пример сценария — это тот, который просто выводит строку "Hello World". Выполните следующую команду.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'OutputDataSet<-InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Входные данные `sp_execute_external_script` для хранимой процедуры включают:

| | |
|-|-|
| @language | Определяет расширение языка для вызова, в данном случае R |
| @script | Определяет команды, передаваемые в среду выполнения R. Весь скрипт R должен быть заключен в этом аргументе в виде текста в Юникоде. Можно также добавить текст в переменную типа **nvarchar** , а затем вызвать переменную |
| @input_data_1 | данные, возвращаемые запросом, переданные в среду выполнения R, которая возвращает данные для SQL Server в виде кадра данных |
|С РЕЗУЛЬТИРУЮЩИМИ НАБОРАМИ | Определяет схему возвращаемой таблицы данных для SQL Server, добавляя "Hello World" в качестве имени столбца, **int** для типа данных. |

Команда выводит следующий текст:

| Всем привет |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Использование входных и выходных данных

По умолчанию `sp_execute_external_script` принимает один набор данных в качестве входных, который обычно предоставляется в виде допустимого SQL-запроса. Затем он возвращает один кадр данных R в качестве выходных данных.

Сейчас давайте будем использовать входные и выходные переменные `sp_execute_external_script`по умолчанию: **InputDataSet** и **OutputDataSet**.

1. Создайте небольшую таблицу тестовых данных.

    ```sql
    CREATE TABLE RTestData (col1 INT NOT NULL)
    
    INSERT INTO RTestData
    VALUES (1);
    
    INSERT INTO RTestData
    VALUES (10);
    
    INSERT INTO RTestData
    VALUES (100);
    GO
    ```

1. `SELECT` Используйте инструкцию для запроса таблицы.
  
    ```sql
    SELECT *
    FROM RTestData
    ```

    **Результаты**

    ![Содержимое таблицы RTestData](./media/select-rtestdata.png)

1. Выполните следующий скрипт R. Он получает данные из таблицы с помощью `SELECT` инструкции, передает их через среду выполнения R и возвращает данные в виде кадра данных. Предложение определяет схему возвращаемой таблицы данных для SQL, добавляя имя столбца *невколнаме.* `WITH RESULT SETS`

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные скрипта R, возвращающие данные из таблицы](./media/r-output-rtestdata.png)

1. Теперь давайте изменим имена входных и выходных переменных. Имена входных и выходных переменных по умолчанию — **InputDataSet** и **OutputDataSet**. Этот сценарий изменяет имена на **SQL_in** и **SQL_out**:

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N' SQL_out <- SQL_in;'
        , @input_data_1 = N' SELECT 12 as Col;'
        , @input_data_1_name = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Обратите внимание, что в R учитывается регистр. Входные и выходные переменные, используемые в скрипте R (**SQL_out**, **SQL_in**), должны соответствовать `@input_data_1_name` именам, определенным в и `@output_data_1_name`, включая регистр.

   > [!TIP]
   > В качестве параметра можно передать только один входной набор данных. Возвращаться может также только один набор данных. Однако вы можете вызывать другие наборы данных из кода R, а в дополнение к набору данных могут возвращаться выходные данные других типов. Кроме того, вы можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами.

1. Можно также создавать значения только с помощью скрипта R без входных данных (`@input_data_1` пустое).

   Следующий скрипт выводит текст "Hello" и "World".

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    mytextvariable <- c("hello", " ", "world");
    OutputDataSet <- as.data.frame(mytextvariable);
    '
        , @input_data_1 = N''
    WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
    ```

    **Результаты**

    ![Результаты запроса, @script использующие в качестве входных данных](./media/r-data-generated-output.png)

## <a name="check-r-version"></a>Проверить версию R

Если вы хотите узнать, какая версия R установлена в экземпляре SQL Server, выполните следующий скрипт.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(version)';
GO
```

Функция R `print` Возвращает версию в окно **сообщений** . В приведенном ниже примере выходных данных видно, что в этом случае установлена версия R 3.4.4.

**Результаты**

```text
STDOUT message(s) from external script:
                   _
platform       x86_64-w64-mingw32
arch           x86_64
os             mingw32
system         x86_64, mingw32
status
major          3
minor          4.4
year           2018
month          03
day            15
svn rev        74408
language       R
version.string R version 3.4.4 (2018-03-15)
nickname       Someone to Lean On
```

## <a name="list-r-packages"></a>Список пакетов R

Корпорация Майкрософт предоставляет ряд пакетов R, предварительно устанавливаемых с SQL Server Службы машинного обучения.

Чтобы просмотреть список установленных пакетов R, включая сведения о версии, зависимостях, лицензии и пути к библиотеке, выполните следующий скрипт.

```SQL
EXEC sp_execute_external_script @language = N'R'
    , @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((
            Package NVARCHAR(255)
            , Version NVARCHAR(100)
            , Depends NVARCHAR(4000)
            , License NVARCHAR(1000)
            , LibPath NVARCHAR(2000)
            ));
```

Выходные данные изменяются `installed.packages()` в R и возвращаются в виде результирующего набора.

**Результаты**

![Установленные пакеты в R](./media/rsql-installed-packages.png) 

## <a name="next-steps"></a>Следующие шаги

Чтобы создать модель машинного обучения с помощью R в SQL Server, следуйте указаниям в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Создание и оценка прогнозной модели в R с помощью SQL Server Службы машинного обучения](quickstart-r-train-score-model.md)

Дополнительные сведения о SQL Server Службы машинного обучения см. в следующих статьях.

- [Работа с типами данных и объектами с помощью R в SQL Server Службы машинного обучения](quickstart-r-data-types-and-objects.md)
- [Написание расширенных функций R с помощью SQL Server Службы машинного обучения](quickstart-r-functions.md)
- [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
