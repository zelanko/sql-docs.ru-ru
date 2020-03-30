---
title: Краткое руководство. Функции Python
description: В этом кратком руководстве вы узнаете, как внедрять математические и служебные функции Python в Службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d939e04c4a82575cf8210f2c11e734b9912c0fe5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "76831408"
---
# <a name="quickstart-python-functions-with-sql-server-machine-learning-services"></a>Краткое руководство. Функции Python в Службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы узнаете, как внедрять математические и служебные функции Python в Службах машинного обучения SQL Server. Зачастую статистические функции, которые сложно реализовать в T-SQL, выполняются в Python всего парой строк кода.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server со [службами машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) и с установленным языком Python.

  Экземпляр SQL Server может находиться в виртуальной машине Azure или на локальном компьютере. Обратите внимание, что функция внешних сценариев по умолчанию отключена, поэтому перед началом работы вам может потребоваться [включить ее](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **служба панели запуска SQL Server** выполняется.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих сценарии Python. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, которые могут подключаться к экземпляру SQL Server и выполнять запросы T-SQL или хранимые процедуры. В этом кратком руководстве используется среда [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты мы будем использовать пакет Python `numpy`, который по умолчанию устанавливается и загружается в службы машинного обучения SQL Server при установке Python. Он содержит сотню функций для общих статистических задач, в том числе функцию `random.normal`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

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

Как упростить формирование другого набора случайных чисел?

С помощью SQL Server это несложно. Вы определяете хранимую процедуру, которая получает предоставленные пользователем аргументы и передает их в качестве переменных в скрипт Python.

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

Инструкции по созданию модели машинного обучения с использованием Python в SQL Server см. в следующем кратком руководстве:

> [!div class="nextstepaction"]
> [Краткое руководство. Создание и оценка модели прогнозов в Python с помощью служб машинного обучения SQL Server](quickstart-python-train-score-model.md)

Дополнительные сведения о службах машинного обучения SQL Server см. в следующей статье:

- [Что такое службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
