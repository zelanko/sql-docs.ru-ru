---
title: Получить сведения для пакета R и Python — службы машинного обучения SQL Server
description: Определить версию пакета R и Python, проверка установки и получить список установленных пакетов на SQL Server R Services или служб машинного обучения.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/08/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 3e7dd580cd7d03235be704a7c46e5171a6526ae8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513001"
---
#  <a name="get-r-and-python-package-information"></a>Получить сведения о пакете R и Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Иногда при работе с несколькими средами или установок R или Python, необходимо убедиться, что код, который вы используете использует среды для Python или правильной рабочей областью для R. Например, если вы обновили машинного обучения компонентов с помощью [привязки](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md), путь к библиотеке R может находиться в той же папке по умолчанию. Кроме того Если установить R Client или экземпляр автономного сервера, возможно несколько библиотек R на компьютере.

Примеры сценариев R и Python в этой статье показано, как получить путь и версии пакетов, используемый сервером SQL Server.

## <a name="get-the-r-library-location"></a>Получить расположение библиотеки r.

Для любой версии SQL Server, выполните следующую инструкцию, чтобы проверить [библиотека пакетов R по умолчанию](installing-and-managing-r-packages.md) для текущего экземпляра:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

При необходимости можно использовать [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) в более новых версиях RevoScaleR в службах машинного обучения SQL Server 2017 или [службы R обновлены R, чтобы по крайней мере RevoScaleR 9.0.1](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Эта хранимая процедура возвращает путь к библиотеке экземпляра и версия RevoScaleR, используемый сервером SQL Server:

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
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) функция может быть выполнена только на локальном компьютере. Функция не возвращает путей к библиотеке для удаленных соединений.

**Результаты**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Получить расположение библиотеки Python

Для **Python** в SQL Server 2017, выполните следующую инструкцию, чтобы проверить библиотеку по умолчанию для текущего экземпляра. Этот пример возвращает список папок, включенных в Python `sys.path` переменной. Список содержит текущий каталог и путь к стандартной библиотеке.

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

Дополнительные сведения о переменной `sys.path` и о том, как он используется для задания интерпретатор путь поиска для модулей, см. в разделе [документации по Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>Перечисление всех пакетов

Существует несколько способов, которые можно получить полный список установленных пакетов. Одним из преимуществ запуска пакета списка команд из sp_execute_external_script является, что вы гарантированно получите пакеты, установленные в библиотеке экземпляра.

### <a name="r"></a>Чтение

В следующем примере используется функция R `installed.packages()` в [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимую процедуру, чтобы получить таблицу пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Этот скрипт возвращает поля имени и версии пакета в файле DESCRIPTION, возвращается только имя.

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

Дополнительные сведения о необязательный и полей по умолчанию для поля DESCRIPTION пакета R, см. в разделе [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

`pip` Модуль устанавливается по умолчанию и поддерживает множество операций для установки список пакетов, помимо поддерживаемые стандартного Python. Можно запустить `pip` из Python командной строки, конечно, но можно также вызвать некоторые функции pip из `sp_execute_external_script`.

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

При выполнении `pip` из командной строки, существует множество других полезных функций: `pip list` возвращает все пакеты, которые установлены, в то время как `pip freeze` перечислены пакеты, установленные `pip`и не перечисляет пакеты, которые сам pip зависит от. Можно также использовать `pip freeze` для создания файла зависимостей.

## <a name="find-a-single-package"></a>Найти один пакет

Если вы установили пакет и хотим убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить следующий вызов хранимой процедуры для загрузки пакета и возвращать только сообщения.

### <a name="r"></a>Чтение

В этом примере ищет и загружает библиотеки RevoScaleR, если он доступен.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Если пакет найден, возвращается сообщение: «Выполнение команд успешно завершено».

+ Если пакет не может быть расположен или загружен, вы получите ошибку, содержащая текст: «есть пакет с именем «MissingPackageName»»

### <a name="python"></a>Python

Эквивалентное проверка для Python выполняется из Python оболочки, с помощью `conda` или `pip` команды. Кроме того выполните следующую инструкцию в хранимой процедуре:

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

## <a name="get-package-version"></a>Получить версию пакета

Вы можете получить R и Python пакета сведения о версии, с помощью Management Studio.

### <a name="r-package-version"></a>Версия пакета R

Эта инструкция возвращает номер версии пакета RevoScaleR и базовой версий R.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("RevoScaleR"))
print(packageDescription("base"))
'
```

### <a name="python-package-version"></a>Версия пакета Python

Эта инструкция возвращает номер версии пакета revoscalepy и версию Python.

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

+ [Установка новых пакетов R](install-additional-r-packages-on-sql-server.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Руководства, примеры, решения](../tutorials/machine-learning-services-tutorials.md)