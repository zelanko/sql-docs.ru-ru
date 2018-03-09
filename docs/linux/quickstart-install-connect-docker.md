---
title: "Приступая к работе с SQL Server 2017 на Docker | Документация Майкрософт"
description: "Это краткое руководство описывает, как использовать Docker для запуска образа контейнера SQL Server 2017. Затем мы создадим базу данных и выполним запрос с помощью sqlcmd."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/07/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.workload: Active
ms.openlocfilehash: 8c3f8bc09ef8c3b6838912027024a3feb97cea5d
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="quickstart-run-the-sql-server-2017-container-image-with-docker"></a>Краткое руководство: Запуск образа контейнера 2017 г. SQL Server с помощью Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это краткое руководство описывает использование Docker для извлечения и запуска образа контейнера SQL Server 2017, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Затем мы подключимся при помощи **sqlcmd** для создания первой базы данных и выполнения запросов.

Этот образ содержит SQL Server, работающий в системе Linux, основанной на Ubuntu 16.04. Он может использоваться с Dосker Engine 1.8+ на Linux или Docker для Mac или Windows.

> [!NOTE]
> В этом кратком руководстве особое внимание уделяется использованию образа mssql-server-**linux**. Образ с Windows не рассматривается, но сведения о нем вы можете найти на странице [mssql-server-windows-developer](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) центра Docker.

## <a id="requirements"></a> Предварительные требования

- Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
- Не менее 2 ГБ места на диске
- Не менее 2 ГБ ОЗУ
- [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

1. Извлеките образ контейнера Linux с SQL Server 2017 из центра Docker.

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   Предыдущая команда извлекает последнюю версию образа контейнера с SQL Server 2017. Если вы хотите извлечь конкретный образ, добавьте метку после двоеточия (например, `microsoft/mssql-server-linux:2017-GA`). Список всех доступных образов см. на странице [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/) центра Docker.
   
   Для команд bash в этой статье `sudo` используется. На MacOS `sudo` не является обязательным. В Linux, если вы не хотите использовать `sudo` для запуска Docker, можно настроить **docker** группы и добавление пользователей в эту группу. Дополнительные сведения см. в разделе [действия после установки для Linux](https://docs.docker.com/install/linux/linux-postinstall/).

1. Чтобы запустить образ контейнера с помощью Docker, выполните следующую команду в оболочке bash (Linux или macOS) или в командной строке PowerShell с повышенными привилегиями.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1401:1433 --name sql1 \
      -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1401:1433 --name sql1 `
      -d microsoft/mssql-server-linux:2017-latest
   ```

   > [!NOTE]
   > Пароль должен удовлетворять политике паролей SQL Server по умолчанию; в противном случае контейнер не сможет настроить SQL Server и прекратит работу. По умолчанию пароль должен быть не короче восьми символов и содержать символы трех из следующих четырех групп: прописные буквы, строчные буквы, десятичные цифры, специальные символы. Проверить журнал ошибок можно, выполнив команду [docker logs](https://docs.docker.com/engine/reference/commandline/logs/).

   > [!NOTE]
   > По умолчанию она создаст контейнер с выпуском SQL Server 2017 Developer. Процесс запуска контейнера с производственными выпусками немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production).

   Следующая таблица содержит описание параметров запуска команды `docker run` из предыдущего примера.

   | Параметр | Описание |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  Присвойте переменной **ACCEPT_EULA** любое значение, чтобы подтвердить свое согласие с [лицензионным соглашением](http://go.microsoft.com/fwlink/?LinkId=746388). Обязательный параметр для образа SQL Server. |
   | **-e 'MSSQL_SA_PASSWORD=\<YourStrong!Passw0rd\>'** | Укажите свой надежный пароль длиной не меньше восьми символов, соответствующий [требованиям к паролям в SQL Server](../relational-databases/security/password-policy.md). Обязательный параметр для образа SQL Server. |
   | **-p 1401:1433** | Сопоставление TCP-порта среды узла (первое значение) с TCP-портом в контейнере (второе значение). В нашем примере SQL Server прослушивает TCP-порт 1433 в контейнере, который перенаправляется на порт 1401 на узле. |
   | **--name sql1** | Укажите свое имя для контейнера вместо сгенерированного случайным образом. При запуске нескольких контейнеров использовать одинаковые имена запрещено. |
   | **microsoft/mssql-server-linux:2017-latest** | Контейнер образа Linux с SQL Server 2017. |

1. Для просмотра ваших контейнеров Docker используйте команду `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   На следующем рисунке изображен примерный вывод команды.

   ![Вывод команды docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. Если в столбце **STATUS** (состояние) отображается состояние **Up** (запущен), то SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

Параметр `-h` (имя узла) может оказаться полезен, но для простоты в этом учебнике он не описывается. Он изменяет внутреннее имя контейнера на пользовательское значение. Это имя отображается при выполнении следующего запроса Transact-SQL.

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Установка параметров `-h` и `--name` равными позволяет легко идентифицировать целевой контейнер.

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

1. Запустите sqlcmd, указав IP-адрес и порт, сопоставленный с портом 1433 в контейнере. В нашем примере это порт 1401 на хост-компьютере.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Выполните команды языка Transact-SQL. По завершении введите `QUIT`.

Другие распространенные средства для подключения к SQL Server:

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md);
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-develop-use-ssms.md);
- [SQL Server Operations Studio (предварительная версия)](../sql-operations-studio/what-is.md);
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

Сведения о восстановлении файлов резервной копии базы данных в контейнере см. в руководстве [Восстановление базы данных SQL Server в контейнере Docker в Linux](tutorial-restore-backup-in-sql-server-container.md). Сведения о других сценариях, таких как запуск нескольких контейнеров, сохраняемость данных и устранение неполадок, см. в руководстве [Настройка образов контейнеров SQL Server 2017 в Docker](sql-server-linux-configure-docker.md).

Кроме того, в репозитории GitHub [mssql docker](https://github.com/Microsoft/mssql-docker) вы найдете ресурсы, отзывы и известные проблемы.
