---
title: Использование Python с помощью revoscalepy для создания модели - машинного обучения SQL Server
description: Написать сценарий Python с помощью revoscalepy функции для создания моделей обработки и анализа данных, которые выполняются удаленно в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 98e13308c74031248778c2dfc9b2c588772223d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961822"
---
# <a name="use-python-with-revoscalepy-to-create-a-model-that-runs-remotely-on-sql-server"></a>Использование Python с помощью revoscalepy для создания модели, который выполняется удаленно на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) библиотека Python от корпорации Майкрософт предоставляет алгоритмы обработки и анализа данных для просмотра данных, визуализации, преобразования и анализа. Эта библиотека включает в себя стратегических в сценариях интеграции Python в SQL Server. На сервере многоядерных **revoscalepy** функции могут выполняться параллельно. В распределенной архитектуре с центральной серверных и клиентских рабочих станциях (разных физических компьютерах, все имеют одинаковые **revoscalepy** библиотеки), можно написать код Python, который запускает локально, но затем переносит выполнение удаленный экземпляр SQL Server, где находятся данные.

Можно найти **revoscalepy** в следующие продукты Майкрософт и распределения:

+ [SQL Server службы машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server (отличные от SQL, изолированный сервер)](https://docs.microsoft.com/machine-learning-server/index)
+ [Клиентские библиотеки Python (для станций разработчиков)](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) 

В этом упражнении демонстрируется способ создания модели линейной регрессии на основе [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), один из алгоритмов в **revoscalepy** , принимающий контекст вычислений в качестве входных данных. Код будет работать в этом упражнении переносит выполнение кода с локального удаленного вычислительной среды, включаемые **revoscalepy** функции, которые позволяют удаленного контекста вычислений.

Путем изучения этого учебника вы узнаете, как:

> [!div class="checklist"]
> * Используйте **revoscalepy** для создания линейной модели
> * Сдвинуть операций из локального контекста удаленных вычислений

## <a name="prerequisites"></a>предварительные требования

Демонстрационные данные, используемые в этом упражнении [ **flightdata** ](demo-data-airlinedemo-in-sql.md) базы данных.

Необходимо, чтобы интегрированная среда разработки для запуска примера кода в этой статье и интегрированной среды разработки, которые должны быть связаны с исполняемому файлу Python.

Чтобы на практике Смена контекста вычислений, вам потребуется [локальной рабочей станции](../python/setup-python-client-tools-sql.md) и экземпляр ядра СУБД SQL Server с [служб машинного обучения](../install/sql-machine-learning-services-windows-install.md) и поддержкой Python. 

> [!Tip]
> Если у вас два компьютера, вы можете имитировать контекст удаленных вычислений на одном физическом компьютере, установив соответствующее приложение. Во-первых, установка [службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) работает как «удаленный» экземпляр. Во-вторых, установка [клиентские библиотеки Python работает](../python/setup-python-client-tools-sql.md) как клиент. У вас будет две копии одной дистрибутив Python и библиотек Microsoft Python на одном компьютере. Необходимо хранить список путей к файлам и нужную копию Python.exe, вы используете для успешного завершения это упражнение.

## <a name="remote-compute-contexts-and-revoscalepy"></a>Контексты удаленных вычислений и revoscalepy

В этом образце показан процесс создания модели Python в удаленном контексте вычислений, который позволяет работать в клиенте, но выберите удаленной среде, например SQL Server, Spark или Machine Learning Server, где фактически выполняются операции. Цель контекста удаленных вычислений — для вычисления, где хранятся данные.

Для выполнения кода Python в SQL Server требует **revoscalepy** пакета. Это специальный пакет Python, предлагаемых корпорацией Майкрософт, аналогичную **RevoScaleR** пакет языка R. **Revoscalepy** пакет поддерживает создание контекстов вычислений и предоставляет инфраструктуру для передачи данных и моделей между рабочей станцией и удаленному серверу. **Revoscalepy** функции, поддерживаемые, выполнение кода в базе данных является [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

На этом занятии вы использовать данные в SQL Server для обучения на основе линейной модели [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), функции в **revoscalepy** , поддерживающий регрессии на очень больших наборов данных. 

На этом занятии также рассматривается базовые сведения о настройке и затем использовать **контекста вычислений SQL Server** в Python. Обсуждение того, как контексты вычислений работать с другими платформами и который контексты вычислений поддерживаются, см. в разделе [контекст вычислений для выполнения скрипта в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).


## <a name="run-the-sample-code"></a>Запустите пример кода

После подготовки базы данных и при наличии данных для обучения, хранятся в таблице, откройте среду разработки Python и выполнение примера кода.

Код выполняет следующие действия:

1. Импортирует необходимые библиотеки и функции.
2. Создает подключение к SQL Server. Создает **источника данных** объектов для работы с данными.
3. Изменяет данные с помощью **преобразования** , чтобы он может использоваться в алгоритм логистической регрессии.
4. Вызовы `rx_lin_mod` и определяет формула, используемая в соответствии с моделью.
5. Создает набор прогнозов, основанных на исходные данные.
6. Создает сводку, исходя из прогнозируемых значений.

Все операции выполняются с помощью экземпляра SQL Server в качестве контекста вычисления.

> [!NOTE]
> Для демонстрации данного образца, запустив из командной строки см. в этом видео: [SQL Server 2017 расширенной аналитики с помощью Python](https://www.youtube.com/watch?v=FcoY795jTcc)

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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Определение источника данных и определение контекста вычисления

Источник данных отличается от контекста вычислений. *Источника данных* определяет данные, используемые в коде. Контекст вычислений определяет, где будет выполняться код. Тем не менее они используют некоторые из той же информации:

+ Python переменные, такие как `sql_query` и `sql_connection_string`, определение источника данных. 

    Передавать эти переменные для [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) конструктор, чтобы реализовать **объекта источника данных** с именем `data_source`.

+ Создании **объект контекста вычислений** с помощью [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) конструктор. Полученный в результате **объект контекста вычислений** называется `sql_cc`.

    В этом примере повторно использует ту же строку подключения, которая использовалась в источнике данных, предполагается, что данные находятся на тот же экземпляр SQL Server, который будет использоваться как контекст вычислений. 
    
    Тем не менее источник данных и контекст вычислений может быть на разных серверах.
 
### <a name="changing-compute-contexts"></a>Изменение контексты вычислений

После определения контекста вычисления, необходимо задать **активный контекст вычисления**. 

По умолчанию большинство операций выполняются локально, которое означает, что если вы не укажете разных контекстах вычислений, данные будут получены из источника данных и код будет выполняться в текущей среде Python.

Чтобы задать активный контекст вычисления двумя способами:
+ Как аргумент метода или функции
+ Путем вызова `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Настройки контекста вычислений в качестве аргумента метода или функции

В этом примере настройки контекста вычислений с помощью аргумента лица **rx** функции.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Этот контекст вычислений используется повторно в вызове [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Задание контекста вычисления явным образом с помощью rx_set_compute_context

Функция [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) позволяет переключаться между вычислительные возможности контекстов, которые уже были определены.

После установки активный контекст вычислений, он остается активным, пока вы не измените его.

### <a name="using-parallel-processing-and-streaming"></a>С помощью параллельной обработки и потоковой передачи

При определении контекста вычислений, можно также задать параметры, управляющие способом обработки данных в контексте вычислений. Эти параметры отличаются в зависимости от типа источника данных.

Для контекстов вычислений SQL Server можно установить размер пакета или предоставить подсказки о Степень параллельности для использования в выполнении задач.

+ Образец была запущена на компьютере с четырьмя процессорами, поэтому `num_tasks` параметр имеет значение 4, чтобы разрешить максимальное использование ресурсов. 
+ Если это значение равно 0, SQL Server использует по умолчанию, который является для параллельного выполнения задач можно при текущих настройках MAXDOP для сервера. Тем не менее точное число задач, которые могут быть выделены зависит от многих других факторов, таких как параметры сервера и других заданий, работающих под управлением.

## <a name="next-steps"></a>Следующие шаги

Эти дополнительные примеры для Python и руководства демонстрируют end-to-end сценарии, использующие более сложные источники данных, а также использовать контексты удаленных вычислений.

+ [Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
