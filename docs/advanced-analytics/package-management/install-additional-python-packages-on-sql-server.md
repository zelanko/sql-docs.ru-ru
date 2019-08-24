---
title: Установка пакетов Python с PIP
description: Узнайте, как использовать PIP для Python для установки новых пакетов Python на экземпляре SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 50463f27f37f9da410d1598002989f7cea6d8158
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000775"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Установка пакетов Python с помощью склмлутилс

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается, как использовать функции в пакете [**склмлутилс**](https://github.com/Microsoft/sqlmlutils) для установки новых пакетов Python в экземпляр SQL Server службы машинного обучения. Устанавливаемые пакеты можно использовать в сценариях Python, работающих в базе данных, с помощью инструкции T-SQL [SP-Execute-External-Transact-SQL](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) .

Дополнительные сведения о расположении пакетов и путях установки см. в разделе [Получение сведений о пакете Python](../package-management/python-package-information.md).

> [!NOTE]
> Стандартная команда Python `pip install` не рекомендуется для добавления пакетов Python на SQL Server. Вместо этого используйте **склмлутилс** , как описано в этой статье.

## <a name="prerequisites"></a>Предварительные требования

+ При использовании параметра язык Python необходимо установить [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) .

+ Установите [Python](https://www.python.org/) на клиентском компьютере, который используется для подключения к SQL Server. Кроме того, может потребоваться среда разработки Python, например [Visual Studio Code](https://code.visualstudio.com/download) с [расширением Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python). 

+ Установите [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) или [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) на клиентском компьютере, который используется для подключения к SQL Server. Можно использовать другие средства управления базами данных или запросов, но в этой статье предполагается Azure Data Studio или SSMS.

### <a name="other-considerations"></a>Другие рекомендации

+ Пакеты должны быть совместимыми с Python 3,5 и запускаться в Windows.

+ Библиотека пакетов Python находится в папке Program Files своего экземпляра SQL Server и по умолчанию для установки в этой папке требуются разрешения администратора. Дополнительные сведения см. в разделе [расположение библиотеки пакетов](../package-management/python-package-information.md#default-python-library-location).

+ Установка пакета производится для каждого экземпляра. При наличии нескольких экземпляров Службы машинного обучения необходимо добавить пакет в каждый из них.

+ Перед добавлением пакета определите, подходит ли этот пакет для среды SQL Server.

  + Мы рекомендуем использовать в базе данных Python для задач, которые используют преимущества тесной интеграции с ядром СУБД, например машинное обучение, а не задачи, которые просто запрашивают базу данных.

  + При добавлении пакетов, которые помещают на сервере слишком много вычислительных операций, производительность снизится.

  + В защищенной SQL Server среде может возникнуть необходимость избежать следующих проблем:
    + Пакеты, которым требуется доступ к сети
    + Пакеты, для которых требуется повышенный доступ к файловой системе
    + Пакеты, используемые для разработки веб-приложений или других задач, не выигрывающие от использования в SQL Server

## <a name="install-sqlmlutils-on-the-client-computer"></a>Установка склмлутилс на клиентском компьютере

Чтобы использовать **склмлутилс**, необходимо сначала установить его на клиентском компьютере, который используется для подключения к SQL Server.

1. Скачайте последнюю версию ZIP-файла склмлутилс https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist с на клиентский компьютер. Не Распакуйте файл.

1. Откройте **командную строку** и выполните следующую команду, чтобы установить пакет **склмлутилс** . Замените полный путь к скачанному ZIP-файлу **склмлутилс** . в этом примере предполагается, что скачанный файл имеет `c:\temp\sqlmlutils_0.6.0.zip`значение.

   ```console
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils_0.6.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>Добавление пакета Python на SQL Server

В следующем примере вы добавите пакет [текстовых средств](https://pypi.org/project/text-tools/) в SQL Server.

### <a name="add-the-package-online"></a>Добавление пакета в режим «в сети»

Если клиентский компьютер, используемый для подключения к SQL Server, имеет доступ к Интернету, можно использовать **склмлутилс** для поиска пакета **текстовых средств** и всех зависимостей через Интернет, а затем установить пакет на экземпляр SQL Server удаленно.

1. На клиентском компьютере откройте **Python** или среду Python.

1. Используйте следующие команды для установки пакета **текстовых средств** . Замените сведения о подключении к базе данных SQL Server.

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="yoursqluser", pwd="yoursqlpassword")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>Добавление пакета в автономный режим

Если клиентский компьютер, используемый для подключения к SQL Server, не имеет подключения к Интернету, можно использовать **PIP** на компьютере с доступом в Интернет для загрузки пакета и всех зависимых пакетов в локальную папку. Затем необходимо скопировать папку на клиентский компьютер, на котором можно установить пакет в автономном режиме.

#### <a name="on-a-computer-with-internet-access"></a>На компьютере с доступом к Интернету

1. Откройте **командную строку** и выполните следующую команду, чтобы создать локальную папку, содержащую пакет **текстовых инструментов** . В этом примере создается папка `c:\temp\text-tools`.

   ```command
   pip download text-tools -d c:\temp\text-tools
   ```

1. `text-tools` Скопируйте папку на клиентский компьютер. В следующем примере предполагается, что вы `c:\temp\packages\text-tools`скопировали его в.

#### <a name="on-the-client-computer"></a>На клиентском компьютере

Используйте **склмлутилс** для установки каждого пакета (WHL-файла), который находится в локальной папке, созданной **PIP** . Не имеет значения порядок установки пакетов.

В этом примере **текстовые средства** не имеют зависимостей, поэтому для установки существует только один файл из `text-tools` папки. В отличие от этого, пакет, такой как **scikit-Graph** , имеет 11 зависимостей, поэтому в папке будут находиться 12 файлов (пакет **scikit-Graph** и 11 зависимых пакетов), и каждый из них будет установлен.

Выполните следующий скрипт Python. Замените сведения о подключении к базе данных SQL Server, укажите фактические путь к файлу и имя пакета. `sqlmlutils.SQLPackageManager` Повторите инструкцию для каждого файла пакета в папке.

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="yoursqluser", pwd="yoursqlpassword")
sqlmlutils.SQLPackageManager(connection).install("c:/temp/packages/text-tools/text_tools-1.0.0-py3-none-any.whl")
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

## <a name="remove-the-package-from-sql-server"></a>Удалить пакет из SQL Server

Если вы хотите удалить пакет **текстовых средств** , используйте следующую команду Python на клиентском компьютере, используя ту же переменную подключения, которая была определена ранее.

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>См. также

+ Сведения о том, как просмотреть пакеты Python, установленные в SQL Server Службы машинного обучения, см. в разделе [Получение сведений о пакете Python](../package-management/python-package-information.md).

+ Сведения об установке пакетов R в SQL Server Службы машинного обучения см. в разделе [Установка новых пакетов r на SQL Server](../r/install-additional-r-packages-on-sql-server.md).
