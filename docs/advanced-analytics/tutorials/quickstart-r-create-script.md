---
title: Краткое руководство. Запуск сценариев R
description: Сведения о выполнении простых скриптов R с помощью Служб машинного обучения SQL Server. Вы узнаете, как применить хранимую процедуру sp_execute_external_script для выполнения скрипта в экземпляре SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 495bb56cf76391c8baa1734665d5064b586d4be8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831782"
---
# <a name="quickstart-run-simple-r-scripts-with-sql-server-machine-learning-services"></a>Краткое руководство. Выполнение простых сценариев R с помощью служб машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы запустите несколько простых скриптов R, используя [Службы машинного обучения SQL Server](../what-is-sql-server-machine-learning.md). Также вы узнаете, как применить хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для выполнения скрипта в экземпляре SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server со [службами машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) и с установленным языком R.

  Экземпляр SQL Server может находиться в виртуальной машине Azure или на локальном компьютере. Обратите внимание, что функция внешних сценариев по умолчанию отключена, поэтому перед началом работы вам может потребоваться [включить ее](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **служба панели запуска SQL Server** выполняется.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих сценарии R. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, которые могут подключаться к экземпляру SQL Server и выполнять запросы T-SQL или хранимые процедуры. В этом кратком руководстве используется среда [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Выполнение простого сценария

Чтобы выполнить сценарий R, необходимо передать его в качестве аргумента в системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Эта хранимая процедура запускает среду выполнения R в контексте SQL Server, передает данные в R, безопасно управляет пользовательскими сеансами R и возвращает результаты клиенту.

В следующих шагах вы выполните этот пример сценария R в своем экземпляре SQL Server:

```r
a <- 1
b <- 2
c <- a/b
d <- a*b
print(c(c, d))
```

1. Откройте среду **SQL Server Management Studio** и подключитесь к экземпляру SQL Server.

1. Передайте весь сценарий R в хранимую процедуру `sp_execute_external_script`.

   Сценарий передается с помощью аргумента `@script`. Все, что находится внутри аргумента `@script`, должно быть допустимым кодом R.

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

1. Далее вычисляется правильный результат, и функция R `print` возвращает результат в окне **Сообщения**.

   Он должен выглядеть примерно так.

    **Результаты**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Выполнение сценария Hello World

Типичный пример — сценарий, который просто выводит строку "Hello World". Выполните следующую команду.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'OutputDataSet<-InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

В хранимую процедуру `sp_execute_external_script` передаются следующие входные данные.

| | |
|-|-|
| @language | Определяет вызываемое расширение языка (в данном случае R). |
| @script | Определяет команды, которые передаются в среду выполнения R. Весь сценарий R должен содержаться в этом аргументе в виде текста в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее. |
| @input_data_1 | Данные, возвращаемые запросом, передаются в среду выполнения R, которая возвращает данные в SQL Server в виде кадра данных. |
|WITH RESULT SETS | Это предложение определяет схему возвращаемой таблицы данных для SQL Server. В данном случае добавляется "Hello World" в качестве имени столбца и **int** в качестве типа данных. |

Эта команда выводит следующий текст:

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Использование входных и выходных данных

По умолчанию процедура `sp_execute_external_script` принимает в качестве входных данных один набор данных, обычно предоставляемый в виде допустимого SQL-запроса. Затем она возвращает один кадр данных R в качестве выходных данных.

Сейчас мы будем использовать заданные по умолчанию входные и выходные переменные процедуры `sp_execute_external_script`: **InputDataSet** и **OutputDataSet**.

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

1. Используйте инструкцию `SELECT` для запроса в эту таблицу.
  
    ```sql
    SELECT *
    FROM RTestData
    ```

    **Результаты**

    ![Содержимое таблицы RTestData](./media/select-rtestdata.png)

1. Выполните следующий сценарий R. Он получает данные из таблицы с помощью инструкции `SELECT`, передает их через среду выполнения R и возвращает результаты в виде кадра данных. Предложение `WITH RESULT SETS` определяет схему таблицы возвращаемых данных для SQL Server, добавляя имя столбца *NewColName*.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Результаты**

    ![Выходные данные сценария R, возвращающего данные из таблицы](./media/r-output-rtestdata.png)

1. Теперь изменим имена входных и выходных переменных. Имена входных и выходных переменных по умолчанию°— **InputDataSet** и **OutputDataSet**. Сценарий изменяет их на **SQL_in** и **SQL_out**:

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N' SQL_out <- SQL_in;'
        , @input_data_1 = N' SELECT 12 as Col;'
        , @input_data_1_name = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Обратите внимание, что в R учитывается регистр. Входные и выходные переменные, используемые в сценарии R (**SQL_out**, **SQL_in**), должны соответствовать именам, определенным в аргументах `@input_data_1_name` и `@output_data_1_name`, включая регистр.

   > [!TIP]
   > В качестве параметра может быть передан только один входной набор данных, и можно возвращать только один набор данных. Однако вы можете вызывать другие наборы данных из кода R, а также возвращать выходные данные других типов в дополнение к набору данных. Вы также можете добавить ключевое слово OUTPUT к любому параметру, чтобы он возвращался с результатами.

1. Также можно формировать значения только с помощью сценария R, без каких-либо входных данных (в аргументе `@input_data_1` задано пустое значение).

   Следующий сценарий выводит текст "hello" и "world".

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

    ![Результаты запроса с использованием @script в качестве входных данных](./media/r-data-generated-output.png)

## <a name="check-r-version"></a>Проверка версии R

Если вы хотите узнать, какая версия R установлена в вашем экземпляре SQL Server, выполните следующий сценарий.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(version)';
GO
```

Функция R `print` возвращает версию в окне **Сообщения**. В приведенном ниже примере можно видеть, что в данном случае установлен R версии 3.4.4.

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

## <a name="list-r-packages"></a>Получение списка пакетов R

Майкрософт предоставляет ряд пакетов R, которые устанавливаются вместе со службами машинного обучения SQL Server.

Чтобы просмотреть список установленных пакетов R, включая сведения о версии, зависимостях, лицензии и пути к библиотеке, выполните следующий сценарий.

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

Выходные данные `installed.packages()` в R и возвращаются в виде результирующего набора.

**Результаты**

![Установленные пакеты в R](./media/rsql-installed-packages.png) 

## <a name="next-steps"></a>Дальнейшие действия

Сведения о том, как работать со структурами данных при использовании языка R в службах машинного обучения SQL Server, см. в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Работа с типами данных и объектами с помощью R в службах машинного обучения SQL Server](quickstart-r-data-types-and-objects.md)

Дополнительные сведения об использовании R в службах машинного обучения SQL Server см. в следующих статьях:

- [Написание расширенных функций R с использованием служб машинного обучения SQL Server](quickstart-r-functions.md)
- [Создание и оценка модели прогнозов в R с помощью служб машинного обучения SQL Server](quickstart-r-train-score-model.md)
- [Что такое службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
