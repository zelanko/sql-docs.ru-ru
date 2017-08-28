---
title: "Установка средств командной строки SQL Server в Linux | Документы Microsoft"
description: "В этом разделе описывается установка средства SQL Server в Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 130da2409070f0acfda0bf78fcf2c4326bbeec92
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Установите sqlcmd и bcp средства командной строки SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Следующие шаги установки программы командной строки, драйверы Microsoft ODBC и их зависимости. **Mssql средства** пакет содержит:

- **sqlcmd**: программа командной строки запроса.
- **BCP**: массового импорта экспорта программы.

Установите средства для вашей платформы.

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

В этом разделе описывается установка средств командной строки. Если вам нужны дополнительные примеры использования **sqlcmd** или **bcp**, в разделе [ссылки](#next-steps) в конце этого раздела.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Установить средства на RHEL 7

Выполните следующие действия для установки **mssql средства** в Red Hat Enterprise Linux. 

1. Перейдите в режим суперпользователя.

   ```bash
   sudo su
   ```

1. Загрузите файл конфигурации Microsoft Red Hat репозитория.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Выход из режима суперпользователя.

   ```bash
   exit
   ```

1. При наличии предыдущей версии **mssql средства** установлены, удалите старую unixODBC пакеты.

   ```bash
   sudo yum update
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Выполните следующие команды для установки **mssql средства** комплект разработчика unixODBC.

   ```bash
   sudo yum update
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Для обновления до последней версии **mssql средства** выполните следующие команды:
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Необязательный**: добавление `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

   Чтобы сделать **sqlcmd и bcp** доступны в оболочке bash для сеансов входа изменения вашей **путь** в **~/.bash_profile** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы сделать **sqlcmd и bcp** доступен в оболочке bash для интерактивной и не-сеансы входа в систему, изменить **путь** в **~/.bashrc** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Установить средства на Ubuntu 16.04

Выполните следующие действия для установки **mssql средства** на Ubuntu. 

1. Импорт ключей GPG общедоступный репозиторий.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Регистрация репозитория Ubuntu корпорации Майкрософт.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Обновление списка источников и выполните команду установки пакета разработчика unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Для обновления до последней версии **mssql средства** выполните следующие команды:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Необязательный**: добавление `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

   Чтобы сделать **sqlcmd и bcp** доступны в оболочке bash для сеансов входа изменения вашей **путь** в **~/.bash_profile** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы сделать **sqlcmd и bcp** доступен в оболочке bash для интерактивной и не-сеансы входа в систему, изменить **путь** в **~/.bashrc** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Установить средства на SLES 12

Выполните следующие действия для установки **mssql средства** на SUSE Linux Enterprise Server. 

1. Добавьте репозиторий Microsoft SQL Server Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Установка **mssql средства** комплект разработчика unixODBC.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Для обновления до последней версии **mssql средства** выполните следующие команды:
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Необязательный**: добавление `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

   Чтобы сделать **sqlcmd и bcp** доступны в оболочке bash для сеансов входа изменения вашей **путь** в **~/.bash_profile** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы сделать **sqlcmd и bcp** доступен в оболочке bash для интерактивной и не-сеансы входа в систему, изменить **путь** в **~/.bashrc** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a>Установить средства на macOS

Предварительный просмотр **sqlcmd** и **bcp** теперь доступен на macOS. Дополнительные сведения см. в разделе [объявления](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

Чтобы установить средства для Mac El Capitan и Сьерра, используйте следующие команды:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
#brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox mssql-tools
#for silent install: 
#ACCEPT_EULA=y brew install --no-sandbox mssql-tools
```

## <a id="docker"></a>Docker

Начиная с SQL Server 2017 г CTP 2.0, средства командной строки SQL Server включаются в образе Docker. При присоединении к образу с интерактивной командной строки средства можно выполнять локально.

## <a name="offline-installation"></a>Автономная установка

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

В следующей таблице приведены расположение для последних пакетов средств:

| Пакет средств | Версия | Загрузить |
|-----|-----|-----|
| Пакет средств Red Hat об/мин | 14.0.5.0-1 | [пакет средств MSSQL об/мин](https://packages.microsoft.com/rhel/7.3/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Пакет средств SLES об/мин | 14.0.5.0-1 | [пакет средств MSSQL об/мин](https://packages.microsoft.com/sles/12/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian средств пакета | 14.0.5.0-1 | [пакет Debian MSSQL средства](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |
| Ubuntu 16.10 Debian средств пакета | 14.0.5.0-1 | [пакет Debian MSSQL средства](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |

Эти пакеты зависят от **msodbcsql**, который необходимо сначала установить. **Msodbcsql** пакет также имеет зависимость от либо **unixODBC devel** (RPM) или **unixodbc-dev** (Debian). Расположение **msodbcsql** пакетов, перечислены в следующей таблице:

| пакет msodbcsql | Версия | Загрузить |
|-----|-----|-----|
| Пакет msodbcsql Red Hat RPM | 13.1.6.0-1 | [пакет RPM msodbcsql](https://packages.microsoft.com/rhel/7.3/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Пакет SLES RPM msodbcsql | 13.1.6.0-1 | [пакет RPM msodbcsql](https://packages.microsoft.com/sles/12/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Пакет Debian msodbcsql Ubuntu 16.04 | 13.1.6.0-1 | [пакет Debian msodbcsql](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |
| Пакет Debian msodbcsql Ubuntu 16.10 | 13.1.6.0-1 | [пакет Debian msodbcsql](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |

Чтобы вручную установить эти пакеты, выполните следующие действия:

1. **Переместить загруженные пакеты на компьютер Linux**. Если используется другой компьютер для загрузки пакетов, один из способов перемещения пакетов на компьютер Linux связана с **scp** для команды.

1. **Установить пакеты и**: Установка **mssql средства** и **msodbc** пакетов. Если возникли ошибки зависимостей, их необходимо игнорировать до следующего шага.

    | Платформа | Команды установки пакета |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo yum localinstall mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | SLES | `sudo zypper install msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo zypper install mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_13.1.6.0-1_amd64.deb`<br/>`sudo dpkg -i mssql-tools_14.0.5.0-1_amd64.deb` |

1. **Разрешить отсутствующие зависимости**: возможно, на этом этапе отсутствующих зависимостей. В противном случае этот шаг можно пропустить. В некоторых случаях необходимо вручную найти и установить эти зависимости.

    Для пакетов RPM вы можете проверить необходимые зависимости с помощью следующих команд:

    ```bash
    rpm -qpR msodbcsql-13.1.6.0-1.x86_64.rpm
    rpm -qpR mssql-tools-14.0.5.0-1.x86_64.rpm
    ```

    Debian пакеты, если у вас есть доступ для утвержденных репозиториев, содержащий эти зависимости, простейшим решением является использование **apt get** команды:

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Эта команда завершает установку пакетов SQL Server также.

    Если это не сработает для Debian пакета, можно проверить необходимые зависимости с помощью следующих команд:

    ```bash
    dpkg -I msodbcsql_13.1.6.0-1_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_14.0.5.0-1_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Следующие шаги

Пример использования **sqlcmd** для подключения к SQL Server и создать базу данных, см. один из следующих быстрого запуска учебники:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-ubuntu.md)

Пример использования **bcp** для массового импорта и экспорта данных, в разделе [массового копирования данных в SQL Server в Linux](sql-server-linux-migrate-bcp.md).

