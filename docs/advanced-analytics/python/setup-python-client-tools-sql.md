---
title: Настройка клиента обработки и анализа данных для разработки Python - машинного обучения SQL Server
description: Настройка локальной среды Python (записная книжка Jupyter или PyCharm) для удаленных подключений для службы машинного обучения SQL Server с помощью Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 569b3d2fbd11cc978f1a810bab6b30ec1d33d2b5
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046534"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Настройка клиента обработки и анализа данных для разработки Python для службы машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция Python доступен, начиная с SQL Server 2017 или более поздней версии, при включении параметра Python в [установки служб машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md). 

Для разработки и развертывания решений Python для SQL Server следует установить корпорации Майкрософт [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и других библиотек Python рабочей станции разработки. Библиотека revoscalepy, который также является на удаленном экземпляре SQL Server, координирует вычислительной запросы между обеих систем. 

В этой статье сведения о настройке рабочей станции разработки Python, так что вы можете взаимодействовать с удаленный экземпляр SQL Server для машинного обучения и интеграция Python. После выполнения действий, описанных в этой статье, вы получите те же библиотеки Python, как на SQL Server. Также будет знать, как принудительно отправлять вычисления из локального сеанса Python к удаленному сеансу Python на сервере SQL Server.

![Клиент серверные компоненты](media/sqlmls-python-client-revo.png "локальные и удаленные сеансы Python и библиотек")

Чтобы проверить установку, можно использовать встроенные записные книжки Jupyter, как описано в этой статье или [привязывать библиотеки](#install-ide) PyCharm или любой другой интегрированной среде разработки, которое вы обычно используете.

> [!Tip]
> Видеозапись с демонстрацией упражнений, см. в разделе [выполнения R и Python удаленно в SQL Server из записных книжек Jupyter](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/).

> [!Note]
> Вместо установки библиотеки клиента использует [изолированный сервер](../install/sql-machine-learning-standalone-windows-install.md) качестве полнофункционального клиента, что некоторые клиенты предпочитают для более глубокого работы сценария. Автономный сервер полностью отделен от SQL Server, но так как он имеет те же библиотеки Python, можно использовать его как клиент для анализа в базе данных SQL Server. Вы также можно использовать для работы, не относящиеся к SQL, включая возможность импортировать и моделирование данных с других платформ данных. При установке изолированного сервера, можно найти исполняемый файл Python в этом месте: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Проверить установку, [откройте записную книжку Jupyter](#python-tools) для выполнения команд, с помощью Python.exe в этом расположении.

## <a name="commonly-used-tools"></a>Широко используемых средств

Какой бы ни разработчик Python, знакомы с SQL или разработчиков на SQL, которые работали с Python и аналитики в базе данных, необходимо будет средство разработки Python и редактор T-SQL-запросов такие как [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) соблюдать все возможности аналитики в базе данных.

Для разработки Python можно использовать Jupyter Notebook, которые были включены в дистрибутив Anaconda, устанавливаемые с SQL Server. В этой статье объясняется, как запустить записные книжки Jupyter, чтобы обеспечить возможность выполнения кода Python локально и удаленно на сервере SQL Server.

SSMS является отдельной загрузкой, используются для создания и выполнения хранимых процедур на сервере SQL Server, в том числе с кодом Python. Практически любой код Python, добавленные в записные книжки Jupyter можно встроить в хранимой процедуре. Можно пошагово выполнить другие краткие руководства, чтобы узнать о [SSMS и embedded Python](../tutorials/quickstart-python-verify.md).

## <a name="1---install-python-packages"></a>1 - Установка пакетов Python

Локальных рабочих станциях должны быть одинаковые версии пакета Python как на SQL Server, включая базовый Anaconda 4.2.0 с дистрибутив Python 3.5.2 и пакетов, характерные для Майкрософт.

Скрипт установки добавляет три библиотеки Microsoft для клиента Python. Скрипт устанавливает [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), которое используется для определения объектов источника данных и контекста вычислений. Он устанавливает [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) предоставляя алгоритмов машинного обучения. [Azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) пакета также устанавливается, но применяется для ввода в эксплуатацию задачи, связанные с контекстом Machine Learning Server автономные (не экземпляр) и могут быть малополезны для аналитики в базе данных.

1. Скачайте скрипт установки.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) Устанавливает версию 9.2.1 пакеты Microsoft Python. Эта версия соответствует экземпляр SQL Server 2017 по умолчанию. 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) Устанавливает пакеты Microsoft Python версии 9.3. Эта версия является хорошим выбором, если удаленный экземпляр SQL Server 2017 [привязан к Machine Learning Server 9.3](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

2. Откройте окно PowerShell с повышенными полномочиями администратора (щелкните правой кнопкой мыши **Запуск от имени администратора**).

3. Перейдите в папку, в которой вы скачали установщик и выполните скрипт. Добавление `-InstallFolder` аргумент командной строки, чтобы указать расположение папки для библиотек. Пример: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Если опустить в папку установки по умолчанию — C:\Program Files\Microsoft\PyForMLS.

Установка займет некоторое время. Вы можете отслеживать ход выполнения в окне PowerShell. По завершении установки у вас есть полный набор пакетов. 

> [!Tip] 
> Мы рекомендуем [Python для Windows часто задаваемые вопросы о](https://docs.python.org/3/faq/windows.html) purppose Общие сведения о запуске программы Python в Windows.

## <a name="2---locate-executables"></a>2 - поиск исполняемых файлов

По-прежнему в PowerShell список содержимого папки установки для подтверждения установки Python.exe, сценарии и другие пакеты. 

1. Введите `cd \` чтобы перейти на корневой диск, а затем введите путь, указанный для `-InstallFolder` на предыдущем шаге. Если опустить этот параметр во время установки, по умолчанию используется `cd C:\Program Files\Microsoft\PyForMLS`.

2. Введите `dir *.exe` списка исполняемых файлов. Вы должны увидеть **python.exe**, **pythonw.exe**, и **удаление anaconda.exe**.

  ![Список исполняемых файлов Python](media/powershell-python-exe.png)
   
В системах наличию нескольких версий Python, не забудьте использовать этой конкретной Python.exe в том случае, если вы хотите загрузить **revoscalepy** и другие пакеты Microsoft.

> [!Note] 
> Сценарий установки не изменяет переменную среды PATH на компьютере, это означает, что нового интерпретатора python и модули, которые вы только что установили недоступны автоматически для других средств, которые могут возникнуть. Справочные сведения о связывании интерпретатора и библиотек Python к средствам, см. в разделе [Установка IDE](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3 - записные книжки Jupyter на open

Anaconda включает записные книжки Jupyter. На следующем шаге создайте записную книжку и выполнять определенный код Python, содержащий библиотеки, который вы только что установлен.

1. В командной строке Powershell по-прежнему в каталоге C:\Program Files\Microsoft\PyForMLS откройте записные книжки Jupyter из папки скриптов:

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  Следует открыть записную книжку в браузере по умолчанию в `https://localhost:8889/tree`.

  Другой способ — дважды щелкните **jupyter notebook.exe**. 

2. Нажмите кнопку **New** и нажмите кнопку **Python 3**.

  ![записная книжка jupyter с выбором нового Python 3](media/jupyter-notebook-new-p3.png)

3. Введите `import revoscalepy` и выполните команду, чтобы нагрузки одной из библиотек характерные для Майкрософт.

4. Введите и запустите `print(revoscalepy.__version__)` для возврата сведений о версии. Вы должны увидеть 9.2.1 или 9.3.0. Можно использовать одну из этих версий с [revoscalepy на сервере](../r/determine-which-packages-are-installed-on-sql-server.md#get-package-vers). 

4. Введите ряд более сложных инструкций. Этот пример создает сводную статистику с помощью [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) для локального набора данных. Другие функции, получить сведения о расположении образцов данных и создания объекта источника данных для локального xdf-файл.

  ```python
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

На следующем рисунке показан ввод и часть выходных данных усекаются для краткости.

  ![записная книжка jupyter, показывающий revoscalepy входные и выходные данные](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4 - получение разрешений SQL

Чтобы подключиться к экземпляру SQL Server для выполнения скриптов и отправки данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, что с помощью имени входа SQL проще для некоторых сценариев, особенно в том случае, если скрипт содержит строки подключения к внешним данным.

Как минимум учетная запись, используемая для запуска кода необходимо иметь разрешение на чтение из базы данных, вы работаете, а также специальное разрешение Выполнение ЛЮБОГО ВНЕШНЕГО СКРИПТА. Большинство разработчиков также требуются разрешения для создания хранимых процедур и для записи данных в таблицы, содержащие данные для обучения или оценки данных. 

Попросите администратора базы данных [настроить следующие разрешения для учетной записи](../security/user-permission.md), в базе данных, где используется Python:

+ **EXECUTE ANY EXTERNAL SCRIPT** для запуска Python на сервере.
+ **db_datareader** привилегий для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи данных для обучения или оценки данных.
+ **db_owner** для создания объектов, таких как хранимые процедуры, таблицы, функции. 
  Необходимо также **db_owner** создавать пример и тестирования базы данных. 

Если код требует пакеты, которые не устанавливаются по умолчанию вместе с SQL Server, упорядочить администратору базы данных, чтобы получить пакеты, установленные с экземпляром. SQL Server является безопасной среде и существуют ограничения на установки пакетов. Ad hoc установку пакетов как часть кода не рекомендуется, даже если вы обладаете правами. Кроме того всегда внимательно рассмотрите влияние на безопасность, прежде чем устанавливать новые пакеты в библиотеке server.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5 - Создание тестовых данных

При наличии разрешений на создание базы данных на удаленном сервере, можно выполнить следующий код, чтобы создать демонстрационной базы данных Iris, используемые для оставшихся шагов в этой статье.

### <a name="1---create-the-irissql-database-remotely"></a>1 - Создание базы данных irissql удаленно

```python
import pyodbc

# creating a new db to load Iris sample in
new_db_name = "irissql"
connection_string = "Driver=SQL Server;Server=localhost;Database={0};Trusted_Connection=Yes;" 
                        # you can also swap Trusted_Connection for UID={your username};PWD={your password}
cnxn = pyodbc.connect(connection_string.format("master"), autocommit=True)
cnxn.cursor().execute("IF EXISTS(SELECT * FROM sys.databases WHERE [name] = '{0}') DROP DATABASE {0}".format(new_db_name))
cnxn.cursor().execute("CREATE DATABASE " + new_db_name)
cnxn.close()

print("Database created")
```

### <a name="2---import-iris-sample-from-sklearn"></a>2 - Импорт примера классификации цветков ириса из SkLearn

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3 - использование Revoscalepy API-интерфейсы для создания таблицы и загрузки данных Iris

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6 - test удаленного подключения

Перед попыткой на следующем шаге, убедитесь, что у вас есть разрешения на экземпляре SQL Server, а также строку подключения к [образца базы данных Iris](../tutorials/demo-data-iris-in-sql.md). Если база данных не существует и у вас достаточно разрешений, вы можете [создать базу данных с помощью следующей процедуры встроенный](#create-iris-remotely).

Замените строку подключения с допустимыми значениями. В примере кода используется `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` , но ваш код должен указать удаленный сервер, возможно с именем экземпляра, а параметр credential, который сопоставляется имя входа пользователя базы данных.

### <a name="define-a-function"></a>Определить функцию

Следующий код определяет функцию, которая будет отправлять для SQL Server на более позднем этапе. При выполнении, в нем данных и библиотек (revoscalepy, pandas, matplotlib) на удаленном сервере для создания точечных диаграмм набора данных iris. Он возвращает bytestream .png записные книжки Jupyter для подготовки к просмотру в браузере.

```python
def send_this_func_to_sql():
    from revoscalepy import RxSqlServerData, rx_import
    from pandas.tools.plotting import scatter_matrix
    import matplotlib.pyplot as plt
    import io
    
    # remember the scope of the variables in this func are within our SQL Server Python Runtime
    connection_string = "Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"
    
    # specify a query and load into pandas dataframe df
    sql_query = RxSqlServerData(connection_string=connection_string, sql_query = "select * from iris_data")
    df = rx_import(sql_query)
    
    scatter_matrix(df)
    
    # return bytestream of image created by scatter_matrix
    buf = io.BytesIO()
    plt.savefig(buf, format="png")
    buf.seek(0)
    
    return buf.getvalue()
```

### <a name="send-the-function-to-sql-server"></a>Отправить функции в SQL Server

В этом примере создания контекста удаленных вычислений и затем отправить выполнение функции в SQL Server с [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). **Rx_exec** функция может быть полезна, поскольку она принимает контекст вычислений в качестве аргумента. Любая функция, которая будет выполняться удаленно должен иметь аргумент контекста вычислений. Некоторые функции, такие как [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) непосредственно поддерживают этот аргумент. Для операций, которые не могут использовать **rx_exec** для доставки кода в контексте удаленных вычислений.

В этом примере нет необработанных данных было перенести из SQL Server в записной книжке Jupyter. Все вычисления происходят в базе данных Iris, и клиенту возвращается только файл изображения.

```python
from IPython import display
import matplotlib.pyplot as plt 
from revoscalepy import RxInSqlServer, rx_exec

# create a remote compute context with connection to SQL Server
sql_compute_context = RxInSqlServer(connection_string=connection_string.format(new_db_name))

# use rx_exec to send the function execution to SQL Server
image = rx_exec(send_this_func_to_sql, compute_context=sql_compute_context)[0]

# only an image was returned to my jupyter client. All data remained secure and was manipulated in my db.
display.Image(data=image)
```

На следующем рисунке показаны входные данные и точечных выходные данные построения.

  ![Отображение выходных данных построения точечной записной книжки jupyter](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7 — запуск Python с помощью средств

Поскольку разработчики часто работают с несколькими версиями Python, установки не добавляет путь к Python. Чтобы использовать исполняемый файл Python и библиотеки, установленные программой установки, связать IDE и **Python.exe** по пути, который также обеспечивает **revoscalepy** и **microsoftml**. 

### <a name="command-line"></a>Командная строка

При запуске **Python.exe** из C:\Program Files\Microsoft\PyForMLS (или любое расположение, указанное для установки библиотеки клиента Python), у вас есть доступ к полной дистрибутив Anaconda, а также Microsoft Python модули, **revoscalepy** и **microsoftml**.

1. Перейдите к C:\Program Files\Microsoft\PyForMLS **Python.exe**.
2. Откройте интерактивную систему помощи: `help()`
3. Введите имя модуля в командной строке справки: `help> revoscalepy`. Справка возвращает имя, содержимое пакета, версию и расположение файла.
4. Возвращает сведения о версии и пакета в **Справка >** строки: `revoscalepy`. Несколько раз нажмите клавишу ВВОД для выхода из справки.
5. Импорт модуля: `import revoscalepy`


### <a name="jupyter-notebooks"></a>Записные книжки Jupyter

В этой статье использует встроенные записные книжки Jupyter для демонстрации вызовов функции **revoscalepy**. Если вы не знакомы с это средство, следующем снимке экрана показано, как сочетаются друг с другом, и поэтому все «просто работает». 

Родительская папка C:\Program Files\Microsoft\PyForMLS содержит Anaconda, а также пакеты корпорации Майкрософт. Записные книжки Jupyter в состав программы Anaconda, в папку Scripts и исполняемые файлы Python, автоматически зарегистрирован с записными книжками Jupyter. Найти в разделе site-packages пакеты можно импортировать в записную книжку, включая три пакеты Microsoft, используемые для обработки и анализа данных и машинного обучения.

  ![Исполняемые файлы и библиотеки](media/jupyter-notebook-python-registration.png)

Если вы используете другую интегрированную среду разработки, необходимо связать библиотек Python исполняемых файлов и функции средства. В следующих разделах приведены инструкции для часто используемых средств.

### <a name="visual-studio"></a>Visual Studio

Если у вас есть [Python в Visual Studio](https://code.visualstudio.com/docs/languages/python), используйте следующие параметры конфигурации для создания среды Python, содержащий пакеты Microsoft Python.

| Параметр конфигурации | value |
|-----------------------|-------|
| **Префикс пути** | C:\Program Files\Microsoft\PyForMLS |
| **Путь к интерпретатору** | C:\Program Files\Microsoft\PyForMLS\python.exe |
| **Оконный интерпретатор** | C:\Program Files\Microsoft\PyForMLS\pythonw.exe |

Помощь по настройке среды Python, см. в разделе [управление средами Python в Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

В PyCharm установите интерпретатор Python исполняемый установленные сервер машинного обучения.

1. В новом проекте, в параметры, нажмите кнопку **добавить локальный**.

2. Введите `C:\Program Files\Microsoft\PyForMLS\`.

Теперь вы можете импортировать **revoscalepy**, **microsoftml**, или **azureml** модулей. Вы также можете **средства** > **консоли Python** открыть интерактивное окно.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда у вас есть средства и работающее подключение к SQL Server, расширить свои познания проходят через краткие руководства по Python с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

> [!div class="nextstepaction"]
> [Краткое руководство. Убедитесь, что существует Python в SQL Server ](../tutorials/quickstart-python-verify.md)