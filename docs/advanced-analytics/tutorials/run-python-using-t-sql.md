---
title: Запустите Python, с помощью T-SQL на сервере SQL Server | Документация Майкрософт
description: Основы для выполнения кода Python с использованием T-SQL и хранимых процедур в экземпляр ядра СУБД SQL Server, для которых включена интеграция Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 59897cbe6abc13b9842dc148ef8c2de4413926d0
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702962"
---
# <a name="run-python-using-t-sql"></a>Запуск Python с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как выполнять код Python в SQL Server 2017. Здесь подробно описаны основы перемещения данных между SQL Server и Python: требований, структуры данных, входных и выходных данных. Здесь также объясняется, как программы-оболочки для правильного кода Python в хранимой процедуре [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для создания, обучения и использования моделей машинного обучения в SQL Server.

## <a name="prerequisites"></a>предварительные требования

Чтобы запустить пример кода в этих упражнениях, сначала необходимо установить SQL Server 2017 и включение служб машинного обучения на экземпляре, как описано в разделе [установить SQL Server 2017 служб машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md). 

Также следует установить [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). Кроме того можно использовать другое средство базами данных управления или запрос, пока он может подключиться к серверу и базе данных и выполняется запрос T-SQL или хранимой процедуры.

При готовности среды, вернитесь на эту страницу, чтобы узнать, как выполнять код Python в контексте хранимой процедуры. 

## <a name="verify-python-exists"></a>Убедитесь, что существует Python

Следующие действия убедитесь, что Python включена и запущена служба панели запуска SQL Server.

1. Проверьте, установлена ли интеграция Python на экземпляре компонента database engine. Вы должны найти **python.exe** в папку с именем **PYTHON_SERVICES** в C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\. Это исполняемый файл Python, который использует SQL Server для выполнения кода Python.

2. Проверьте, включен ли внешних скриптов. В среде Management Studio выполните следующую инструкцию:

    ```sql
    sp_configure 'external scripts enabled'
    ```

    Если **run_value** -1, средство обучения машины, установленных и готова к использованию.

    Распространенной причиной ошибок в том, что [службы панели запуска SQL Server](../concepts/extensibility-framework.md#launchpad), который управляет связью между SQL Server и Python, была остановлена. Состояние запуска можно просмотреть с помощью Windows **служб** панели либо открыв диспетчер конфигурации SQL Server. Если данная служба остановлена, перезапустите его.

3. Убедитесь, что среда выполнения Python работает и взаимодействие с SQL Server. Чтобы сделать это, откройте новую **запроса** окно в SQL Server Management Studio и подключитесь к экземпляру, где был установлен Python.

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    Если все хорошо, вы увидите сообщение с результатом следующего вида

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. Если возникают ошибки, существует ряд вещей, которые можно сделать, чтобы убедиться, что сервер и Python может взаимодействовать. 

    Необходимо добавить группу пользователей Windows `SQLRUserGroup` как имя для входа на экземпляре, чтобы убедиться, что панель запуска могут обеспечивать взаимодействие между кодом Python и SQL Server. (Той же группе используется для обоих R и выполнение кода Python). Дополнительные сведения см. в разделе [неявная проверка подлинности включена](../security/add-sqlrusergroup-to-database.md).
    
    Кроме того может потребоваться включить сетевые протоколы, которые были отключены, или открыть брандмауэр SQL Server мог обмениваться данными с внешними клиентами. Дополнительные сведения см. в разделе [Устранение неполадок при установке](../common-issues-external-script-execution.md).

### <a name="call-revoscalepy-functions"></a>Вызов функций revoscalepy

Чтобы убедиться, что **revoscalepy** нет, выполните скрипт, который содержит [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) , формирующий статистические сводных данных. Этот сценарий демонстрируется извлечение данных xdf-пример в файл из встроенных примеры, включенные в revoscalepy. Предоставляет функцию RxOptions **sampleDataDir** параметр, который возвращает расположение файлов образца.

Поскольку rx_summary возвращает объект типа `class revoscalepy.functions.RxSummary.RxSummaryResults`, который содержит несколько элементов, можно использовать для извлечения только кадр данных в табличном формате pandas.

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

## <a name="basic-python-interaction"></a>Основные взаимодействия Python

Существует два способа для выполнения кода Python в SQL Server:

+ Добавить скрипт Python в качестве аргумента системные хранимые процедуры, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Из [удаленного клиента Python](../python/setup-python-client-tools-sql.md), подключение к SQL Server и выполнить код, используя SQL Server в качестве контекста вычисления. Для этого требуется [revoscalepy](../python/what-is-revoscalepy.md).

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
+ Если вы используете все библиотеки, которые не загружаются по умолчанию, необходимо использовать инструкцию импорта в начале сценария для их загрузки. SQL Server добавляет несколько библиотек конкретного продукта. Дополнительные сведения см. в разделе [библиотек Python](../python/python-libraries-and-data-types.md).
+ Если библиотека еще не установлен, остановите и установить пакет Python за пределами SQL Server, как описано здесь: [Установка новых пакетов Python в SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>Входы и выходы

По умолчанию [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) принимает один входной набор данных, которая обычно предоставляется в виде допустимый SQL-запрос. 

Другие виды входные данные могут передаваться как переменные SQL: например, можно передать обученной модели как переменную, например с помощью функции сериализации [pickle](https://docs.python.org/3.0/library/pickle.html) или [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) для записи модели двоичный формат.

Хранимая процедура возвращает один Python [pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) кадр данных в качестве выходных данных, но можно также выводить скалярных величин и модели как переменные. Например можно выходные данные обученной модели в качестве двоичной переменной и передать его в инструкцию T-SQL INSERT для записи в таблицу модели. Можно также создавать графики (в двоичном формате) или скаляры (отдельных значений, таких как дата и время, затраченное время для обучения модели и так далее).

Теперь давайте взглянем на просто значение по умолчанию входных и выходных переменных sp_execute_external_script: `InputDataSet` и `OutputDataSet`. 

1. Запустите следующий код, чтобы произвести некоторые расчеты и выведет результаты.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    OutputDataSet = c
    '
    WITH RESULT SETS ((ResultValue float))
    ```

2. Должно появиться сообщение об ошибке, так как в коде Python создается скаляр, не является кадром данных.

    **Результаты**

    ```text
    line 43, in transform
        raise TypeError('OutputDataSet should be of type pandas.DataFrame')
    ```

3. Теперь посмотрим, что произойдет при передаче набор табличных данных в Python, с помощью входной переменной по умолчанию `InputDataSet`. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    Хранимая процедура возвращает data.frame автоматически, вам не нужно предпринимать дополнительных в коде Python.

    **Результаты**

    | Нет columnname|
    |------|
    | 1|

    По умолчанию одной табличной входной набор данных содержит имя, `InputDataSet`. Тем не менее, это имя можно изменить, добавив строку, аналогичную следующей: `@input_data_1_name = N'myResultName'`.

    Имена столбцов, используемых Python никогда не сохраняются в выходных данных. Несмотря на то, что входной запрос заданное имя столбца `Col1`, это имя не возвращается, а также все заголовки столбцов, используемые с помощью скрипта Python. Для указания столбца имя и тип данных, при возврате данных в SQL Server, используйте T-SQL `WITH RESULT SETS` предложение.

4. В этом примере представлен новые имена для входных и выходных переменных.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    MyOutput = MyInput
    ',
    @input_data_1_name = N'MyInput',
    @input_data_1 = N'SELECT 1 as Col1',
    @output_data_1_name = N'MyOutput'
    WITH RESULT SETS ((ResultValue int))
    ```

    Предложение с РЕЗУЛЬТИРУЮЩИЙ НАБОР определяет схему для выходных данных, так как имена столбцов в Python с data.frame никогда не возвращаются.

    **Результаты**

    | ResultValue|
    |------|
    | 1|

5. Теперь давайте рассмотрим типичную ошибку Python. Измените строку в предыдущем примере из `@input_data_1_name = N'MyInput'` для `@input_data_1_name = N'myinput'`.

    Ошибки Python передаются вам как сообщения, по вспомогательной службы, используемый сервером SQL Server. Сообщения могут быть длинными и содержать ошибок SQL Server или ошибки запуска вместе с ошибками Python, поэтому будьте пациента в углубиться по тексту. Ключевое послание звучит в этой строке:

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    Помните, что Python, например R, с учетом регистра. Таким образом при получении любого типа ошибки, не забудьте проверить ваши имена переменных и поиск проблем с типами данных, интервалов и отступов.

## <a name="python-data-structures"></a>Структуры данных Python

SQL Server основан на Python **pandas** пакет, который отлично подходит для работы с табличными данными. Тем не менее вы уже видели, что нельзя передавать скалярного из Python в SQL Server и ожидается «просто работают». В этом разделе мы рассмотрим некоторые определения типов данных, чтобы подготовиться к дополнительные проблемы, которые могут возникнуть в при передаче табличных данных между Python и SQL Server.

+ Кадр данных — это таблица с _нескольких_ столбцов.
+ Один столбец таблицы данных, — это объект списка по принципу, назовем Series.
+ Одно значение представляет собой ячейку кадр данных, а также должна быть вызвана по индексу.

Так как вы предоставит единый результат вычисления, в качестве кадра данных, если data.frame требует табличной структуры? Одним из решений является представление одно скалярное значение как ряд, то легко преобразовать в кадр данных. 

1. В этом примере выполняет некоторые простые математические и преобразует скалярного выражения объединяются в ряд. Ряд требует индекса, которое можно назначить вручную, как показано ниже, или программным способом.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    s = pandas.Series(c, index =["simple math example 1"])
    print(s)
    '
    ```

2. Поскольку ряды еще не преобразован в формат Data.Frame, значения возвращаются в окне сообщения, но вы увидите, что результаты, в более табличном формате.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. К длине ряда, можно добавить новые значения с помощью массива. 

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    '
    ```

    Если вы не укажете индекса, индекс создается со значениями, начиная с 0 и длину массива.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Если увеличить число **индекс** значения, но не добавляйте новые **данных** значения, повторяющиеся значения данных для заполнения ряда.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    '
    ```

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    simple math example 2    0.5
    dtype: float64
    ```

### <a name="convert-series-to-data-frame"></a>Преобразовать в кадр данных ряда

Скалярные математические результаты преобразуется в табличную структуру, по-прежнему необходимо преобразовывать их в формат, поддерживающий работу SQL Server. 

1. Чтобы преобразовать последовательность в формат Data.Frame, вызовите pandas [кадр данных](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) метод.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s)
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

2. Обратите внимание на то, что значения индекса не выводятся, даже если вы используете индекс для получения конкретных значений из кадра данных.

    **Результаты**

    |ResultValue|
    |------|
    |0,5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>Выходные значения в кадр данных с помощью индекса

Давайте посмотрим, как работает преобразование в формат Data.Frame с наших двух рядов, содержащий результаты простых математических операций. Первый содержит индекс последовательных значений, созданных Python. Второй использует произвольные индекса из строковых значений.

1. В этом примере возвращает значение из серии, в котором используется индекс целого числа.

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    Помните, что автоматически созданный индекс начинается с 0. Попробуйте использовать готовую значение индекса диапазона и посмотрите, что получится.

2. Теперь давайте получение одного значения из других кадров данных с индексом строки. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    **Результаты**

    |ResultValue|
    |------|
    |0,5|

    Если вы попытаетесь использовать числовой индекс для получения значения из этой серии, вы получите ошибку.

В этом упражнении предназначался дать вам представление о том, как работать с разной структурой данных Python и убедитесь, что получение правильного результата в формате кадра данных. Может завершения, выводя одно значение как кадр данных есть дороже ее стоимость! К счастью можно легко передать все виды значений и из него хранимой процедуры как переменные. Это описано в следующем разделе.

## <a name="tips"></a>Советы

+ Среди языков программирования Python является одним из наиболее гибкий по отношению к одинарные и двойные кавычки; они практически взаимозаменяемыми. 

    Тем не менее, T-SQL используются одинарные кавычки для только определенных операций и `@script` аргумент используются одинарные кавычки для заключения в них код Python как строка Юникода. Таким образом может потребоваться кода Python и изменить некоторые одинарные кавычки, двойные кавычки.

+ Не удалось найти хранимую процедуру, `sp_execute_external_script`? Это означает, что, возможно, еще не закончена настройка экземпляра для поддержки выполнения внешних скриптов. После запуска программы установки SQL Server 2017 и выбор Python в качестве язык машинного обучения, необходимо явным образом включить функции с помощью `sp_configure`, а затем перезапустите экземпляр. 

    Дополнительные сведения см. в разделе [установить SQL Server 2017 служб машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md).

## <a name="next-steps"></a>Следующие шаги

[Настройка демонстрационный набор данных Iris](demo-data-iris-in-sql.md)