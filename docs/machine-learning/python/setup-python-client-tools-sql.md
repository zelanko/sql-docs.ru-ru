---
title: Настройка клиента Python для обработки и анализа данных
description: Настройте локальную среду Python (Jupyter Notebook или PyCharm) для удаленных подключений к службам машинного обучения SQL Server с помощью Python.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/04/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 93c36fbfc42ac35d973068d551ecf61ed30791fa
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88178246"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Настройка клиента обработки и анализа данных для разработки на Python в службах машинного обучения SQL Server
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

Интеграция Python доступна в SQL Server 2017 и более поздних версиях, если включить параметр для Python во время [установки служб машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md). 

Чтобы разрабатывать и развертывать решения Python для SQL Server, установите библиотеку Майкрософт [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и другие библиотеки Python для рабочей станции разработки. Библиотека revoscalepy, которая также находится на удаленном экземпляре SQL Server, координирует вычислительные запросы между обеими системами. 

Из этой статьи вы узнаете, как настроить рабочую станцию разработки на Python, чтобы вы могли взаимодействовать с удаленным сервером SQL Server, на котором включены машинное обучение и интеграция Python. После выполнения действий, описанных в этой статье, у вас будут те же библиотеки Python, что и на сервере SQL Server. Вы также узнаете, как отправлять вычисления из локального сеанса Python в удаленный сеанс Python на сервере SQL Server.

![Клиент-серверные компоненты](media/sqlmls-python-client-revo.png "Локальные и удаленные сеансы и библиотеки Python")

Чтобы проверить установку, можно использовать встроенное приложение Jupyter Notebook, как описано в этой статье, или [связать библиотеки](#install-ide) с PyCharm или любой другой интегрированной средой разработки, которой вы обычно пользуетесь.

> [!Tip]
> Видеодемонстрацию этих упражнений см. в статье [Удаленный запуск R и Python в SQL Server с помощью Jupyter Notebook](https://youtu.be/D5erljpJDjE).

> [!Note]
> Вместо установки клиентской библиотеки можно использовать [автономный сервер](../install/sql-machine-learning-standalone-windows-install.md) в качестве полнофункционального клиента. Некоторые заказчики предпочитают эту конфигурацию для более глубокой работы сценария. Автономный сервер полностью отделен от SQL Server, но поскольку он содержит те же библиотеки Python, которые установлены на SQL Server, его можно использовать в качестве клиента для анализа баз данных SQL Server. Его также можно использовать для решения задач, не связанных с SQL, в том числе для импорта и моделирования данных из других платформ данных. Если вы устанавливаете автономный сервер, исполняемый файл Python можно найти в следующем расположении: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Чтобы проверить установку, [откройте записную книжку Jupyter](#python-tools), чтобы выполнять команды с помощью исполняемого файла Python.exe в этом расположении.

## <a name="commonly-used-tools"></a>Часто используемые инструменты

Независимо от того, являетесь ли вы разработчиком Python, который мало знаком с SQL, или разработчиком SQL, который мало знаком с Python и анализом данных в базе данных, для использования всех возможностей анализа баз данных вам потребуется как средство разработки Python, так и редактор запросов T-SQL, например [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Для разработки на Python можно использовать приложение Jupyter Notebook, которое входит в дистрибутив Anaconda, устанавливаемый SQL Server. В этой статье объясняется, как запустить Jupyter Notebook, чтобы можно было выполнять код Python локально и удаленно на SQL Server.

Набор средств SSMS необходимо скачать отдельно. Он подходит для создания и выполнения хранимых процедур в SQL Server, в том числе процедур, содержащих код Python. Практически любой код Python, написанный в Jupyter Notebook, можно внедрять в хранимые процедуры. Вы можете ознакомиться с другими пошаговыми руководствами, чтобы получить дополнительные сведения об [SSMS и внедрении кода Python](../tutorials/quickstart-python-create-script.md).

## <a name="1---install-python-packages"></a>1\. Установка пакетов Python

На локальных рабочих станциях должны быть установлены те же версии пакетов Python, что и в SQL Server, включая базовый дистрибутив Anaconda 4.2.0 с Python 3.5.2, а также пакеты Майкрософт.

Сценарий установки добавляет в клиент Python три библиотеки Майкрософт в клиент Python. Сценарий устанавливает библиотеку [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), используемую для определения объектов источника данных и контекста вычислений. Он также устанавливает библиотеку [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package), предоставляющую алгоритмы машинного обучения. Также устанавливается пакет [azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk), однако этот пакет применяется к задачам внедрения, связанным с автономным контекстом Machine Learning Server (а не с контекстом экземпляра), и использование этого пакета для анализа баз данных может быть ограничено.

1. Скачайте сценарий установки.

   + [https://aka.ms/mls-py](https://aka.ms/mls-py) устанавливает версию 9.2.1 пакетов Python Майкрософт. Эта версия соответствует экземпляру SQL Server по умолчанию. 

   + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) устанавливает версию 9.3 пакетов Python Майкрософт. Эту версию лучше использовать в том случае, если удаленный экземпляр SQL Server [привязан к Machine Learning Server 9.3](../install/upgrade-r-and-python.md).

2. Откройте окно PowerShell с повышенными правами администратора (щелкните правой кнопкой мыши **Запуск от имени администратора**).

3. Перейдите в папку, в которую был скачан установщик, и запустите сценарий. Добавьте аргумент командной строки `-InstallFolder`, чтобы указать расположение папки для библиотек. Пример: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Если не указать папку установки, по умолчанию будет использована следующая папка: C:\Program Files\Microsoft\PyForMLS.

Для выполнения установки требуется некоторое время. Ход выполнения можно отслеживать в окне PowerShell. После завершения установки вы получите полный набор пакетов. 

> [!Tip] 
> Общие сведения о запуске программ Python в Windows см. в разделе [Часто задаваемые вопросы по Python для Windows](https://docs.python.org/3/faq/windows.html).

## <a name="2---locate-executables"></a>2\. Обнаружение исполняемых файлов

Оставаясь в окне PowerShell, выведите список файлов в папке установки, чтобы убедиться, что файл Python.exe, сценарии и другие пакеты установлены. 

1. Введите `cd \`, чтобы перейти к корневому каталогу диска, а затем введите путь, указанный для `-InstallFolder` на предыдущем шаге. Если этот параметр не был указан во время установки, по умолчанию используется `cd C:\Program Files\Microsoft\PyForMLS`.

2. Введите `dir *.exe`, чтобы получить список исполняемых файлов. Вы должны увидеть исполняемые файлы **python.exe**, **pythonw.exe** и **uninstall-anaconda.exe**.

   ![Список исполняемых файлов Python](media/powershell-python-exe.png)
   
В системах с несколькими версиями Python не забывайте использовать этот конкретный файл Python.exe, если необходимо загрузить **revoscalepy** и другие пакеты Майкрософт.

> [!Note] 
> Сценарий установки не изменяет переменную среды PATH на компьютере. Это означает, что новые интерпретаторы Python и модули, которые вы только что установили, не будут автоматически доступны для других инструментов. Справку по связыванию интерпретатора Python и библиотек с инструментами см. в разделе [Установка интегрированной среды разработки](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3\. Открытие Jupyter Notebook

Приложение Jupyter Notebook входит в состав дистрибутива Anaconda. В качестве следующего шага создайте записную книжку и выполните какой-нибудь код Python, в котором используются только что установленные библиотеки.

1. В командной строке PowerShell, по-прежнему находясь в каталоге C:\Program Files\Microsoft\PyForMLS, откройте приложение Jupyter Notebook из папки Scripts:

   ```powershell
   .\Scripts\jupyter-notebook
   ```

   Должна открыться записная книжка в браузере по умолчанию по адресу `https://localhost:8889/tree`.

   Другой способ запуска — дважды щелкнуть файл **jupyter-notebook.exe**. 

2. Выберите **Создать**, а затем **Python 3**.

   ![Записная книжка Jupyter с выбранными пунктами "Создать" > "Python 3"](media/jupyter-notebook-new-p3.png)

3. Введите и выполните команду `import revoscalepy`, чтобы загрузить одну из библиотек Майкрософт.

4. Введите и выполните команду `print(revoscalepy.__version__)`, чтобы получить сведения о версии. Вы должны увидеть версию 9.2.1 или 9.3.0. Вы можете использовать любую из этих версий с [библиотекой revoscalepy на сервере](../package-management/r-package-information.md).

4. Введите более сложную последовательность инструкций. В этом примере формируется сводная статистика для локального набора данных с помощью метода [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). Другие функции получают расположение демонстрационных данных и создают объект источника данных для локального XDF-файла.

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

На следующем снимке экрана показаны входные и выходные данные (выходные данные обрезаны для краткости).

  ![Записная книжка Jupyter с входными и выходными данными revoscalepy](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4\. Получение разрешений SQL

Чтобы подключиться к экземпляру SQL Server для выполнения сценариев и передачи данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, но в некоторых случаях проще использовать имя входа SQL, особенно если сценарий содержит строки подключения к внешним данным.

У учетной записи, используемой для выполнения кода, должно быть разрешение на чтение для баз данных, с которыми вы работаете, а также специальное разрешение EXECUTE ANY EXTERNAL SCRIPT. Большинству разработчиков также требуются разрешения на создание хранимых процедур и на запись данных в таблицы, содержащие данные обучения или данные оценки. 

Попросите администратора базы данных [настроить следующие разрешения для учетной записи](../security/user-permission.md) в базе данных, в которой используется Python:

+ **EXECUTE ANY EXTERNAL SCRIPT** для запуска Python на сервере.
+ Привилегии **db_datareader** для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи данных обучения и данных оценки.
+ **db_owner** для создания таких объектов, как хранимые процедуры, таблицы и функции. 
  Разрешение **db_owner** также потребуется для создания примеров баз данных и тестовых баз данных. 

Если для кода требуются пакеты, которые по умолчанию не установлены в SQL Server, обратитесь к администратору базы данных, чтобы установить необходимые пакеты. SQL Server представляет собой защищенную среду, и существуют ограничения на места установки пакетов. Нерегламентированная установка пакетов в составе вашего кода не рекомендуется, даже если у вас есть необходимые разрешения. Также тщательно оцените влияние на безопасность сервера перед установкой новых пакетов в библиотеку сервера.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5\. Создание тестовых данных

Если у вас есть разрешения на создание базы данных на удаленном сервере, можно выполнить следующий код, чтобы создать демонстрационную базу данных "Ирисы Фишера", которая будет использоваться для выполнения оставшихся действий в этой статье.

### <a name="1---create-the-irissql-database-remotely"></a>1\. Удаленное создание базы данных irissql

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

### <a name="2---import-iris-sample-from-sklearn"></a>2\. Импорт примера "Ирисы Фишера" из SkLearn

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3\. Использование API-интерфейсов Revoscalepy для создания таблицы и загрузки данных "Ирисы Фишера"

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6\. Проверка удаленного подключения

Перед выполнением следующего шага убедитесь, что у вас есть разрешения на экземпляр SQL Server и строка подключения к [демонстрационной базе данных "Ирисы Фишера"](../tutorials/demo-data-iris-in-sql.md). Если база данных не существует и у вас есть необходимые разрешения, можно [создать базу данных, используя следующие встроенные инструкции](#create-iris-remotely).

Замените значения параметров в строке подключения на соответствующие значения параметров для вашей среды. В примере кода используется строка подключения `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"`, но в вашем коде необходимо указать удаленный сервер, возможно, с именем экземпляра и параметр учетных данных, который сопоставляется с именем входа пользователя базы данных.

### <a name="define-a-function"></a>Определение функции

В следующем коде определяется функция, которая будет отправлена на сервер SQL Server на более позднем шаге. При выполнении этого кода он использует данные и библиотеки (revoscalepy, pandas, matplotlib) на удаленном сервере для создания точечных диаграмм для набора данных "Ирисы Фишера". Этот код возвращает байтовый поток из файла PNG обратно в Jupyter Notebook для отображения в браузере.

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

### <a name="send-the-function-to-sql-server"></a>Отправка функции в SQL Server

В этом примере создается удаленный контекст вычислений, и выполнение функции отправляется на сервер SQL Server с помощью [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). Функция **rx_exec** удобна, так как она принимает контекст вычислений в качестве аргумента. Любая функция, которую требуется выполнить удаленно, должна принимать контекст вычислений в качестве аргумента. Некоторые функции, например [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod), поддерживают этот аргумент напрямую. Для операций, которые не принимают этот аргумент, можно использовать **rx_exec** для доставки кода в удаленный контекст вычислений.

В этом примере необработанные данные из SQL Server в Jupyter Notebook не передаются. Все вычисления выполняются в базе данных "Ирисы Фишера", и клиенту возвращается только файл изображения.

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

На следующем снимке экрана показаны входные данные и выходные данные в виде точечной диаграммы.

  ![Записная книжка Jupyter с выходными данными в виде точечной диаграммы](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7\. Запуск Python

Поскольку разработчики часто работают с несколькими версиями Python, программа установки не добавляет путь к Python в переменную PATH. Чтобы использовать исполняемый файл и библиотеки Python, установленные программой установки, свяжите интегрированную среду разработки с файлом **Python.exe** по пути, по которому также находятся библиотеки **revoscalepy** и **microsoftml**. 

### <a name="command-line"></a>Командная строка

При запуске файла **Python.exe** из папки C:\Program Files\Microsoft\PyForMLS (или из любого другого расположения, указанного при установке клиентской библиотеки Python) у вас есть доступ ко всему дистрибутиву Anaconda и к модулям Python Майкрософт **revoscalepy** и **microsoftml**.

1. Перейдите в папку C:\Program Files\Microsoft\PyForMLS и дважды щелкните файл **Python.exe**.
2. Откройте интерактивную справку: `help()`.
3. Введите имя модуля в командной строке справки: `help> revoscalepy`. Справка возвращает имя, содержимое пакета, версию и расположение файла.
4. Получите сведения о версии и пакете в командной строке **help>** : `revoscalepy`. Нажмите клавишу ВВОД несколько раз, чтобы выйти из справки.
5. Импортируйте модуль: `import revoscalepy`.


### <a name="jupyter-notebooks"></a>Jupyter Notebook

В этой статье для демонстрации вызовов функций **revoscalepy** используется встроенное приложение Jupyter Notebook. Если вы не знакомы с этим средством, на следующем снимке экрана показаны его компоненты и механизм их работы. 

Родительская папка C:\Program Files\Microsoft\PyForMLS содержит дистрибутив Anaconda и пакеты Майкрософт. Приложение Jupyter Notebook включено в состав дистрибутива Anaconda (оно находится в папке Scripts), и исполняемые файлы Python регистрируются с помощью Jupyter Notebook. Пакеты в каталоге site-packages можно импортировать в записную книжку. К этим пакетам относятся три пакета Майкрософт, которые используются для обработки и анализа данных и машинного обучения.

  ![Исполняемые файлы и библиотеки](media/jupyter-notebook-python-registration.png)

При использовании другой интегрированной среды разработки необходимо связать исполняемые файлы и библиотеки функций Python с вашим инструментом. В следующих разделах приводятся инструкции по часто используемым инструментам.

### <a name="visual-studio"></a>Visual Studio

Если вы используете [Python в Visual Studio](https://code.visualstudio.com/docs/languages/python), воспользуйтесь следующими параметрами конфигурации, чтобы создать среду Python, включающую пакеты Python Майкрософт.

| Параметр конфигурации | value |
|-----------------------|-------|
| **Путь префикса** | C:\Program Files\Microsoft\PyForMLS |
| **Путь к интерпретатору** | C:\Program Files\Microsoft\PyForMLS\python.exe |
| **Оконный интерпретатор** | C:\Program Files\Microsoft\PyForMLS\pythonw.exe |

Сведения о настройке среды Python см. в разделе [Управление средами Python в Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

В PyCharm задайте в качестве интерпретатора исполняемый файл Python, установленный Machine Learning Server.

1. В новом проекте в окне "Параметры" щелкните **Добавить локальный путь**.

2. Введите `C:\Program Files\Microsoft\PyForMLS\`.

Теперь можно импортировать модули **revoscalepy**, **microsoftml** или **azureml**. Также можно открыть интерактивное окно, выбрав **Инструменты** > **Консоль Python**.

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда у вас есть инструменты и рабочее подключение к SQL Server, вы можете расширить свои навыки, выполнив краткие пошаговые руководства Python в [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

> [!div class="nextstepaction"]
> [Краткое руководство. Создание и выполнение простых сценариев Python с помощью служб машинного обучения SQL Server](../tutorials/quickstart-python-create-script.md)
