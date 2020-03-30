---
title: Краткое руководство. Структуры данных Python
description: В этом кратком руководстве вы узнаете, как работать со структурами данных и объектами данных в Python и Службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0f04e021664a92241c8c029d296a298b10c142d2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "76831902"
---
# <a name="quickstart-data-structures-and-objects-using-python-in-sql-server-machine-learning-services"></a>Краткое руководство. Работа с типами данных и объектами при использовании Python в службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы узнаете, как использовать структуры данных при использовании Python в службах машинного обучения SQL Server, см. в этом кратком руководстве.

В SQL Server в качестве основы используется пакет Python **pandas**, который отлично подходит для работы с табличными данными. Однако нельзя просто передать скалярное значение из Python в SQL Server и ждать, что это "просто сработает". В этом кратком руководстве вы вспомните некоторые базовые определения типов данных, чтобы подготовиться к решению дополнительных проблем, с которыми вы можете столкнуться при передаче табличных данных между Python и SQL Server.

Основные понятия, которые необходимо знать:

- Кадр данных — это таблица с _несколькими_ столбцами.
- Кадр данных с одним столбцом — объект в виде списка, называемый рядом.
- Одно значение кадра данных называется ячейкой, доступ к ней осуществляется по индексу.

Как можно предоставить единственный результат вычисления в виде кадра данных, если для объекта data.frame требуется табличная структура? Одним из ответов является представление одного скалярного значения в виде ряда, который легко преобразовать в кадр данных. 

> [!NOTE]
> При возврате дат Python в SQL использует тип DATETIME, который имеет ограниченный диапазон дат от 1753-01-01 (-53690) до 9999-12-31 (2958463). 

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server со [службами машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) и с установленным языком Python.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих сценарии Python. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, которые могут подключаться к экземпляру SQL Server и выполнять запросы T-SQL или хранимые процедуры. В этом кратком руководстве используется среда [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="scalar-value-as-a-series"></a>Скалярное значение в виде ряда

В этом примере выполняется некоторые простые математические операции и преобразуется скаляр в ряд.

1. Для ряда требуется индекс, который можно назначить вручную, как показано здесь, или программным способом.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   print(c)
   s = pandas.Series(c, index =["simple math example 1"])
   print(s)
   '
   ```

   Поскольку ряд не был преобразован в объект data.frame, значения возвращаются в окне сообщения, но можно увидеть, что результаты больше напоминают табличный формат.

   **Результаты**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   dtype: float64
   ```

1. Чтобы увеличить длину ряда, можно добавить новые значения с использованием массива. 

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   '
   ```

   Если индекс не указан, создается индекс со значениями, начиная с 0 и заканчивая длиной массива.

   **Результаты**

   ```text
   STDOUT message(s) from external script: 
   0    0.5
   1    2.0
   dtype: float64
   ```

1. Если увеличить число **индексных значений**, но не добавить новые **данные**, значения данных будут повторяться для заполнения ряда.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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

## <a name="convert-series-to-data-frame"></a>Преобразование рядя в кадр данных

После преобразования скалярных математических результатов в табличную структуру все еще необходимо преобразовать их в формат, который может обрабатывать SQL Server.

1. Чтобы преобразовать ряд в объект data.frame, вызовите метод [DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) библиотеки pandas.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   Результат показан ниже. Даже если вы используете индекс для получения конкретных значений из data.frame, значения индекса не являются частью выходных данных.

   **Результаты**

   |ResultValue|
   |------|
   |0,5|
   |2|

## <a name="output-values-into-dataframe"></a>Вывод данных в data.frame

Теперь мы выведем определенные значения из двух рядов математических результатов в объект data.frame. Первый имеет индекс с последовательными значениями, созданными Python. Во втором используется произвольный индекс строковых значений.

1. В следующем примере возвращается значение из ряда с помощью целочисленного индекса.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **Результаты**

   |ResultValue|
   |------|
   |2.0|

   Помните, что автоматически созданный индекс начинается с 0. Попробуйте использовать значение индекса вне допустимого диапазона и посмотрите, что произойдет.

1. Теперь получим одно значение из другого кадра данных, используя строковый индекс.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
   print(s)
   df = pd.DataFrame(s, index=["simple math example 1"])
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **Результаты**

   |ResultValue|
   |------|
   |0,5|

   При попытке использовать числовой индекс для получения значения из этого ряда появляется сообщение об ошибке.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о написании расширенных функций Python в SQL Server см. в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Написание расширенных функций Python с использованием служб машинного обучения SQL Server](quickstart-python-functions.md)

Дополнительные сведения об использовании Python в службах машинного обучения SQL Server см. в следующих статьях:

- [Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md)
- [Что такое службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
