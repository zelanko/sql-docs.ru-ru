---
title: Краткое руководство. Python "Hello World"
description: В этом кратком руководстве вы узнаете основные понятия, выполняя сценарий Python "Hello World" в SQL Server Службы машинного обучения. Будет использоваться системная хранимая процедура T-SQL sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1149c7888bc783c9d4f658eed5e8405214d6ffc4
ms.sourcegitcommit: 187f6d327421e64f1802a3085f88bbdb0c79b707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530967"
---
# <a name="quickstart-run-a-hello-world-python-script-on-sql-server-machine-learning-services"></a>Краткое руководство. Запуск скрипта Python "Hello World" на SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы узнаете основные понятия, выполняя сценарий Python "Hello World" в SQL Server Службы машинного обучения. Вы будете использовать системную хранимую процедуру T-SQL **sp_execute_external_script** .

## <a name="prerequisites"></a>Предварительные требования

Предыдущее краткое руководство. [Проверка наличия Python в SQL Server](quickstart-python-verify.md)содержит сведения и ссылки для настройки среды Python, необходимой для этого краткого руководства.

## <a name="basic-python-interaction"></a>Простое взаимодействие Python

Существует два способа выполнения кода Python в SQL Server:

+ Добавьте скрипт Python в качестве аргумента системной хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ На [удаленном клиенте Python](../python/setup-python-client-tools-sql.md)подключитесь к SQL Server и выполните код, используя SQL Server в качестве контекста вычислений. Для этого требуется [revoscalepy](../python/ref-py-revoscalepy.md).

Следующее упражнение сосредоточено на первой модели взаимодействия: как передать код Python в хранимую процедуру.

1. Запустите некоторый простой код, чтобы увидеть передачу данных между SQL Server и Python.

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

2. Предполагая, что все настроено правильно, и Python и SQL Server взаимодействуют друг с другом, правильный результат вычисляется, а функция Python `print` возвращает результат в окнах **сообщений** .

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Хотя получение сообщений **stdout** удобно при тестировании кода, чаще приходится возвращать результаты в табличном формате, чтобы его можно было использовать в приложении или записать в таблицу.

Сейчас помните следующие правила:

+ Все, что `@script` находится внутри аргумента, должно быть допустимым кодом Python. 
+ Код должен соответствовать всем правилам Python в отношении отступов, имен переменных и т. д. При возникновении ошибки проверьте пробелы и регистр.
+ В разных языках программирования Python является одним из наиболее гибких в сравнении с одинарными и двойными кавычками. они значительно взаимозаменяемы. Однако T-SQL использует одинарные кавычки только для определенных моментов, а `@script` аргумент использует одинарные кавычки, чтобы заключить код Python в строку в Юникоде. Поэтому может потребоваться проверить код Python и заменить некоторые одинарные кавычки на двойные кавычки.
+ Если вы используете библиотеки, которые не загружены по умолчанию, необходимо использовать инструкцию import в начале скрипта, чтобы загрузить их. SQL Server добавляет несколько библиотек для конкретных продуктов. Дополнительные сведения см. в разделе [библиотеки Python](../python/python-libraries-and-data-types.md).
+ Если библиотека еще не установлена, закройте и установите пакет Python за пределами SQL Server, как описано здесь: [Установка новых пакетов Python в SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Выполнение скрипта Hello World

В следующем упражнении выполняются другие простые скрипты Python.

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

К этим хранимым процедурам относятся следующие входные данные:

+ *@language* параметр определяет расширение языка для вызова, в данном случае Python.
+ *@script* параметр определяет команды, передаваемые в среду выполнения Python. Весь сценарий Python должен быть заключен в этот аргумент как текст в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее.
+ *@input_data_1* данные, возвращаемые запросом, передаются в среду выполнения Python, которая возвращает данные для SQL Server в виде кадра данных.
+ Предложение WITH RESULTSET SETS определяет схему возвращаемой таблицы данных для SQL Server, добавляя "Hello World" в качестве имени столбца, **int** для типа данных.

**Результаты**

| Hello World |
|-------------|
| 1 |

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы выполнили пару простых скриптов Python, внимательно рассмотрим структурирование входов и выходов.

> [!div class="nextstepaction"]
> [Краткое руководство Обработку входных и выходных данных](quickstart-python-inputs-and-outputs.md)
