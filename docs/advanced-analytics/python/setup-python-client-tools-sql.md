---
title: Настройка клиента обработки и анализа данных для разработки на Python
description: Настройте локальную среду Python (Jupyter Notebook или PyCharm) для удаленных подключений к SQL Server Службы машинного обучения с помощью Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b5f406ec4b6cfbd65db7a4ecd3a1ad14dff6d8e1
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470232"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Настройка клиента обработки и анализа данных для разработки на Python на SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Интеграция с Python доступна начиная с SQL Server 2017 или более поздней версии при включении параметра Python в [службы машинного обучения (в базе данных)](../install/sql-machine-learning-services-windows-install.md). 

Для разработки и развертывания решений Python для SQL Server установите [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и другие библиотеки Python на рабочей станции разработки. Библиотека revoscalepy, которая также находится на удаленном экземпляре SQL Server, координирует вычислительные запросы между обеими системами. 

Из этой статьи вы узнаете, как настроить рабочую станцию разработки на Python, чтобы вы могли взаимодействовать с удаленными SQL Server, включенными для машинного обучения и интеграции Python. После выполнения действий, описанных в этой статье, вы получите те же библиотеки Python, что и в SQL Server. Вы также узнаете, как отправлять вычисления из локального сеанса Python в удаленный сеанс Python на SQL Server.

![Клиент-серверные компоненты](media/sqlmls-python-client-revo.png "Локальные и удаленные сеансы и библиотеки Python")

Чтобы проверить установку, можно использовать встроенные записные книжки Jupyter, как описано в этой статье, или [связать библиотеки](#install-ide) с PyCharm или любой другой интегрированной средой разработки, которая используется в обычном режиме.

> [!Tip]
> Видеодемонстрацию этих упражнений см. [в статье удаленное выполнение R и Python в SQL Server из записных книжек Jupyter](https://youtu.be/D5erljpJDjE).

> [!Note]
> Альтернативой установке клиентской библиотеки является использование [изолированного сервера](../install/sql-machine-learning-standalone-windows-install.md) в качестве полнофункционального клиента, который некоторые клиенты предпочитают использовать более глубокий сценарий. Изолированный сервер полностью отделен от SQL Server, но, поскольку он содержит те же библиотеки Python, его можно использовать в качестве клиента для SQL Server аналитики в базе данных. Его также можно использовать для работы, не связанной с SQL, включая возможность импорта и моделирования данных из других платформ данных. Если вы устанавливаете автономный сервер, исполняемый файл Python можно найти в следующем расположении: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Чтобы проверить установку, [откройте записную книжку Jupyter](#python-tools) для выполнения команд с помощью Python. exe в этом расположении.

## <a name="commonly-used-tools"></a>Часто используемые средства

Если вы являетесь разработчиком Python, новым для SQL, или разработчиком SQL, новым для Python и аналитической аналитики в базе данных, вам потребуется как средство разработки Python, так и редактор запросов T-SQL, например [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) для выполнения всех возможностей Аналитика в базе данных.

Для разработки на Python можно использовать записные книжки Jupyter, которые поставляются в дистрибутив Anaconda, установленный SQL Server. В этой статье объясняется, как запустить записные книжки Jupyter, чтобы можно было выполнять код Python локально и удаленно на SQL Server.

SSMS — это отдельная загрузка, которая полезна для создания и выполнения хранимых процедур на SQL Server, включая те, которые содержат код Python. Практически любой код Python, написанный в записных книжках Jupyter, можно внедрять в хранимую процедуру. Вы можете пошагово пройти другие краткие руководства, чтобы узнать о [SSMS и Embedded Python](../tutorials/quickstart-python-verify.md).

## <a name="1---install-python-packages"></a>1\. Установка пакетов Python

На локальных рабочих станциях должны быть установлены те же версии пакетов Python, что и в SQL Server, включая базовый Anaconda 4.2.0 с пакетом 3.5.2 для Python, а также пакеты, относящиеся к корпорации Майкрософт.

Сценарий установки добавляет в клиент Python три библиотеки, относящиеся к Microsoft. Скрипт устанавливает [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), используемый для определения объектов источника данных и контекста вычислений. Он устанавливает [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , предоставляющий алгоритмы машинного обучения. Пакет [azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) также устанавливается, но применяется к задачам в области действия, связанным с автономным (не экземпляром) Machine Learning Server контексте и может быть ограниченным использованием для аналитики в базе данных.

1. Скачайте сценарий установки.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py)устанавливает версию 9.2.1 пакетов Microsoft Python. Эта версия соответствует экземпляру SQL Server 2017 по умолчанию. 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py)устанавливает пакеты Microsoft Python версии 9,3. Эта версия лучше подходит, если удаленный экземпляр SQL Server 2017 [привязан к Machine Learning Server 9,3](../install/upgrade-r-and-python.md).

2. Откройте окно PowerShell с повышенными правами администратора (щелкните правой кнопкой мыши **Запуск от имени администратора**).

3. Перейдите в папку, в которую был скачан установщик, и запустите сценарий. Добавьте аргумент `-InstallFolder` командной строки, чтобы указать расположение папки для библиотек. Пример: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Если опустить папку установки, значение по умолчанию — C:\Program Филес\микрософт\пиформлс.

Для завершения установки требуется некоторое время. Ход выполнения можно отслеживать в окне PowerShell. После завершения установки вы получите полный набор пакетов. 

> [!Tip] 
> Мы рекомендуем [часто задаваемые вопросы по Python для Windows](https://docs.python.org/3/faq/windows.html) для получения общих сведений пурппосе о запуске программ Python в Windows.

## <a name="2---locate-executables"></a>2\. Обнаружение исполняемых файлов

По-прежнему в PowerShell перечислите содержимое папки установки, чтобы убедиться, что установлены Python. exe, сценарии и другие пакеты. 

1. Введите `cd \` , чтобы перейти к корневому диску, а затем введите путь, указанный `-InstallFolder` для на предыдущем шаге. Если этот параметр пропущен во время установки, по умолчанию используется `cd C:\Program Files\Microsoft\PyForMLS`значение.

2. Введите `dir *.exe` , чтобы вывести список исполняемых файлов. Вы должны увидеть **Python. exe**, **писонв. exe**и **унинсталл-Анаконда. exe**.

  ![Список исполняемых файлов Python](media/powershell-python-exe.png)
   
В системах с несколькими версиями Python не забывайте использовать этот конкретный Python. exe, если вы хотите загрузить **revoscalepy** и другие пакеты Майкрософт.

> [!Note] 
> Сценарий установки не изменяет переменную среды PATH на компьютере. Это означает, что новые интерпретаторы Python и модули, которые вы только что установили, не будут автоматически доступны другим средствам. Справку по связыванию интерпретатора Python и библиотек с инструментами см. в разделе [Установка интегрированной среды разработки](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3\. Открытие записных книжек Jupyter

Anaconda включает записные книжки Jupyter. В качестве следующего шага создайте записную книжку и выполните код Python, содержащий только что установленные библиотеки.

1. В командной строке PowerShell, которая по-прежнему находится в каталоге C:\Program Филес\микрософт\пиформлс, откройте записные книжки Jupyter в папке Scripts:

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  Записная книжка должна открываться в браузере `https://localhost:8889/tree`по умолчанию по адресу.

  Еще один способ запуска — дважды щелкнуть **Жупитер-нотебук. exe**. 

2. Щелкните **создать** , а затем выберите **Python 3**.

  ![Записная книжка jupyter с новым выбором Python 3](media/jupyter-notebook-new-p3.png)

3. Введите `import revoscalepy` и выполните команду, чтобы загрузить одну из библиотек, характерных для Microsoft.

4. Введите и выполните `print(revoscalepy.__version__)` , чтобы вернуть сведения о версии. Вы должны увидеть 9.2.1 или 9.3.0. [На сервере](../package-management/installed-package-information.md)можно использовать любую из этих версий с revoscalepy. 

4. Введите более сложную последовательность инструкций. В этом примере формируется сводная статистика с использованием [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) через локальный набор данных. Другие функции получают расположение демонстрационных данных и создают объект источника данных для локального файла Xdf-.

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

На следующем снимке экрана показаны входные данные и часть выходных данных, обрезанные для краткости.

  ![Записная книжка jupyter, демонстрирующая входные и выходные данные revoscalepy](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4\. получение разрешений SQL

Чтобы подключиться к экземпляру SQL Server для выполнения скриптов и передачи данных, необходимо иметь допустимое имя входа на сервере базы данных. Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Обычно рекомендуется использовать встроенную проверку подлинности Windows, но использовать имя входа SQL проще в некоторых сценариях, особенно если скрипт содержит строки подключения к внешним данным.

Как минимум, учетная запись, используемая для выполнения кода, должна иметь разрешение на чтение из баз данных, с которыми вы работаете, а специальное разрешение ВЫПОЛНЯЕТ любой внешний сценарий. Большинству разработчиков также требуются разрешения на создание хранимых процедур и запись данных в таблицы, содержащие обучающие данные или данные с оценками. 

Попросите администратора базы данных [настроить следующие разрешения для вашей учетной записи](../security/user-permission.md)в базе данных, где используется Python:

+ **Выполните любой внешний скрипт** для запуска Python на сервере.
+ **db_datareader** привилегии для выполнения запросов, используемых для обучения модели.
+ **db_datawriter** для записи обучающих данных или оценочных данных.
+ **db_owner** для создания таких объектов, как хранимые процедуры, таблицы, функции. 
  Кроме того, для создания образцов и тестовых баз данных требуется **db_owner** . 

Если для кода требуются пакеты, которые не устанавливаются по умолчанию с SQL Server, следует попытаться установить пакеты с экземпляром с помощью администратора базы данных. SQL Server является защищенной средой, а также существуют ограничения на установку пакетов. Нерегламентированная Установка пакетов как часть кода не рекомендуется, даже если у вас есть права. Кроме того, прежде чем устанавливать новые пакеты в серверную библиотеку, всегда тщательно продумайте последствия безопасности.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5\. Создание тестовых данных

Если у вас есть разрешения на создание базы данных на удаленном сервере, можно выполнить следующий код, чтобы создать демонстрационную базу данных IRI, которая будет использоваться для выполнения оставшихся действий в этой статье.

### <a name="1---create-the-irissql-database-remotely"></a>1\. удаленное создание базы данных ирисскл

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

### <a name="2---import-iris-sample-from-sklearn"></a>2\. импорт примера IRI из SkLearn

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3\. Использование API-интерфейсов Revoscalepy для создания таблицы и загрузки данных диафрагмы

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6\. Тестирование удаленного подключения

Прежде чем пытаться выполнить следующий шаг, убедитесь, что у вас есть разрешения на экземпляр SQL Server и строку подключения к [образцу базы данных IRI](../tutorials/demo-data-iris-in-sql.md). Если база данных не существует и у вас есть необходимые разрешения, можно [создать базу данных, используя эти встроенные инструкции](#create-iris-remotely).

Замените строку подключения допустимыми значениями. В примере кода используется `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` , но в коде должен быть указан удаленный сервер, возможно, имя экземпляра и параметр учетных данных, сопоставляемый с именем входа пользователя базы данных.

### <a name="define-a-function"></a>Определение функции

В следующем коде определяется функция, которая будет отправлена в SQL Server на более позднем шаге. При выполнении он использует данные и библиотеки (revoscalepy, Pandas, Matplotlib) на удаленном сервере для создания точечных диаграмм набора данных IRI. Он возвращает ByteStream из файла PNG обратно в записные книжки Jupyter для отображения в браузере.

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

В этом примере создайте удаленный контекст вычислений, а затем отправьте выполнение функции в SQL Server с [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). Функция **rx_exec** полезна, так как она принимает контекст вычислений в качестве аргумента. Любая функция, которую требуется выполнить удаленно, должна иметь аргумент контекста вычислений. Некоторые функции, такие как [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) , напрямую поддерживают этот аргумент. Для операций, которые не позволяют, можно использовать **rx_exec** для доставки кода в удаленном контексте вычислений.

В этом примере не пришлось передавать необработанные данные из SQL Server в Jupyter Notebook. Все вычисления выполняются в базе данных IRI, и клиенту возвращается только файл изображения.

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

На следующем снимке экрана показаны входные и точечные выходные диаграммы.

  ![Записная книжка jupyter с изображением точечной диаграммы](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7\. запуск Python из средств

Поскольку разработчики часто работают с несколькими версиями Python, программа установки не добавляет Python в ваш путь. Чтобы использовать исполняемый файл и библиотеки Python, установленные программой установки, свяжите интегрированную среду разработки с **Python. exe** по пути, который также предоставляет **revoscalepy** и **microsoftml**. 

### <a name="command-line"></a>Командная строка

При запуске **Python. exe** из C:\Program филес\микрософт\пиформлс (или другого расположения, указанного для установки клиентской библиотеки Python) у вас есть доступ к полному дистрибутиву Anaconda и модулям Microsoft Python, **revoscalepy** и **microsoftml**.

1. Перейдите в папку C:\Program Филес\микрософт\пиформлс и дважды щелкните **Python. exe**.
2. Открыть интерактивную справку:`help()`
3. Введите имя модуля в строке справки: `help> revoscalepy`. Help возвращает имя, содержимое пакета, версию и расположение файла.
4. Возврат сведений о версии и пакете в **справку >** запросе: `revoscalepy`. Нажмите клавишу ВВОД несколько раз, чтобы выйти из справки.
5. Импорт модуля:`import revoscalepy`


### <a name="jupyter-notebooks"></a>Записные книжки Jupyter

В этой статье для демонстрации вызовов функций к **revoscalepy**используются встроенные записные книжки Jupyter. Если вы не знакомы с этим средством, на следующем снимке экрана показано, как эти элементы объединяются и почему все это работает. 

Родительская папка C:\Program Филес\микрософт\пиформлс содержит Anaconda и пакеты Майкрософт. Записные книжки Jupyter включены в папку Scripts, а исполняемые файлы Python регистрируются с помощью записных книжек Jupyter. Пакеты, найденные в разделе пакеты сайта, можно импортировать в записную книжку, включая три пакета Майкрософт, которые используются для обработки и анализа данных и машинного обучения.

  ![Исполняемые файлы и библиотеки](media/jupyter-notebook-python-registration.png)

При использовании другой интегрированной среды разработки необходимо связать исполняемые файлы и библиотеки функций Python с вашим инструментом. В следующих разделах приводятся инструкции по часто используемым средствам.

### <a name="visual-studio"></a>Visual Studio

Если у вас есть [Python в Visual Studio](https://code.visualstudio.com/docs/languages/python), используйте следующие параметры конфигурации, чтобы создать среду Python, включающую пакеты Microsoft Python.

| Параметр конфигурации | value |
|-----------------------|-------|
| **Путь префикса** | C:\Program Филес\микрософт\пиформлс |
| **Путь к интерпретатору** | C:\Program Филес\микрософт\пиформлс\писон.ЕКСЕ |
| **Интерпретатор с окнами** | C:\Program Филес\микрософт\пиформлс\писонв.ЕКСЕ |

Сведения о настройке среды Python см. [в статье Управление окружениями Python в Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

В PyCharm задайте для интерпретатора исполняемый файл Python, установленный Machine Learning Server.

1. В новом проекте в меню Параметры выберите команду **добавить локальную**.

2. Введите `C:\Program Files\Microsoft\PyForMLS\`.

Теперь вы можете импортировать модули **revoscalepy**, **microsoftml**или **azureml** . Можно также выбрать **инструменты** > **консоль Python** , чтобы открыть интерактивное окно.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда у вас есть инструменты и работающее подключение к SQL Server, расширьте свои навыки, запустив краткие руководства по Python с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

> [!div class="nextstepaction"]
> [QuickStart Проверка наличия Python в SQL Server](../tutorials/quickstart-python-verify.md)