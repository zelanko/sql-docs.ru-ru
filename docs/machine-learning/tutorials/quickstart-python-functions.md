---
title: Краткое руководство. Функции Python
titleSuffix: SQL machine learning
description: В этом кратком руководстве вы узнаете, как использовать математические и служебные функции Python в машинном обучении SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/21/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 5aef8010c48e08931998f1bd7e49c3797ef4e81a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784093"
---
# <a name="quickstart-python-functions-with-sql-machine-learning"></a>Краткое руководство. Функции Python с использованием машинного обучения SQL
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этом кратком руководстве вы узнаете, как использовать математические и служебные функции Python в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md) или [Кластерах больших данных](../../big-data-cluster/machine-learning-services.md). Зачастую статистические функции, которые сложно реализовать в T-SQL, выполняются в Python всего парой строк кода.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этом кратком руководстве вы узнаете, как использовать математические и служебные функции Python в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md). Зачастую статистические функции, которые сложно реализовать в T-SQL, выполняются в Python всего парой строк кода.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
В этом кратком руководстве вы узнаете, как использовать математические и служебные функции Python в [Службах машинного обучения управляемого экземпляра SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview). Зачастую статистические функции, которые сложно реализовать в T-SQL, выполняются в Python всего парой строк кода.
::: moniker-end

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

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты давайте воспользуемся пакетом Python `numpy`, который устанавливается и загружается по умолчанию. Он содержит сотню функций для общих статистических задач, в том числе функцию `random.normal`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

Например, следующий код Python возвращает 100 чисел со средним значением 50 и стандартным отклонением 3.

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

Чтобы вызвать эту строку Python из T-SQL, добавьте функцию Python в параметр скрипта Python `sp_execute_external_script`. На выходе должен получиться кадр данных, поэтому используйте для преобразования `pandas`.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=100, loc=50, scale=3));
'
    , @input_data_1 = N'   ;'
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

Как упростить формирование другого набора случайных чисел? Вы определяете хранимую процедуру, которая получает предоставленные пользователем аргументы и передает их в качестве переменных в скрипт Python.

```sql
CREATE PROCEDURE MyPyNorm (
      @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=mynumbers, loc=mymean, scale=mysd));
'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- В первой строке определяется каждый из входных параметров SQL, необходимых при выполнении хранимой процедуры.

- Строка, начинающаяся с `@params`, определяет все переменные, используемые в коде Python, и соответствующие типы данных SQL.

- Следующие строки сопоставляют имена параметров SQL с соответствующими именами переменных Python.

Теперь, когда функция Python упакована в хранимой процедуре, вы можете легко вызвать ее и передать различные значения, как показано ниже:

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>Использование служебных функций Python для устранения неполадок

В пакетах Python предусмотрено множество служебных функций для изучения текущей среды Python. Они могут оказаться полезными, если вы нашли несоответствия в выполнении кода Python в SQL Server и внешних средах.

Например, с помощью функций управления системным временем в пакете `time` вы можете оценить количество времени, затрачиваемого процессами Python, и проанализировать проблемы, связанные с производительностью.

```sql
EXECUTE sp_execute_external_script
      @language = N'Python'
    , @script = N'
import time
start_time = time.time()

# Run Python processes

elapsed_time = time.time() - start_time
'
    , @input_data_1 = N' ;';
```

## <a name="next-steps"></a>Дальнейшие действия

Сведения о создании модели машинного обучения с использованием Python и машинного обучения SQL приведены в следующем кратком руководстве:

> [!div class="nextstepaction"]
> [Краткое руководство. Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md)
