---
title: Использование Python с revoscalepy для создания модели
description: Напишите скрипт Python с помощью функций revoscalepy, чтобы создать модели обработки и анализа данных, которые выполняются удаленно в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 596e5f6b5145dc258c781ca7b88a69fc962d7021
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714713"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Использование Python с revoscalepy для создания модели, которая выполняется удаленно на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Библиотека [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) Python от корпорации Майкрософт предоставляет алгоритмы обработки и анализа данных для изучения, визуализации, преобразования и аналитики. Эта библиотека имеет стратегическую важность в сценариях интеграции Python в SQL Server. На многоядерном сервере функции **revoscalepy** могут выполняться параллельно. В распределенной архитектуре с центральным сервером и клиентскими рабочими станциями (на разных физических компьютерах, у которых есть одна и та же библиотека **revoscalepy** ), можно написать код Python, который начинается локально, но затем перемещает выполнение на удаленный экземпляр SQL Server где находятся данные.

**Revoscalepy** можно найти в следующих продуктах и дистрибутивах Майкрософт:

+ [Службы машинного обучения SQL Server (в базе данных)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (не SQL, изолированный сервер)](https://docs.microsoft.com/machine-learning-server/index)
+ [Клиентские библиотеки Python (для рабочих станций разработки)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

В этом упражнении показано, как создать модель линейной регрессии на основе [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), одного из алгоритмов в **revoscalepy** , принимающих контекст вычислений в качестве входных данных. Код, который вы будете выполнять в этом упражнении, сдвигает выполнение кода из локальной среды в удаленную вычислительную среду, которая включается функциями **revoscalepy** , которые обеспечивают удаленный контекст вычисления.

Выполнив инструкции из этого руководства, вы научитесь:

> [!div class="checklist"]
> * Использование **revoscalepy** для создания линейной модели
> * Операции сдвига из локальной среды в удаленном контексте вычислений

## <a name="prerequisites"></a>предварительные требования

Примерами данных, используемыми в этом упражнении, является база данных [**флигхтдата**](demo-data-airlinedemo-in-sql.md) .

Для запуска примера кода в этой статье требуется интегрированная среда разработки, а интегрированная среда разработки должна быть связана с исполняемым файлом Python.

Чтобы попрактиковаться в смене контекста вычислений, требуется [Локальная рабочая станция](../python/setup-python-client-tools-sql.md) и SQL Server экземпляр ядра СУБД с включенными [службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) и Python. 

> [!Tip]
> Если у вас нет двух компьютеров, можно имитировать удаленный контекст вычислений на одном физическом компьютере, установив соответствующие приложения. Во первых, установка [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) работает как удаленный экземпляр. Во вторых, установка [клиентских библиотек Python работает](../python/setup-python-client-tools-sql.md) в качестве клиента. На одном компьютере будут находиться две копии одного и того же дистрибутива Python и библиотеки Microsoft Python. Для успешного выполнения упражнения необходимо будет отследить пути к файлам и скопировать используемую копию Python. exe.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Удаленные контексты вычислений и revoscalepy

В этом примере демонстрируется процесс создания модели Python в удаленном контексте вычислений, который позволяет работать с клиентом, но выбрать удаленную среду, например SQL Server, Spark или Machine Learning Server, где фактически выполняются операции. Цель удаленного контекста вычислений заключается в том, чтобы привести вычисления в место, где находятся данные.

Для выполнения кода Python в SQL Server требуется пакет **revoscalepy** . Это специальный пакет Python, предоставляемый корпорацией Майкрософт, аналогичный пакету **RevoScaleR** для языка R. Пакет **revoscalepy** поддерживает создание контекстов вычислений и предоставляет инфраструктуру для передачи данных и моделей между локальной рабочей станцией и удаленным сервером. Функция **revoscalepy** , которая поддерживает выполнение кода в базе данных, — это [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

На этом занятии вы используете данные в SQL Server для обучения линейной модели на основе [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), функции в **revoscalepy** , которая поддерживает регрессию для очень больших наборов данных. 

На этом занятии также демонстрируются основные сведения о настройке и использовании **контекста вычислений SQL Server** в Python. Обсуждение того, как контексты вычислений работают с другими платформами и какие контексты вычислений поддерживаются, см. в разделе [контекст вычислений для выполнения скриптов в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


## <a name="run-the-sample-code"></a>Запуск примера кода

После подготовки базы данных и данных для обучения, хранящихся в таблице, откройте среду разработки Python и запустите пример кода.

Код выполняет следующие действия:

1. Импортирует необходимые библиотеки и функции.
2. Создает подключение к SQL Server. Создает объекты **источника данных** для работы с данными.
3. Изменяет данные с помощью **преобразований** , чтобы их можно было использовать в алгоритме логистической регрессии.
4. Вызывает `rx_lin_mod` и определяет формулу, используемую для соответствия модели.
5. Формирует набор прогнозов на основе исходных данных.
6. Создает сводку на основе прогнозируемых значений.

Все операции выполняются с использованием экземпляра SQL Server в качестве контекста вычислений.

> [!NOTE]
> Демонстрацию этого примера, выполняемого из командной строки, см. в этом видео: [SQL Server 2017 Расширенная аналитика с помощью Python](https://www.youtube.com/watch?v=FcoY795jTcc)

### <a name="sample-code"></a>Образец кода

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

import os

def test_linmod_sql():
    sql_server = os.getenv('PYTEST_SQL_SERVER', '.')
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=sqlpy;Trusted_Connection=True;'
    print("connectionString={0!s}".format(sql_connection_string))

    data_source = RxSqlServerData(
        sql_query = "select top 10 * from airlinedemosmall",
        connection_string = sql_connection_string,

        column_info = {
            "ArrDelay" : { "type" : "integer" },
            "DayOfWeek" : {
                "type" : "factor",
                "levels" : [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ]
            }
        })

    sql_compute_context = RxInSqlServer(
        connection_string = sql_connection_string,
        num_tasks = 4,
        auto_cleanup = False
        )

    #
    # Run linmod locally
    #
    linmod_local = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source)
    #
    # Run linmod remotely
    #
    linmod = rx_lin_mod("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)

    # Predict results
    # 
    predict = rx_predict(linmod, data = rx_import(input_data = data_source))
    summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)
```

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Определение источника данных и определение контекста вычислений

Источник данных отличается от контекста вычислений. *Источник данных* определяет данные, используемые в коде. Контекст вычислений определяет, где будет выполняться код. Однако они используют одни и те же сведения:

+ Переменные Python, такие как `sql_query` и `sql_connection_string`, определяют источник данных. 

    Передайте эти переменные в конструктор [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) , чтобы реализовать **объект источника данных** с `data_source`именем.

+ **Объект контекста вычислений** создается с помощью конструктора [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) . `sql_cc`Результирующий **объект контекста вычислений** называется.

    В этом примере повторно используется та же строка подключения, которая использовалась в источнике данных, исходя из предположения, что данные находятся на том же экземпляре SQL Server, который будет использоваться в качестве контекста вычислений. 
    
    Однако источник данных и контекст вычислений могут находиться на разных серверах.
 
### <a name="changing-compute-contexts"></a>Изменение контекстов вычислений

После определения контекста вычислений необходимо задать **активный контекст вычислений**. 

По умолчанию большинство операций выполняются локально. Это означает, что если не указать другой контекст вычислений, данные будут получены из источника данных, а код будет выполняться в текущей среде Python.

Существует два способа задать активный контекст вычислений:
+ В качестве аргумента метода или функции
+ Путем вызова метода`rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Установка контекста вычислений в качестве аргумента метода или функции

В этом примере вы задаете контекст вычислений с помощью аргумента отдельной функции **RX** .
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Этот контекст вычислений повторно используется в вызове [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Явное определение контекста вычислений с помощью rx_set_compute_context

Функция [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) позволяет переключаться между контекстами вычислений, которые уже определены.

После установки активного контекста вычислений он остается активным, пока вы не измените его.

### <a name="using-parallel-processing-and-streaming"></a>Использование параллельной обработки и потоковой передачи

При определении контекста вычислений можно также задать параметры, определяющие способ обработки данных в контексте вычислений. Эти параметры зависят от типа источника данных.

Для SQL Server контекстов вычислений можно задать размер пакета или указать указания степени параллелизма, которая будет использоваться в выполняющихся задачах.

+ Пример был запущен на компьютере с четырьмя процессорами, поэтому `num_tasks` параметру присвоено значение 4, чтобы разрешить максимальное использование ресурсов. 
+ Если присвоить этому параметру значение 0, то SQL Server использует значение по умолчанию, которое позволяет выполнять максимально возможное число задач в соответствии с текущими параметрами MAXDOP для сервера. Однако точное количество задач, которые могут быть выделены, зависит от многих других факторов, таких как параметры сервера и других выполняемых заданий.

## <a name="next-steps"></a>Следующие шаги

Эти дополнительные примеры и учебники Python демонстрируют комплексные сценарии использования более сложных источников данных, а также использование удаленных контекстов вычислений.

+ [Язык Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
