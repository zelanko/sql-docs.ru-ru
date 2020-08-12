---
title: Краткое руководство. Структуры данных Python
titleSuffix: SQL machine learning
description: В этом кратком руководстве вы узнаете, как работать со структурами данных и объектами данных в Python с использованием Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/21/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: ed35820d38ea31ea0b7f8bae9b0a440398d55674
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784099"
---
# <a name="quickstart-data-structures-and-objects-using-python-with-sql-machine-learning"></a>Краткое руководство. Использование структур данных и объектов при работе с Python и машинным обучением SQL
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этом кратком руководстве вы узнаете, как использовать структуры и типы данных при применении Python в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md) или [Кластерах больших данных](../../big-data-cluster/machine-learning-services.md). Вы узнаете о том, как перемещать данные между Python и SQL Server, и о типичных проблемах, возникающих при этом.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этом кратком руководстве вы узнаете, как использовать структуры и типы данных при работе с Python в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md). Вы узнаете о том, как перемещать данные между Python и SQL Server, и о типичных проблемах, возникающих при этом.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
В этом кратком руководстве вы узнаете, как использовать структуры и типы данных при работе с Python в [Службах машинного обучения управляемого экземпляра SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview). Вы узнаете о том, как перемещать данные между Python и управляемым экземпляром SQL Azure, и о типичных проблемах, возникающих при этом.
::: moniker-end

В машинном обучении SQL в качестве основы используется пакет Python **pandas**, который отлично подходит для работы с табличными данными. Однако нельзя просто передать скалярное значение из Python в вашу базу данных и ждать, что это *просто сработает*. В этом кратком руководстве вы вспомните некоторые базовые определения типов данных, чтобы подготовиться к решению дополнительных проблем, с которыми вы можете столкнуться при передаче табличных данных между Python и базой данных.

Основные понятия, которые необходимо знать:

- Кадр данных — это таблица с _несколькими_ столбцами.
- Кадр данных с одним столбцом — объект в виде списка, называемый рядом.
- Одно значение кадра данных называется ячейкой, доступ к ней осуществляется по индексу.

Как можно предоставить единственный результат вычисления в виде кадра данных, если для объекта data.frame требуется табличная структура? Одним из ответов является представление одного скалярного значения в виде ряда, который легко преобразовать в кадр данных.

> [!NOTE]
> При возврате дат Python в SQL использует тип DATETIME, который имеет ограниченный диапазон дат от 1753-01-01 (-53690) до 9999-12-31 (2958463).

## <a name="prerequisites"></a>Предварительные требования

Для работы с этим кратким руководством необходимо следующее.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- Службы машинного обучения SQL Server. Сведения об установке Служб машинного обучения см. в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md) или [руководстве по установке для Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Можно также [включить Службы машинного обучения в кластерах больших данных SQL Server](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
- Службы машинного обучения SQL Server. Сведения об установке Служб машинного обучения см. в [руководстве по установке для Windows](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
- Службы машинного обучения в управляемом экземпляре SQL Azure. Сведения о регистрации см. в статье [Общие сведения о Службах машинного обучения в управляемом экземпляре SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview).
::: moniker-end

- Средство для выполнения SQL-запросов, содержащих сценарии Python. В этом кратком руководстве используется [Azure Data Studio](../../azure-data-studio/what-is.md).

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

После преобразования скалярных математических результатов в табличную структуру все еще необходимо преобразовать их в формат, который может обрабатывать машинное обучение SQL.

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

Дополнительные сведения о написании расширенных функций Python с использованием машинного обучения SQL см. в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Создание сложных функций Python](quickstart-python-functions.md)
