---
title: "Для создания модели с помощью Python с revoscalepy | Документы Microsoft"
ms.custom: SQL2016_New_Updated
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: c497ad3e302f2950a65cf41aaa41237f19171ab4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="use-python-with-revoscalepy-to-create-a-model"></a>Для создания модели с помощью Python с revoscalepy

В этом примере показано, как можно создать модель линейной регрессии в SQL Server, с помощью алгоритма из **revoscalepy** пакета.

**Revoscalepy** пакетом для Python, содержащего объекты, преобразования, и алгоритмы, похожие на те для **RevoScaleR** пакет языка R. С этой библиотеки можно создать контекст вычислений, перемещение данных между контексты вычислений, преобразования данных и обучения моделей прогнозирования с помощью популярные алгоритмы, такие как логистическая и линейной регрессии, деревья принятия решений и многое другое.

Дополнительные сведения см. в разделе [возможности revoscalepy?](../python/what-is-revoscalepy.md) и [Python функции ссылки](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="prerequisites"></a>Предварительные требования

> [!IMPORTANT]
> Для выполнения кода Python в SQL Server, необходимо установить SQL Server 2017 г CTP-версии 2.0 или более поздней версии, а также необходимо установить и включить функцию, **службы обучения машины** с Python. Другие версии SQL Server не поддерживают интеграцию Python.

## <a name="run-the-sample-code"></a>Запуск кода примера

Этот код выполняет следующие действия:

1. Импортирует необходимые библиотеки и функции
2. Создает подключение к SQL Server и создает объекты источника данных для работы с данными
3. Изменяет данные так, что он может использоваться алгоритм логистической регрессии
4. Вызовы `rx_lin_mod` и определяется формула, используемая в соответствии с моделью
5. Создает набор прогнозов, основанных на исходный набор данных
6. Создает сводную на основе прогнозируемых значений

Все операции выполняются с использованием экземпляра SQL Server в контексте.

Как правило процесс вызова Python в контексте удаленных вычислений аналогично тому, как использовать R в контексте удаленных вычислений. Выполните пример как сценарий Python из командной строки или с помощью среды разработки Python, которая включает компоненты интеграции Python, предоставляемые в этом выпуске. В коде можно создать и использовать объект контекста вычислений чтобы указать, где определенные вычисления для выполнения.

> [!NOTE]
> Убедитесь, что имена базы данных и среды, соответствующим образом изменить.
> 
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
    
    sql_connection_string = 'Driver=SQL Server;Server=' + sqlServer + ';Database=PyTestDb;Trusted_Connection=True;'
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

## <a name="discussion"></a>Обсуждение

Позволяет просмотреть код и выделите некоторых ключевых шагов.

### <a name="defining-a-data-source-and-compute-context"></a>Определение данных источника и контекста вычислений

Источник данных отличается от контекст вычислений. _Источника данных_ определяет данные, используемые в коде. _Контекста вычислений_ определяет, где будет выполняться код.

1. Создание переменных Python, таких как `sql_query` и `sql_connection_string`, определяющие источник и данные, которые вы хотите использовать. Передавать эти переменные для [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) конструктор, чтобы реализовать **объекта источника данных** с именем `data_source`.
2. Создать объект контекста вычислений с помощью [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserverdata) конструктор. В этом примере передать та же строка подключения, созданного ранее, предполагается, что данные находятся на одном экземпляре SQL Server, на котором будет выполняться в контексте. Тем не менее источник данных и контекст вычислений может находиться на разных серверах. Итоговый **объект контекста вычислений** называется `sql_cc`.
3. Выберите активный контекст. По умолчанию операции выполняются локально, это значит, что если не указать контекст различных вычислений, данные будут получены из источника данных и модели Подгонка будет работать в текущей среды Python.

### <a name="changing-compute-contexts"></a>Изменение контекстов вычислений

В этом примере был переключен контекст вычислений с помощью аргумента отдельного **rx** функции.
    
`linmod = rx_lin_mod_ex("ArrDelay ~ DayOfWeek", data = data, compute_context = sql_compute_context)`

То же самое происходит в вызове **rxsummary**, когда повторно контекст вычислений.

`summary = rx_summary("ArrDelay ~ DayOfWeek", data = data_source, compute_context = sql_compute_context)`

Можно также использовать функцию [rx_set_computecontext](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rx-set-compute-context) для переключения между контексты вычислений, которые уже были определены.

### <a name="setting-the-degree-of-parallelism"></a>Настройка степени параллелизма

При определении контекст вычислений, можно также задать параметры, управляющие способ обработки данных в контексте вычислений. Эти параметры отличаются в зависимости от типа источника данных.

В контексте вычислений SQL Server можно задать размер пакета или предоставить подсказки о степени параллелизма для использования при выполнении задачи.

Образец был запущен на компьютере с четырьмя процессорами, чтобы задать мы *num_tasks* параметр 4. Если это значение равно 0, SQL Server использует значение по умолчанию, используемого для параллельного выполнения задач столько максимально при текущих настройках MAXDOP для сервера. Тем не менее даже на серверах с большим числом процессоров точное число задач, которые могут быть распределены зависит от ряда других факторов, например параметры сервера и других работающих заданий.

## <a name="related-samples"></a>Связанные примеры

См. Эти примеры Python и учебники по Дополнительные советы и демонстрации начала до конца.

+ [Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Создать прогнозную модель с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)
+ [Развертывание и использование моделей Python](../python/publish-consume-python-code.md)
