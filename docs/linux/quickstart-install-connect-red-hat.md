---
title: RHEL. Установка SQL Server в Linux
titleSuffix: SQL Server
description: В этом кратком руководстве описано, как установить SQL Server 2017 или SQL Server 2019 в Red Hat Enterprise Linux (RHEL), а затем создать базу данных и выполнить к ней запрос с помощью средства sqlcmd.
author: VanMSFT
ms.custom: seo-lt-2019
ms.author: vanto
ms.date: 01/08/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: d94e90e67814ec2dd1541abdbd52b04152681d84
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75776403"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Краткое руководство. Установка SQL Server и создание базы данных в Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом кратком руководстве вы установите SQL Server 2017 или SQL Server 2019 в Red Hat Enterprise Linux (RHEL). Затем вы подключитесь с помощью **sqlcmd** для создания первой базы данных и выполнения запросов.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве вы установите SQL Server 2019 в Red Hat Enterprise Linux (RHEL) 8. Затем вы подключитесь с помощью **sqlcmd** для создания первой базы данных и выполнения запросов.

::: moniker-end

> [!TIP]
> Для выполнения этого руководства требуется ввод данных пользователем и подключение к Интернету. Если вас интересуют процедуры [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) установки, см. [руководство по установке SQL Server на Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Предварительные требования

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Требуется компьютер, на котором установлена ОС RHEL 7.3, 7.4, 7.5, 7.6 или 8 и имеется **по крайней мере 2 ГБ** памяти.

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Требуется компьютер, на котором установлена ОС RHEL 7.3, 7.4, 7.5 или 7.6 и имеется **по крайней мере 2 ГБ** памяти.

::: moniker-end

Чтобы установить Red Hat Enterprise Linux на собственном компьютере, перейдите на страницу [https://access.redhat.com/products/red-hat-enterprise-linux/evaluation](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Можно также создать виртуальные машины RHEL в Azure. См. статью [Создание виртуальных машин Linux и управление ими с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm) и используйте параметр `--image RHEL` в вызове `az vm create`.

Если вы ранее установили выпуск CTP или RC сервера SQL Server, необходимо удалить старый репозиторий, прежде чем выполнять эти действия. Дополнительные сведения см. в статье [Настройка репозиториев Linux для SQL Server 2017 и 2019](sql-server-linux-change-repo.md).

Сведения о других требованиях к системе см. в статье [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в RHEL, выполните следующие команды в терминале для установки пакета **mssql-server**.

1. Скачайте файл конфигурации репозитория Microsoft SQL Server 2017 Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > Если вы хотите установить SQL Server 2019, необходимо зарегистрировать вместо этого репозиторий SQL Server 2019. Используйте следующую команду для установки SQL Server 2019:
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo
   > ```

2. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

3. Когда установка пакета завершится, выполните команду **mssql-conf setup** и следуйте указаниям, чтобы задать пароль системного администратора и выбрать выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Следующие выпуски SQL Server 2017 имеют бесплатные лицензии: Evaluation, Developer и Express.

   > [!NOTE]
   > Для учетной записи системного администратора необходимо установить надежный пароль (минимальная длина — 8 символов; должен содержать строчные и прописные буквы, десятичные цифры и (или) символы, отличные от букв и цифр).

4. По завершении настройки убедитесь в том, что служба работает.

   ```bash
   systemctl status mssql-server
   ```

5. Чтобы разрешить удаленные подключения, откройте порт SQL Server в брандмауэре в RHEL. По умолчанию для SQL Server используется TCP-порт 1433. Если вы используете **FirewallD** для брандмауэра, можно использовать следующие команды.

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

В результате сервер SQL Server будет запущен на компьютере RHEL и готов к использованию!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в RHEL, выполните следующие команды в терминале для установки пакета **mssql-server**.

1. Скачайте файл конфигурации репозитория Microsoft SQL Server 2019 Red Hat:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo
   ```

2. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

3. Когда установка пакета завершится, выполните команду **mssql-conf setup** и следуйте указаниям, чтобы задать пароль системного администратора и выбрать выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Для учетной записи системного администратора необходимо установить надежный пароль (минимальная длина — 8 символов; должен содержать строчные и прописные буквы, десятичные цифры и (или) символы, отличные от букв и цифр).

4. По завершении настройки убедитесь в том, что служба работает.

   ```bash
   systemctl status mssql-server
   ```

5. Чтобы разрешить удаленные подключения, откройте порт SQL Server в брандмауэре в RHEL. По умолчанию для SQL Server используется TCP-порт 1433. Если вы используете **FirewallD** для брандмауэра, можно использовать следующие команды.

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

В результате сервер SQL Server 2019 будет запущен на компьютере RHEL и готов к использованию!

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="tools"></a>Установка программ командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с помощью средства, которое позволяет выполнять инструкции Transact-SQL в SQL Server. Ниже приведены инструкции по установке программ командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Скачайте файл конфигурации репозитория Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Если установлена предыдущая версия **mssql-tools**, удалите все старые пакеты unixODBC.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Чтобы установить **mssql-tools** с помощью пакета разработчика unixODBC, выполните приведенные ниже команды.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Для удобства добавьте путь `/opt/mssql-tools/bin/` в переменную среды **PATH**. Это позволит запускать программы, не указывая полный путь. Выполните следующие команды, чтобы изменить переменную среды **PATH** как для сеансов входа в систему, так и для интерактивных сеансов и сеансов без входа в систему.

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="tools"></a>Установка программ командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с помощью средства, которое позволяет выполнять инструкции Transact-SQL в SQL Server. Ниже приведены инструкции по установке программ командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Скачайте файл конфигурации репозитория Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
   ```

1. Если установлена предыдущая версия **mssql-tools**, удалите все старые пакеты unixODBC.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Чтобы установить **mssql-tools** с помощью пакета разработчика unixODBC, выполните приведенные ниже команды.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Для удобства добавьте путь `/opt/mssql-tools/bin/` в переменную среды **PATH**. Это позволит запускать программы, не указывая полный путь. Выполните следующие команды, чтобы изменить переменную среды **PATH** как для сеансов входа в систему, так и для интерактивных сеансов и сеансов без входа в систему.

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

::: moniker-end

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
