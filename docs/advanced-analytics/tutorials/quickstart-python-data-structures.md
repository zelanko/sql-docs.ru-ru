---
title: Работа с типами данных и объектами Python и SQL
titleSuffix: SQL Server Machine Learning Services
description: В этом кратком руководстве вы узнаете, как работать с типами данных и объектами данных в Python и SQL Server с помощью SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e3606072fefa9b74adcfdb914d02e4e82c11e0eb
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199436"
---
# <a name="quickstart-handle-data-types-and-objects-using-python-in-sql-server-machine-learning-services"></a>Краткое руководство. Работа с типами данных и объектами с помощью Python в SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве показано, как использовать структуры данных при использовании Python в SQL Server Службы машинного обучения.

SQL Server полагается на пакет Python **Pandas** , который отлично подходит для работы с табличными данными. Однако нельзя передать скалярное значение из Python в SQL Server и предполагается, что это просто работа. В этом кратком руководстве вы ознакомитесь с некоторыми базовыми определениями типов данных, чтобы подготовиться к дополнительным проблемам, которые могут быть выполнены во время передачи табличных данных между Python и SQL Server.

Основные понятия, которые необходимо изучить:

+ Кадр данных — это таблица с _несколькими_ столбцами.
+ Единственным столбцом в кадре данных является объект, подобный списку, называемый серией.
+ Одно значение кадра данных называется ячейкой и доступ к нему осуществляется по индексу.

Как можно предоставить один результат вычисления как кадр данных, если для данных. Frame требуется табличная структура? Одним из ответов является представление одного скалярного значения в виде ряда, которое легко преобразовать в кадр данных. 

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server с [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) с установленным языком Python.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих скрипты Python. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, если они могут подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="scalar-value-as-a-series"></a>Скалярное значение в виде ряда

Этот пример выполняет некоторые простые математические операции и преобразует скаляр в ряд.

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

   Поскольку ряд не был преобразован в Data. Frame, значения возвращаются в окне сообщения, но можно увидеть, что результаты имеют более табличный формат.

   **Результаты**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   dtype: float64
   ```

1. Чтобы увеличить длину ряда, можно добавить новые значения с помощью массива. 

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

   Если индекс не указан, создается индекс со значениями, начинающимися с 0 и заканчивая длиной массива.

   **Результаты**

   ```text
   STDOUT message(s) from external script: 
   0    0.5
   1    2.0
   dtype: float64
   ```

1. Если увеличить количество значений **индекса** , но не добавлять новые значения **данных** , значения данных повторяются для заполнения ряда.

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

## <a name="convert-series-to-data-frame"></a>Преобразовать ряд в рамку данных

После преобразования скалярных математических результатов в табличную структуру все равно необходимо преобразовать их в формат, который SQL Server может быть обработано.

1. Для преобразования ряда в Data. Frame вызовите [метод Pandas данных](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) .

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

   Результат показан ниже. Даже если вы используете индекс для получения конкретных значений из Data. Frame, значения индекса не являются частью выходных данных.

   **Результаты**

   |ресултвалуе|
   |------|
   |0,5|
   |2|

## <a name="output-values-into-dataframe"></a>Выходные значения в Data. Frame

Теперь вы выводите определенные значения из двух рядов математических результатов в файл Data. Frame. Первый имеет индекс последовательных значений, созданных Python. Во втором используется произвольный индекс строковых значений.

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

   |ресултвалуе|
   |------|
   |2.0|

   Помните, что автоматически созданный индекс начинается с 0. Попробуйте использовать значение индекса вне допустимого диапазона и посмотрите, что произойдет.

1. Теперь получите одно значение из другого фрейма данных, используя строковый индекс.

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

   |ресултвалуе|
   |------|
   |0,5|

   При попытке использовать числовой индекс для получения значения из этой серии появляется сообщение об ошибке.

## <a name="next-steps"></a>Следующие шаги

Далее предстоит создать прогнозную модель с помощью Python в SQL Server.

> [!div class="nextstepaction"]
> [Создание и оценка прогнозной модели в Python](quickstart-python-train-score-model.md)

Дополнительные сведения о SQL Server Службы машинного обучения см. в следующих статьях:

- [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
