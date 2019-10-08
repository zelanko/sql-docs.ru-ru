---
title: Написание дополнительных функций Python
titleSuffix: SQL Server Machine Learning Services
description: В этом кратком руководстве описано, как написать функцию Python для расширенных статистических вычислений с помощью SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e369e83c99543cc31287932a25949c2ddec98e89
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72007724"
---
# <a name="quickstart-write-advanced-python-functions-with-sql-server-machine-learning-services"></a>Краткое руководство. Создавайте дополнительные функции Python с помощью SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве описывается, как внедрять математические и служебные функции Python в хранимую процедуру SQL с SQL Server Службы машинного обучения. Расширенные статистические функции, которые сложно реализовать в T-SQL, могут выполняться в Python только с одной строкой кода.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server с [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) с установленным языком Python.

  Ваш экземпляр SQL Server может находиться на виртуальной машине Azure или в локальной среде. Просто имейте в виду, что функция внешних скриптов по умолчанию отключена, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **Служба панель запуска SQL Server** запущена перед началом работы.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих скрипты Python. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, если они могут подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты давайте воспользуемся пакетом Python `numpy`, который по умолчанию устанавливается и загружается в SQL Server Службы машинного обучения с установленным Python. Он содержит сотню функций для общих статистических задач, в том числе функцию `random.normal`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

Например, следующий код Python возвращает 100 чисел в среднем 50, учитывая стандартное отклонение 3.

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

Чтобы вызвать эту строку Python из T-SQL, добавьте функцию Python в параметре скрипта Python `sp_execute_external_script`. Выходные данные предполагают кадр данных, поэтому для его преобразования используйте `pandas`.

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

Это легко при объединении с SQL Server. Вы определяете хранимую процедуру, которая получает аргументы от пользователя, а затем передает эти аргументы в скрипт Python в виде переменных.

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

- Строка, начинающаяся с `@params`, определяет все переменные, используемые кодом Python, и соответствующие типы данных SQL.

- Сразу после этого строки сопоставляют имена параметров SQL с соответствующими именами переменных Python.

Теперь, когда функция Python заключена в хранимую процедуру, можно легко вызвать функцию и передать различные значения следующим образом:

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>Использование служебных функций Python для устранения неполадок

Пакеты Python предоставляют разнообразные служебные функции для изучения текущей среды Python. Эти функции могут оказаться полезными, если поиск расхождений выполняется в SQL Server и во внешних средах.

Например, можно использовать системные функции времени в пакете `time` для измерения времени, используемого процессами Python, и анализа проблем производительности.

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

## <a name="next-steps"></a>Следующие шаги

Чтобы создать модель машинного обучения на языке Python в SQL Server, следуйте указаниям в этом кратком руководстве:

> [!div class="nextstepaction"]
> [Краткое руководство. Создание и оценка прогнозной модели в Python с помощью SQL Server Службы машинного обучения @ no__t-0

Дополнительные сведения о SQL Server Службы машинного обучения см. в следующих статьях:

- [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
