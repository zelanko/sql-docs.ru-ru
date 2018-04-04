---
title: Для создания модели с помощью Python с revoscalepy | Документы Microsoft
titleSuffix: SQL Server
ms.date: 02/28/2018
mms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: f54d131868caf332351d7806881ea89238843236
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Для создания модели с помощью Python с revoscalepy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

На этом занятии вы узнаете, как можно выполнять код Python из клиента удаленной разработки, для создания модели линейной регрессии в SQL Server. 

## <a name="prerequisites"></a>предварительные требования

+ На этом занятии рассматривается различных данных, чем предыдущие занятия. Необходимо сначала выполнить предыдущие занятия. Однако если выполнены предыдущие занятия и сервер уже настроен для выполнения Python, используйте этого сервера и базы данных как контекст вычислений.

+ Для выполнения кода Python, используя SQL Server в качестве вычислительных контексте требуется SQL Server 2017 или более поздней версии. Кроме того, необходимо явно установить и включить функцию, затем **службы обучения машины**, выбрав параметр языка Python.

    Если вы установили предварительную версию служб SQL Server 2017 г., следует обновить для по крайней мере RTM-версии. Чтобы развернуть и улучшения функций Python продолжалось более поздние версии службы. Некоторые возможности работы с этим учебником может не работать в ранних предварительных версий.

+ В этом примере используется стандартные среды Python, с именем `PYTEST_SQL_SERVER`. Среде был настроен для хранения **revoscalepy** и другие необходимые библиотеки. 

    Если у вас среду с запуском Python, это необходимо сделать отдельно. Инструкции для создания или изменения среды Python находится вне области видимости для этого учебника. Дополнительные сведения о настройке клиента Python, который содержит нужные библиотеки см. в разделе [клиента Python установите](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) и [Python ссылки на средства](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

## <a name="remote-compute-contexts-and-revoscalepy"></a>Контексты удаленных вычислений и revoscalepy

В этом примере демонстрируется процесс создания модели Python в удаленной _контекста вычислений_, позволяющее работает на клиентском компьютере, но выберите удаленной среде, например SQL Server, Spark или компьютере обучения, сервер, где фактически выполняются операции. Использование контекстов вычислений делает проще написать код, один раз и развернуть ее на любой поддерживаемый среде.

Для выполнения кода Python в SQL Server требуется **revoscalepy** пакета. Это специальный пакет Python, предоставленного корпорацией Майкрософт, аналогично **RevoScaleR** пакет языка R. **Revoscalepy** пакет поддерживает создание контекстов вычислений и предоставляет инфраструктуру для передачи данных и моделей между локальной рабочей станции и удаленном сервере. **Revoscalepy** функции, поддерживаемые выполнение кода в базе данных — [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).

На этом занятии вы использовать данные в SQL Server для обучения на основе линейной модели [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), функция в **revoscalepy** с поддержкой регрессии на очень больших наборов данных. 

На этом занятии также демонстрирует основные принципы настройки и затем использовать **контекста вычислений SQL Server** на Python. Сведения о том, как контексты вычислений, для работы с другими платформами и поддерживаются которой контекстов вычислений см. в разделе [контекст вычислений для выполнения скрипта в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)

## <a name="prepare-the-database-and-sample-data"></a>Подготовка базы данных и образец данных

1. На этом занятии рассматривается базы данных `sqlpy`. Если вы не выполняли ни одно из предыдущих занятий, можно создать базу данных, выполнив следующий код:

    ```sql
    CREATE DATABASE sqlpy;
    GO;
    USE sqlpy;
    GO;
    ```

    > [!IMPORTANT]
    > Если вы хотите использовать другую базу данных, убедитесь, что в образце кода и их изменения имени базы данных в строке подключения.

2. Этот образец использует авиакомпании набора данных, который доступен в R и Python. После создания базы данных для ваших примеров Python заполнить таблицу данных, как описано здесь: [выборку данных в RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/sample-built-in-data).

3. Измените имя этой среды для использования среды доступны на клиентском компьютере.

## <a name="run-the-sample-code"></a>Запуск кода примера

После подготовки базы данных и при наличии данных для обучения, хранящихся в таблице, откройте среду разработки Python и выполнение примера кода.

Код выполняет следующие действия.

1. Импортирует необходимые библиотеки и функции.
2. Создает подключение к SQL Server. Создает **источника данных** объекты для работы с данными.
3. Изменяет данные с помощью **преобразования** , чтобы он может использоваться алгоритм логистической регрессии.
4. Вызовы `rx_lin_mod` и определяется формула, используемая в соответствии с моделью.
5. Создает набор прогнозов, основанных на исходных данных.
6. Создает сводную на основе предсказанных значений.

Все операции выполняются с использованием экземпляра SQL Server в контексте.

> [!NOTE]
> Демонстрационное данного образца, запустив из командной строки см. в этом видео: [SQL Server 2017 г Advanced Analytics с Python](https://www.youtube.com/watch?v=FcoY795jTcc)

### <a name="sample-code"></a>Образец кода

```python
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_lin_mod, rx_predict, rx_summary
from revoscalepy import RxOptions, rx_import

from pandas import Categorical
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

### <a name="defining-a-data-source-vs-defining-a-compute-context"></a>Определение источника данных и определение контекст вычислений.

Источник данных отличается от контекст вычислений. _Источника данных_ определяет данные, используемые в коде. _Контекста вычислений_ определяет, где будет выполняться код. Тем не менее они используют некоторые те же данные:

+ Python переменные, такие как `sql_query` и `sql_connection_string`, определить источник данных. 

    Передавать эти переменные для [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) конструктор, чтобы реализовать **объекта источника данных** с именем `data_source`.

+ Вы создаете **объект контекста вычислений** с помощью [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) конструктор. Итоговый **объект контекста вычислений** называется `sql_cc`.

    В этом примере повторно использует та же строка подключения, которая использовалась в источнике данных, предполагается, что данные находятся на одном экземпляре SQL Server, на котором будет выполняться в контексте. 
    
    Тем не менее источник данных и контекст вычислений может находиться на разных серверах.
 
### <a name="changing-compute-contexts"></a>Изменение контекстов вычислений

После определения контекста вычислений, необходимо задать **активный контекст**. 

По умолчанию большинство операций выполняются локально, это значит, что если не указать контекст различных вычислений, данные будут получены из источника данных и код будет выполняться в текущей среды Python.

Чтобы задать активный контекст двумя способами.
+ Как аргумент метода или функции
+ Путем вызова `rx_set_computecontext`

#### <a name="set-compute-context-as-an-argument-of-a-method-or-function"></a>Задать контекст вычислений как аргумент метода или функции

В этом примере был переключен контекст вычислений с помощью аргумента отдельного **rx** функции.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

Этот контекст вычислений используется повторно в вызове [rxsummary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary):.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

#### <a name="set-a-compute-context-explicitly-using-rxsetcomputecontext"></a>Задать явным образом с помощью rx_set_compute_context контекст вычислений.

Функция [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) позволяет переключаться между контекстов, которые уже были определены вычислений.

После установки активного контекста вычислений, он остается активным, пока не потребуется изменить его.

### <a name="using-parallel-processing-and-streaming"></a>С помощью параллельной обработки и потоковой передачи

При определении контекст вычислений, можно также задать параметры, управляющие способ обработки данных в контексте вычислений. Эти параметры отличаются в зависимости от типа источника данных.

В контексте вычислений SQL Server можно задать размер пакета или предоставить подсказки о степени параллелизма для использования при выполнении задачи.

+ Образец был запущен на компьютере с четырьмя процессорами, поэтому `num_tasks` параметра равным 4 позволяет максимально использовать ресурсы. 
+ Если это значение равно 0, SQL Server использует значение по умолчанию, используемого для параллельного выполнения задач столько максимально при текущих настройках MAXDOP для сервера. Однако точное число задач, которые могут быть выделены зависит от ряда других факторов, например параметры сервера и других заданий, работающих под управлением.

## <a name="related-samples"></a>Связанные примеры

Эти дополнительные Python образцы и учебники демонстрируют конца в конец сценарии, использующие более сложных источников данных, а также использование контекстах удаленных вычислений.

+ [Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Создать прогнозную модель с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Создать прогнозную модель с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
