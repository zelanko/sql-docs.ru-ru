---
title: "Приступая к работе с 2017 г. SQL Server в SUSE Linux Enterprise Server | Документы Microsoft"
description: "Этого краткого руководства показано, как установить 2017 г. SQL Server в SUSE Linux Enterprise Server, а затем создать и запросов к базе данных с помощью sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.workload: On Demand
ms.openlocfilehash: c69d708c793b2a7a3513a5885d84f7f534e03e6b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Установка SQL Server и создать базу данных на SUSE Linux Enterprise Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом учебнике быстрого запуска сначала установите 2017 г. SQL Server на v12 SUSE Linux Enterprise Server (SLES) с пакетом обновления 2. Подключитесь с **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этот учебник требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономного](sql-server-linux-setup.md#offline) процедуры установки. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Предварительные требования

Необходимо иметь компьютер SP2 SLES версии 12 с **по крайней мере 3,25 ГБ** памяти. Файловая система должна быть **XFS** или **EXT4**. Других файловых систем, таких как **BTRFS**, не поддерживаются.

Чтобы установить SUSE Linux Enterprise Server на компьютере, перейдите к [https://www.suse.com/products/server](https://www.suse.com/products/server). Можно также создать SLES виртуальных машин в Azure. В разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image SLES` в вызове `az vm create`.

> [!NOTE]
> В настоящее время [подсистемы Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве целевого объекта установки.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server на SLES, выполните следующие команды в конечном для установки **mssql server** пакета:

> [!IMPORTANT]
> Если вы ранее установили CTP-версия или версия-КАНДИДАТ release 2017 г. SQL Server, необходимо сначала удалить старое хранилище перед регистрацией один репозиториев общедоступной версии. Дополнительные сведения см. в разделе [изменить репозиториев из репозитория предварительного просмотра в репозитории GA](sql-server-linux-change-repo.md).

1. Загрузите файл конфигурации Microsoft SQL Server SLES репозитория:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   sudo zypper --gpg-auto-import-keys refresh
   ```

   > [!NOTE]
   > Это накопительное обновление (CU) репозитория. Дополнительные сведения о параметрах репозитория и различия между ними см. в разделе [изменение исходных репозиториев](sql-server-linux-setup.md#repositories).

1. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo zypper install -y mssql-server
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

1. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433), в брандмауэре. Если вы используете брандмауэр SuSE, то придется изменить **/etc/sysconfig/SuSEfirewall2** файла конфигурации. Изменить **FW_SERVICES_EXT_TCP** входа включать номер порта сервера SQL.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

На этом этапе SQL Server выполняется на компьютере SLES и готов к использованию!

## <a id="tools"></a>Установите средства командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с помощью средства, можно выполнить инструкции Transact-SQL на сервере SQL Server. Следующие шаги установки средства командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Добавьте репозиторий Microsoft SQL Server Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Установка **mssql средства** комплект разработчика unixODBC.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Для удобства добавьте `/opt/mssql-tools/bin/` для вашей **путь** переменной среды. Это позволяет запустить средства без указания полного пути. Выполните следующие команды для изменения **путь** для интерактивной и не-сеансы входа в систему и сеансов входа:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd** — лишь один инструмент для подключения к SQL Server для выполнения запросов и выполнять задачи управления и разработки. Другие средства включают в себя [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md) и [кода Visual Studio](sql-server-linux-develop-use-vscode.md).

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
