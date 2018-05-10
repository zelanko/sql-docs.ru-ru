---
title: Получить сведения о пакете R и Python для машинного обучения SQL Server | Документы Microsoft
description: Определить версию пакета R и Python, проверка установки и получить список установленных пакетов на SQL Server R Services или службы обучения машины.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3295bbdbb00c73c9aaa37dcb15d35121b82454bb
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
#  <a name="get-r-and-python-package-information-on-sql-server-machine-learning"></a>Получение информации о пакете R и Python в SQL Server машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Если установлено несколько сред Python или использование нескольких средств R, его можно легко установить пакет неправильный библиотеки или среды и затем не сможет найти его позже. В этой статье приведены запросы и инструкции полезны для версии пакета determininga и получить список пакетов, установленных в текущей среде SQL Server.

## <a name="verify-the-current-default-library"></a>Проверка текущей библиотеки по умолчанию

Для **R** в SQL Server, выполните следующую инструкцию, чтобы проверить библиотеки по умолчанию для текущего экземпляра:

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Для **Python** в SQL Server, выполните следующую инструкцию, чтобы проверить библиотеки по умолчанию для текущего экземпляра:

```sql
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

## <a name="generate-a-package-list-using-a-stored-procedure"></a>Создать список пакетов, с помощью хранимой процедуры

Существует несколько способов, которые можно получить полный список пакетов, установленных в настоящее время. Одно из преимуществ запуска пакета список команд из sp_execute_external_script является, обязательно получить пакеты, установленные в библиотеке экземпляра.

### <a name="r"></a>Чтение

В следующем примере используется функция R `installed.packages()` в [!INCLUDE [tsql](..\..\includes\tsql-md.md)] хранимую процедуру, чтобы получить таблицу пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Чтобы избежать анализа полей в файле DESCRIPTION, возвращается только имя.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
NameOnly <- packagematrix[,1];
OutputDataSet <- as.data.frame(NameOnly);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250) ))
```

Дополнительные сведения о необязательный и поля по умолчанию для поля ОПИСАНИЯ пакета R см. в разделе [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

`pip` Модуль устанавливается по умолчанию и поддерживает множество операций установлен список пакетов, в дополнение к поддерживаемым Стандартная Python. Можно запустить `pip` из Python командной строки, конечно, но также можно вызывать некоторые функции pip из `sp_execute_external_script`.

```sql
execute sp_execute_external_script 
@language = N'Python', 
@script = N'
import pip
import pandas as pd
installed_packages = pip.get_installed_distributions()
installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

При выполнении `pip` из командной строки, существует множество полезных функций: `pip list` возвращает все пакеты, которые устанавливаются, тогда как `pip freeze` перечислены пакеты, установленные с `pip`и не перечисляет пакеты, которые pip сам зависит от. Можно также использовать `pip freeze` для создания файла зависимостей.

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Проверьте, установлен ли пакет с помощью экземпляра

Если вы установили пакет и хотели бы убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить следующий вызов хранимой процедуры для загрузки пакета и вернуть только сообщения.

### <a name="r"></a>Чтение

В этом примере ищет и загружает библиотеку RevoScaleR, если он доступен.

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'require("RevoScaleR")'
GO
```

+ Если найти пакет, будет возвращено сообщение: «Команд выполнена успешно».

+ Если найти или загрузить пакет невозможно, возникает ошибка, содержащий текст: «не найден пакет, который называется «MissingPackageName»»

### <a name="python"></a>Python

Эквивалент проверка Python может выполняться из Python оболочки с помощью `conda` или `pip` команд. Кроме того выполните следующую инструкцию в хранимой процедуре:

```sql
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import pip
import pkg_resources
pckg_name = "revoscalepy"
pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

## <a name="view-installed-packages-using-a-utility-or-ide"></a>Просмотр установленных пакетов с помощью программы или интегрированной среды разработки

Большинство средств разработки предоставляют обозреватель объектов или список пакетов, которые были установлены или загружены в текущую рабочую область или среды. В этом разделе содержатся короткий рекомендации по использованию популярных средств R или Python.

### <a name="r-tools"></a>Средства R

Существует несколько способов получить список установленных или загруженных пакетов с помощью служебных программ R. 

+ Из локальной программу R, используйте базовая функция R, например `installed.packages()`, который входит в `utils` пакета. Чтобы получить список, который является точным для экземпляра, необходимо явно указать путь к библиотеке или использовать средства R, связанных с библиотекой экземпляра.

### <a name="python-tools"></a>Средства Python

Расширения Python для Visual Studio сделать очень легко просмотреть пакеты, установленные в текущей среде или в других виртуальных сред, перечисленные в Интегрированной среде разработки. Можно настроить несколько сред, выберите среду из списка и просмотреть пакеты или установить новые пакеты для этой среды.

+ [Среды Python](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

Код Visual Studio является свободного редактор, который поддерживает Python, с помощью нескольких доступных linters Python. Несмотря на то, что пакет браузера, например в Visual Studio не предоставляет VS Code, он поддерживает, Настройка и переключение между несколькими средами.

+ [Python в коде Visual Studio](https://code.visualstudio.com/docs/languages/python)

Для выполнения может потребоваться дополнительная настройка **revoscalepy** команды из удаленного клиента:

+ [Установка пользовательские пакеты Python и интерпретатора локально в Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)

Этот блог предоставляет полезные советы по настройке других средах Python, включая PyCharm для работы с **revoscalepy**.

+ [Начало работы с Python веб-служб с помощью сервера машины обучения](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)

## <a name="use-functions-from-machine-learning-server"></a>Использование функций с компьютера сервера обучения

Так как библиотеки, используемые с SQL Server поддержку выполнения кода с помощью удаленного клиента, чтобы узнать, какие пакеты могут использовать эти функции будут установлены в удаленной среде.

### <a name="revoscaler"></a>RevoScaleR

Если вы работаете в удаленных клиентов и не имеют доступа к серверу, можно получить список пакетов, установленных на сервере SQL Server с помощью функции RevoScaleR. Указываются контекст вычислений, в которой необходимо иметь разрешение на подключение к серверу SQL Server. 

+ [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) находит путь для пакета в контексте удаленного вычислений.

+ [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) получает сведения о пакеты, установленные в контекст вычислений.

Например выполните следующий код R для получения списка пакетов, доступных в заданном контексте вычислений SQL Server.

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

Следующий пример возвращает расположение библиотеки в локальном контексте и версия пакета RevoScaleR.

```R
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

### <a name="revoscalepy"></a>revoscalepy

Функции, аналогичные действиям для RevoScaleR в настоящее время недоступны. Искать их в более поздней версии **revoscalepy**.

## <a name="get-library-location-and-version"></a>Получить расположение библиотеки и версии

Иногда при работе с несколькими средами или установок R и Python, необходимо убедиться, что код, который вы используете используется среда для Python или нужной рабочей области для R.

Например при обновлении машинного обучения компонентов с помощью привязки, путь к библиотеке R может быть в той же папке по умолчанию. Кроме того Если вы устанавливаете R клиента или экземпляр изолированный сервер, может потребоваться несколько библиотек R на компьютере.

Эти примеры показывают, как получить полный путь к версии библиотеки, который используется SQL Server.

### <a name="r"></a>Чтение

Эта хранимая процедура возвращает путь к библиотеке экземпляра и версию пакета RevoScaleR, используемый сервером SQL Server:

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) функция может выполняться только на конечном компьютере. Функция не может возвращать путей к библиотеке для удаленных соединений.

**Результаты**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```

### <a name="python"></a>Python

Этот пример возвращает список папок, включенных в Python `sys.path` переменной. Список содержит текущий каталог и путь к стандартной библиотеке.

```sql
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Результаты**

```text
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Дополнительные сведения о переменной `sys.path` и он используется для задания пути поиска интерпретатора для модулей, в разделе [документации Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

