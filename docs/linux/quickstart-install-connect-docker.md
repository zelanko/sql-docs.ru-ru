---
title: "Приступая к работе с SQL Server 2017 г. на Docker | Документы Microsoft"
description: "Краткого руководства показано, как использовать Docker для выполнения образ контейнера 2017 г. SQL Server. Затем создайте и запросов к базе данных с помощью sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.workload: Active
ms.openlocfilehash: 0cfea0b32221f6aa1ebb8cb947640de3b670c79c
ms.sourcegitcommit: b09bccd6dfdba55b022355e892c29cb50aadd795
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Запускать образ контейнера 2017 г. SQL Server с помощью Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом кратком руководстве использовать Docker для извлечения и запустить образ контейнера 2017 г. SQL Server, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Подключитесь с **sqlcmd** для создания первой базы данных и выполнения запросов.

Этот образ состоит из SQL Server на основании Ubuntu 16.04 Linux. Он может использоваться с подсистемой Dосker 1.8 + на Linux или Docker для Mac и Windows.

> [!NOTE]
> В этом кратком руководстве особое внимание уделяется с помощью mssql-server -**linux** изображения. Непокрытые образа Windows, но Дополнительные сведения о нем на [страницы Docker Hub mssql-server-windows разработчика](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a id="requirements"></a> Предварительные требования

- Подсистема docker 1.8 + для какого-либо поддерживается дистрибутив Linux или Docker для Mac и Windows. Дополнительные сведения см. в разделе [установить Docker](https://docs.docker.com/engine/installation/).
- Минимум 2 ГБ места на диске
- Минимум 2 ГБ ОЗУ
- [Требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>По запросу, а затем запускать образ контейнера

1. Образ контейнера Linux 2017 г. SQL Server по запросу из Docker Hub.

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   Предыдущая команда извлекает последнюю образ контейнера 2017 г. SQL Server. Если вы хотите запросить конкретный образ, добавлении двоеточие и имя тега (например, `microsoft/mssql-server-linux:2017-GA`). Для просмотра всех доступных образов, в разделе [страница концентратора Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Чтобы запустить образ контейнера с помощью Docker, можно использовать следующую команду в оболочке bash (Linux/macOS) или командную строку PowerShell.

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
   > Пароль должен соответствовать политика паролей по умолчанию SQL Server, в противном случае программа установки SQL server не может контейнера и прекратит работу. По умолчанию пароль должен содержать по крайней мере 8 символов и содержать символы трех из следующих четырех: прописные буквы, строчные буквы, цифры и символы. Можно проверить журнал ошибок при выполнении [docker журналы](https://docs.docker.com/engine/reference/commandline/logs/) команды.

   > [!NOTE]
   > По умолчанию это создает контейнер выпуск Developer 2017 г. SQL Server. Процесс запуска выпуски производства в контейнерах немного отличается. Дополнительные сведения см. в разделе [запуска производства образы контейнеров](sql-server-linux-configure-docker.md#production).

   Ниже приводится описание этих параметров в предыдущем `docker run` пример:

   | Параметр | Описание |
   |-----|-----|
   | **-e "ACCEPT_EULA = Y"** |  Задать **ACCEPT_EULA** переменную, чтобы любое значение, чтобы подтвердить свое согласие с [лицензионное соглашение конечного пользователя](http://go.microsoft.com/fwlink/?LinkId=746388). Требуется для образа SQL Server. |
   | **-e 'MSSQL_SA_PASSWORD=\<YourStrong!Passw0rd\>'** | Укажите свои собственные надежный пароль, по крайней мере 8 символов и соответствует [требования к паролю для SQL Server](../relational-databases/security/password-policy.md). Требуется для образа SQL Server. |
   | **-p 1401:1433** | Сопоставление порта TCP на хост-среды (первое значение) с TCP-порт в контейнере (второе значение). В этом примере SQL Server прослушивает TCP 1433 в контейнере, и оно предоставляется на порт 1401 на узле. |
   | **— Имя sql1** | Укажите имя файла для контейнера, а не случайным. Если выполняется более одного контейнера, не может использовать таким же именем. |
   | **microsoft/mssql-server-linux:2017-latest** | Образ контейнера Linux 2017 г. SQL Server. |

1. Чтобы просмотреть в контейнеры Docker, используйте `docker ps` команды.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   Вы увидите выходные данные, аналогичные следующим образом:

   ![Выходные данные команды docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. Если **состояние** столбце отображается состояние **копирование**, затем SQL Server работает в контейнере и прослушивается порт, указанный в **ПОРТЫ** столбца. Если **состояние** столбца отображается контейнер к SQL Server **завершил работу**, см. [Устранение неполадок конфигурации руководства](sql-server-linux-configure-docker.md#troubleshooting).

`-h` Параметр (имя узла) также полезен, но он не используется в этом учебнике для простоты. Это изменяет внутреннее имя контейнера пользовательское значение. Это имя, вы увидите возвращается в следующем запросе Transact-SQL:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Установка `-h` и `--name` то же значение является удобным способом легко идентифицировать целевой контейнер.

## <a name="change-the-sa-password"></a>Измените пароль учетной записи SA

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

В следующих действиях используется средство командной строки SQL Server **sqlcmd**, внутри контейнера для подключения к SQL Server.

1. Используйте `docker exec -it` команду, чтобы запустить интерактивный bash оболочки внутри вашей запущенного контейнера. В следующем примере `sql1` задается имя `--name` параметр при создании контейнера.

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. Один раз внутри контейнера, подключите локально с помощью sqlcmd. SQLCMD не в пути по умолчанию, поэтому необходимо указать полный путь.

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

1. Чтобы выйти из интерактивного командной строки в контейнере, введите `exit`. Контейнер продолжается после выхода из оболочки интерактивный bash.

## <a id="connectexternal"></a>Подключение из вне контейнера

Также можно соединиться с экземпляром SQL Server на компьютере Docker с помощью любого внешнего средства macOS, Windows или Linux, поддерживающее подключения SQL.

В следующих шагах используется **sqlcmd** вне контейнера для подключения к SQL Server, запущенный в контейнере. Эти шаги предполагают, уже установлены в нерабочее контейнера средства командной строки SQL Server. Применяются те же механизмы, при использовании других средств, но процесс подключения является уникальным для каждого средства.

1. Найти IP-адрес для компьютера, на котором размещен контейнер. В Linux, используйте **ifconfig** или **IP-адрес**. В Windows, используйте **ipconfig**.

1. Выполнение программы sqlcmd, указав IP-адрес и порт сопоставлен порт 1433 в контейнере. В этом примере это порт 1401 на хост-компьютере.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Выполнение команд Transact-SQL. По завершении введите `QUIT`.

Другие общие средства для подключения к SQL Server включают:

- [Код Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-develop-use-ssms.md)
- [SQL Server Operations Studio (Предварительная версия)](../sql-operations-studio/what-is.md)
- [mssql-cli (Preview)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

## <a name="remove-your-container"></a>Удаление контейнера

Если вы хотите удалить контейнер SQL Server, используемые в этом учебнике, выполните следующие команды:

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> Остановка и удаление контейнера окончательно удаляет все данные SQL Server в контейнере. Если необходимо сохранить данные, [создайте и скопируйте файл резервной копии из контейнера](tutorial-restore-backup-in-sql-server-container.md) или использовать [контейнера данных сохраняемости метод](sql-server-linux-configure-docker.md#persist).

## <a name="docker-demo"></a>Демонстрация docker

После вы попытались использовать образ контейнера SQL Server для Docker, можно узнать, как использовать Docker для улучшения разработки и тестирования. В следующем видео показано, как можно использовать Docker в непрерывной интеграции и сценария развертывания.

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>Следующие шаги

Учебник по восстановлению файлов резервной копии базы данных в контейнер, в разделе [восстановление базы данных SQL Server в контейнер Linux Docker](tutorial-restore-backup-in-sql-server-container.md). Другие сценарии, например для запуска несколько контейнеров данных сохраняемости и устранение неполадок, в статье [образов контейнеров Настройка 2017 г SQL Server на Docker](sql-server-linux-configure-docker.md).

Кроме того, ознакомьтесь [mssql docker репозитории GitHub](https://github.com/Microsoft/mssql-docker) ресурсы, отзывы и известные проблемы.
