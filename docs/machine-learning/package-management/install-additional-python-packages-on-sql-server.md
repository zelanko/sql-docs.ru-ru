---
title: Установка пакетов Python с помощью sqlmlutils
description: Узнайте, как использовать Python pip для установки новых пакетов Python на экземпляре Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/30/2020
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4e72ded2e2f2a51805403132c662bff3d70c97ce
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487122"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Установка пакетов Python с помощью sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается использование функций в пакете [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) для установки новых пакетов Python в экземпляре Служб машинного обучения SQL Server. Устанавливаемые пакеты можно использовать в сценариях Python, выполняющихся в базе данных, с помощью инструкции T-SQL [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Дополнительные сведения о расположении пакетов и путях установки см. в разделе [Получение сведений о пакете Python](../package-management/python-package-information.md).

> [!NOTE]
> Для добавления пакетов Python в SQL Server 2019 не рекомендуется выполнять стандартную команду Python `pip install`. Вместо нее используйте **sqlmlutils**, как описано в этой статье.

## <a name="prerequisites"></a>Предварительные требования

+ Необходимо установить [Службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) с параметром языка Python.

+ Установите [python](https://www.python.org/) на клиентском компьютере, который используется для подключения к SQL Server. Кроме того, может потребоваться среда разработки Python, например [Visual Studio Code](https://code.visualstudio.com/download) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python). 

+ Установите [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) или [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) на клиентском компьютере, который используется для подключения к SQL Server. Можно использовать другие средства управления базами данных или инструменты работы с запросами, но в этой статье применяются Azure Data Studio или SSMS.

### <a name="other-considerations"></a>Другие замечания

+ Пакеты должны соответствовать используемой версии Python. Дополнительные сведения о версии Python, включенной в каждую версию SQL Server, см. в разделе о [версиях Python и R в статье с общими сведениями о Службах машинного обучения SQL Server (Python и R)](../sql-server-machine-learning-services.md#versions).

+ Библиотека пакетов Python находится в папке Program Files своего экземпляра SQL Server и по умолчанию для установки в этой папке требуются права администратора. Дополнительные сведения см. в статье [Расположение библиотеки пакетов](../package-management/python-package-information.md#default-python-library-location).

+ Установка пакета производится для каждого экземпляра. При наличии нескольких экземпляров Служб машинного обучения необходимо добавить пакет в каждый из них.

+ Перед добавлением пакета определите, подходит ли этот пакет для среды SQL Server.

  + Мы рекомендуем использовать Python в базе данных для задач, которые используют преимущества тесной интеграции с ядром СУБД, например машинное обучение, а не задач, которые просто отправляют запросы в базу данных.

  + Если вы добавляете пакеты, которые приводят к слишком большой вычислительной нагрузке на сервер, производительность снизится.

  + В защищенной среде SQL Server может потребоваться отказаться от следующих пакетов:
    + пакеты, которым требуется доступ к сети;
    + пакеты, которым требуется доступ к файловой системе с повышенными правами;
    + пакеты, используемые для веб-разработки или других задач, малоэффективных в SQL Server.

## <a name="install-sqlmlutils-on-the-client-computer"></a>Установка пакета sqlmlutils на клиентском компьютере

Сначала пакет **sqlmlutils** необходимо установить на клиентском компьютере, который используется для подключения к SQL Server. Убедитесь, что установили `pip`. Дополнительные сведения об установке pip см. в [этой статье](https://pip.pypa.io/en/stable/installing/).

1. Скачайте последнюю версию ZIP-файла **sqlmlutils** со страницы https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist на клиентский компьютер. Не распаковывайте файл.

1. Откройте **командную строку** и выполните следующие команды для установки пакета **sqlmlutils**. Замените полный путь к скачанному ZIP-файлу **sqlmlutils** (в этом примере предполагается, что загружен файл `c:\temp\sqlmlutils-1.0.0.zip`).

   ```console
   pip install "pymssql<3.0"
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils-1.0.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>Добавление пакета Python в SQL Server

В следующем примере вы добавите пакет [text-tools](https://pypi.org/project/text-tools/) в SQL Server.

### <a name="add-the-package-online"></a>Добавление пакета в сетевом режиме

Если клиентский компьютер, используемый для подключения к SQL Server, имеет доступ к Интернету, с помощью пакета **sqlmlutils** можно найти пакет **text-tools** и все зависимости через Интернет, а затем удаленно установить пакет в экземпляре SQL Server.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

1. На клиентском компьютере откройте **Python** или среду Python.

1. Для установки пакета **text-tools** используйте следующие команды. Замените сведения о подключении к базе данных SQL Server (если используется проверка подлинности Windows, вам не нужны параметры `uid` и `pwd`).

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

1. На клиентском компьютере откройте **Python** или среду Python.

1. Для установки пакета **text-tools** используйте следующие команды. Подставьте собственные значения для подключения к базе данных SQL Server.

::: moniker-end

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="server", database="database", uid="username", pwd="password")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>Добавление пакета в автономном режиме

Если клиентский компьютер, используемый для подключения к SQL Server, не имеет подключения к Интернету, можно использовать **pip** на компьютере с доступом в Интернет для загрузки пакета и всех зависимых пакетов в локальную папку. Затем папка копируется на клиентский компьютер для установки в автономном режиме.

#### <a name="on-a-computer-with-internet-access"></a>На компьютере с доступом к Интернету

1. Откройте **командную строку** и выполните следующую команду, чтобы создать локальную папку, содержащую пакет **text-tools**. В этом примере создается папка `c:\temp\text-tools`.

   ```console
   pip download text-tools -d c:\temp\text-tools
   ```

1. Скопируйте папку `text-tools` на клиентский компьютер. В следующем примере предполагается, что вы скопировали ее в `c:\temp\packages\text-tools`.

#### <a name="on-the-client-computer"></a>На клиентском компьютере

Используйте **sqlmlutils**, чтобы установить каждый пакет (WHL-файл), который находится в локальной папке, созданной с помощью **pip**. Порядок установки пакетов не имеет значения.

В этом примере **text-tools** не имеет зависимостей, поэтому нужно установить только один файл из папки `text-tools`. Зато, например, у пакета **scikit-plot** имеется 11 зависимостей, поэтому в папке будет находиться 12 файлов (**scikit-plot** и 11 зависимых пакетов), и каждый из них будет установлен.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

Выполните следующий скрипт Python. Замените фактический путь к файлу и имя пакета, а также сведения о подключении к базе данных SQL Server (если используется проверка подлинности Windows, вам не нужны параметры `uid` и `pwd`). Повторите инструкцию `sqlmlutils.SQLPackageManager` для каждого файла пакета в папке.

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

Выполните следующий скрипт Python. Замените фактический путь к файлу и имя пакета, а также сведения о подключении к базе данных SQL Server. Повторите инструкцию `sqlmlutils.SQLPackageManager` для каждого файла пакета в папке.

::: moniker-end

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="username", pwd="password"))
sqlmlutils.SQLPackageManager(connection).install("text_tools-1.0.0-py3-none-any.whl")
```

## <a name="use-the-package-in-sql-server"></a>Использование пакета в SQL Server

Теперь пакет можно использовать в скрипте Python в SQL Server. Пример:

```python
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
from text_tools.finders import find_best_string
corpus = "Lorem Ipsum text"
query = "Ipsum"
first_match = find_best_string(query, corpus)
print(first_match)
  '
```

## <a name="remove-the-package-from-sql-server"></a>Удаление пакета из SQL Server

Если вы хотите удалить пакет **text-tools**, используйте следующую команду Python на клиентском компьютере, указав переменную подключения, которая была определена ранее.

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>См. также раздел

+ Сведения о том, как просмотреть пакеты Python, установленные в Службах машинного обучения SQL Server, см. в разделе [Получения сведений о пакете Python](../package-management/python-package-information.md).

+ Сведения об установке пакетов R в Службы машинного обучения SQL Server см. в разделе [Установка новых пакетов R в SQL Server](install-additional-r-packages-on-sql-server.md).
