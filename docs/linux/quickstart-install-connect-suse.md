---
title: Начало работы с SQL Server 2017 на базе SUSE Linux Enterprise Server | Документация Майкрософт
description: В этом кратком руководстве показано, как установить SQL Server 2017 на базе SUSE Linux Enterprise Server, а затем создать и запрос к базе данных с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: 7534ea052c5c277edb195c2a6a2a12ead1661e33
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102592"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Краткое руководство: Установка SQL Server и создать базу данных на базе SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве вы сначала установить SQL Server 2017 на SUSE Linux Enterprise Server (SLES) версии 12 с пакетом обновления 2. Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этого учебника требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) процедуры установки см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь компьютер SLES версии 12 с пакетом обновления 2 с **по крайней мере 2 ГБ** памяти. Файловая система должна быть **XFS** или **EXT4**. Другие файловые системы, такие как **BTRFS**, не поддерживаются.

Чтобы установить SUSE Linux Enterprise Server на своем локальном компьютере, перейдите к [ https://www.suse.com/products/server ](https://www.suse.com/products/server). Кроме того, можно создать виртуальные машины SLES в Azure. См. в разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)и использовать `--image SLES` в вызове `az vm create`.

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве целевого объекта установки.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в SLES, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета:

> [!IMPORTANT]
> Если вы ранее установили CTP-версии или версии-кандидате SQL Server 2017, необходимо сначала удалить старое хранилище перед регистрацией один из репозиториев общедоступной версии. Дополнительные сведения см. в разделе [изменить репозиториев из репозитория предварительной версии в общедоступную Версию репозиторий](sql-server-linux-change-repo.md).

1. Загрузите файл конфигурации репозитория Microsoft SQL Server SLES:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Это накопительное обновление (CU) хранилища. Дополнительные сведения о параметрах репозитория и различий между ними, см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

1. Обновите свои хранилища.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
1. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo zypper install -y mssql-server
   ```

1. После завершения установки пакета запустите **установки mssql-conf** и следуйте инструкциям на экране, чтобы задать пароль системного Администратора и выберите ваш выпуск.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Если вы используете SQL Server 2017 в этом руководстве, свободно Лицензируются следующие выпуски: Evaluation, Developer и Express.

   > [!NOTE]
   > Не забудьте указать надежный пароль для учетной записи SA (минимум длина 8 символов, заглавные и строчные буквы, десятичные цифры и не буквенно-цифровых символов).

1. После завершения конфигурации, убедитесь, что служба запущена:

   ```bash
   systemctl status mssql-server
   ```

1. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433) в брандмауэре. Если вы используете брандмауэр SuSE, необходимо изменить **/etc/sysconfig/SuSEfirewall2** файла конфигурации. Изменить **FW_SERVICES_EXT_TCP** запись, чтобы добавлять номер порта SQL Server.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

На этом этапе SQL Server работает на вашем компьютере SLES и готов к использованию!

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
