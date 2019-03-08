---
title: Начало работы с SQL Server в SUSE Linux Enterprise Server
titleSuffix: SQL Server
description: В этом кратком руководстве показано, как установить SQL Server 2017 или SQL Server 2019 в SUSE Linux Enterprise Server, а затем создать и запрос к базе данных с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: 66d4015f31c08d0d67069147effac15ff5edd8ea
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579474"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Краткое руководство. Установка SQL Server и создать базу данных на базе SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом кратком руководстве вы устанавливаете SQL Server 2017 или предварительной версии SQL Server 2019 на SUSE Linux Enterprise Server (SLES) версии 12 с пакетом обновления 2. После этого следует подключиться с помощью **sqlcmd** создать свою первую базу данных и выполнения запросов.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве установкой предварительной версии SQL Server 2019 на SUSE Linux Enterprise Server (SLES) версии 12 с пакетом обновления 2. После этого следует подключиться с помощью **sqlcmd** создать свою первую базу данных и выполнения запросов.

::: moniker-end

> [!TIP]
> Этого учебника требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) процедуры установки см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь компьютер SLES версии 12 с пакетом обновления 2 с **по крайней мере 2 ГБ** памяти. Файловая система должна быть **XFS** или **EXT4**. Другие файловые системы, такие как **BTRFS**, не поддерживаются.

Чтобы установить SUSE Linux Enterprise Server на своем локальном компьютере, перейдите к [ https://www.suse.com/products/server ](https://www.suse.com/products/server). Кроме того, можно создать виртуальные машины SLES в Azure. См. в разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image SLES` в вызове `az vm create`.

Если вы ранее установили CTP-версии или версии-кандидате SQL Server 2017, необходимо сначала удалить старое хранилище, затем выполните следующие действия. Дополнительные сведения см. в разделе [репозиториев Настройка виртуальных машин Linux для SQL Server 2017 и 2019](sql-server-linux-change-repo.md).

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве целевого объекта установки.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в SLES, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета:

1. Загрузите файл конфигурации репозитория Microsoft SQL Server 2017 SLES:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!TIP]
   > Если вы хотите попробовать SQL Server 2019, вместо этого необходимо зарегистрировать **предварительной версии (2019)** репозитория. Используйте следующую команду для установки SQL Server 2019:
   >
   > ```bash
   > sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   > ```

2. Обновите свои хранилища.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo zypper install -y mssql-server
   ```

4. После завершения установки пакета запустите **установки mssql-conf** и следуйте инструкциям на экране, чтобы задать пароль системного Администратора и выберите ваш выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Свободно лицензируются следующих выпусков SQL Server 2017: Evaluation, Developer и Express.

   > [!NOTE]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум длина 8 символов, заглавные и строчные буквы, десятичные цифры и не буквенно-цифровых символов).

5. После завершения конфигурации, убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```

6. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433) в брандмауэре. Если вы используете брандмауэр SuSE, необходимо изменить **/etc/sysconfig/SuSEfirewall2** файла конфигурации. Изменить **FW_SERVICES_EXT_TCP** запись, чтобы добавлять номер порта SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

На этом этапе SQL Server работает на вашем компьютере SLES и готов к использованию!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в SLES, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета:

1. Загрузите файл конфигурации репозитория SLES предварительной версии Microsoft SQL Server 2019:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   ```

2. Обновите свои хранилища.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo zypper install -y mssql-server
   ```

4. После завершения установки пакета запустите **установки mssql-conf** и следуйте инструкциям на экране, чтобы задать пароль системного Администратора и выберите ваш выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум длина 8 символов, заглавные и строчные буквы, десятичные цифры и не буквенно-цифровых символов).

5. После завершения конфигурации, убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```

6. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433) в брандмауэре. Если вы используете брандмауэр SuSE, необходимо изменить **/etc/sysconfig/SuSEfirewall2** файла конфигурации. Изменить **FW_SERVICES_EXT_TCP** запись, чтобы добавлять номер порта SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

На этом этапе предварительной версии SQL Server 2019 работает на вашем компьютере SLES и готов к использованию!

::: moniker-end


## <a id="tools"></a>Установка программ командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с инструментом, который можно запустить инструкции Transact-SQL в SQL Server. Следующие шаги, чтобы установить средства командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Добавьте репозиторий Microsoft SQL Server Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Установка **mssql-tools** с пакетом разработчика unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Для удобства добавьте `/opt/mssql-tools/bin/` для вашей **путь** переменной среды. Это позволяет запустить средства без указания полного пути. Выполните следующие команды для изменения **путь** для обоих сеансов входа и интерактивных/сеансов без входа:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
