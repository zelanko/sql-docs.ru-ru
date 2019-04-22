---
title: 'Краткое руководство для выполнения кода «Hello, World!» основные R в T-SQL: машинного обучения SQL Server'
description: Краткое руководство по R-скриптов SQL Server. Ознакомиться с основами вызов сценария R в упражнении Здравствуй, мир при помощи системной хранимой процедуры sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1c3ee703bca46bf46dba8225e1d28da3174dc932
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59240172"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Краткое руководство. R-сценарий «Hello world» в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве вы узнаете основные понятия, выполнив «Hello World» R скрипт inT-SQL, представив Введение **sp_execute_external_script** системной хранимой процедуры. 

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте R в SQL Server существует](quickstart-r-verify.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

## <a name="basic-r-interaction"></a>Основные взаимодействия R

Существует два способа, возможность выполнения кода R в базе данных SQL:

+ Добавьте сценарий R в качестве аргумента системные хранимые процедуры, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).
+ Из [удаленного клиента R](https://docs.microsoft.com/sql/advanced-analytics/r/set-up-a-data-science-client), подключиться к базе данных SQL и выполнить код, с помощью базы данных SQL в качестве контекста вычисления.

Следующее упражнение сосредоточена на первой модели взаимодействия: как передать код R в хранимую процедуру.

1. Выполните простой сценарий, чтобы увидеть, каким образом выполняет сценарий R в базе данных SQL.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'R',
    @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

2. Предположим, что у вас есть все настроено правильно правильный результат вычисляется и R `print` функция возвращает результат **сообщений** окна.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    При получении **stdout** сообщения полезен при тестировании кода, более часто необходимо возвращать результаты в табличном формате, чтобы использовать его в приложении также можно записать их в таблицу. См. в разделе [краткое руководство: Дескриптор входных и выходных данных с помощью языка R в SQL Server](rtsql-working-with-inputs-and-outputs.md) Дополнительные сведения.

Помните, что все содержимое `@script` аргумент должен быть действительный код R.

## <a name="run-a-hello-world-script"></a>Запуск сценария Hello World

Следующее упражнение выполняется другой простые скрипты R.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'OutputDataSet<-InputDataSet',
  @input_data_1 =N'SELECT 1 AS hello'
  WITH RESULT SETS (([Hello World] int));
GO
```

Входные данные для этой хранимой процедуры включают:

+ *@language* Определяет расширение языка для вызова, в этом случае R.
+ *@script* параметр определяет команды, передаваемые в среду выполнения R. Весь скрипт R должен быть заключен в этом аргументе в виде текста в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее.
+ *@input_data_1* данные, возвращенные запросом, переданный в среду выполнения R, которая возвращает данные в SQL Server в качестве кадра данных.
+ С РЕЗУЛЬТИРУЮЩИМИ НАБОРАМИ предложение определяет схему таблицы возвращаемых данных для SQL Server, добавив «Hello, World!» в качестве имени столбца, **int** для типа данных.

**Результаты**

| Всем привет |
|-------------|
| 1 |

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы запустили несколько простые скрипты R, внимательно ознакомьтесь структурирование входные и выходные данные.

> [!div class="nextstepaction"]
> [Краткое руководство. Обрабатывать входные и выходные данные](quickstart-r-inputs-and-outputs.md)
