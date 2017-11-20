---
title: "Автоматическая установка SQL Server в SUSE Linux Enterprise Server | Документы Microsoft"
description: "Пример сценария SQL Server — автоматическая установка на SUSE Linux Enterprise Server"
author: edmacauley
ms.author: edmacauley
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: e181fb02497f1673a8993687d159f6636aca4959
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="sample-unattended-sql-server-installation-script-for-suse-linux-enterprise-server"></a>Пример: Сценария установки автоматической установки SQL Server для SUSE Linux Enterprise Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Этот пример скрипта Bash устанавливает 2017 г. SQL Server на SP2 v12 SUSE Linux Enterprise Server (SLES) без интерактивного ввода данных. Он предоставляет примеры установке ядра СУБД, средства командной строки SQL Server, агент SQL Server и выполняет шаги после установки. При необходимости можно установить компонент full-text search и создать пользователя с правами администратора.

> [!TIP]
> Если не требуется использовать сценарий автоматической установки, то самый быстрый способ установки SQL Server является выполните [краткого руководства по SLES](quickstart-install-connect-suse.md). Другие сведения о настройке в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Предварительные требования

- Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
- Файловая система должна быть **XFS** или **EXT4**. Других файловых систем, таких как **BTRFS**, не поддерживаются.
- Другие требования к системе см. в разделе [требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

> [!IMPORTANT]
> 2017 г. SQL Server требуется libsss_nss_idmap0, не предоставляемых репозиториев SLES по умолчанию. Его можно установить из пакета SDK SP2 SLES версии 12.

## <a name="sample-script"></a>Пример сценария

```bash
#!/bin/bash

# Use the following variables to control your install:

# Password for the SA user (required)
MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'

# Product ID of the version of SQL server you're installing
# Must be evaluation, developer, express, web, standard, enterprise, or your 25 digit product key
# Defaults to developer
MSSQL_PID='evaluation'

# Install SQL Server Agent (recommended)
SQL_INSTALL_AGENT='y'

# Install SQL Server Full Text Search (optional)
# SQL_INSTALL_FULLTEXT='y'

# Create an additional user with sysadmin privileges (optional)
# SQL_INSTALL_USER='<Username>'
# SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'

if [ -z $MSSQL_SA_PASSWORD ]
then
  echo Environment variable MSSQL_SA_PASSWORD must be set for unattended install
  exit 1
fi

echo Adding Microsoft repositories...
sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
sudo zypper --gpg-auto-import-keys refresh

#Add the SLES v12 SP2 SDK to obtain libsss_nss_idmap0
sudo SUSEConnect -p sle-sdk/12.2/x86_64

echo Installing SQL Server...
sudo zypper install -y mssql-server

echo Running mssql-conf setup...
sudo MSSQL_SA_PASSWORD=$MSSQL_SA_PASSWORD \
     MSSQL_PID=$MSSQL_PID \
     /opt/mssql/bin/mssql-conf -n setup accept-eula

echo Installing mssql-tools and unixODBC developer...
sudo ACCEPT_EULA=Y zypper install -y mssql-tools unixODBC-devel

# Add SQL Server tools to the path by default:
echo Adding SQL Server tools to your path...
echo PATH="$PATH:/opt/mssql-tools/bin" >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc

# Optional SQL Server Agent installation:
if [ ! -z $SQL_INSTALL_AGENT ]
then
  echo Installing SQL Server Agent...
  sudo zypper install -y mssql-server-agent
fi

# Optional SQL Server Full Text Search installation:
if [ ! -z $SQL_INSTALL_FULLTEXT ]
then
    echo Installing SQL Server Full-Text Search...
    sudo zypper install -y mssql-server-fts
fi

# Configure firewall to allow TCP port 1433:
echo Configuring SuSEfirewall2 to allow traffic on port 1433...
sudo SuSEfirewall2 open INT TCP 1433
sudo SuSEfirewall2 stop
sudo SuSEfirewall2 start

# Example of setting post-installation configuration options
# Set trace flags 1204 and 1222 for deadlock tracing:
# echo Setting trace flags...
# sudo /opt/mssql/bin/mssql-conf traceflag 1204 1222 on

# Restart SQL Server after making configuration changes:
echo Restarting SQL Server...
sudo systemctl restart mssql-server

# Connect to server and get the version:
counter=1
errstatus=1
while [ $counter -le 5 ] && [ $errstatus = 1 ]
do
  echo Waiting for SQL Server to start...
  sleep 5s
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "SELECT @@VERSION" 2>/dev/null
  errstatus=$?
  ((counter++))
done

# Display error if connection failed:
if [ $errstatus = 1 ]
then
  echo Cannot connect to SQL Server, installation aborted
  exit $errstatus
fi

# Optional new user creation:
if [ ! -z $SQL_INSTALL_USER ] && [ ! -z $SQL_INSTALL_USER_PASSWORD ]
then
  echo Creating user $SQL_INSTALL_USER
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "CREATE LOGIN [$SQL_INSTALL_USER] WITH PASSWORD=N'$SQL_INSTALL_USER_PASSWORD', DEFAULT_DATABASE=[master], CHECK_EXPIRATION=ON, CHECK_POLICY=ON; ALTER SERVER ROLE [sysadmin] ADD MEMBER [$SQL_INSTALL_USER]"
fi

echo Done!
```

### <a name="running-the-script"></a>Запуск сценария

Выполнение скрипта

1. Вставьте образец в другом текстовом редакторе и сохраните его с запоминающимися имя, например `install_sql.sh`.

1. Настройка `MSSQL_SA_PASSWORD`, `MSSQL_PID`и любые другие переменные, которые вы хотите изменить.

1. Пометить скрипт как исполняемый файл

   ```bash
   chmod +x install_sql.sh
   ```

1. Запустите сценарий

   ```bash
   ./install_sql.sh
   ```

### <a name="understanding-the-script"></a>Основные сведения о скрипте
Первое, что сценарий Bash делает задано несколько переменных. Это могут быть переменные сценария, как в примере или переменных среды. Переменная ``` MSSQL_SA_PASSWORD ``` — **необходимые** по установке SQL Server, другие типы являются пользовательских переменных, созданных для скрипта. Пример скрипта выполняет следующие действия:

1. Импортируйте открытые ключи GPG корпорации Майкрософт.

1. Зарегистрируйте репозиториев Microsoft SQL Server и средства командной строки.

1. Обновление локального хранилища

1. Установка SQL Server

1. Настройка SQL Server с ```MSSQL_SA_PASSWORD``` и автоматически принимать лицензионное соглашение.

1. Автоматически примите лицензионное соглашение для средства командной строки SQL Server, установите их и установить пакет разработки unixodbc.

1. Добавьте в путь для удобства использования средства командной строки SQL Server.

1. Установка агента SQL Server, если переменная сценария ```SQL_INSTALL_AGENT``` , на значение по умолчанию.

1. При необходимости можно установить SQL Server Full-Text search, если переменная ```SQL_INSTALL_FULLTEXT``` имеет значение.

1. Разблокируйте порт 1433 для TCP-Соединений в брандмауэре системы, необходимые для подключения к SQL Server из другой системы.

1. При необходимости установить флаги трассировки для трассировки взаимоблокировки. (требуется раскомментировать строки)

1. Установлен SQL Server, чтобы он работали, необходимо перезапустить процесс.

1. Убедитесь, что SQL Server установлен правильно, скрывая все сообщения об ошибках.

1. Создайте нового пользователя администратора сервера, если ```SQL_INSTALL_USER``` и ```SQL_INSTALL_USER_PASSWORD``` одновременно установлены.

## <a name="next-steps"></a>Следующие шаги

Упростить несколько автоматической установки и создания автономного Bash скрипт, который задает переменные среды, соответствующие. Можно удалить все переменные образец скрипта использует и поместить их в свои собственные сценарии Bash.

```bash
#!/bin/bash
export MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'
export MSSQL_PID='evaluation'
export SQL_INSTALL_AGENT='y'
export SQL_INSTALL_USER='<Username>'
export SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'
export SQL_INSTALL_AGENT='y'
```

Затем выполните скрипт Bash следующим образом:
```bash
. ./my_script_name.sh
```

Дополнительные сведения о SQL Server в Linux см. в разделе [Linux Обзор SQL Server на](sql-server-linux-overview.md).

