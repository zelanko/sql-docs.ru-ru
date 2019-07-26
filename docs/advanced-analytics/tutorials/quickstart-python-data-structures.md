---
title: Краткое руководство по работе с структурами данных в Python
description: В этом кратком руководстве по скрипту Python в SQL Server Узнайте, как использовать структуры данных с системной хранимой процедурой sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 17b2c150368b32960907d6fdd2e31b109f51d771
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469639"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>Краткое руководство. Структуры данных Python в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве показано, как использовать структуры данных при использовании Python в SQL Server Службы машинного обучения.

SQL Server полагается на пакет Python **Pandas** , который отлично подходит для работы с табличными данными. Однако нельзя передать скалярное значение из Python в SQL Server и предполагается, что это просто работа. В этом кратком руководстве мы рассмотрим некоторые базовые определения типов данных, чтобы подготовиться к дополнительным проблемам, которые могут быть выполнены во время передачи табличных данных между Python и SQL Server.

+ Кадр данных — это таблица с _несколькими_ столбцами.
+ Единственным столбцом таблицы данных является объект, подобный списку, называемый серией.
+ Одно значение является ячейкой кадра данных и должно вызываться по индексу.

Как можно предоставить один результат вычисления как кадр данных, если для данных. Frame требуется табличная структура? Одним из ответов является представление одного скалярного значения в виде ряда, которое легко преобразовать в кадр данных. 

## <a name="prerequisites"></a>Предварительные требования

Предыдущее краткое руководство. [Проверка наличия Python в SQL Server](quickstart-python-verify.md)содержит сведения и ссылки для настройки среды Python, необходимой для этого краткого руководства.

## <a name="scalar-value-as-a-series"></a>Скалярное значение в виде ряда

Этот пример выполняет некоторые простые математические операции и преобразует скаляр в ряд.

1. Для ряда требуется индекс, который можно назначить вручную, как показано здесь, или программным способом.

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

2. Поскольку ряд не был преобразован в Data. Frame, значения возвращаются в окне сообщения, но можно увидеть, что результаты имеют более табличный формат.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Чтобы увеличить длину ряда, можно добавить новые значения с помощью массива. 

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

    Если индекс не указан, создается индекс со значениями, начинающимися с 0 и заканчивая длиной массива.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Если увеличить количество значений **индекса** , но не добавлять новые значения **данных** , значения данных повторяются для заполнения ряда.

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

## <a name="convert-series-to-data-frame"></a>Преобразовать ряд в рамку данных

После преобразования скалярных математических результатов в табличную структуру нам все равно нужно преобразовать их в формат, который SQL Server может быть обработано. 

1. Для преобразования ряда в Data. Frame вызовите [метод Pandas данных](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) .

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

2. Результат показан ниже. Даже если вы используете индекс для получения конкретных значений из Data. Frame, значения индекса не являются частью выходных данных.

    **Результаты**

    |ресултвалуе|
    |------|
    |0,5|
    |2|

## <a name="output-values-into-dataframe"></a>Выходные значения в Data. Frame

Давайте посмотрим, как преобразование в Data. Frame работает с двумя рядами, содержащими результаты простых математических операций. Первый имеет индекс последовательных значений, созданных Python. Во втором используется произвольный индекс строковых значений.

1. Этот пример возвращает значение из ряда, использующего целочисленный индекс.

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

    Помните, что автоматически созданный индекс начинается с 0. Попробуйте использовать значение индекса вне допустимого диапазона и посмотрите, что произойдет.

2. Теперь давайте получаем одно значение из другого фрейма данных, имеющего строковый индекс. 

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

    |ресултвалуе|
    |------|
    |0,5|

    При попытке использовать числовой индекс для получения значения из этой серии появляется сообщение об ошибке.

## <a name="next-steps"></a>Следующие шаги

Далее предстоит создать прогнозную модель с помощью Python в SQL Server.

> [!div class="nextstepaction"]
> [Создание, обучение и использование модели Python с хранимыми процедурами в SQL Server](quickstart-python-train-score-in-tsql.md)