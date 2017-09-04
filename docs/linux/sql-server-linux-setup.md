---
title: "Установка SQL Server 2017 г. для Linux | Документы Microsoft"
description: "Установка, обновление и удаление SQL Server в Linux. В этом разделе рассматриваются сценарии online, вне сети и автоматической установки."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.translationtype: MT
ms.sourcegitcommit: 303d3b74da3fe370d19b7602c0e11e67b63191e7
ms.openlocfilehash: f746037f695301881ce9a993f3d556db44f44292
ms.contentlocale: ru-ru
ms.lasthandoff: 08/29/2017

---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Руководство по установке для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом разделе объясняется, как для установки, обновления и удаления 2017 г. SQL Server в Linux. В Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) и Ubuntu поддерживается SQL Server, RC2 2017 г. Она также доступна как образ Docker, который можно запустить на подсистема Docker в Linux или Docker для Windows или Mac.

> [!TIP]
> Чтобы быстро приступить к работе, перейти к одной части краткого руководства для [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), или [Docker](quickstart-install-connect-docker.md).

## <a id="supportedplatforms"></a>Поддерживаемые платформы

2017 г. SQL Server поддерживается на следующих платформах Linux:

| Платформа | Поддерживаемые версии | Получить
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 | [Получить RHEL 7.3](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | с пакетом обновления 2 для версии 12 | [Получить SP2 SLES версии 12](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Получить Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Подсистема docker** | 1.8+ | [Получить Docker](http://www.docker.com/products/overview)

## <a id="system"></a>Требования к системе

2017 г. SQL Server имеет следующие требования к системе для Linux:

|||
|-----|-----|
| **Память** | 3,25 ГБ |
| **Файловая система** | **XFS** или **EXT4** (других файловых систем, таких как **BTRFS**, не поддерживаются) |
| **Место на диске** | 6 ГБ |
| **Быстродействие процессора** | 2 ГГц |
| **Процессорных ядер** | 2 ядра |
| **Тип процессора** | x64 совместим только |

> [!NOTE]
> Модуль SQL Server был протестирован до 1 ТБ памяти в данный момент.

## <a id="platforms"></a>Установка SQL Server

SQL Server в Linux можно установить из командной строки. Соответствующие инструкции см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)

## <a id="upgrade"></a>Обновление SQL Server

Чтобы обновить **mssql server** пакета до последней версии, используйте один из приведенных ниже команд, в зависимости от используемой платформы:

| Платформа | Выполнение команд пакета обновления |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Эти команды загрузить последние пакет и замените двоичные файлы, расположенные в группе `/opt/mssql/`. Созданное пользователем базы данных и системных баз данных не зависит от этой операции.

## <a id="rollback"></a>Откат SQL Server

Для отката или возврат к предыдущей версии SQL Server в предыдущем выпуске выполните следующие действия:

1. Укажите номер версии для пакета SQL Server, который вы хотите перейти на. Список номеров пакета см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

1. Перейти к предыдущей версии SQL Server. В приведенных ниже команд, замените `<version_number>` с номером версии SQL Server, определенный на шаге 1.

   | Платформа | Выполнение команд пакета обновления |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Она поддерживается только может понижаться до выпуска в пределах той же основной версии, например 2017 г. SQL Server.

> [!IMPORTANT]
> Возврат к предыдущей версии поддерживаются только между RC2 и версии-кандидата 1 в данный момент.

## <a id="uninstall"></a>Удаление SQL Server

Чтобы удалить **mssql server** пакета в Linux, используйте один из приведенных ниже команд, в зависимости от используемой платформы:

| Платформа | Команды удаления пакета |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

После удаления пакета не приводит к удалению файлов созданной базе данных. Если вы хотите удалить файлы базы данных, используйте следующую команду:

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a>Автоматическая установка

Можно выполнить автоматическую установку следующим образом:

- Необходимо выполнить начального действия в [быстрого запуска учебники](#platforms) репозиториями регистрация и установка SQL Server.
- При запуске `mssql-conf setup`, задайте [переменных среды](sql-server-linux-configure-environment-variables.md) и использовать `-n` (без запроса) параметра.

В следующем примере настраивается Developer edition, SQL Server с **MSSQL_PID** переменной среды. Он также принимает условия лицензионного соглашения (**ACCEPT_EULA**) и задает пароль пользователя SA (**MSSQL_SA_PASSWORD**). `-n` Параметр выполняет unprompted установку, где значения конфигурации извлекаются из переменных среды.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

Можно также создать скрипт, который выполняет другие действия. Например можно установить другие пакеты SQL Server.

Более подробный пример сценария см. следующие примеры:

- [Red Hat сценарий автоматической установки](sample-unattended-install-redhat.md)
- [SUSE сценарий автоматической установки](sample-unattended-install-suse.md)
- [Ubuntu сценарий автоматической установки](sample-unattended-install-ubuntu.md)

## <a id="offline"></a>Автономную установку

Если компьютер Linux не имеет доступа к сети хранилища, используемых в [краткие](#platforms), можно непосредственно загрузить файлы пакета. Эти пакеты находятся в хранилище Майкрософт по адресу [https://packages.microsoft.com](https://packages.microsoft.com).

> [!TIP]
> После успешной установки шаги, указанные в краткие руководства необязательно для загрузки или вручную установить ниже пакетов. Этот раздел предназначен только для сценария автономной работы.

1. **Загрузите пакет ядра базы данных для вашей платформы**. Найти ссылки для загрузки пакета в разделе сведений пакета [заметки о выпуске](sql-server-linux-release-notes.md).

1. **Переместить загруженного пакета на компьютер Linux**. Если используется другой компьютер для загрузки пакетов, один из способов перемещения пакетов на компьютер Linux связана с **scp** команды.

1. **Установить пакет ядра базы данных**. Используйте одну из следующих команд в зависимости от используемой платформы. Замените точное имя, загруженный в этом примере имя файла пакета.

   | Платформа | Команда удаления пакета |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > Можно также установить пакеты RPM (RHEL и SLES) с `rpm -ivh` команда, но команды в предыдущей таблице зависимости автоматически устанавливать доступные утвержденный репозиториев.

1. **Разрешить отсутствующие зависимости**: возможно, на этом этапе отсутствующих зависимостей. В противном случае этот шаг можно пропустить. В Ubuntu — команду, если у вас есть доступ для утвержденных репозиториев, содержащий эти зависимости простейшим решением является использование `apt-get -f install` команды. Эта команда также завершается установка SQL Server. Чтобы вручную проверить зависимости, используйте следующие команды:

   | Платформа | Команда list зависимости |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   После устранения отсутствующие зависимости, попытайтесь установить mssql сервера пакета еще раз.

1. **Завершите установку SQL Server**. Используйте **mssql conf** для завершения работы программы установки SQL Server:

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>Следующие шаги

После установки можно также установить другие дополнительные пакеты SQL Server.

- [Средства командной строки SQL Server](sql-server-linux-setup-tools.md)
- [SQL Server, агент](sql-server-linux-setup-sql-agent.md)
- [Полнотекстовый поиск SQL Server](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

Подключитесь к экземпляру SQL Server, чтобы начать создание и управление базами данных. Чтобы приступить к работе, см. в учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)

