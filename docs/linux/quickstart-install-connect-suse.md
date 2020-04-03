---
title: SUSE. Установка SQL Server в Linux
description: В этом кратком руководстве рассказывается, как установить SQL Server 2017 или SQL Server 2019 в SUSE Linux Enterprise Server, а затем создать и запросить базу данных с помощью средства sqlcmd.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: bb7a6689d2cf6638f2d4e2de078e4e4412225595
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "79487612"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Краткое руководство. Установка SQL Server и создание базы данных в SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом кратком руководстве вы установите SQL Server 2017 или SQL Server 2019 в SUSE Linux Enterprise Server (SLES) версии 12 с пакетом обновления 2 (SP2). Затем вы подключитесь с помощью **sqlcmd** для создания первой базы данных и выполнения запросов.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве вы установите SQL Server 2019 в SUSE Linux Enterprise Server (SLES) версии 12. Затем вы подключитесь с помощью **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!IMPORTANT]
> SQL Server 2019 поддерживается в SUSE Enterprise Linux Server версии 12 с пакетом обновления 2, 3, 4 или 5 (SP2, SP3, SP4 или SP5).

::: moniker-end

> [!TIP]
> Для выполнения этого руководства требуется ввод данных пользователем и подключение к Интернету. Если вас интересуют процедуры [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) установки, см. [руководство по установке SQL Server на Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Предварительные требования

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Требуется компьютер, на котором установлена ОС SLES версии 12 с пакетом обновления 2 (SP2) и имеется **по крайней мере 2 ГБ** памяти. Должна использоваться файловая система **XFS** или **EXT4**. Другие файловые системы, например **BTRFS**, не поддерживаются.

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Требуется компьютер, на котором установлена ОС SLES версии 12 с пакетом обновления 2, 3, 4 или 5 (SP2, SP3, SP4 или SP5) и имеется **по крайней мере 2 ГБ** памяти. Должна использоваться файловая система **XFS** или **EXT4**. Другие файловые системы, например **BTRFS**, не поддерживаются.

::: moniker-end

Чтобы установить SUSE Linux Enterprise Server на собственном компьютере, перейдите на страницу [https://www.suse.com/products/server](https://www.suse.com/products/server). Можно также создать виртуальные машины SLES в Azure. См. статью [Создание виртуальных машин Linux и управление ими с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm) и используйте параметр `--image SLES` в вызове `az vm create`.

Если вы ранее установили выпуск CTP или RC сервера SQL Server, необходимо удалить старый репозиторий, прежде чем выполнять эти действия. Дополнительные сведения см. в статье [Настройка репозиториев Linux для SQL Server 2017 и 2019](sql-server-linux-change-repo.md).

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве цели установки.

Сведения о других требованиях к системе см. в статье [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a name="install-sql-server"></a><a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в SLES, выполните следующие команды в терминале для установки пакета **mssql-server**:

1. Скачайте файл конфигурации репозитория Microsoft SQL Server 2017 SLES:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!TIP]
   > Если вы хотите установить SQL Server 2019, необходимо зарегистрировать вместо этого репозиторий SQL Server 2019. Используйте следующую команду для установки SQL Server 2019:
   >
   > ```bash
   > sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2019.repo
   > ```

2. Обновите репозитории.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo zypper install -y mssql-server
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
   systemctl status mssql-server
   ```

6. Если вы планируете подключаться удаленно, может потребоваться открыть в брандмауэре TCP-порт SQL Server (по умолчанию 1433). Если вы используете брандмауэр SuSE, необходимо изменить файл конфигурации **/etc/sysconfig/SuSEfirewall2**. Измените запись **FW_SERVICES_EXT_TCP**, добавив номер порта SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

В результате сервер SQL Server будет запущен на компьютере SLES и готов к использованию!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="install-sql-server"></a><a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в SLES, выполните следующие команды в терминале для установки пакета **mssql-server**:

1. Скачайте файл конфигурации репозитория Microsoft SQL Server 2019 SLES:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2019.repo
   ```

2. Обновите репозитории.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo zypper install -y mssql-server
   ```

4. Когда установка пакета завершится, выполните команду **mssql-conf setup** и следуйте указаниям, чтобы задать пароль системного администратора и выбрать выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Для учетной записи системного администратора необходимо установить надежный пароль (минимальная длина — 8 символов; должен содержать строчные и прописные буквы, десятичные цифры и (или) символы, отличные от букв и цифр).

5. По завершении настройки убедитесь в том, что служба работает.

   ```bash
   systemctl status mssql-server
   ```

6. Если вы планируете подключаться удаленно, может потребоваться открыть в брандмауэре TCP-порт SQL Server (по умолчанию 1433). Если вы используете брандмауэр SuSE, необходимо изменить файл конфигурации **/etc/sysconfig/SuSEfirewall2**. Измените запись **FW_SERVICES_EXT_TCP**, добавив номер порта SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

В результате сервер SQL Server 2019 будет запущен на компьютере SLES и готов к использованию!

::: moniker-end


## <a name="install-the-sql-server-command-line-tools"></a><a id="tools"></a>Установка программ командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с помощью средства, которое позволяет выполнять инструкции Transact-SQL в SQL Server. Ниже приведены инструкции по установке программ командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Добавьте репозиторий Microsoft SQL Server в Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Установите **mssql-tools** с помощью пакета разработчика unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Для удобства добавьте путь `/opt/mssql-tools/bin/` в переменную среды **PATH**. Это позволит запускать программы, не указывая полный путь. Выполните следующие команды, чтобы изменить переменную среды **PATH** как для сеансов входа в систему, так и для интерактивных сеансов и сеансов без входа в систему.

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
