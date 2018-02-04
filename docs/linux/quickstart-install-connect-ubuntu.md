---
title: "Приступая к работе с SQL Server 2017 г. на Ubuntu | Документы Microsoft"
description: "Краткого руководства показано, как установить на Ubuntu 2017 г. SQL Server, а затем создать и запросов к базе данных с помощью sqlcmd."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Active
ms.openlocfilehash: ac570feda5ce20ee8d255abb25b83a327c84c7f3
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="install-sql-server-and-create-a-database-on-ubuntu"></a>Установка SQL Server и создать базу данных на Ubuntu

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве сначала установите 2017 г. SQL Server на Ubuntu 16.04. Подключитесь с **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этот учебник требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономного](sql-server-linux-setup.md#offline) процедуры установки. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь компьютер Ubuntu 16.04 с **по крайней мере 2 ГБ** памяти.

Чтобы установить Ubuntu на компьютере, перейдите к [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server). Можно также создать Ubuntu виртуальных машин в Azure. В разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> В настоящее время [подсистемы Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве целевого объекта установки.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server на Ubuntu, выполните следующие команды в конечном для установки **mssql server** пакета.

> [!IMPORTANT]
> Если вы ранее установили CTP-версия или версия-КАНДИДАТ release 2017 г. SQL Server, необходимо сначала удалить старое хранилище перед регистрацией один репозиториев общедоступной версии. Дополнительные сведения см. в разделе [изменить репозиториев из репозитория предварительного просмотра в репозитории GA](sql-server-linux-change-repo.md).

1. Импортируйте ключи GPG общедоступный репозиторий:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Регистрация в Microsoft SQL Server Ubuntu репозиторий:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > Это накопительное обновление (CU) репозитория. Дополнительные сведения о параметрах репозитория и различия между ними см. в разделе [изменение исходных репозиториев](sql-server-linux-setup.md#repositories).

1. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. После завершения установки пакета, запустите **установки mssql conf** и следуйте инструкциям на экране, чтобы задать пароль учетной записи SA и выберите ваш выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Если вы пытаетесь 2017 г. SQL Server в этом учебнике, свободно Лицензируются следующие выпуски: Evaluation, Developer и Express.

   > [!NOTE]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум 8 символов, заглавные и строчные буквы, десятичные цифры или отличные от буквенно-цифровых символов).

1. После завершения конфигурации убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```

1. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433), в брандмауэре.

На этом этапе SQL Server выполняется на компьютере Ubuntu и готов к использованию!

## <a id="tools"></a>Установите средства командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с помощью средства, можно выполнить инструкции Transact-SQL на сервере SQL Server. Следующие шаги установки средства командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Импортируйте ключи GPG общедоступный репозиторий:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Регистрация репозитория Microsoft Ubuntu:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
   ```

1. Обновление списка источников и выполните команду установки пакета разработчика unixODBC:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-tools unixodbc-dev
   ```

1. Для удобства добавьте `/opt/mssql-tools/bin/` для вашей **путь** переменной среды. Это позволяет запустить средства без указания полного пути. Выполните следующие команды для изменения **путь** для интерактивной и не-сеансы входа в систему и сеансов входа:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd** — лишь один инструмент для подключения к SQL Server для выполнения запросов и выполнять задачи управления и разработки. Ниже перечислены другие инструменты.
>
> * [SQL Server Operations Studio (Предварительная версия)](../sql-operations-studio/what-is.md)
> * [Среда SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)
> * [Код Visual Studio](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (Preview)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
