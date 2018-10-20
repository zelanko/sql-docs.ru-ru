---
title: Использование Python с помощью revoscalepy для создания модели | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5c8ff387c3abda3f147700dce6349009a027a778
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461960"
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Использование Python с помощью revoscalepy для создания модели
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

На этом занятии вы узнаете, как выполнять код Python в клиенте удаленного разработки для создания модели линейной регрессии в SQL Server. 

## <a name="prerequisites"></a>предварительные требования

+ На этом занятии рассматривается различных данных, чем предыдущие занятия. Необходимо сначала выполнить предыдущие занятия. Тем не менее, если вы прошли все предыдущие занятия и сервер уже настроен на запуск Python, сервера и используйте базы данных как в контексте вычислений.
+ Выполнять код Python, используя SQL Server в качестве вычислений контекст должен быть SQL Server 2017 или более поздней версии. Кроме того, необходимо явным образом установить и затем активировать соответствующую функцию **служб машинного обучения**, выбрав параметр языка Python.

    Если вы установили предварительную версию SQL Server 2017, необходимо обновить для по крайней мере версии RTM. Разверните узел и совершенствующих функциональные возможности Python продолжалось последующих выпусках службы. Некоторые функции работы с этим руководством может не работать в ранних предварительных версий.

+ В этом примере используется предопределенный окружение Python, с именем `PYTEST_SQL_SERVER`. Среда настроена для хранения **revoscalepy** и другие необходимые библиотеки. 

    Если у вас среде, настроенной для выполнения Python, вы должны сделать отдельно. Описание способов для создания или изменения среды Python выходит из области действия в этом руководстве. Дополнительные сведения о том, как настроить клиент Python, который содержит правильные библиотеки см. в разделе [клиента установить Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) и [Python ссылку к средствам](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

## <a name="remote-compute-contexts-and-revoscalepy"></a>Контексты удаленных вычислений и revoscalepy

В этом примере демонстрируется процесс создания модели Python в удаленном _контекста вычислений_, позволяющее работает на клиентском компьютере, но выберите удаленной среде, например SQL Server, Spark или Machine Learning Server, где фактически выполняются операции. Использование контекстов вычисления упрощает написать код единожды и развернуть его в любую поддерживаемую среду.

Для выполнения кода Python в SQL Server требует **revoscalepy** пакета. Это специальный пакет Python, предлагаемых корпорацией Майкрософт, аналогичную **RevoScaleR** пакет языка R. **Revoscalepy** пакет поддерживает создание контекстов вычислений и предоставляет инфраструктуру для передачи данных и моделей между рабочей станцией и удаленному серверу. **Revoscalepy** функции, поддерживаемые, выполнение кода в базе данных является [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

На этом занятии вы использовать данные в SQL Server для обучения на основе линейной модели [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), функции в **revoscalepy** , поддерживающий регрессии на очень больших наборов данных. 

На этом занятии также рассматривается базовые сведения о настройке и затем использовать **контекста вычислений SQL Server** в Python. Обсуждение того, как контексты вычислений работать с другими платформами и который контексты вычислений поддерживаются, см. в разделе [контекст вычислений для выполнения скрипта в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)

## <a name="prepare-the-database-and-sample-data"></a>Подготовка базы данных и образцы данных

1. На этом занятии рассматривается базе **sqlpy**. Если вы не выполнили любой из предыдущих занятий, можно создать базу данных, выполнив следующий код:

    ```sql
    CREATE DATABASE sqlpy;
    GO
    USE sqlpy;
    GO
    ```

    > [!IMPORTANT]
    > Если вы хотите использовать другую базу данных, обязательно измените пример кода и измените имя базы данных в строке подключения.

2. Этот пример использует набора данных по Авиабилетам, который доступен в R и Python. После создания базы данных для ваших примеров Python, заполнить таблицу данных, как описано здесь: [выборка данных в RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/sample-built-in-data).

3. Измените имя этой среды для использования среды доступны на клиентском компьютере.

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
> Пример данного образца, запустив из командной строки, см. в этом видео: [SQL Server 2017 расширенной аналитики с помощью Python](https://www.youtube.com/watch?v=FcoY795jTcc)

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

Источник данных отличается от контекста вычислений. _Источника данных_ определяет данные, используемые в коде. _Контекста вычислений_ определяет, где будет выполняться код. Тем не менее они используют некоторые из той же информации:

+ Python переменные, такие как `sql_query` и `sql_connection_string`, определение источника данных. 

    Передавать эти переменные для [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) конструктор, чтобы реализовать **объекта источника данных** с именем `data_source`.

+ Создании **объект контекста вычислений** с помощью [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) конструктор. Полученный в результате **объект контекста вычислений** называется `sql_cc`.

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

Этот контекст вычислений используется повторно в вызове [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Задание контекста вычисления явным образом с помощью rx_set_compute_context

Функция [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) позволяет переключаться между вычислительные возможности контекстов, которые уже были определены.

После установки активный контекст вычислений, он остается активным, пока вы не измените его.

### <a name="using-parallel-processing-and-streaming"></a>С помощью параллельной обработки и потоковой передачи

При определении контекста вычислений, можно также задать параметры, управляющие способом обработки данных в контексте вычислений. Эти параметры отличаются в зависимости от типа источника данных.

Для контекстов вычислений SQL Server можно установить размер пакета или предоставить подсказки о Степень параллельности для использования в выполнении задач.

+ Образец была запущена на компьютере с четырьмя процессорами, поэтому `num_tasks` параметр имеет значение 4, чтобы разрешить максимальное использование ресурсов. 
+ Если это значение равно 0, SQL Server использует по умолчанию, который является для параллельного выполнения задач можно при текущих настройках MAXDOP для сервера. Тем не менее точное число задач, которые могут быть выделены зависит от многих других факторов, таких как параметры сервера и других заданий, работающих под управлением.

## <a name="related-samples"></a>Связанные примеры

Эти дополнительные примеры для Python и руководства демонстрируют end-to-end сценарии, использующие более сложные источники данных, а также использовать контексты удаленных вычислений.

+ [Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
