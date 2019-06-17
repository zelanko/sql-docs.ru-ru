---
title: Установка программ командной строки SQL Server в Linux
titleSuffix: SQL Server
description: В этой статье описывается установка средств SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/07/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.openlocfilehash: d6e10c384d799ee416facee150e5e2318b381ea6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66810280"
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Установка sqlcmd и bcp средства командной строки SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Средства командной строки, драйверы Microsoft ODBC и их зависимости, установите следующие действия. **Mssql-tools** пакет содержит:

- **sqlcmd**: Программа командной строки запроса.
- **BCP**: Служебная программа для массового импорта экспорта.

Установите средства для выбранной платформы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

В этой статье описывается установка средств командной строки. Если вы ищете примеры использования **sqlcmd** или **bcp**, см. в разделе [ссылки](#next-steps) в конце этого раздела.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Установите средства на RHEL 7

Выполните следующие действия для установки **mssql-tools** в Red Hat Enterprise Linux. 

1. Перейти в режим суперпользователя.

   ```bash
   sudo su
   ```

1. Скачайте файл конфигурации репозитория Microsoft Red Hat.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Выйти из режима суперпользователя.

   ```bash
   exit
   ```

1. При наличии предыдущей версии **mssql-tools** установлен, удалите старые пакеты unixODBC.

   ```bash
   sudo yum remove mssql-tools unixODBC-utf16-devel
   ```

1. Выполните следующие команды для установки **mssql-tools** с пакетом разработчика unixODBC.

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Для обновления до последней версии **mssql-tools** выполните следующие команды:
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Необязательный**: Добавить `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

   Чтобы сделать **sqlcmd и bcp** доступен из оболочки bash для сеансов входа изменить ваш **путь** в **~/.bash_profile** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы сделать **sqlcmd и bcp** доступен из оболочки bash для интерактивного/сеансов без входа, изменить **путь** в **~/.bashrc** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Установите средства на Ubuntu 16.04

Выполните следующие действия для установки **mssql-tools** в Ubuntu. 

1. Импорт общедоступного репозитория ключей GPG.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Зарегистрируйте репозиторий Microsoft Ubuntu.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Обновите список источников и запустите команду установки с пакетом разработчика unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Для обновления до последней версии **mssql-tools** выполните следующие команды:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Необязательный**: Добавить `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

   Чтобы сделать **sqlcmd и bcp** доступен из оболочки bash для сеансов входа изменить ваш **путь** в **~/.bash_profile** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы сделать **sqlcmd и bcp** доступен из оболочки bash для интерактивного/сеансов без входа, изменить **путь** в **~/.bashrc** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Установка средств в SLES 12

Выполните следующие действия для установки **mssql-tools** в SUSE Linux Enterprise Server. 

1. Добавьте репозиторий Microsoft SQL Server Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Установка **mssql-tools** с пакетом разработчика unixODBC.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Для обновления до последней версии **mssql-tools** выполните следующие команды:
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Необязательный**: Добавить `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

   Чтобы сделать **sqlcmd и bcp** доступен из оболочки bash для сеансов входа изменить ваш **путь** в **~/.bash_profile** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы сделать **sqlcmd и bcp** доступен из оболочки bash для интерактивного/сеансов без входа, изменить **путь** в **~/.bashrc** файл с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> Установите средства на macOS

Предварительный просмотр **sqlcmd** и **bcp** теперь доступен в Mac OS. Дополнительные сведения см. в разделе [объявления](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

*Установка [Homebrew](https://brew.sh) Если у вас его еще нет:*

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Чтобы установить средства для Mac El Capitan и Sierra, используйте следующие команды:

```
# brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install mssql-tools
#for silent install: 
#HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=y brew install mssql-tools
```

## <a id="docker"></a> Docker

Средства командной строки SQL Server включены в образ Docker. При подключении к образу с интерактивной командной строке средства можно запустить локально.

## <a name="offline-installation"></a>Автономная установка

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

1. Во-первых, найдите и скопируйте **mssql-tools** пакет для вашего дистрибутива Linux:

   | Дистрибутив Linux | **MSSQL-tools** размещение пакета |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools) |

1. Также найдите и скопируйте **msodbcsql** пакет, который представляет зависимость. **Msodbcsql** пакета также имеет зависимость от либо **unixODBC разраб** (Red Hat и SLES) или **unixodbc-dev** (Ubuntu). Расположение **msodbcsql** пакетов, перечислены в следующей таблице:

   | Дистрибутив Linux | Расположение пакетов ODBC |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [**msodbcsql**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql)<br/>[**unixodbc-dev**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/u/unixodbc/) |

1. **Переместить скачанные пакеты на компьютер Linux**. Если вы использовали другую машину, чтобы скачать пакеты, один из способов перемещения пакетов на компьютер Linux, — с **scp** команда.

1. **Установка пакетов и**: Установка **mssql-tools** и **msodbc** пакетов. Если все ошибки зависимостей, их можно пропустите до следующего шага.

    | Платформа | Команды для установки пакета |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-<version>.rpm`<br/>`sudo yum localinstall mssql-tools-<version>.rpm` |
    | SLES | `sudo zypper install msodbcsql-<version>.rpm`<br/>`sudo zypper install mssql-tools-<version>.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_<version>.deb`<br/>`sudo dpkg -i mssql-tools_<version>.deb` |

1. **Разрешить отсутствующие зависимости**: Возможно, отсутствуют зависимости на этом этапе. В противном случае этот шаг можно пропустить. В некоторых случаях необходимо вручную найти и установить эти зависимости.

    Для пакетов RPM можно проверить необходимые зависимости, выполнив следующие команды:

    ```bash
    rpm -qpR msodbcsql-<version>.rpm
    rpm -qpR mssql-tools-<version>.rpm
    ```

    Для пакетов Debian, если у вас есть доступ для утвержденных репозиториев, содержащий эти зависимости, самым простым решением является использование **apt-get** команды:

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Эта команда завершает установку пакетов, а также SQL Server.

    Если это не работает для Debian пакета, можно проверить необходимые зависимости, выполнив следующие команды:

    ```bash
    dpkg -I msodbcsql_<version>_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_<version>_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Следующие шаги

Пример использования **sqlcmd** для подключения к SQL Server и создать базу данных, см. в одном из следующих кратких руководств:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустить в Docker](quickstart-install-connect-ubuntu.md)

Пример использования **bcp** для массового импорта и экспорта данных, см. в разделе [массовое копирование данных в SQL Server в Linux](sql-server-linux-migrate-bcp.md).
