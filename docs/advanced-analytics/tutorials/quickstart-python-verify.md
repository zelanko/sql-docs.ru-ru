---
title: Краткое руководство по проверке наличия Python в SQL Server
description: Краткое руководство по проверке существования Python и Службы машинного обучения в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 98e89cf61e5c53793108a455873382da00a8ea35
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715453"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>Краткое руководство. Проверка наличия Python в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server включает поддержку языка Python для анализа данных на резидентных SQL Server данных. Выполнение скрипта осуществляется с помощью хранимых процедур с использованием любого из следующих подходов:

+ Встроенная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) , передающая скрипт Python в качестве входного параметра.
+ Заключите скрипт Python в создаваемую [пользовательскую хранимую процедуру](sqldev-in-database-r-for-sql-developers.md) .

В этом кратком руководстве вы убедитесь, что [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md) установлен и настроен.

## <a name="prerequisites"></a>Предварительные требования

Для этого упражнения требуется доступ к экземпляру SQL Server с установленными [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) .

Ваш экземпляр SQL Server может находиться на виртуальной машине Azure или в локальной среде. Просто имейте в виду, что функция внешних скриптов по умолчанию отключена, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **Служба панель запуска SQL Server** запущена перед началом работы.

Вам также понадобится средство для выполнения SQL-запросов. Скрипты Python можно запускать с помощью любого средства управления базами данных или запросов, если оно может подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-python-exists"></a>Проверка существования Python

Вы можете убедиться, что Службы машинного обучения (включено для экземпляра SQL Server и какая версия Python установлена. Выполните следующие действия.

1. Откройте SQL Server Management Studio и подключитесь к экземпляру SQL Server.

2. Выполните приведенный ниже код. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. Функция Python `print` Возвращает версию в окно **сообщений** . В приведенном ниже примере выходных данных можно увидеть, что в SQL Server в этом случае установлен Python версии 3.5.2.

    **Результаты**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

При возникновении ошибок существует множество вещей, которые можно выполнить, чтобы убедиться, что экземпляр и Python могут обмениваться данными.

Прежде всего, устраните все проблемы установки. Настройка после установки необходима для включения использования библиотек внешних кодов. См. раздел [Install SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md). Аналогичным образом убедитесь, что служба панели запуска запущена.

Кроме того, необходимо добавить группу `SQLRUserGroup` пользователей Windows в качестве имени входа для экземпляра, чтобы панель запуска могла обеспечить взаимодействие между Python и SQL Server. (Для выполнения кода R и Python используется одна и та же группа.) Дополнительные сведения см. [в статье Создание имени входа для SQLRUserGroup](../security/create-a-login-for-sqlrusergroup.md).

Кроме того, может потребоваться включить отключенные сетевые протоколы или открыть брандмауэр, чтобы SQL Server могли взаимодействовать с внешними клиентами. Дополнительные сведения см. в разделе [Устранение неполадок в программе установки](../common-issues-external-script-execution.md).

## <a name="call-revoscalepy-functions"></a>Вызов функций revoscalepy

Чтобы убедиться, что **revoscalepy** доступен, запустите пример скрипта, включающий [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) , который создает статистические сводные данные. В приведенном ниже сценарии показано, как извлечь файл данных sample. Xdf-из встроенных примеров, входящих в revoscalepy. Функция Рксоптионс предоставляет параметр **сампледатадир** , возвращающий Расположение образцов файлов.

Поскольку rx_summary возвращает объект типа `class revoscalepy.functions.RxSummary.RxSummaryResults`, который содержит несколько элементов, можно использовать Pandas для извлечения только фрейма данных в табличном формате.

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

## <a name="list-python-packages"></a>Вывод списка пакетов Python

Корпорация Майкрософт предоставляет ряд пакетов Python, предварительно устанавливаемых с Службы машинного обучения в экземпляре SQL Server. Чтобы просмотреть список установленных пакетов Python, включая версию, выполните следующие действия.

1. Выполните приведенный ниже скрипт на экземпляре SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. Выходные данные выводятся `pip.get_installed_distributions()` в Python и возвращаются `STDOUT` в виде сообщений.

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

Теперь, когда ваш экземпляр готов к работе с Python, внимательно ознакомьтесь с простым взаимодействием Python.

> [!div class="nextstepaction"]
> [QuickStart Сценарий Python "Hello World" в SQL Server](quickstart-python-run-using-t-sql.md)
