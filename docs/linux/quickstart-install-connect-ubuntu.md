---
title: Начало работы с SQL Server 2017 в Ubuntu | Документация Майкрософт
description: В этом кратком руководстве показано, как установить SQL Server 2017 на Ubuntu, а затем создать и запрос к базе данных с помощью sqlcmd.
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
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 30c05b25301004afbd1d9ed0b2a365b5a37f256d
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101826"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Краткое руководство: Установка SQL Server и создать базу данных в Ubuntu

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве вы сначала установить SQL Server 2017 на Ubuntu 16.04. Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Этого учебника требуется ввод данных пользователем и подключение к Интернету. Если вы заинтересованы в [автоматической](sql-server-linux-setup.md#unattended) или [автономной](sql-server-linux-setup.md#offline) процедуры установки см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь компьютер Ubuntu 16.04 с **по крайней мере 2 ГБ** памяти.

Чтобы установить Ubuntu на своем локальном компьютере, перейдите к [ http://www.ubuntu.com/download/server ](http://www.ubuntu.com/download/server). Также можно создать виртуальные машины Ubuntu в Azure. См. в разделе [Создание и управление виртуальными машинами Linux с помощью Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> В настоящее время [подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) для Windows 10 не поддерживается в качестве целевого объекта установки.

Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Установка SQL Server

Чтобы настроить SQL Server в Ubuntu, выполните следующие команды в окне терминала, чтобы установить **mssql-server** пакета.

> [!IMPORTANT]
> Если вы ранее установили CTP-версии или версии-кандидате SQL Server 2017, необходимо сначала удалить старое хранилище перед регистрацией один из репозиториев общедоступной версии. Дополнительные сведения см. в разделе [изменить репозиториев из репозитория предварительной версии в общедоступную Версию репозиторий](sql-server-linux-change-repo.md).

1. Импорт ключей GPG общедоступного репозитория:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Зарегистрируйте репозиторий Microsoft SQL Server Ubuntu:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > Это накопительное обновление (CU) хранилища. Дополнительные сведения о параметрах репозитория и различий между ними, см. в разделе [Настройка репозиториев для SQL Server в Linux](sql-server-linux-change-repo.md).

1. Выполните следующие команды для установки SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
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

1. Если вы планируете удаленное подключение, также может потребоваться открыть порт SQL Server TCP (по умолчанию 1433) в брандмауэре.

На этом этапе SQL Server выполняется на компьютере Ubuntu и готов к использованию!

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

1. **Необязательный**: добавление `/opt/mssql-tools/bin/` для вашей **путь** переменной среды в оболочке bash.

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
