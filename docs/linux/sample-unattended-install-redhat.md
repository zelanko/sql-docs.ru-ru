---
title: Автоматическая установка SQL Server на Red Hat Enterprise Linux
titleSuffix: SQL Server
description: Пример скрипта SQL Server — автоматическая установка на Red Hat Enterprise Linux
author: VanMSFT
ms.author: vanto
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 696ba88a9f2d5f29de8dc3afb45af8c392f2de68
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "67910440"
---
# <a name="sample-unattended-sql-server-installation-script-for-red-hat-enterprise-linux"></a>Образец. Скрипт автоматической установки SQL Server для Red Hat Enterprise Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом примере скрипта Bash выполняется установка SQL Server 2017 на Red Hat Enterprise Linux (RHEL) без интерактивного ввода. В нем демонстрируются примеры установки ядра СУБД, программ командной строки SQL Server и агента SQL Server, а также действий, которые необходимо выполнить после установки. При необходимости вы можете установить компонент полнотекстового поиска и создать пользователя с правами администратора.

> [!TIP]
> Если вам не требуется скрипт автоматической установки, можно воспользоваться самым простым способом установки SQL Server, который описывается в [кратком руководстве для Red Hat](quickstart-install-connect-red-hat.md). Дополнительные сведения об установке см. в разделе [Руководство по установке SQL Server на Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>предварительные требования

- Для работы с SQL Server на Linux потребуется не менее 2 ГБ памяти.
- Должна использоваться файловая система **XFS** или **EXT4**. Другие файловые системы, например **BTRFS**, не поддерживаются.
- Сведения о других требованиях к системе см. в статье [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="sample-script"></a>Пример скрипта
Сохраните этот пример скрипта в файл и затем замените значения переменных в скрипте в соответствии с требованиями. Также вы можете задать любые переменные скрипта как переменные среды, предварительно удалив их из файла скрипта.

```bash
#!/bin/bash -e

# Use the following variables to control your install:

# Password for the SA user (required)
MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'

# Product ID of the version of SQL server you're installing
# Must be evaluation, developer, express, web, standard, enterprise, or your 25 digit product key
# Defaults to developer
MSSQL_PID='evaluation'

# Install SQL Server Agent (recommended)
SQL_ENABLE_AGENT='y'

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
sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo

echo Installing SQL Server...
sudo yum install -y mssql-server

echo Running mssql-conf setup...
sudo MSSQL_SA_PASSWORD=$MSSQL_SA_PASSWORD \
     MSSQL_PID=$MSSQL_PID \
     /opt/mssql/bin/mssql-conf -n setup accept-eula

echo Installing mssql-tools and unixODBC developer...
sudo ACCEPT_EULA=Y yum install -y mssql-tools unixODBC-devel

# Add SQL Server tools to the path by default:
echo Adding SQL Server tools to your path...
echo PATH="$PATH:/opt/mssql-tools/bin" >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc

# Optional Enable SQL Server Agent :
if [ ! -z $SQL_ENABLE_AGENT ]
then
  echo Enable SQL Server Agent...
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
fi

# Optional SQL Server Full Text Search installation:
if [ ! -z $SQL_INSTALL_FULLTEXT ]
then
    echo Installing SQL Server Full-Text Search...
    sudo yum install -y mssql-server-fts
fi

# Configure firewall to allow TCP port 1433:
echo Configuring firewall to allow traffic on port 1433...
sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
sudo firewall-cmd --reload

# Example of setting post-installation configuration options
# Set trace flags 1204 and 1222 for deadlock tracing:
#echo Setting trace flags...
#sudo /opt/mssql/bin/mssql-conf traceflag 1204 1222 on

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

## <a name="running-the-script"></a>Запуск скрипта

Выполнение скрипта

1. Вставьте этот пример в предпочитаемый текстовый редактор и сохраните его под удобным для запоминания именем, например `install_sql.sh`.

1. Настройте `MSSQL_SA_PASSWORD`, `MSSQL_PID` и любые другие переменные, которые требуется изменить.

1. Пометка скрипта исполняемым

   ```bash
   chmod +x install_sql.sh
   ```

1. Выполнение скрипта

   ```bash
   ./install_sql.sh
   ```

## <a name="understanding-the-script"></a>Основные сведения о скрипте

Сначала этот скрипт Bash устанавливает значения некоторых переменных.  Это могут быть как переменные скрипта, например этого образца, так и переменные среды.  Переменная `MSSQL_SA_PASSWORD` является **обязательной** для установки SQL Server. Остальные переменные являются пользовательскими и при необходимости задаются для скрипта.  Этот пример скрипта выполняет следующие операции:

1. Импорт открытых ключей, например Microsoft GPG.

1. Регистрация репозиториев Майкрософт для SQL Server и программ командной строки.

1. Обновление локальных репозиториев

1. Установка SQL Server

1. Задайте конфигурацию SQL Server с ```MSSQL_SA_PASSWORD``` и автоматически примите условия лицензионного соглашения.

1. Автоматически примите лицензионное соглашение для программ командной строки SQL Server, установите их, а затем установите пакет unixodbc-dev.

1. Для удобства работы добавьте программы командной строки SQL Server в путь.

1. Если задана переменная скрипта ```SQL_INSTALL_AGENT``` (по умолчанию включена), установите агент SQL Server.

1. Если задана переменная ```SQL_INSTALL_FULLTEXT```, при необходимости установите компонент полнотекстового поиска SQL Server.

1. В брандмауэре системы разблокируйте порт TCP 1433, который используется для подключения к SQL Server из других систем.

1. При необходимости установите флаги трассировки для отслеживания состояний взаимоблокировки. (требуется раскомментировать строки)

1. Установка SQL Server завершена. Прежде чем начать работу с ней, перезапустите процесс.

1. Проверьте корректность установки SQL Server (при необходимости скрывайте сообщения об ошибках).

1. Если одновременно заданы переменные ```SQL_INSTALL_USER``` и ```SQL_INSTALL_USER_PASSWORD```, создайте нового пользователя с правами администратора сервера.

## <a name="next-steps"></a>Следующие шаги

Чтобы оптимизировать многократную автоматическую установку, создайте автономный скрипт Bash, который будет задавать нужные переменные среды.  Вы можете удалить любые переменные из этого примера скрипта и поместить их в отдельный скрипт Bash.

```bash
#!/bin/bash
export MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'
export MSSQL_PID='evaluation'
export SQL_INSTALL_AGENT='y'
export SQL_INSTALL_USER='<Username>'
export SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'
export SQL_INSTALL_AGENT='y'
```

После этого запустите скрипт Bash следующим образом:
```bash
. ./my_script_name.sh
```

Дополнительные сведения об SQL Server на Linux см. в разделе [Сведения об SQL Server на Linux](sql-server-linux-overview.md).
