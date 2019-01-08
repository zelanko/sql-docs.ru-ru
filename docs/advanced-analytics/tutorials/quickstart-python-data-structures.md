---
title: Краткое руководство по работе со структурами данных в Python - машинного обучения SQL Server
description: В этом кратком руководстве для сценариев Python в SQL Server, узнайте, как использовать структуры данных с помощью системной хранимой процедуры sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0105cf099bbee30d167c498646778520fcdbd805
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046877"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>Краткое руководство. Структуры данных Python в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве показано, как использовать структуры данных, при использовании Python в службах машинного обучения SQL Server.

SQL Server основан на Python **pandas** пакет, который отлично подходит для работы с табличными данными. Тем не менее нельзя передавать скалярного из Python в SQL Server и ожидается «просто работают». В этом кратком руководстве мы рассмотрим некоторые определения типов данных, чтобы подготовиться к дополнительные проблемы, которые могут возникнуть в при передаче табличных данных между Python и SQL Server.

+ Кадр данных — это таблица с _нескольких_ столбцов.
+ Один столбец таблицы данных, — это объект списка по принципу, назовем Series.
+ Одно значение представляет собой ячейку кадр данных, а также должна быть вызвана по индексу.

Как бы вы опубликовать один результат вычисления, в качестве кадра данных, если data.frame требует табличной структуры? Одним из решений является представление одно скалярное значение как ряд, то легко преобразовать в кадр данных. 

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте Python в SQL Server существует](quickstart-python-verify.md), сведения и ссылки по настройке среды Python, необходимые для этого краткого руководства.

## <a name="scalar-value-as-a-series"></a>Скалярное значение как ряд

В этом примере выполняет некоторые простые математические и преобразует скалярного выражения объединяются в ряд.

1. Ряд требует индекса, которое можно назначить вручную, как показано ниже, или программным способом.

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

## <a name="convert-series-to-data-frame"></a>Преобразовать в кадр данных ряда

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

2. Ниже приведен результат. Даже если индекс используется для получения конкретных значений из кадра данных, значения индекса не являются частью выходных данных.

    **Результаты**

    |ResultValue|
    |------|
    |0,5|
    |2|

## <a name="output-values-into-dataframe"></a>Выходные значения в кадр данных

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

## <a name="next-steps"></a>Следующие шаги

Далее предстоит создать прогнозную модель с помощью Python в SQL Server.

> [!div class="nextstepaction"]
> [Создавать, обучать и использовать модели Python с хранимыми процедурами в SQL Server](quickstart-python-train-score-in-tsql.md)