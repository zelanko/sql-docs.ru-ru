---
title: Начало работы с SQL Server в Red Hat Enterprise Linux | Документация Майкрософт
description: В этом кратком руководстве показано, как установить SQL Server 2017 или SQL Server 2019 в Red Hat Enterprise Linux, а затем создать и запрос к базе данных с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.custom: sql-linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 8d5b044adbdc0e5a846013aff1922b3cb1cb5dc8
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669453"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Краткое руководство: Установка SQL Server и создать базу данных в Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом кратком руководстве вы устанавливаете SQL Server 2017 или SQL Server 2019 на Red Hat Enterprise Linux (RHEL) 7.3 +. После этого следует подключиться с помощью **sqlcmd** создать свою первую базу данных и выполнения запросов.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве вы установите предварительную версию SQL Server 2019 на Red Hat Enterprise Linux (RHEL) 7.3 +. После этого следует подключиться с помощью **sqlcmd** создать свою первую базу данных и выполнения запросов.

::: moniker-end

> [!TIP]
> Этого учебника требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) процедуры установки см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь RHEL 7.3 или 7.4 машину с **по крайней мере 2 ГБ** памяти.

Чтобы установить Red Hat Enterprise Linux на своем локальном компьютере, перейдите к [ https://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Кроме того, можно создать виртуальные машины RHEL в Azure. См. в разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image RHEL` в вызове `az vm create`.

Если вы ранее установили CTP-версии или версии-кандидате SQL Server 2017, необходимо сначала удалить старое хранилище, затем выполните следующие действия. Дополнительные сведения см. в разделе [репозиториев Настройка виртуальных машин Linux для SQL Server 2017 и 2019 ](sql-server-linux-change-repo.md).

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server на RHEL, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета:

1. Загрузите файл конфигурации репозитория Microsoft SQL Server 2017 Red Hat:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > Если вы хотите попробовать SQL Server 2019, вместо этого необходимо зарегистрировать **предварительной версии (2019)** репозитория. Используйте следующую команду для установки SQL Server 2019:
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   > ```

2. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

3. После завершения установки пакета запустите **установки mssql-conf** и следуйте инструкциям на экране, чтобы задать пароль системного Администратора и выберите ваш выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > В следующих выпусках SQL Server 2017 свободно лицензируются: Evaluation, Developer и Express.

   > [!NOTE]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум длина 8 символов, заглавные и строчные буквы, десятичные цифры и не буквенно-цифровых символов).

4. После завершения конфигурации, убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```

5. Чтобы разрешить удаленные соединения, откройте порт SQL Server в брандмауэре на RHEL. По умолчанию SQL Server используется порт TCP 1433. Если вы используете **FirewallD** для брандмауэра, можно использовать следующие команды:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

На этом этапе SQL Server работает на вашем компьютере RHEL и готов к использованию!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server на RHEL, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета:

1. Скачайте предварительную версию Microsoft SQL Server 2019 файл конфигурации репозитория Red Hat:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   ```

2. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

3. После завершения установки пакета запустите **установки mssql-conf** и следуйте инструкциям на экране, чтобы задать пароль системного Администратора и выберите ваш выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум длина 8 символов, заглавные и строчные буквы, десятичные цифры и не буквенно-цифровых символов).

4. После завершения конфигурации, убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```

5. Чтобы разрешить удаленные соединения, откройте порт SQL Server в брандмауэре на RHEL. По умолчанию SQL Server используется порт TCP 1433. Если вы используете **FirewallD** для брандмауэра, можно использовать следующие команды:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

На этом этапе предварительной версии SQL Server 2019 работает на вашем компьютере RHEL и готов к использованию!

::: moniker-end

## <a id="tools"></a>Установка программ командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с инструментом, который можно запустить инструкции Transact-SQL в SQL Server. Следующие шаги, чтобы установить средства командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Скачайте файл конфигурации репозитория Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. При наличии предыдущей версии **mssql-tools** установлен, удалите старые пакеты unixODBC.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Выполните следующие команды для установки **mssql-tools** с пакетом разработчика unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Для удобства добавьте `/opt/mssql-tools/bin/` для вашей **путь** переменной среды. Это позволяет запустить средства без указания полного пути. Выполните следующие команды для изменения **путь** для обоих сеансов входа и интерактивных/сеансов без входа:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
