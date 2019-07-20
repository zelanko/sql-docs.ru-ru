---
title: Получение сведений о пакете R и Python
description: Определите версию пакета R и Python, проверьте установку и получите список установленных пакетов на SQL Server R Services или Службы машинного обучения.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: dec0fe7147eab6a4b6545decf99e1731d773957c
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343415"
---
#  <a name="get-r-and-python-package-information"></a>Получение сведений о пакете R и Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Иногда при работе с несколькими средами или установками R или Python необходимо убедиться, что выполняемый код использует ожидаемую среду для Python или правильную рабочую область для R. Например, если вы обновили [R или Python](../install/upgrade-r-and-python.md), путь к библиотеке R может находиться в папке, отличной от папки по умолчанию. Кроме того, если установить клиент R или экземпляр отдельного сервера, на компьютере может быть несколько библиотек R.

Примеры сценариев R и Python в этой статье показывают, как получить путь и версию пакетов, используемых SQL Server.

## <a name="get-the-r-library-location"></a>Получение расположения библиотеки R

Для любой версии SQL Server выполните следующую инструкцию, чтобы проверить библиотеку пакетов R по умолчанию для текущего экземпляра:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

При необходимости можно использовать [рксскллибпасс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) в более новых версиях RevoScaleR в SQL Server 2017 службы машинного обучения или службах [r, обновленных r, по меньшей мере RevoScaleR 9.0.1](../install/upgrade-r-and-python.md). Эта хранимая процедура возвращает путь к библиотеке экземпляров и версию RevoScaleR, используемую SQL Server:

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
> Функция [рксскллибпасс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) может выполняться только на локальном компьютере. Функция не может вернуть пути к библиотеке для удаленных соединений.

**Результаты**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Получение расположения библиотеки Python

Для **Python** в SQL Server 2017 выполните следующую инструкцию, чтобы проверить библиотеку по умолчанию для текущего экземпляра. Этот пример возвращает список папок, включаемых в переменную `sys.path` Python. Список включает текущий каталог и путь к стандартной библиотеке.

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

Дополнительные сведения о переменной `sys.path` и о том, как она используется для задания пути поиска для модулей, см. в документации по [Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) .

## <a name="list-all-packages"></a>Список всех пакетов

Существует несколько способов получить полный список пакетов, установленных в настоящий момент. Одним из преимуществ выполнения команд списка пакетов из sp_execute_external_script является то, что вы гарантировано получаете пакеты, установленные в библиотеке экземпляров.

### <a name="r"></a>R

В следующем примере функция `installed.packages()` R используется [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимой процедуре для получения матрицы пакетов, установленных в библиотеке R_SERVICES для текущего экземпляра. Этот скрипт возвращает поля имени и версии пакета в файле описания, возвращается только имя.

```sql
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

Дополнительные сведения о необязательном поле и полях по умолчанию для поля Описание пакета R [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)см. в разделе.

### <a name="python"></a>Python

`pip` Модуль устанавливается по умолчанию и поддерживает множество операций для перечисления установленных пакетов, а также поддерживаемых стандартом Python. Конечно, можно `pip` запустить из командной строки Python, но можно также вызвать некоторые функции PIP из. `sp_execute_external_script`

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

При запуске `pip` из командной строки существует множество других полезных функций: получает все установленные `pip list` пакеты, в то время как `pip freeze` список пакетов, установленных `pip`, и не перечисляет пакеты, которые имеют свою пошаговую функцию. зависит от. Также можно использовать `pip freeze` для создания файла зависимостей.

## <a name="find-a-single-package"></a>Поиск одного пакета

Если вы установили пакет и хотите убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить следующий вызов хранимой процедуры, чтобы загрузить пакет и вернуть только сообщения.

### <a name="r"></a>R

В этом примере выполняется поиск и загрузка библиотеки RevoScaleR, если она доступна.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Если пакет найден, возвращается сообщение: "Команды успешно завершены".

+ Если пакет не удается найти или загрузить, появляется сообщение об ошибке, содержащее текст: "нет пакета с именем" Миссингпаккаженаме "

### <a name="python"></a>Python

Аналогичную проверку Python можно выполнить из оболочки Python с помощью `conda` команд или. `pip` Кроме того, можно выполнить следующую инструкцию в хранимой процедуре:

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

<a name="get-package-vers"></a>

## <a name="get-package-version"></a>Получение версии пакета

Сведения о версии пакета R и Python можно получить с помощью Management Studio.

### <a name="r-package-version"></a>Версия пакета R

Эта инструкция возвращает версию пакета RevoScaleR и базовую версию R.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("RevoScaleR"))
print(packageDescription("base"))
'
```

### <a name="python-package-version"></a>Версия пакета Python

Эта инструкция возвращает версию пакета revoscalepy и версию Python.

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import revoscalepy
import sys
print(revoscalepy.__version__)
print(sys.version)
'
```

## <a name="next-steps"></a>Следующие шаги

+ [Установка новых пакетов R](../r/install-additional-r-packages-on-sql-server.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Руководства, примеры, решения](../tutorials/machine-learning-services-tutorials.md)