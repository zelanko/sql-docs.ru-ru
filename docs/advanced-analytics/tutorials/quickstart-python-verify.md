---
title: Краткое руководство по проверке Python существует в SQL Server
description: Краткое руководство по проверке существование Python и служб машинного обучения в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0a2c525c89a70f4a36749d7b9c6fb769362d517b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962047"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>Краткое руководство. Проверка наличия Python в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server включает поддержку языка Python для обработки и анализа аналитики данных в резидентных данных SQL Server. Выполнение скрипта является посредством хранимых процедур, используя один из следующих методов:

+ Встроенные [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) хранимую процедуру, передавая скрипт Python в качестве входного параметра.
+ Wrap скрипт Python в [пользовательская хранимая процедура](sqldev-in-database-r-for-sql-developers.md) , созданный.

В этом кратком руководстве вы проверите, [службы машинного обучения SQL Server 2017](../what-is-sql-server-machine-learning.md) установлен и настроен.

## <a name="prerequisites"></a>Предварительные требования

В этом упражнении требуется доступ к экземпляру SQL Server с [службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md) установлен.

Экземпляр SQL Server может быть в виртуальной машине Azure или локально. Только Имейте в виду, что внешние средства написания сценариев отключен по умолчанию, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедитесь, что **службы панели запуска SQL Server** запущен перед запуском.

Вам также необходимо средство для выполнения запросов SQL. Можно выполнить скрипты Python, с помощью любой базы данных управления или запроса средство, поскольку он может подключиться к экземпляру SQL Server и выполняется запрос T-SQL или хранимой процедуры. В этом кратком руководстве [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-python-exists"></a>Убедитесь, что существует Python

Можно проверить, службы машинного обучения (включен для экземпляра SQL Server и установленной версии Python. Выполните следующие действия.

1. Откройте SQL Server Management Studio и подключитесь к экземпляру SQL Server.

2. Запустите приведенный ниже код. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. Python `print` функция возвращает версию для **сообщений** окна. В приведенном ниже примере, вы увидите SQL Server в этом случае у версия Python 3.5.2 установлен.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

Если возникают ошибки, существует ряд вещей, которые можно сделать, чтобы убедиться, что экземпляр и Python может взаимодействовать.

Во-первых исключить любые проблемы установки. После установки настроек не требуется, чтобы включить использование библиотек внешнего кода. См. в разделе [установить SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md). Аналогичным образом Убедитесь, что запущена служба панели запуска.

Также необходимо добавить группу пользователей Windows `SQLRUserGroup` как имя для входа на экземпляре, чтобы убедиться, что панель запуска могут обеспечивать взаимодействие между кодом Python и SQL Server. (Той же группе используется для обоих R и выполнение кода Python). Дополнительные сведения см. в разделе [создать имя входа для SQLRUserGroup](../security/create-a-login-for-sqlrusergroup.md).

Кроме того может потребоваться включить сетевые протоколы, которые были отключены, или открыть брандмауэр SQL Server мог обмениваться данными с внешними клиентами. Дополнительные сведения см. в разделе [Устранение неполадок при установке](../common-issues-external-script-execution.md).

## <a name="call-revoscalepy-functions"></a>Вызов функций revoscalepy

Чтобы убедиться, что **revoscalepy** нет, выполните пример скрипта, включает в себя [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) , формирующий статистические сводных данных. Приведенный ниже сценарий демонстрируется извлечение данных xdf-пример в файл из встроенных примеры, включенные в revoscalepy. Предоставляет функцию RxOptions **sampleDataDir** параметр, который возвращает расположение файлов образца.

Поскольку rx_summary возвращает объект типа `class revoscalepy.functions.RxSummary.RxSummaryResults`, который содержит несколько элементов, можно использовать для извлечения только кадр данных в табличном формате pandas.

```sql
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

## <a name="list-python-packages"></a>Перечисление пакетов Python

Корпорация Майкрософт предоставляет ряд пакетов Python, предварительно установленные с помощью служб машинного обучения в вашем экземпляре SQL Server. Для просмотра списка Python, какие пакеты устанавливаются, включая версию, выполните следующие действия.

1. Запустите приведенный ниже сценарий в экземпляре SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. Выходные данные — от `pip.get_installed_distributions()` в Python и возвращаются в виде `STDOUT` сообщений.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    xlwt 1.2.0
    XlsxWriter 0.9.6
    xlrd 1.0.0
    win-unicode-console 0.5
    widgetsnbextension 2.0.0
    wheel 0.29.0
    Werkzeug 0.12.1
    wcwidth 0.1.7
    unicodecsv 0.14.1
    traitlets 4.3.2
    tornado 4.4.2
    toolz 0.8.2
    testpath 0.3
    tables 3.2.2
    sympy 1.0
    statsmodels 0.8.0
    sqlparse 0.1.19
    SQLAlchemy 1.1.9
    snowballstemmer 1.2.1
    six 1.10.0
    simplegeneric 0.8.1
    seaborn 0.7.1
    scipy 0.19.0
    scikit-learn 0.18.1
    ...
    ```

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы убедитесь, что экземпляр готов для работы с Python, внимательно ознакомьтесь собой базовый взаимодействие Python.

> [!div class="nextstepaction"]
> [Краткое руководство. Скрипт Python «Hello world» в SQL Server](quickstart-python-run-using-t-sql.md)
