---
title: "Установка SQL Server 2017 г. для Linux | Документы Microsoft"
description: "Установка, обновление и удаление SQL Server в Linux. В этом разделе рассматриваются сценарии online, вне сети и автоматической установки."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/26/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.workload: Active
ms.openlocfilehash: 8d61ba8334d81c46643d15b38173b6b2dd2e1a93
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Руководство по установке для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом разделе объясняется, как для установки, обновления и удаления 2017 г. SQL Server в Linux. В Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) и Ubuntu поддерживается 2017 г. SQL Server. Она также доступна как образ Docker, который можно запустить на подсистема Docker в Linux или Docker для Windows или Mac.

> [!TIP]
> Чтобы быстро приступить к работе, перейти к одной части краткого руководства для [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), или [Docker](quickstart-install-connect-docker.md).

## <a id="supportedplatforms"></a>Поддерживаемые платформы

2017 г. SQL Server поддерживается на следующих платформах Linux:

| Платформа | Поддерживаемые версии | Получить
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 или 7.4 | [Получить RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
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

Если вы используете **сетевой файловой системы (NFS)** удаленные общие ресурсы в рабочей среде, ознакомьтесь со следующими требованиями поддержки:

- Использование NFS версии **4.2 или более поздней версии**. NFS более ранних версий не поддерживают необходимые компоненты, такие как fallocate и создания разреженный файл, общие для современных файловых систем.
- Найдите только **/var/opt/mssql** каталогов на подключения NFS. Другие файлы, такие как системные файлы SQL Server и не поддерживаются.
- Убедитесь, что клиенты NFS использовать параметр «nolock» при подключении к удаленной общей папке.

## <a id="platforms"></a>Установка SQL Server

SQL Server в Linux можно установить из командной строки. Соответствующие инструкции см. в следующих учебниках краткое руководство:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

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

## <a id="versioncheck"></a>Проверьте установленную версию SQL Server

Чтобы проверить текущую версию и выпуск SQL Server в Linux, используйте следующую процедуру:

1. Если еще не установлен, установите [средства командной строки SQL Server](sql-server-linux-setup-tools.md).

1. Используйте **sqlcmd** для выполнения команды Transact-SQL, отображающий SQL Server версии и выпуска.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

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

## <a id="repositories"></a>Настройка исходных репозиториев

При установке или обновлении SQL Server, можно получить последнюю версию SQL Server из репозитория настроенных Microsoft.

### <a name="repository-options"></a>Параметры хранилища

Существует два основных типа хранилища для каждого распределения.

- **Накопительный пакет обновления (CU)**: репозиторий накопительное обновление (CU) содержит пакеты для базовой версии SQL Server и исправления или улучшения версии. Накопительные пакеты обновления относятся только к версии, например 2017 г. SQL Server. Их появления в обычных ритме.

- **GDR**: GDR репозитория пакетов для базовой версии SQL Server и только важные исправления и обновления для системы безопасности содержит версии. Эти обновления также добавляются в следующий выпуск CU.

Каждое CU и GDR содержит полный пакет SQL Server и все последующие обновления для этого репозитория. Обновление с версии GDR на текущую версию поддерживается изменение настроенного хранилища SQL Server. Вы также можете [понизить](#rollback) для любого из выпусков в ваш основной номер версии (например: 2017 г.). Обновление с накопительным пакетом обновления версии GDR не поддерживается.

### <a name="check-your-configured-repository"></a>Проверьте настроенные репозиторий

Если вы хотите проверить настроен репозиторий, используйте следующие методики зависят от платформы.

| Платформа | Процедура |
|-----|-----|
| RHEL | 1. Просматривать файлы в **/etc/yum.repos.d** каталога:`sudo ls /etc/yum.repos.d`<br/>2. Найдите файл, который настраивает каталог SQL Server, такие как **mssql server.repo**.<br/>3. Распечатать содержимое файла:`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4. **Имя** свойство является настроенного репозитория.|
| SLES | 1. Выполните следующую команду:`sudo zypper info mssql-server`<br/>2. **Репозитория** свойство является настроенного репозитория. |
| Ubuntu | 1. Выполните следующую команду:`sudo cat /etc/apt/sources.list`<br/>2. Проверьте URL-адреса для сервера mssql пакета. |

В конец URL-адрес репозитория проверяет тип репозитория:

- **MSSQL сервера**: предварительный просмотр репозитория.
- **MSSQL server 2017 г.**: CU репозитория.
- **MSSQL-server-2017 г gdr**: GDR репозитория.

### <a name="change-the-source-repository"></a>Измените исходный репозиторий

Чтобы настроить репозитории CU или GDR, выполните следующие действия:

> [!NOTE]
> [Быстрого запуска учебники](#platforms) настройте CU репозитория. При выполнении этих учебников, выполните следующие действия, чтобы продолжить использование репозитории CU необязательно. Эти шаги необходимы только для изменения вашего настроенного репозитория.

1. При необходимости удалите ранее настроенного репозитория.

   | Платформа | Хранилище | Команда удаления репозитория |
   |---|---|---|
   | RHEL | **все** | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | **CTP-ВЕРСИИ** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | | **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
   | | **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|
   | Ubuntu | **CTP-ВЕРСИИ** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
   | | **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
   | | **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

1. Для **Ubuntu только**, Импорт ключей GPG общедоступный репозиторий.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Настройте новый репозиторий.

   | Платформа | Хранилище | Command |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [Установка](#platforms) или [обновление](#upgrade) SQL Server и все связанные пакеты из нового репозитория.

   > [!IMPORTANT]
   > На этом этапе, если вы решили использовать один из учебников по установке, такие как [по основам](#platforms), помните, что вы настроили целевой репозиторий. В учебниках по не нужно повторять этот шаг. Это особенно важно, если настроить хранилище GDR, так как статьи краткого руководства используйте CU репозитория.

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
