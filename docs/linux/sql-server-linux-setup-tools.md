---
title: Установка программ командной строки SQL Server в Linux
titleSuffix: SQL Server
description: В этой статье описывается установка средств SQL Server в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 06/07/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.openlocfilehash: 23610c3144c7cf03a4c93be900bfc60a449448ed
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78340426"
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Установка программ командной строки SQL Server sqlcmd и bcp в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ниже приведены инструкции по установке программ командной строки, драйверов ODBC Майкрософт и их зависимостей. Пакет **mssql-tools** содержит следующие компоненты:

- **sqlcmd** — программа командной строки для выполнения запросов;
- **bcp** — служебная программа для массового импорта и экспорта.

Установите программы для своей платформы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

В этой статье описывается установка программ командной строки. Примеры использования **sqlcmd** или **bcp** можно найти по [ссылкам](#next-steps) в конце этой статьи.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Установка средств в RHEL 7

Чтобы установить **mssql-tools** в Red Hat Enterprise Linux, выполните указанные ниже действия. 

1. Перейдите в режим суперпользователя.

   ```bash
   sudo su
   ```

1. Скачайте файл конфигурации репозитория Microsoft Red Hat.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Выйдите из режима суперпользователя.

   ```bash
   exit
   ```

1. Если установлена предыдущая версия **mssql-tools**, удалите все старые пакеты unixODBC.

   ```bash
   sudo yum remove mssql-tools unixODBC-utf16-devel
   ```

1. Чтобы установить **mssql-tools** с помощью пакета разработчика unixODBC, выполните приведенные ниже команды.

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Чтобы произвести обновление до последней версии **mssql-tools**, выполните следующие команды:
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Необязательно**: Добавьте путь `/opt/mssql-tools/bin/` в переменную среды **PATH** в оболочке bash.

   Чтобы программы **sqlcmd и bcp** были доступны из оболочки bash в рамках сеансов входа в систему, измените переменную среды **PATH** в файле **~/.bash_profile** с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы программы **sqlcmd и bcp** были доступны из оболочки bash в рамках интерактивных сеансов и сеансов без входа в систему, измените переменную среды **PATH** в файле **~/.bashrc** с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Установка средств в Ubuntu 16.04

Чтобы установить **mssql-tools** в Ubuntu, выполните указанные ниже действия. 

1. Импортируйте открытые ключи GPG из репозитория.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Зарегистрируйте репозиторий Ubuntu для Майкрософт.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Обновите список источников и выполните команду установки с помощью пакета разработчика unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Чтобы произвести обновление до последней версии **mssql-tools**, выполните следующие команды:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Необязательно**: Добавьте путь `/opt/mssql-tools/bin/` в переменную среды **PATH** в оболочке bash.

   Чтобы программы **sqlcmd и bcp** были доступны из оболочки bash в рамках сеансов входа в систему, измените переменную среды **PATH** в файле **~/.bash_profile** с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы программы **sqlcmd и bcp** были доступны из оболочки bash в рамках интерактивных сеансов и сеансов без входа в систему, измените переменную среды **PATH** в файле **~/.bashrc** с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Установка средств в SLES 12

Чтобы установить **mssql-tools** в SUSE Linux Enterprise Server, выполните указанные ниже действия. 

1. Добавьте репозиторий Microsoft SQL Server в Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Установите **mssql-tools** с помощью пакета разработчика unixODBC.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Чтобы произвести обновление до последней версии **mssql-tools**, выполните следующие команды:
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Необязательно**: Добавьте путь `/opt/mssql-tools/bin/` в переменную среды **PATH** в оболочке bash.

   Чтобы программы **sqlcmd и bcp** были доступны из оболочки bash в рамках сеансов входа в систему, измените переменную среды **PATH** в файле **~/.bash_profile** с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Чтобы программы **sqlcmd и bcp** были доступны из оболочки bash в рамках интерактивных сеансов и сеансов без входа в систему, измените переменную среды **PATH** в файле **~/.bashrc** с помощью следующей команды:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> Установка средств в macOS

В macOS доступна предварительная версия программ **sqlcmd** и **bcp**. Дополнительные сведения см. в [объявлении о выпуске](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

*Установите программу [Homebrew](https://brew.sh), если ее еще нет:*

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

Если [SQL Server выполняется в контейнере Docker](quickstart-install-connect-docker.md), программы командной строки SQL Server уже включены в образ контейнера SQL Server в Linux. Если подключиться к запущенному контейнеру с помощью интерактивной оболочки bash, можно запускать программы локально.

## <a name="offline-installation"></a>Автономная установка

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

1. Сначала найдите и скопируйте пакет **mssql-tools** для своего дистрибутива Linux:

   | Дистрибутив Linux | Расположение пакета **mssql-tools** |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools) |

1. Кроме того, найдите и скопируйте пакет **msodbcsql**, который является зависимостью. Пакет **msodbcsql** также имеет зависимость от **unixODBC-devel** (Red Hat и SLES) или от **unixodbc-dev** (Ubuntu). Расположение пакетов **msodbcsql** приведено в следующей таблице:

   | Дистрибутив Linux | Расположение пакетов ODBC |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [**msodbcsql**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql)<br/>[**unixodbc-dev**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/u/unixodbc/) |

1. **Переместите скачанные пакеты на компьютер Linux**. Если для скачивания пакетов вы использовали другой компьютер, переместить пакеты на компьютер Linux можно с помощью команды **scp**.

1. **Установите пакеты**. Установите пакеты **mssql-tools** и **msodbc**. Если возникают ошибки зависимостей, игнорируйте их до следующего шага.

    | Платформа | Команды для установки пакетов |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-<version>.rpm`<br/>`sudo yum localinstall mssql-tools-<version>.rpm` |
    | SLES | `sudo zypper install msodbcsql-<version>.rpm`<br/>`sudo zypper install mssql-tools-<version>.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_<version>.deb`<br/>`sudo dpkg -i mssql-tools_<version>.deb` |

1. **Разрешите отсутствующие зависимости**. На этом этапе зависимости могут отсутствовать. Если это не так, пропустите этот шаг. В некоторых случаях необходимо найти и установить зависимости вручную.

    Для пакетов RPM проверить требуемые зависимости можно с помощью следующих команд:

    ```bash
    rpm -qpR msodbcsql-<version>.rpm
    rpm -qpR mssql-tools-<version>.rpm
    ```

    Для пакетов Debian, если у вас есть доступ к утвержденным репозиториям, содержащим эти зависимости, самым простым решением является использование команды **apt-get**.

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Эта команда также завершает установку пакетов SQL Server.

    Если эта команда не работает для пакета Debian, проверить требуемые зависимости можно с помощью следующих команд:

    ```bash
    dpkg -I msodbcsql_<version>_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_<version>_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Дальнейшие действия

Пример использования **sqlcmd** для подключения к SQL Server и создания базы данных см. в одном из следующих кратких руководств:

- [Установка в Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установка в SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установка в Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запуск в Docker](quickstart-install-connect-ubuntu.md)

Пример использования **bcp** для массового импорта и экспорта данных см. в статье [Массовое копирование данных в SQL Server на Linux](sql-server-linux-migrate-bcp.md).
