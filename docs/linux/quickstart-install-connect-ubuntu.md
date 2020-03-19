---
title: 'Ubuntu: Установка SQL Server в Linux'
description: В этом кратком руководстве рассказывается, как установить SQL Server 2017 или SQL Server 2019 в Ubuntu, а затем создать и запросить базу данных с помощью средства sqlcmd.
author: VanMSFT
ms.author: vanto
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.custom: seo-lt-2019
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 69f1ac170d70c10d9a7061b3fc18f6c8a62db704
ms.sourcegitcommit: efb2bb07700f645b3fbfcb400a0666de01388305
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79319854"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Краткое руководство. Установка SQL Server и создание базы данных в Ubuntu
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]


<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом кратком руководстве вы установите SQL Server 2017 в Ubuntu 16.04. Затем вы подключитесь с помощью **sqlcmd** для создания первой базы данных и выполнения запросов.

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве вы установите SQL Server 2019 в Ubuntu 18.04. Затем вы подключитесь с помощью **sqlcmd** для создания первой базы данных и выполнения запросов.

::: moniker-end

> [!TIP]
> Для выполнения этого руководства требуется ввод данных пользователем и подключение к Интернету. Если вас интересуют процедуры автоматической или автономной установки, см. [руководство по установке SQL Server на Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Предварительные требования

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Требуется компьютер, на котором установлена ОС Ubuntu 16.04 и имеется **по крайней мере 2 ГБ** памяти.

Чтобы установить Ubuntu 16.04 на собственный компьютер, перейдите на страницу <http://releases.ubuntu.com/xenial/>. Можно также создать виртуальные машины Ubuntu в Azure. См. статью [Создание виртуальных машин Linux и управление ими с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве цели установки.

Сведения о других требованиях к системе см. в статье [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

> [!NOTE]
> Ubuntu 18.04 пока не поддерживается официально, однако SQL Server можно запускать с некоторыми [изменениями](https://blogs.msdn.microsoft.com/sql_server_team/installing-sql-server-2017-for-linux-on-ubuntu-18-04-lts/).

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Требуется компьютер, на котором установлена ОС Ubuntu 18.04 и имеется **по крайней мере 2 ГБ** памяти.

Чтобы установить Ubuntu 18.04 на собственный компьютер, перейдите на страницу <http://releases.ubuntu.com/bionic/>. Можно также создать виртуальные машины Ubuntu в Azure. См. статью [Создание виртуальных машин Linux и управление ими с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве цели установки.

Сведения о других требованиях к системе см. в статье [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в Ubuntu, выполните следующие команды в терминале для установки пакета **mssql-server**:

1. Импортируйте открытые ключи GPG из репозитория:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Зарегистрируйте репозиторий Ubuntu для Microsoft SQL Server:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!TIP]
   > Если вы хотите установить SQL Server 2019, необходимо зарегистрировать вместо этого репозиторий SQL Server 2019. Используйте следующую команду для установки SQL Server 2019:
   >
   > ```bash
   > sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
   > ```

3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Когда установка пакета завершится, выполните команду **mssql-conf setup** и следуйте указаниям, чтобы задать пароль системного администратора и выбрать выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Следующие выпуски SQL Server 2017 имеют бесплатные лицензии: Evaluation, Developer и Express.

   > [!NOTE]
   > Для учетной записи системного администратора необходимо установить надежный пароль (минимальная длина — 8 символов; должен содержать строчные и прописные буквы, десятичные цифры и (или) символы, отличные от букв и цифр).

5. По завершении настройки убедитесь в том, что служба работает.

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. Если вы планируете подключаться удаленно, может потребоваться открыть в брандмауэре TCP-порт SQL Server (по умолчанию 1433).

В результате сервер SQL Server будет запущен на компьютере Ubuntu и готов к использованию!

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в Ubuntu, выполните следующие команды в терминале для установки пакета **mssql-server**:

1. Импортируйте открытые ключи GPG из репозитория:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Зарегистрируйте репозиторий Microsoft SQL Server Ubuntu для SQL Server 2019:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/mssql-server-2019.list)"
   ```

3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Когда установка пакета завершится, выполните команду **mssql-conf setup** и следуйте указаниям, чтобы задать пароль системного администратора и выбрать выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Для учетной записи системного администратора необходимо установить надежный пароль (минимальная длина — 8 символов; должен содержать строчные и прописные буквы, десятичные цифры и (или) символы, отличные от букв и цифр).

5. По завершении настройки убедитесь в том, что служба работает.

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. Если вы планируете подключаться удаленно, может потребоваться открыть в брандмауэре TCP-порт SQL Server (по умолчанию 1433).

В результате SQL Server 2019 будет запущен на компьютере Ubuntu и готов к использованию!

::: moniker-end

## <a id="tools"></a>Установка программ командной строки SQL Server

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Чтобы создать базу данных, необходимо подключиться с помощью средства, которое позволяет выполнять инструкции Transact-SQL в SQL Server. Ниже приведены инструкции по установке программ командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

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

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Чтобы создать базу данных, необходимо подключиться с помощью средства, которое позволяет выполнять инструкции Transact-SQL в SQL Server. Ниже приведены инструкции по установке программ командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

Чтобы установить **mssql-tools** в Ubuntu, выполните указанные ниже действия. 

1. Импортируйте открытые ключи GPG из репозитория.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Зарегистрируйте репозиторий Ubuntu для Майкрософт.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
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

::: moniker-end

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
