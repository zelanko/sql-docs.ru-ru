---
title: Приступая к работе с 2017 г. SQL Server в Red Hat Enterprise Linux | Документы Microsoft
description: Краткого руководства показано, как установить 2017 г. SQL Server в Red Hat Enterprise Linux, а затем создать и запросов к базе данных с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: de149b0a75a550101e761baa109bc07dac062fcd
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455356"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Краткое руководство: Установка SQL Server и создать базу данных в Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве сначала необходимо установить 2017 г. SQL Server в Red Hat Enterprise Linux (RHEL) 7.3 +. Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этот учебник требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономного](sql-server-linux-setup.md#offline) процедуры установки. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь RHEL 7.3 или 7.4 машину с **по крайней мере 2 ГБ** памяти.

Чтобы установить Red Hat Enterprise Linux на компьютере, перейдите к [ http://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Можно также создать RHEL виртуальных машин в Azure. В разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image RHEL` в вызове `az vm create`.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server на RHEL, выполните следующие команды в конечном для установки **mssql server** пакета:

> [!IMPORTANT]
> Если вы ранее установили CTP-версия или версия-КАНДИДАТ release 2017 г. SQL Server, необходимо сначала удалить старое хранилище перед регистрацией один репозиториев общедоступной версии. Дополнительные сведения см. в разделе [изменить репозиториев из репозитория предварительного просмотра в репозитории GA](sql-server-linux-change-repo.md).

1. Чтобы Загрузите файл конфигурации репозитория Microsoft SQL Server Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Это накопительное обновление (CU) репозитория. Дополнительные сведения о параметрах репозитория и различия между ними см. в разделе [настроить репозитории для SQL Server в Linux](sql-server-linux-change-repo.md).

1. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo yum install -y mssql-server
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
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Выполните следующие команды для установки **mssql средства** комплект разработчика unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
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
> * [SQL Server Operations Studio (предварительная версия)](../sql-operations-studio/what-is.md);
> * [Среда SQL Server Management Studio](sql-server-linux-manage-ssms.md)
> * [Код Visual Studio](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (предварительная версия)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
