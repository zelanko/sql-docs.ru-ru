---
title: Настройка клиентских средств Python для использования с SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/13/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: python
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: c0054fd0dc9ecb3dbf9035ddff0f6828a85b471d
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="set-up-python-client-tools-for-use-with-sql-server"></a>Настройка Python клиентские средства для работы с SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается настройка среды Python на компьютере Windows, чтобы поддерживать выполнение кода Python в SQL Server. Сюда входят следующие сценарии:

+ Тестировать и разрабатывать решения на удаленной рабочей станции Python и отправить код в SQL Server для выполнения в контексте вычислений SQL Server. 

    Как правило, требуется установить полнофункциональную среду разработки Python. 
    
    Локальной среде Python должен быть совместимым с среды Python в экземпляре SQL Server, и необходимо установить библиотеки, поддерживающие контекстах удаленных вычислений.

+ Создание и тестирование кода с помощью выделенного средства Python и затем перенести код в SQL Server для запуска в хранимой процедуре.

    Для разработки сервера использовать полнофункциональную среду IDE Python. Однако прежде чем развертывать код, проверить его в среде, эмулирующее среду SQL Server.

+ В основном выполнять код Python в хранимой процедуре в SQL Server, и вы не разрабатываете кода Python. Предполагается, что код тестирования и отладки, прежде чем поместить его в хранимой процедуре. Однако иногда может потребоваться выполнение кода за пределами SQL Server, чтобы определить источник проблемы.

    Вы не хотите устанавливать любые инструменты Python на сервере и будет использовать установлены с распределением средства по умолчанию. Вы можете настроить среду Python, использующего библиотеку экземпляра, чтобы убедиться, что код работает вне хранимой процедуры.

## <a name="requirements"></a>Требования

Независимо от того, какие инструменты можно использовать для разработки кода Python каждый раз выполнять код Python в SQL Server или использовать данные SQL Server предъявляются следующие требования:

+ Чтобы использовать Python, требуется SQL Server 2017 или более поздней версии. Необходимо также установить функцию, которая поддерживает службы обучения машины (в базе данных) и явно включить компонент. Дополнительные сведения см. в разделе [Настройка 2017 г. SQL Server](../r/set-up-sql-server-r-services-in-database.md).

    Если вы установили более раннего выпуска 2017 г. SQL Server, могут возникнуть ошибки при попытке выполнения команд Python из этой служебной программы командной строки. Мы рекомендуем вам [обновление до последней версии](#bkmk_update) по возможности. 

+ Необходимо убедиться, что учетная запись, используемая для запуска кода имеет разрешения для подключения к базе данных, а также для выполнения кода Python. Специальное разрешение `EXECUTE ANY EXTERNAL SCRIPT` является обязательным для всех учетных записей, использующих скрипт R или Python. 

+ Необходимо убедиться, что учетная запись имеет все разрешения базы данных, которые могут быть необходимы для чтения данных или создавать новые объекты. 

+ Если код требует выполнения пакетов, которые не устанавливаются по умолчанию вместе с SQL Server, упорядочите администратору базы данных, чтобы получить пакеты, установленные в среде Python, который используется экземпляром. SQL Server является безопасной среде, и существуют ограничения на установки пакетов. 

    Нерегламентированные пакеты как часть кода не рекомендуется установить, даже при наличии прав. Кроме того всегда внимательно рассмотрите влияние на безопасность, прежде чем устанавливать новые пакеты в библиотеке server.

> [!NOTE]
> Если вы собираетесь использовать Python с сервером машины обучения, который поддерживает дополнительные вычисления контекстах, например в Linux или Spark кластеров, см. в следующих статьях:
> 
> + [Как установить пользовательские пакеты Python и интерпретатора локально в Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)
> + [Связать интерпретатор Python, установленным сервером обучения машины Python tools и среды разработки](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)

## <a name="default-tools-included-with-standard-install"></a>По умолчанию средства, включенные в стандартной установке

Установка по умолчанию 2017 г. SQL Server с компьютера-службами обучения (в базе данных) и Python добавляет следующие стандартные средства Python и ресурсы:

+ Образец данных Python
+ Дистрибутив anaconda 4.2 
+ Исполняемые файлы python.exe Python и pythonw.exe

По умолчанию — установка в эту папку: `~\Program Files\Microsoft SQL Server\<instance_name>\PYTHON_SERVICES`. 

## <a name="open-python-from-the-command-line"></a>Откройте Python из командной строки 

Для использования среды выполнения Python, которая устанавливается с экземпляром, можно запустить исполняемый файл Python в пути установки. Основные инструкции доступны на [Python для Windows часто задаваемые вопросы о](https://docs.python.org/3/faq/windows.html).

> [!IMPORTANT]
> Как правило, чтобы избежать конфликта ресурсов, рекомендуется, чтобы вы **не** запустить Python из библиотеки экземпляра на сервере, если вы считаете, что возможно экземпляр SQL Server выполняется код Python. Однако с помощью средства в библиотеке экземпляр может быть полезен, если вы пытаетесь отладить проблему, которая возникает только при использовании в SQL Server и для просмотра подробных сообщений об ошибках или убедитесь, что установлены все необходимые пакеты.

1. Перейдите в папку, где установлен экземпляр библиотеки. Например, при установке по умолчанию является `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

2. Найдите Python.exe. 

3. Щелкните правой кнопкой мыши и выберите **Запуск от имени администратора** открыть интерактивное окно командной строки.

## <a name="bkmk_update"></a> Обновление компонентов Python

Можно обновить компоненты Python, загрузив и установив более поздней версии, используя сценарий, описанный здесь: [Python установки клиента в Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter#install-on-windows)
> 
> Используется для загрузки скрипта установщик [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033). Если требуется другая версия, см. раздел [Установка компонентов обучения компьютер без доступа к Интернету](http://bing.com)

## <a name="set-up-a-python-development-environment"></a>Настройка среды разработки Python

Просто отладки скриптов из командной строки, можно решить с помощью стандартных средств Python со службами обучения компьютера или в текстовом редакторе. Тем не менее если при разработке новых решений или при работе с удаленного клиента, рекомендуется использовать полнофункциональную среду IDE Python. Ниже приведены часто используемых параметров.

+ [Visual Studio Community Edition 2017 г](https://www.visualstudio.com/vs/features/python/) с Python
+ [AI средства для Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python в коде Visual Studio](https://code.visualstudio.com/docs/languages/python)
+ Популярные сторонние средства, такие как PyCharm, Spyder и Eclipse

Корпорация Майкрософт рекомендует Visual Studio, так как он поддерживает проекты базы данных, а также в проектах обучения машины. Дополнительные сведения о настройке среды Python см [среды управления Python в Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

## <a name="install-revoscalepy"></a>Установить revoscalepy

Даже при успешной установке службы обучения компьютера может появиться ошибка при попытке загрузить **revoscalepy** функции из командной строки Python. Эти шаги описывают, как можно установить обновление для использования **revoscalepy**.

1. Загрузить сценарий установки из https://aka.ms/mls93-py (или использовать https://aka.ms/mls-py для 9.2. выпуск). Скрипт устанавливает Anaconda 4.2.0, включая Python 3.5.2, а также все пакеты, перечисленные ранее.

2. Открытие нового окна PowerShell с повышенными разрешениями (администратор).

3. Откройте папку, куда была загружена программа установки и запуска сценария:

```ps1
cd {{download-directory}}
.\Install-PyForMLS.ps1
```

Можно также запустить `-InstallFolder` аргумент командной строки и укажите новый путь, как часть команды. Например: 

```ps1
.\Install-PyForMLS.ps1 -InstallFolder "<installation_path>")
```

Если возникает сообщение об ошибке, может потребоваться приостановить политики выполнения для конкретного файла, в течение сеанса, следующим образом: 

```ps1
powershell -ExecutionPolicy Bypass -File "C:\<installation_path>\Install-PyForMLS.ps1"
```

Также можно приостановить выполнение политик в течение всего сеанса. При использовании этой инструкции политики выполнения задано значение `Unrestricted` в течение сеанса и не изменяет конфигурацию и записи изменений на диск.

```ps1
Set-ExecutionPolicy Bypass -Scope Process
```

## <a name="verify-that-python-and-revoscalepy-are-working"></a>Проверьте работоспособность Python и revoscalepy

После установки всех средств и библиотек, необходимо подключиться к серверу и убедитесь, вы можете создать контекст вычислений или Python можно обмениваться данными с SQL Server.

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Убедитесь, что работает, revoscalepy из командной строки Python

Чтобы убедиться, что **revoscalepy** модуль может быть загружен, выполните в следующем образце кода Python интерактивной командной. Код приводит к возникновению ошибки Сводка данных, используя данные образца Python и [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). 

```Python
import os
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

Образец пути данных выводится на печать, чтобы определить, какой экземпляр Python, вызывается.

### <a name="verify-that-python-can-be-called-from-sql-server"></a>Убедитесь, что Python можно вызвать из SQL Server

Чтобы убедиться, что Python взаимодействует с SQL Server, откройте SQL Server Management Studio. (Например, можно использовать другое аналогичное средство [операций SQL Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is).) Откройте новый **запроса** и выполните команду любой простой Python в контексте хранимой процедуры:

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

Он может занять некоторое время для запуска среды выполнения Python в первый раз, но если ошибок нет, известно, что работа панели запуска SQL Server и Python можно запустить из SQL Server.

Чтобы убедиться, что **revoscalepy** доступна в библиотеке, экземпляр SQL Server, запустите сценарий на основе [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary), с некоторые небольшие изменения для формирования результатов, совместимые с SQL Server. 

```SQL
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

Поскольку rx_summary возвращает объект типа `class revoscalepy.functions.RxSummary.RxSummaryResults`, который содержит несколько элементов, для обработки результатов в SQL Server, можно извлечь только кадр данных в табличном формате.

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>Проверка выполнения Python в SQL Server в качестве контекста удаленных вычислений.

Если вы установили **revoscalepy** в локальной среде разработки Python, должен иметь возможность подключения к экземпляру SQL Server 2017 г., где была включена Python и выполнение аналогичные примера кода, используя сервер в качестве вычислительных контекст. 


```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=;Database=TestDB;Trusted_Connection=True"
sqlcc = RxInSqlServer(
    connection_string = sql_conn_string,
    num_tasks = 1,
    auto_cleanup = False,
    console_output = True,
    execution_timeout_seconds = 0,
    wait = True
    )
rx_set_compute_context(sqlcc)

# get sample data and path
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

# generate summary
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

В этом образце сводки объект возвращается консоли, а не возвращение правильного формата табличных данных в SQL Server. 

Кроме того поскольку [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) был вызван, образец данных загружается из папки образцов на сервере SQL Server, а не из папки локальной samples.
