---
title: 'Краткое руководство по Python основные «Hello, World!» код выполнения в T-SQL: машинного обучения SQL Server'
description: Краткое руководство по скрипт Python в SQL Server. Основы вызова скрипта Python, с помощью системной хранимой процедуры sp_execute_external_script в упражнении hello world.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/10/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6d8da3ce90e915344f2380d4cd5cc866db6715ef
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59476639"
---
# <a name="quickstart-hello-world-python-script-in-sql-server"></a>Краткое руководство. Скрипт Python «Hello world» в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве вы узнаете основные понятия, выполнив Python «Hello, World!» скрипт inT-SQL, представив Введение **sp_execute_external_script** системной хранимой процедуры. 

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте Python в SQL Server существует](quickstart-python-verify.md), сведения и ссылки по настройке среды Python, необходимые для этого краткого руководства.

## <a name="basic-python-interaction"></a>Основные взаимодействия Python

Существует два способа для выполнения кода Python в SQL Server:

+ Добавить скрипт Python в качестве аргумента системные хранимые процедуры, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Из [удаленного клиента Python](../python/setup-python-client-tools-sql.md), подключение к SQL Server и выполнить код, используя SQL Server в качестве контекста вычисления. Для этого требуется [revoscalepy](../python/ref-py-revoscalepy.md).

Следующее упражнение сосредоточена на первой модели взаимодействия: как передать код Python в хранимую процедуру.

1. Запустите немного простого кода, чтобы увидеть, как данные передаются назад и вперед между SQL Server и Python.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. При условии, что у вас есть все настроено правильно, что Python и SQL Server при разговоре с друг с другом, правильный результат вычисляется и Python `print` функция возвращает результат **сообщений** windows.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    При получении **stdout** сообщения удобно при тестировании кода, более часто необходимо возвращать результаты в табличном формате, чтобы использовать его в приложении также можно записать их в таблицу.

Сейчас помните, эти правила:

+ Все содержимое `@script` аргумент должен быть указан корректный код Python. 
+ Код должен следовать всем правилам Python относительно отступов, имена переменных и т. д. Когда отобразится сообщение об ошибке, проверьте, пробелы и регистр.
+ Среди языков программирования Python является одним из наиболее гибкий по отношению к одинарные и двойные кавычки; они практически взаимозаменяемыми. Тем не менее, T-SQL используются одинарные кавычки для только определенных операций и `@script` аргумент используются одинарные кавычки для заключения в них код Python как строка Юникода. Таким образом может потребоваться кода Python и изменить некоторые одинарные кавычки, двойные кавычки.
+ Если вы используете все библиотеки, которые не загружаются по умолчанию, необходимо использовать инструкцию импорта в начале сценария для их загрузки. SQL Server добавляет несколько библиотек конкретного продукта. Дополнительные сведения см. в разделе [библиотек Python](../python/python-libraries-and-data-types.md).
+ Если библиотека еще не установлен, остановите и установить пакет Python за пределами SQL Server, как описано здесь: [Установка новых пакетов Python в SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Запуск сценария Hello World

Следующее упражнение выполняет другой простой сценарии Python.

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

Входные данные для этой хранимой процедуры включают:

+ *@language* Определяет расширение языка для вызова, в этом случае Python.
+ *@script* параметр определяет команды, передаваемые в среду выполнения Python. Всего скрипта Python должны заключаться в этот аргумент в виде текста в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее.
+ *@input_data_1* данные, возвращенные запросом, переданный в среду выполнения Python, которая возвращает данные в SQL Server в качестве кадра данных.
+ С РЕЗУЛЬТИРУЮЩИМИ НАБОРАМИ предложение определяет схему таблицы возвращаемых данных для SQL Server, добавив «Hello, World!» в качестве имени столбца, **int** для типа данных.

**Результаты**

| Всем привет |
|-------------|
| 1 |

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы запустили несколько простых скриптов Python, внимательно ознакомьтесь структурирование входные и выходные данные.

> [!div class="nextstepaction"]
> [Краткое руководство. Обрабатывать входные и выходные данные](quickstart-python-inputs-and-outputs.md)
