---
title: "Приступая к работе с 2017 г. SQL Server в Red Hat Enterprise Linux | Документы Microsoft"
description: "Этого краткого руководства показано, как установить 2017 г. SQL Server в Red Hat Enterprise Linux, а затем создать и запросов к базе данных с помощью sqlcmd."
author: sabotta
ms.author: carlasab
manager: craigg
ms.date: 07/24/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 53f3c2dbda293d6c3f9beb8bd16287b6aa0d9e26
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-and-create-a-database-on-red-hat"></a>Установка SQL Server и создать базу данных в Red Hat

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

В этом учебнике быстрого запуска сначала необходимо установить RC2 2017 г. SQL Server в Red Hat Enterprise Linux (RHEL) 7.3. Подключитесь с **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этот учебник требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономного](sql-server-linux-setup.md#offline) процедуры установки. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Предварительные требования

Необходимо иметь компьютер RHEL 7.3 с **по крайней мере 3,25 ГБ** памяти.

Чтобы установить Red Hat Enterprise Linux на компьютере, перейдите к [http://access.redhat.com/products/red-hat-enterprise-linux/evaluation](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Можно также создать RHEL виртуальных машин в Azure. В разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image RHEL` в вызове `az vm create`.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server на RHEL, выполните следующие команды в конечном для установки **mssql server** пакета:

1. Чтобы Загрузите файл конфигурации репозитория Microsoft SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server.repo
   ```

1. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo yum update
   sudo yum install -y mssql-server
   ```

1. После завершения установки пакета, запустите **установки mssql conf** и следуйте инструкциям на экране, чтобы задать пароль учетной записи SA и выбранного выпуска.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```
   > [!TIP]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум 8 символов, заглавные и строчные буквы, десятичные цифры или отличные от буквенно-цифровых символов).

   > [!TIP]
   > При установке версии-кандидата 2, не приобретенных лицензий необходимы для попробовать выполнить одно из выпусков. Поскольку версия-кандидат, независимо от выбранного выпуска появится следующее сообщение:
   >
   > `This is an evaluation version.  There are [175] days left in the evaluation period.`
   >
   > Это сообщение не отражает выбранного выпуска. Он относится к предварительной версии, для версии-кандидата 2.

1. После завершения конфигурации убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```
   
1. Чтобы разрешить удаленные соединения, откройте порт в брандмауэре на RHEL SQL Server. Порт SQL Server по умолчанию — TCP 1433. Если вы используете **FirewallD** для вашего брандмауэра можно использовать следующие команды:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

На этом этапе SQL Server выполняется на компьютере RHEL и готов к использованию!

## <a id="tools"></a>Установите средства командной строки SQL Server

Чтобы создать базу данных, необходимо подключиться с помощью средства, можно выполнить инструкции Transact-SQL на сервере SQL Server. Следующие шаги установки средства командной строки SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) и [bcp](../tools/bcp-utility.md).

1. Загрузите файл конфигурации Microsoft Red Hat репозитория.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. При наличии предыдущей версии **mssql средства** установлены, удалите старую unixODBC пакеты.

   ```bash
   sudo yum update
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Выполните следующие команды для установки **mssql средства** комплект разработчика unixODBC.

   ```bash
   sudo yum update
   sudo yum install -y mssql-tools unixODBC-devel
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
