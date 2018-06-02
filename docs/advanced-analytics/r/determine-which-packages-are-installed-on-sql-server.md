---
title: Получить сведения о пакете R и Python для машинного обучения SQL Server | Документы Microsoft
description: Определить версию пакета R и Python, проверка установки и получить список установленных пакетов на SQL Server R Services или службы обучения машины.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 85ea4658ca8b60fc24d7e4f7849de1655eab6082
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707892"
---
#  <a name="get-r-and-python-package-information"></a>Получить сведения о пакете R и Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Иногда при работе с несколькими средами или установок R и Python, необходимо убедиться, что код, который вы используете использует среду ожидаемый Python или нужной рабочей области для R. Например, если вы обновили машинного обучения компонентов с помощью [привязки](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md), возможно, путь к библиотеке R в другой папке по умолчанию. Кроме того Если вы устанавливаете R клиента или экземпляр изолированный сервер, может потребоваться несколько библиотек R на компьютере.

Примеры сценариев R и Python в этой статье показано, как получить полный путь к версии пакетов, используемый сервером SQL Server.

## <a name="get-the-r-library-location"></a>Получить расположение библиотеки R

Для любой версии SQL Server, выполните следующую инструкцию, чтобы проверить [библиотеки пакета по умолчанию R](installing-and-managing-r-packages.md) для текущего экземпляра:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

При необходимости можно использовать [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) в более новых версиях RevoScaleR в службах SQL Server 2017 г машины обучения или [R Services обновленном R для на наименьших RevoScaleR 9.0.1](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Эта хранимая процедура возвращает путь к библиотеке экземпляра и версии RevoScaleR, используемый сервером SQL Server:

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) функция может выполняться только на локальном компьютере. Функция не может возвращать путей к библиотеке для удаленных соединений.

**Результаты**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Получить расположение библиотеки Python

Для **Python** в 2017 г. SQL Server, выполните следующую инструкцию, чтобы проверить библиотеки по умолчанию для текущего экземпляра. Этот пример возвращает список папок, включенных в Python `sys.path` переменной. Список содержит текущий каталог и путь к стандартной библиотеке.

```sql
EXECUTE sp_execute_external_script
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

## <a name="list-all-packages"></a>Список всех пакетов

Существует несколько способов, которые можно получить полный список пакетов, установленных в настоящее время. Одно из преимуществ запуска пакета список команд из sp_execute_external_script является, обязательно получить пакеты, установленные в библиотеке экземпляра.

### <a name="r"></a>Чтение

В следующем примере используется функция R `installed.packages()` в [!INCLUDE [tsql](..\..\includes\tsql-md.md)] хранимую процедуру, чтобы получить таблицу пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Этот скрипт возвращает поля имя и версия пакета в файле DESCRIPTION, возвращается только имя.

```SQL
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Дополнительные сведения о необязательный и поля по умолчанию для поля ОПИСАНИЯ пакета R см. в разделе [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

`pip` Модуль устанавливается по умолчанию и поддерживает множество операций установлен список пакетов, в дополнение к поддерживаемым Стандартная Python. Можно запустить `pip` из Python командной строки, конечно, но также можно вызывать некоторые функции pip из `sp_execute_external_script`.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
  import pip
  import pandas as pd
  installed_packages = pip.get_installed_distributions()
  installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
  df = pd.DataFrame(installed_packages_list)
  OutputDataSet = df'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

При выполнении `pip` из командной строки, существует множество полезных функций: `pip list` возвращает все пакеты, которые устанавливаются, тогда как `pip freeze` перечислены пакеты, установленные с `pip`и не перечисляет пакеты, которые pip сам зависит от. Можно также использовать `pip freeze` для создания файла зависимостей.

## <a name="find-a-single-package"></a>Поиск одного пакета

Если вы установили пакет и хотели бы убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить следующий вызов хранимой процедуры для загрузки пакета и вернуть только сообщения.

### <a name="r"></a>Чтение

В этом примере ищет и загружает библиотеку RevoScaleR, если он доступен.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Если найти пакет, будет возвращено сообщение: «Команд выполнена успешно».

+ Если найти или загрузить пакет невозможно, возникает ошибка, содержащий текст: «не найден пакет, который называется «MissingPackageName»»

### <a name="python"></a>Python

Эквивалент проверка Python может выполняться из Python оболочки с помощью `conda` или `pip` команд. Кроме того выполните следующую инструкцию в хранимой процедуре:

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
  import pip
  import pkg_resources
  pckg_name = "revoscalepy"
  pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
  installed_pckg = pckgs.query(''key == @pckg_name'')
  print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

## <a name="get-package-information-in-r-and-python-tools"></a>Получить сведения о пакете в средствах R и Python

Все предыдущие инструкций предполагается, что вы используете средство SQL Server как Management Studio (SSMS). При необходимости с помощью средств R и Python, приведенные ниже инструкции объясняется, как получить сведения о библиотеке и пакета из командной строки R или Python.

### <a name="r-commands"></a>Команды R

Библиотека экземпляра для R — \Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library.

Запуск стандартных средств R из этих расположений, чтобы убедиться, что используются пакеты из экземпляра библиотеки.

+ \MSSQL14. MSSQLSERVER\R_SERVICES\bin\R.exe для командной строки с R
+ \MSSQL14. MSSQLSERVER\R_SERVICES\bin\x64\Rgui.exe R консольного приложения

Стандартные команды R или RevoScaleR команды можно использовать для получения сведений о пакете. Пакет RevoScaleR загружаются автоматически. 

Возвращает сведения о пакете RevoScaleR:

    > print(Revo.version)

Возвращает список всех установленных пакетов:

    > installed.packages()

Возвращает версию R:

    > packageDescription("base")

### <a name="python-commands"></a>Команды Python

Поддержка Python является только 2017 г. SQL Server. Библиотека экземпляра для Python — \Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\.

Откройте окно команд Python из этого расположения, чтобы убедиться, что пакеты из экземпляра библиотеки используются:

+ \MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Python.exe

Открытие интерактивной справки:

    > help()

Введите имя модуля в командной строке справки, чтобы получить содержимое пакета, версия и расположение файла:

    help> revoscalepy

<a name="pip-conda"></a>

### <a name="python-package-managers-pip-and-conda"></a>Python пакета диспетчеры (Pip и Conda)

Anaconda включает средства Python для управления пакетами. На значение по умолчанию экземпляра, Pip, Conda и других средств можно найти в \Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts.

Программа установки SQL Server не добавить Pip или Conda в системный путь и на экземпляре SQL Server производства указывать необязательные исполняемые файлы из пути является лучшим способом. Тем не менее для сред разработки и тестирования, можно добавить папку «скрипты» для переменной среды PATH для запуска команды Pip и Conda из любого места.

1. Перейдите к C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Щелкните правой кнопкой мыши **conda.exe** > **Запуск от имени администратора**и введите `conda list` для получения списка пакетов, установленных в текущей среде.

1. Аналогичным образом, щелкните правой кнопкой мыши **pip.exe** > **Запуск от имени администратора**и введите `pip list` для возвращают одинаковые данные. 


## <a name="next-steps"></a>Следующие шаги

+ [Установка новых пакетов R](install-additional-r-packages-on-sql-server.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Руководства, примеры, решения](../tutorials/machine-learning-services-tutorials.md)