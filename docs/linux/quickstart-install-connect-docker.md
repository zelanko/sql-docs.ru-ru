---
title: "Приступая к работе с SQL Server 2017 г. на Docker | Документы Microsoft"
description: "Этого краткого руководства показано, как использовать Docker для выполнения образ контейнера 2017 г. SQL Server. Затем создайте и запросов к базе данных с помощью sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 95c360dad72a9cd075f2a85d2581dc8021adf941
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Запускать образ контейнера 2017 г. SQL Server с помощью Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом учебнике быстрого запуска использовать Docker для извлечения и запускать контейнер образ SQL Server 2017 г., RC2, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Подключитесь с **sqlcmd** для создания первой базы данных и выполнения запросов.

Этот образ состоит из SQL Server на основании Ubuntu 16.04 Linux. Он может использоваться с подсистемой Dосker 1.8 + на Linux или Docker для Mac и Windows.

> [!NOTE]
> В этом кратком руководстве особое внимание уделяется с помощью образа mssql-server-linux. Непокрытые образа Windows, но Дополнительные сведения о нем на [Docker Hub страница windows для сервера mssql](https://hub.docker.com/r/microsoft/mssql-server-windows/).

## <a id="requirements"></a> Предварительные требования

- Подсистема docker 1.8 + для какого-либо поддерживается дистрибутив Linux или Docker для Mac и Windows.
- Менее 4 ГБ места на диске
- Не менее 4 ГБ ОЗУ
- [Требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

> [!IMPORTANT]
> По умолчанию в Docker для Mac и Docker для Windows является 2 ГБ для виртуальной Машины Moby, поэтому следует изменить его до 4 ГБ. Если на компьютере Mac или Windows используйте следующие процедуры увеличить размер памяти.

### <a name="increase-docker-memory-to-4-gb-mac"></a>Увеличьте объем памяти Docker 4 ГБ (Mac)

Следующие шаги увеличить объем памяти для Docker для Mac на 4 ГБ.

1. Щелкните эмблему Docker в строке состояния top.
1. Выберите **предпочтения**.
1. Переместите индикатор памяти в 4 ГБ или более.
1. Нажмите кнопку **перезапустите** кнопку в кнопке экрана.

### <a name="increase-docker-memory-to-4-gb-windows"></a>Увеличьте объем памяти Docker 4 ГБ (Windows)

Следующие шаги увеличить объем памяти для Docker для Windows до 4 ГБ.

1. Щелкните правой кнопкой мыши значок Docker из панели задач.
1. Нажмите кнопку **параметры** в соответствующее меню.
1. Нажмите кнопку **Advanced** вкладки.
1. Переместите индикатор памяти в 4 ГБ или более.
1. Нажмите кнопку **применить** кнопки.

## <a name="pull-and-run-the-container-image"></a>По запросу, а затем запускать образ контейнера

1. Образ контейнера по запросу из Docker Hub.

    ```bash
    docker pull microsoft/mssql-server-linux
    ```

    > [!TIP]
    > Для Linux, в зависимости от конфигурации системы или пользователя, может потребоваться в начале каждого `docker` с `sudo`.

1. Чтобы запустить образ контейнера с помощью Docker, можно использовать следующую команду в оболочке bash (Linux/macOS):

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -e 'MSSQL_PID=Developer' --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux
    ```

    При использовании Docker для Windows, используйте следующую команду с повышенными привилегиями PowerShell командной строки:

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux
    ```

    > [!NOTE]
    > Единственное различие между bash (Linux/macOS) и примерах PowerShell (Windows) — одинарные и двойные кавычки вокруг переменные среды. Выполните команду docker завершается сбоем, если используется не тот. В оставшейся части этого раздела bash и блоки кода PowerShell предоставляются для удобства. Если имеется только один из примеров, она работает на всех платформах, включая Windows.

    Ниже приводится описание этих параметров в предыдущем `docker run` пример:

    | Параметр | Description |
    |-----|-----|
    | **-e "ACCEPT_EULA = Y"** |  Задать **ACCEPT_EULA** переменную, чтобы любое значение, чтобы подтвердить свое согласие с [лицензионное соглашение конечного пользователя](http://go.microsoft.com/fwlink/?LinkId=746388). Требуется для образа SQL Server. |
    | **-e "MSSQL_SA_PASSWORD =\<YourStrong! Passw0rd\>"** | Укажите свои собственные надежный пароль, по крайней мере 8 символов и соответствует [требования к паролю для SQL Server](../relational-databases/security/password-policy.md). Требуется для образа SQL Server. |
    | **-e "MSSQL_PID = разработчика"** | Задает ключ, выпуск или продукта. В этом примере свободно лицензионный выпуск Developer используется для тестирования в нерабочей. Другие значения в разделе [SQL Server можно настроить параметры с переменными среды на Linux](sql-server-linux-configure-environment-variables.md). |
    | **--Добавление cap SYS_PTRACE** | Добавляет возможность отслеживать процесс Linux. Это позволяет SQL Server для создания файлов дампа при возникновении исключения. |
    | **1401:1433 -p** | Сопоставление порта TCP на хост-среды (первое значение) с TCP-порт в контейнере (второе значение). В этом примере SQL Server прослушивает TCP 1433 в контейнере, и оно предоставляется на порт 1401 на узле. |
    | **Microsoft и mssql-server-linux** | Образ контейнера SQL Server Linux. Если не указано иное, по умолчанию используется **последние** изображения. |

1. Чтобы просмотреть в контейнеры Docker, используйте `docker ps` команды.

    ```bash
    docker ps -a
    ```

    Вы увидите выходные данные, аналогичные следующим образом:

    ![Выходные данные команды docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. Если **состояние** столбце отображается состояние **копирование**, затем SQL Server работает в контейнере и прослушивается порт, указанный в **ПОРТЫ** столбца. Если **состояние** столбца отображается контейнер к SQL Server **завершил работу**, см. [Устранение неполадок конфигурации руководства](sql-server-linux-configure-docker.md#troubleshooting).

Существует две полезные `docker run` параметры, не используемые в предыдущем примере для простоты. `-h` Параметр (имя узла) изменяет внутреннее имя контейнера пользовательское значение. Это имя, вы увидите возвращается в следующем запросе Transact-SQL:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Также может оказаться `--name` параметр полезно имя контейнера, а не с именем созданного контейнера. Установка `-h` и `--name` то же значение является удобным способом легко идентифицировать целевой контейнер.

## <a name="change-the-sa-password"></a>Измените пароль учетной записи SA

Учетная запись SA является системным администратором на экземпляре SQL Server, который создается во время установки. После создания контейнера SQL Server, `MSSQL_SA_PASSWORD` указанной переменной среды можно обнаружить, запустив `echo $MSSQL_SA_PASSWORD` в контейнере. В целях безопасности смените пароль SA.

1. Выберите надежный пароль для пользователя SA.

1. Используйте `docker exec` для запуска **sqlcmd** изменение пароля с помощью Transact-SQL. Замените `<Old Password>` и `<New Password>` значениями ваш пароль.

> ```bash
> docker exec -it <Container ID> /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<Old Password>' -Q 'ALTER LOGIN SA WITH PASSWORD="<New Password>";'
> ```

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

В следующих действиях используется средство командной строки SQL Server **sqlcmd**, внутри контейнера для подключения к SQL Server.

1. Используйте `docker exec -it` команду, чтобы запустить интерактивный bash оболочки внутри вашей запущенного контейнера. В следующем примере `e69e056c702d` — это идентификатор контейнера.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Не всегда необходимо указывать идентификатор весь контейнер. Необходимо указать достаточно символов, для его однозначной идентификации. Поэтому в этом примере может быть достаточно, чтобы использовать `e6` или `e69` вместо полного идентификатора.

1. Один раз внутри контейнера, подключите локально с помощью sqlcmd. SQLCMD не в пути по умолчанию, поэтому необходимо указать полный путь.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
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

## <a name="connect-from-outside-the-container"></a>Подключение из вне контейнера

Также можно соединиться с экземпляром SQL Server на компьютере Docker с помощью любого внешнего средства macOS, Windows или Linux, поддерживающее подключения SQL.

В следующих шагах используется **sqlcmd** вне контейнера для подключения к SQL Server, запущенный в контейнере. Эти шаги предполагают, уже установлены в нерабочее контейнера средства командной строки SQL Server. Применяются те же механизмы, при использовании других средств, но процесс подключения является уникальным для каждого средства.

1. Найти IP-адрес для компьютера, на котором размещен контейнер. В Linux, используйте **ifconfig** или **IP-адрес**. В Windows, используйте **ipconfig**.

1. Выполнение программы sqlcmd, указав IP-адрес и порт сопоставлен порт 1433 в контейнере. В этом примере это порт 1401 на хост-компьютере.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
   ```

1. Выполнение команд Transact-SQL. По завершении введите `QUIT`.

Другие общие средства для подключения к SQL Server включают:

- [Код Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-develop-use-ssms.md)

## <a name="next-steps"></a>Следующие шаги

Другие сценарии, например для запуска нескольких контейнеров, сохранение данных и troublehshooting, в статье [образов контейнеров Настройка 2017 г SQL Server на Docker](sql-server-linux-configure-docker.md).

Кроме того, ознакомьтесь [mssql docker репозитории GitHub](https://github.com/Microsoft/mssql-docker) ресурсы, отзывы и известные проблемы.

