---
title: Начало работы с SQL Server в Ubuntu
titleSuffix: SQL Server
description: В этом кратком руководстве показано, как установить SQL Server 2017 или SQL Server 2019 в Ubuntu, а затем создать и запрос к базе данных с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: bb262bdb82dd694e624573fa867cf7663d0cc850
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54298941"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Краткое руководство. Установка SQL Server и создать базу данных в Ubuntu
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

  > [!div class="nextstepaction"]
  > [Поделитесь своим мнением о SQL документация содержания!](https://aka.ms/sqldocsurvey)

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом кратком руководстве вы устанавливаете SQL Server 2017 или предварительной версии SQL Server 2019 на Ubuntu 16.04. После этого следует подключиться с помощью **sqlcmd** создать свою первую базу данных и выполнения запросов.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве установкой предварительной версии SQL Server 2019 на Ubuntu 16.04. После этого следует подключиться с помощью **sqlcmd** создать свою первую базу данных и выполнения запросов.

::: moniker-end

> [!TIP]
> Этого учебника требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) процедуры установки см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь компьютер Ubuntu 16.04 с **по крайней мере 2 ГБ** памяти.

Чтобы установить Ubuntu на своем локальном компьютере, перейдите к [ https://www.ubuntu.com/download/server ](https://www.ubuntu.com/download/server). Также можно создать виртуальные машины Ubuntu в Azure. См. в разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве целевого объекта установки.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в Ubuntu, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета.

1. Импорт ключей GPG общедоступного репозитория:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Зарегистрируйте репозиторий Microsoft SQL Server Ubuntu:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!TIP]
   > Если вы хотите попробовать SQL Server 2019, вместо этого необходимо зарегистрировать **предварительной версии (2019)** репозитория. Используйте следующую команду для установки SQL Server 2019:
   >
   > ```bash
   > sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
   > ```

3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
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

6. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433) в брандмауэре.

На этом этапе SQL Server выполняется на компьютере Ubuntu и готов к использованию!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в Ubuntu, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета.

1. Импорт ключей GPG общедоступного репозитория:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Зарегистрируйте репозиторий Microsoft SQL Server Ubuntu для предварительной версии SQL Server 2019:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
   ```

3. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
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

6. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433) в брандмауэре.

На этом этапе предварительной версии SQL Server 2019 выполняется на компьютере Ubuntu и готов к использованию!

::: moniker-end

## <a id="tools"></a>Установка программ командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с инструментом, который можно запустить инструкции Transact-SQL в SQL Server. Следующие шаги, чтобы установить средства командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

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

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
