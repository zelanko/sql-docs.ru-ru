---
title: Настройка клиентских средств Python для использования с помощью машинного обучения SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6f6823870060992586756dffa93aac6937d27d65
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "40401304"
---
# <a name="set-up-python-client-tools-for-use-with-sql-server-machine-learning"></a>Настройка Python клиентские средства для использования с помощью машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция Python впервые появился в SQL Server 2017 или более поздней версии, при добавлении поддержки Python для служб машинного обучения (в базе данных). Дополнительные сведения см. в разделе [установить SQL Server служб машинного обучения](../install/sql-machine-learning-services-windows-install.md).

В этой статье сведения о настройке рабочих станций для разработки, таким образом, можно подключиться к удаленному серверу SQL включена для Python.

### <a name="evaluation-and-independent-development"></a>Оценка и независимая Разработка
 
Если у вас есть developer edition и план, чтобы локально поработать над скрипт Python, планируется переместить в SQL Server, вы можете сразу перейти к [Установка IDE](#install-ide) и указать средству локальных библиотек Python, используемый сервером SQL Server.

> [!Tip]
> Для демонстрации и видеоруководство, см. в разделе [выполнения R и Python удаленно, в SQL Server из записных книжек Jupyter или любой интегрированной среде разработки](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) или это [видео YouTube](https://youtu.be/D5erljpJDjE).

## <a name="1---install-python-packages"></a>1 - Установка пакетов Python

Локальных рабочих станциях должны быть одинаковые версии пакета Python как на SQL Server: revoscalepy и microsftml. Дополнительные пакеты Python доступны, но обычно используется в других сценариях, в контексте Machine Learning Server автономные (не экземпляр). 

1. Загрузите сценарий установки из [ https://aka.ms/mls93-py ](https://aka.ms/mls93-py) (или используйте [ https://aka.ms/mls-py ](https://aka.ms/mls-py) для 9.2. выпуск). Скрипт установит Anaconda 4.2.0, включающий Python 3.5.2, а также все пакеты, перечисленные ранее.

  Компоненты Python предоставляются через [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033). Если требуется другой версии, см. в разделе [загрузки CAB-файла](../install/sql-ml-cab-downloads.md)

2. Откройте окно PowerShell с повышенными полномочиями администратора (щелкните правой кнопкой мыши **Запуск от имени администратора**).

3. Перейдите в папку, в которой вы скачали установщик и выполните скрипт. Добавление `-InstallFolder` аргумент командной строки, чтобы указать расположение папки для библиотек. Пример: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls")
   ```

   Установка займет некоторое время. Вы можете отслеживать ход выполнения в окне PowerShell. По завершении установки у вас есть полный набор пакетов. Например, если вы указали `C:\mspythonlibs` как имя папки, необходимо найти пакеты с `C:\mspythonlibs\Lib\site-packages`. В противном случае по умолчанию используется `C:\Program Files\Microsoft\PyForMLS1`.

Сценарий установки не изменяет переменную среды PATH на компьютере, поэтому нового интерпретатора python и модули, которые вы только что установили недоступны автоматически для ваши средства. Справочные сведения о связывании интерпретатора и библиотек Python к средствам, см. в разделе [5 — Установка IDE](#install-ide).

<a name="python-tool"></a>
 
## <a name="2---open-a-python-prompt"></a>2 - откройте строку Python

Интеграция Python в Microsoft включает в себя встроенные средства и данные в дополнение к определенному продукту библиотек, таких как revoscalepy и microsoftml. Доступны следующие элементы на экземплярах сервера и клиента после завершения установки:

+ Образец данных Python
+ Дистрибутив anaconda 4.2 
+ Python.exe исполняемые файлы Python и pythonw.exe

> [!Tip] 
> Мы рекомендуем [Python для Windows часто задаваемые вопросы о](https://docs.python.org/3/faq/windows.html) purppose Общие сведения о запуске программы Python в Windows.

### <a name="on-client-workstations"></a>На клиентских рабочих станциях

Чтобы использовать исполнимого файла Python, установленного в сценарии установки:

1. Перейдите к `C:\Program Files\Microsoft\PyForMLS\python.exe` или любое расположение, выбранное для пути установки.

2. Щелкните правой кнопкой мыши **Python.exe** и выберите **Запуск от имени администратора** открыть интерактивное окно командной строки.

### <a name="on-sql-server"></a>На сервере SQL Server

Программа установки SQL Server добавляет стандартные средства Python и ресурсы, к экземпляру сервера. Если вы используете выпуск developer edition и нужно проверить версию Python или выполнить специальные команды:

1. Перейдите к `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

2. Щелкните правой кнопкой мыши **Python.exe** и выберите **Запуск от имени администратора** открыть интерактивное окно командной строки.

> [!Note]
> Как правило, чтобы избежать конфликта ресурсов, мы рекомендуем вам **не** запустите Python из библиотеки экземпляра на сервере, если вы считаете, что возможно экземпляр SQL Server выполняется код Python. Тем не менее с помощью средств в библиотеке экземпляр может быть полезен, если вы пытаетесь отладить проблему, которая возникает только при работе в SQL Server и нужно просмотреть более подробные сообщения об ошибках, или убедитесь, что установлены все необходимые пакеты.

## <a name="3---permissions"></a>3 - разрешения

Чтобы подключиться к экземпляру SQL Server для выполнения скриптов и отправки данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, что с помощью имени входа SQL проще для некоторых сценариев.

Как минимум учетная запись, используемая для запуска кода необходимо иметь разрешение на чтение из базы данных, вы работаете, а также специальное разрешение Выполнение ЛЮБОГО ВНЕШНЕГО СКРИПТА. Большинство разработчиков также требуются разрешения на создание новых объектов в виде хранимых процедур, содержащий скрипт и записывать данные в таблицы, содержащий данные для обучения или оценки данных. 

Обратитесь к администратору базы данных, чтобы настроить следующие разрешения для учетной записи, в базе данных, где используется Python:

+ **EXECUTE ANY EXTERNAL SCRIPT** для запуска Python на сервере.
+ **db_datareader** привилегий для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи данных для обучения или оценки данных.
+ **db_owner** для создания объектов, таких как хранимые процедуры, таблицы, функции. 
  Необходимо также **db_owner** создавать пример и тестирования базы данных. 

Если код требует пакеты, которые не устанавливаются по умолчанию вместе с SQL Server, упорядочить администратору базы данных, чтобы получить пакеты, установленные с экземпляром. SQL Server является безопасной среде и существуют ограничения на установки пакетов. Ad hoc установку пакетов как часть кода не рекомендуется, даже если вы обладаете правами. Кроме того всегда внимательно рассмотрите влияние на безопасность, прежде чем устанавливать новые пакеты в библиотеке server.

## <a name="4---test-connections"></a>4 - Тестирование подключений

После установки всех средств и библиотек, необходимо подключиться к серверу и убедитесь, что можно создать контекст вычисления, или что Python может взаимодействовать с SQL Server.

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Убедитесь, что этот revoscalepy работает из командной строки Python

Чтобы убедиться, что **revoscalepy** модуль может быть загружен, запустите следующий образец кода из интерактивной командной строки Python. Код создает сводку данных, с данными, Python и [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). 

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

Путь к данным примера выводится, чтобы можно было определить, какой экземпляр Python, вызывается.

### <a name="verify-that-python-can-be-called-from-a-local-sql-server"></a>Убедитесь, что Python может вызываться из локального SQL Server

В среде локальной разработки, убедитесь, что Python взаимодействует с локальным [экземпляра SQL Server, настроенного для внешних сценариев](../install/sql-machine-learning-services-windows-install.md). Используйте SQL Server Management Studio, чтобы открыть новое **запроса** и выполните команду любой простой Python команды в контексте хранимой процедуры:

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

Может занять некоторое время для запуска среды выполнения Python в первый раз, но при отсутствии ошибок, вы знаете, что панель запуска SQL Server работает, и Python можно запустить из SQL Server.

Чтобы убедиться, что **revoscalepy** доступна в библиотеке экземпляра SQL Server, запустите сценарий на основе [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary), с некоторыми небольшими изменениями, для формирования результатов, совместимые с SQL Server. 

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

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>Проверьте выполнение Python в SQL Server в удаленном контексте вычисления

Если вы установили **revoscalepy** в локальной среде разработки Python, должны иметь возможность подключения к удаленному экземпляру SQL Server 2017, где включен Python и выполнить аналогичные пример кода с помощью сервера как контекст вычислений. 

Для выполнения сценария укажите допустимое имя сервера и базы данных. Этого сценария не использует базу данных, но строка подключения требует его.

```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=<server-name>;Database=TestDB;Trusted_Connection=True"
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

В этом образце сводки объект возвращается консоли, а не возвращающие табличные данные правильного для SQL Server. 

Кроме того поскольку [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) был вызван, образец данных загружается из папки samples на компьютере SQL Server, а не из папки локального samples.


<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5 — Установка IDE

Просто при отладке скриптов из командной строки, можно получить с помощью стандартных инструментов Python. Тем не менее если вы разрабатываете новые решения, или работа с удаленного клиента, рекомендуется использовать полнофункциональную среду IDE Python. Популярные доступны следующие действия:

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) с Python
+ [Средства ии для Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python в Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
+ Популярные сторонние средства, такие как PyCharm, Spyder и Eclipse

Мы рекомендуем Visual Studio, так как он поддерживает проекты базы данных, а также проектов службы машинного обучения. Помощь по настройке среды Python, см. в разделе [управление средами Python в Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

Поскольку разработчики часто работают с несколькими версиями Python, установки не добавляет путь к Python. Чтобы использовать исполняемый файл Python и библиотеки, установленные программой установки, связать IDE и **Python.exe** по пути, который также обеспечивает revoscalepy и microsoftml. Например, для проекта Python в Visual Studio, своей пользовательской среды указать `C:\Program Files\Microsoft\PyForMLS`, `C:\Program Files\Microsoft\PyForMLS\python.exe` и `C:\Program Files\Microsoft\PyForMLS\pythonw.exe` для **префикс пути**, **интерпретатор путь**и  **Оконный интерпретатор**, соответственно.

Дополнительные сведения см. в разделе [инструменты Python ссылку и интегрированными средами разработки](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Данная статья написана для Microsoft Machine Learning Server, отличаются пути Python, но показано создание ссылок на библиотеки Python с помощью различных средств.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда у вас есть средства и работающее подключение к SQL Server, пройдите по учебнику, чтобы рассмотреть функции revoscalepy и переключении контекста вычислений.

> [!div class="nextstepaction"]
> [Создание модели с помощью revoscalepy и контекст удаленных вычислений](../tutorials/use-python-revoscalepy-to-create-model.md)