---
title: Начало работы с SQL Server контейнеров в Docker | Документация Майкрософт
description: В этом кратком руководстве показано, как использовать Docker для запуска SQL Server 2017 и образы контейнеров 2019 г. Затем мы создадим базу данных и выполним запрос с помощью sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.prod_service: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: bdd0cd86d3a20e61712f40c97e688b0d3728bcb4
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713736"
---
# <a name="quickstart-run-sql-server-container-images-with-docker"></a>Краткое руководство: Образы контейнеров запуск SQL Server с помощью Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Это краткое руководство описывает использование Docker для извлечения и запуска образа контейнера SQL Server 2017, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

> [!TIP]
> Если вы хотите попробовать SQL Server 2019 изображение для предварительного просмотра, см. в разделе [предварительной версии SQL Server 2019 в этой статье](quickstart-install-connect-docker.md?view=sql-server-linux-ver15).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом кратком руководстве, использовать Docker для извлечения и запуска образа контейнера SQL Server 2019 предварительной версии, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

::: moniker-end

Этот образ содержит SQL Server, работающий в системе Linux, основанной на Ubuntu 16.04. Он может использоваться с Dосker Engine 1.8+ на Linux или Docker для Mac или Windows. В этом кратком руководстве особое внимание уделяется использованию образа mssql-server-**linux**. Образ с Windows не рассматривается, но сведения о нем вы можете найти на странице [mssql-server-windows-developer](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) центра Docker.

## <a id="requirements"></a> Предварительные требования

- Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
- Не менее 2 ГБ места на диске
- Не менее 2 ГБ ОЗУ
- [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

<!--The following H2 is versioned for 2017 and 2019. Much of the content is duplicated, so
any changes to one section should be duplicated in the other-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="pullandrun2017"></a> Извлечение и запуск образа контейнера

1. Извлеките образ контейнера Linux с SQL Server 2017 из центра Docker.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!TIP]
   > Если вы хотите попробовать SQL Server 2019 изображение для предварительного просмотра, см. в разделе [предварительной версии SQL Server 2019 в этой статье](quickstart-install-connect-docker.md?view=sql-server-linux-ver15#pullandrun2019).

   Предыдущая команда извлекает последнюю версию образа контейнера с SQL Server 2017. Если вы хотите извлечь конкретный образ, добавьте метку после двоеточия (например, `mcr.microsoft.com/mssql/server:2017-GA`). Список всех доступных образов см. на странице [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/) центра Docker.

   Для команд bash в этой статье `sudo` используется. В Mac OS `sudo` может не потребоваться. В Linux, если вы не хотите использовать `sudo` для запуска Docker, можно настроить **docker** группы и добавление пользователей в эту группу. Дополнительные сведения см. в разделе [действия после установки для Linux](https://docs.docker.com/install/linux/linux-postinstall/).

2. Чтобы запустить образ контейнера с помощью Docker, выполните следующую команду в оболочке bash (Linux или macOS) или в командной строке PowerShell с повышенными привилегиями.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!NOTE]
   > Пароль должен удовлетворять политике паролей SQL Server по умолчанию; в противном случае контейнер не сможет настроить SQL Server и прекратит работу. По умолчанию пароль должен быть не короче восьми символов и содержать символы трех из следующих четырех групп: прописные буквы, строчные буквы, десятичные цифры, специальные символы. Проверить журнал ошибок можно, выполнив команду [docker logs](https://docs.docker.com/engine/reference/commandline/logs/).

   > [!NOTE]
   > По умолчанию она создаст контейнер с выпуском SQL Server 2017 Developer. Процесс запуска контейнера с производственными выпусками немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production).

   Следующая таблица содержит описание параметров запуска команды `docker run` из предыдущего примера.

   | Параметр | Описание |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](http://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
   | **-e "SA_PASSWORD =\<YourStrong! Passw0rd\>"** | Укажите свой надежный пароль длиной не меньше восьми символов, соответствующий [требованиям к паролям в SQL Server](../relational-databases/security/password-policy.md). Обязательный параметр для образа SQL Server. |
   | **-p 1433:1433** | Сопоставление TCP-порта среды узла (первое значение) с TCP-портом в контейнере (второе значение). В этом примере SQL Server прослушивает TCP 1433 в контейнере, и он предоставляется к порту 1433 на узле. |
   | **--name sql1** | Укажите свое имя для контейнера вместо сгенерированного случайным образом. При запуске нескольких контейнеров использовать одинаковые имена запрещено. |
   | **microsoft/mssql-server-linux:2017-latest** | Контейнер образа Linux с SQL Server 2017. |

3. Для просмотра ваших контейнеров Docker используйте команду `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   На следующем рисунке изображен примерный вывод команды.

   ![Вывод команды docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. Если в столбце **STATUS** (состояние) отображается состояние **Up** (запущен), то SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

Параметр `-h` (имя узла) может оказаться полезен, но для простоты в этом учебнике он не описывается. Он изменяет внутреннее имя контейнера на пользовательское значение. Это имя отображается при выполнении следующего запроса Transact-SQL.

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Установка параметров `-h` и `--name` равными позволяет легко идентифицировать целевой контейнер.

::: moniker-end
<!--End of 2017 "Pull and run" section-->

<!--This is the 2019 version of the "Pull and run" section-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="pullandrun2019"></a> Извлечение и запуск образа контейнера

1. Получите образ контейнера SQL Server 2019 CTP-версии 2.0 Linux из Docker Hub.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   > [!TIP]
   > В этом кратком руководстве использует образ Docker 2019 CTP-версии 2.0 для SQL Server. Если вы хотите запустить образ SQL Server 2017, см. в разделе [версию этой статьи в SQL Server 2017](quickstart-install-connect-docker.md?view=sql-server-linux-2017#pullandrun2017).

   Предыдущая команда извлекает последний образ контейнера SQL Server 2019 CTP 2.0 зависимости в Ubuntu. Вместо этого использовать образы контейнеров, в зависимости от RedHat, см. в разделе [образы контейнеров на основе запуска RHEL](sql-server-linux-configure-docker.md#rhel). Если вы хотите извлечь конкретный образ, добавьте метку после двоеточия (например, `mcr.microsoft.com/mssql/server:2017-GA`). Список всех доступных образов см. на странице [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/) центра Docker.

   Для команд bash в этой статье `sudo` используется. В Mac OS `sudo` может не потребоваться. В Linux, если вы не хотите использовать `sudo` для запуска Docker, можно настроить **docker** группы и добавление пользователей в эту группу. Дополнительные сведения см. в разделе [действия после установки для Linux](https://docs.docker.com/install/linux/linux-postinstall/).

2. Чтобы запустить образ контейнера с помощью Docker, выполните следующую команду в оболочке bash (Linux или macOS) или в командной строке PowerShell с повышенными привилегиями.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
   ```

   > [!NOTE]
   > Пароль должен удовлетворять политике паролей SQL Server по умолчанию; в противном случае контейнер не сможет настроить SQL Server и прекратит работу. По умолчанию пароль должен быть не короче восьми символов и содержать символы трех из следующих четырех групп: прописные буквы, строчные буквы, десятичные цифры, специальные символы. Проверить журнал ошибок можно, выполнив команду [docker logs](https://docs.docker.com/engine/reference/commandline/logs/).

   > [!NOTE]
   > По умолчанию она создаст контейнер с Developer edition, SQL Server 2019 CTP-версии 2.0.

   Следующая таблица содержит описание параметров запуска команды `docker run` из предыдущего примера.

   | Параметр | Описание |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](http://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
   | **-e "SA_PASSWORD =\<YourStrong! Passw0rd\>"** | Укажите свой надежный пароль длиной не меньше восьми символов, соответствующий [требованиям к паролям в SQL Server](../relational-databases/security/password-policy.md). Обязательный параметр для образа SQL Server. |
   | **-p 1433:1433** | Сопоставление TCP-порта среды узла (первое значение) с TCP-портом в контейнере (второе значение). В этом примере SQL Server прослушивает TCP 1433 в контейнере, и он предоставляется к порту 1433 на узле. |
   | **--name sql1** | Укажите свое имя для контейнера вместо сгенерированного случайным образом. При запуске нескольких контейнеров использовать одинаковые имена запрещено. |
   | **Microsoft/mssql-server-linux:vNext-CTP2.0** | Образ контейнера SQL Server 2019 CTP-версии 2.0 Linux. |

3. Для просмотра ваших контейнеров Docker используйте команду `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   На следующем рисунке изображен примерный вывод команды.

   ![Вывод команды docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. Если в столбце **STATUS** (состояние) отображается состояние **Up** (запущен), то SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

Параметр `-h` (имя узла) может оказаться полезен, но для простоты в этом учебнике он не описывается. Он изменяет внутреннее имя контейнера на пользовательское значение. Это имя отображается при выполнении следующего запроса Transact-SQL.

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Установка параметров `-h` и `--name` равными позволяет легко идентифицировать целевой контейнер.

::: moniker-end
<!--End of 2019 "Pull and run" section-->

## <a name="change-the-sa-password"></a>Смена пароля администратора

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

На следующем шаге воспользуемся средством командной строки SQL Server **sqlcmd** внутри контейнера для подключения к SQL Server.

1. Выполните команду `docker exec -it`, чтобы запустить интерактивную оболочку bash внутри запущенного контейнера. В следующем примере `sql1` — это имя, заданное в параметре `--name` при создании контейнера.

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. После входа в контейнер подключитесь локально с помощью sqlcmd. Средство sqlcmd не включено в путь по умолчанию, поэтому необходимо указать полный путь.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   > [!TIP]
   > Вы можете опустить пароль в командной строке. В этом случае вы получите приглашение для его ввода.

1. Если все сработает должным образом, вы перейдете к приглашению команды **sqlcmd**: `1>`.

## <a name="create-and-query-data"></a>Создание и запрос данных

В следующих разделах приведено пошаговое руководство по созданию базы данных, добавлению данных и запуску простого запроса с использованием **sqlcmd** и Transact-SQL.

### <a name="create-a-new-database"></a>Создание базы данных

Выполните следующие шаги, чтобы создать базу данных `TestDB`.

1. В приглашении команды **sqlcmd** вставьте следующую команду Transact-SQL, чтобы создать тестовую базу данных:

   ```sql
   CREATE DATABASE TestDB
   ```

1. В следующей строке напишите запрос, который должен вернуть имена всех баз данных на сервере:

   ```sql
   SELECT Name from sys.Databases
   ```

1. Две предыдущие команды были выполнены не сразу. Необходимо ввести `GO` на новой строке, чтобы выполнить предыдущие команды:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Вставка данных

Теперь создайте таблицу `Inventory` и вставьте две новых строки.

1. В приглашении команды **sqlcmd** переключите контекст на новую базу данных `TestDB`:

   ```sql
   USE TestDB
   ```

1. Создайте таблицу `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Вставьте данные в новую таблицу:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Введите `GO`, чтобы выполнить предыдущие команды:

   ```sql
   GO
   ```

### <a name="select-data"></a>Выбор данных

Теперь выполните запрос, чтобы вернуть данные из таблицы `Inventory`.

1. В приглашении команды **sqlcmd** введите запрос, который должен вернуть из таблицы `Inventory` строки, где количество превышает 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Выполните команду:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Выход из приглашения команды sqlcmd

1. Чтобы завершить сеанс **sqlcmd**, введите `QUIT`:

   ```sql
   QUIT
   ```

1. Чтобы выйти из интерактивной командной строки в контейнере, введите команду `exit`. Контейнер продолжит работать после выхода из интерактивной оболочки bash.

## <a id="connectexternal"></a> Подключение из-за пределов контейнера

Подключиться к экземпляру SQL Server на компьютере Docker можно также с помощью любого внешнего инструмента в macOS, Windows или Linux, поддерживающего подключения SQL.

В следующем примере используется **sqlcmd** вне контейнера для подключения к SQL Server, запущенному в контейнере. В этом примере предполагается, что в среде вне контейнера, из которой происходит подключение, уже установлены средства командной строки SQL Server. При использовании других средств действует тот же принцип, но процесс подключения является уникальным для каждого средства.

1. Определите IP-адрес компьютера, на котором размещен контейнер. В Linux используйте команды **ifconfig** или **IP-адрес**. В Windows используйте команду **ipconfig**.

1. Запустите sqlcmd, указав IP-адрес и порт, сопоставленный с портом 1433 в контейнере. В этом примере это тот же порт 1433, на хост-компьютере. Если вы не указали другой порт сопоставленные на хост-компьютере, использовать его здесь.

   ```bash
   sqlcmd -S 10.3.2.4,1433 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Выполните команды языка Transact-SQL. По завершении введите `QUIT`.

Другие распространенные средства для подключения к SQL Server:

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md);
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-manage-ssms.md);
- [Studio данных Azure (Предварительная версия)](../azure-data-studio/what-is.md)
- [mssql-cli (предварительная версия)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/).

## <a name="remove-your-container"></a>Удаление контейнера

Чтобы удалить контейнер SQL Server, используемый в этом руководстве, выполните следующие команды.

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> Остановка и удаление контейнера безвозвратно удаляет все данные SQL Server в контейнере. Чтобы сохранить данные, [создайте и скопируйте файл резервной копии за пределы контейнера](tutorial-restore-backup-in-sql-server-container.md) или используйте [метод постоянного хранения данных контейнера](sql-server-linux-configure-docker.md#persist).

## <a name="docker-demo"></a>Демонстрация возможностей Docker

После того как вы научились использовать образ контейнера SQL Server для Docker, возможно, вы захотите узнать, как использовать Docker для упрощения разработки и тестирования. Следующий видеоролик рассказывает о том, как можно использовать Docker в сценарии непрерывной интеграции и развертывания.

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>Следующие шаги

Сведения о восстановлении файлов резервной копии базы данных в контейнере см. в руководстве [Восстановление базы данных SQL Server в контейнере Docker в Linux](tutorial-restore-backup-in-sql-server-container.md). Чтобы изучить другие сценарии, такие как запуск нескольких контейнеров, сохраняемость данных и устранение неполадок, см. в разделе [SQL Server можно настроить образы контейнеров в Docker](sql-server-linux-configure-docker.md).

Кроме того, в репозитории GitHub [mssql docker](https://github.com/Microsoft/mssql-docker) вы найдете ресурсы, отзывы и известные проблемы.
