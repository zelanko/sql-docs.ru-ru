---
title: Получение сведений о пакете Python
description: Узнайте, как получить сведения об установленных пакетах Python, включая версии и расположения установки, на SQL Server Службы машинного обучения.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bccfc97fe75a718ce76ea0d1292bfc7ea6cb6564
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69641181"
---
# <a name="get-python-package-information"></a>Получение сведений о пакете Python

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как получить сведения об установленных пакетах Python, включая версии и расположения установки, на SQL Server Службы машинного обучения. Примеры сценариев Python показывают, как составить список таких сведений о пакете, как путь и версия установки.

## <a name="default-python-library-location"></a>Расположение библиотеки Python по умолчанию

При установке машинного обучения с помощью SQL Server на уровне экземпляра создается отдельная библиотека пакетов для каждого устанавливаемого языка. В Windows библиотека экземпляров является защищенной папкой, зарегистрированной в SQL Server.

Все скрипты или код, выполняемые в базе данных на SQL Server, должны загружать функции из библиотеки экземпляров. SQL Server не может получить доступ к пакетам, установленным в других библиотеках. Это относится и к удаленным клиентам: любой код Python, выполняющийся в контексте вычислений сервера, может использовать только пакеты, установленные в библиотеке экземпляров.
Для защиты серверных ресурсов Библиотека экземпляров по умолчанию может быть изменена только администратором компьютера.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Путь к двоичным файлам Python по умолчанию:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Путь к двоичным файлам Python по умолчанию:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

Предполагается, что экземпляр SQL по умолчанию — MSSQLSERVER. Если SQL Server устанавливается как определяемый пользователем именованный экземпляр, вместо него используется указанное имя.

Выполните следующую инструкцию, чтобы проверить библиотеку по умолчанию для текущего экземпляра. Этот пример возвращает список папок, включаемых в переменную `sys.path` Python. Список содержит текущий каталог и путь к стандартной библиотеке.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

Дополнительные сведения о переменной `sys.path` и ее использовании для задания пути поиска модулей см. в разделе [путь поиска модуля](https://docs.python.org/2/tutorial/modules.html#the-module-search-path).

## <a name="default-python-packages"></a>Пакеты Python по умолчанию

Следующие пакеты Python устанавливаются с SQL Server Службы машинного обучения при выборе компонента Python во время установки.

| Пакеты | Version |  Описание |
| ---------|---------|--------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельного выполнения функций Rx для импорта и преобразования данных, моделирования, визуализации и анализа. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2 | Добавляет алгоритмы машинного обучения в Python. |

### <a name="component-upgrades"></a>Обновление компонентов

По умолчанию пакеты Python обновляются с помощью пакетов обновления и накопительных обновлений. Дополнительные пакеты и обновление полных версий основных компонентов Python возможны только при обновлении продукта или путем привязки поддержки Python к Microsoft Machine Learning Server.

Дополнительные сведения см. [в статье обновление компонентов R и Python в SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-python-packages"></a>Пакеты Python с открытым исходным кодом по умолчанию

При выборе параметра язык Python во время установки устанавливается дистрибутив Anaconda 4,2 (через Python 3,5). В дополнение к библиотекам кода Python Стандартная установка включает примеры данных, модульные тесты и примеры сценариев.

> [!IMPORTANT]
> Никогда не следует вручную перезаписывать версию Python, установленную SQL Server установки с более поздними версиями в Интернете. Пакеты Microsoft Python основаны на конкретных версиях Anaconda. Изменение установки может привести к его дестабилизации.

## <a name="list-all-installed-python-packages"></a>Список всех установленных пакетов Python

`pip` Модуль устанавливается по умолчанию и поддерживает множество операций для перечисления установленных пакетов, а также поддерживаемых стандартом Python. Можно запустить `pip` из командной строки Python, но можно также вызвать некоторые функции PIP из `sp_execute_external_script`.

В следующем примере скрипта отображается список установленных пакетов и их версий.

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
OutputDataSet = df
  '
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

## <a name="find-a-single-python-package"></a>Поиск одного пакета Python

Если вы установили пакет Python и хотите убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить хранимую процедуру для загрузки пакета и возврата сообщений.

Например, следующий код выполняет поиск `scikit-learn` пакета.
Если пакет найден, код возвращает сообщение «Package scikit-учиться установлено».

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import pip
import pkg_resources
pckg_name = "scikit-learn"
pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
  '
```

<a name="get-package-vers"></a>

В следующем примере возвращаются версии пакета revoscalepy и Python.

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

+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Получение сведений о пакете R](r-package-information.md)
+ [Установка новых пакетов R](../r/install-additional-r-packages-on-sql-server.md)
+ [Учебники по R и Python](../tutorials/machine-learning-services-tutorials.md)
