---
title: Приступая к работе с 2017 г. SQL Server в SUSE Linux Enterprise Server | Документы Microsoft
description: Краткого руководства показано, как установить 2017 г. SQL Server в SUSE Linux Enterprise Server, а затем создать и запросов к базе данных с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: 77dd13139eba88a40cbf20094b880c5046ebfb05
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455361"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Краткое руководство: Установка SQL Server и создать базу данных на SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве сначала установить 2017 г. SQL Server в SUSE Linux Enterprise Server (SLES) версии 12 SP2. Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этот учебник требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономного](sql-server-linux-setup.md#offline) процедуры установки. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь компьютер SP2 SLES версии 12 с **по крайней мере 2 ГБ** памяти. Файловая система должна быть **XFS** или **EXT4**. Других файловых систем, таких как **BTRFS**, не поддерживаются.

Чтобы установить SUSE Linux Enterprise Server на компьютере, перейдите к [ https://www.suse.com/products/server ](https://www.suse.com/products/server). Можно также создать SLES виртуальных машин в Azure. В разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image SLES` в вызове `az vm create`.

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
   ```

   > [!NOTE]
   > Это накопительное обновление (CU) репозитория. Дополнительные сведения о параметрах репозитория и различия между ними см. в разделе [настроить репозитории для SQL Server в Linux](sql-server-linux-change-repo.md).

1. Обновите свои хранилища.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
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
> **Sqlcmd** — лишь один инструмент для подключения к SQL Server для выполнения запросов и выполнять задачи управления и разработки. Ниже перечислены другие инструменты.
>
> * [SQL Server Operations Studio (предварительная версия)](../sql-operations-studio/what-is.md);
> * [Среда SQL Server Management Studio](sql-server-linux-manage-ssms.md)
> * [Код Visual Studio](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (предварительная версия)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
