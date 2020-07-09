---
title: Восстановление базы данных SQL Server в Docker
description: В этом руководстве описано, как восстановить резервную копию базы данных SQL Server в новом контейнере Docker на базе Linux.
author: VanMSFT
ms.author: vanto
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 5d5fd2e96e9d0695f098eab02fb3d4ab86e5d256
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85902332"
---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Восстановление базы данных SQL Server в контейнере Docker на базе Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом руководстве показано, как переместить файл резервной копии SQL Server в образ контейнера Linux SQL Server 2017, запущенный в Docker, и восстановить его.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом руководстве показано, как переместить файл резервной копии SQL Server в образ контейнера Linux SQL Server 2019, запущенный в Docker, и восстановить его.

::: moniker-end

> [!div class="checklist"]
> * Извлеките и запустите образ контейнера Linux SQL Server.
> * Скопируйте файл базы данных Wide World Importers в контейнер.
> * Восстановите базу данных в контейнере.
> * Запустите инструкции Transact-SQL для просмотра и изменения базы данных.
> * Создайте резервную копию измененной базы данных.

## <a name="prerequisites"></a>предварительные требования

* Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
* Не менее 2 ГБ места на диске
* Не менее 2 ГБ ОЗУ
* [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Откройте терминал bash в Linux или Mac либо сеанс PowerShell с повышенными привилегиями в Windows.

1. Извлеките образ контейнера Linux с SQL Server 2017 из центра Docker.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!TIP]
   > В рамках этого руководства примеры команд Docker приводятся как для оболочки bash (Linux/Mac), так и для PowerShell (Windows).

1. Чтобы запустить образ контейнера с помощью Docker, выполните следующую команду:

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql1' -p 1401:1433 \
      -v sql1data:/var/opt/mssql \
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql1" -p 1401:1433 `
      -v sql1data:/var/opt/mssql `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   Эта команда создает контейнер SQL Server 2017 с выпуском Developer (по умолчанию). Порт SQL Server **1433** доступен на узле как порт **1401**. Необязательный параметр `-v sql1data:/var/opt/mssql` создает контейнер томов данных с именем **sql1ddata**. Он используется для сохранения данных, созданных SQL Server.

   > [!IMPORTANT]
   > В этом примере используется контейнер томов данных в DOCKER. Если вместо этого вы решили сопоставлять каталог узлов, обратите внимание на то, что в Docker для Mac и Windows существуют ограничения для этого подхода. Дополнительные сведения см. в статье [Настройка образов контейнеров SQL Server в Docker](sql-server-linux-configure-docker.md#persist).

1. Для просмотра ваших контейнеров Docker используйте команду `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

1. Если в столбце **STATUS** (состояние) отображается состояние **Up** (запущен), то SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

  ```bash
  $ sudo docker ps -a

  CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
  941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
  ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Откройте терминал bash в Linux или Mac либо сеанс PowerShell с повышенными привилегиями в Windows.

1. Извлеките образ контейнера Linux с SQL Server 2019 из центра Docker.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04
   ```

   > [!TIP]
   > В рамках этого руководства примеры команд Docker приводятся как для оболочки bash (Linux/Mac), так и для PowerShell (Windows).

1. Чтобы запустить образ контейнера с помощью Docker, выполните следующую команду:

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql1' -p 1401:1433 \
      -v sql1data:/var/opt/mssql \
      -d mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql1" -p 1401:1433 `
      -v sql1data:/var/opt/mssql `
      -d mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04
   ```

   Эта команда создает контейнер SQL Server 2019 с выпуском Developer (по умолчанию). Порт SQL Server **1433** доступен на узле как порт **1401**. Необязательный параметр `-v sql1data:/var/opt/mssql` создает контейнер томов данных с именем **sql1ddata**. Он используется для сохранения данных, созданных SQL Server.

1. Для просмотра ваших контейнеров Docker используйте команду `docker ps`.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

1. Если в столбце **STATUS** (состояние) отображается состояние **Up** (запущен), то SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a

   CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
   941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
   ```

::: moniker-end

## <a name="change-the-sa-password"></a>Смена пароля администратора

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="copy-a-backup-file-into-the-container"></a>Копирование файла резервной копии в контейнер

В этом руководстве используется [образец базы данных Wide World Importers](../sample/world-wide-importers/wide-world-importers-documentation.md). Выполните следующие действия, чтобы скачать файл резервной копии базы данных Wide World Importers и скопировать его в контейнер SQL Server.

1. Сначала используйте команду **docker exec** для создания папки резервного копирования. Следующая команда создает каталог **/var/opt/mssql/backup** внутри контейнера SQL Server.

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. Затем скачайте файл [WideWorldImporters-Full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0) на хост-компьютер. Приведенные ниже команды переходят в каталог home/user и скачивают файл резервной копии в виде **wwi.bak**.

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. Используйте **docker cp**, чтобы скопировать файл резервной копии в контейнер в каталог **/var/opt/mssql/backup**.

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>Восстановление базы данных

Теперь файл резервной копии находится в контейнере. Перед восстановлением резервной копии важно узнать логические имена и типы файлов в резервной копии. Следующие команды Transact-SQL проверяют резервную копию и выполняют восстановление с помощью **sqlcmd** в контейнере.

> [!TIP]
> В этом руководстве средство **sqlcmd** используется в контейнере, так как оно предустановлено в этом контейнере. Однако вы также можете запустить инструкции Transact-SQL с помощью других клиентских сред извне контейнера, таких как [Visual Studio Code](sql-server-linux-develop-use-vscode.md) или [SQL Server Management Studio](sql-server-linux-manage-ssms.md). Для подключения используйте порт узла, сопоставленный с портом 1433 в контейнере. В нашем примере это **localhost,1401** на хост-компьютере и удаленный **Host_IP_Address,1401**.

1. Запустите **sqlcmd** внутри контейнера, чтобы вывести список логических имен файлов и путей внутри резервной копии. Для этого используется инструкция **RESTORE FILELISTONLY** Transact-SQL.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost \
      -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/wwi.bak"' \
      | tr -s ' ' | cut -d ' ' -f 1-2
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost `
      -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/wwi.bak'"
   ```

   Выходные данные должны иметь следующий вид.

   ```
   LogicalName   PhysicalName
   ------------------------------------------
   WWI_Primary   D:\Data\WideWorldImporters.mdf
   WWI_UserData   D:\Data\WideWorldImporters_UserData.ndf
   WWI_Log   E:\Log\WideWorldImporters.ldf
   WWI_InMemory_Data_1   D:\Data\WideWorldImporters_InMemory_Data_1
   ```

1. Вызовите команду **RESTORE DATABASE**, чтобы восстановить базу данных внутри контейнера. Укажите новые пути для каждого из файлов в предыдущем шаге.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE DATABASE WideWorldImporters FROM DISK = "/var/opt/mssql/backup/wwi.bak" WITH MOVE "WWI_Primary" TO "/var/opt/mssql/data/WideWorldImporters.mdf", MOVE "WWI_UserData" TO "/var/opt/mssql/data/WideWorldImporters_userdata.ndf", MOVE "WWI_Log" TO "/var/opt/mssql/data/WideWorldImporters.ldf", MOVE "WWI_InMemory_Data_1" TO "/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE DATABASE WideWorldImporters FROM DISK = '/var/opt/mssql/backup/wwi.bak' WITH MOVE 'WWI_Primary' TO '/var/opt/mssql/data/WideWorldImporters.mdf', MOVE 'WWI_UserData' TO '/var/opt/mssql/data/WideWorldImporters_userdata.ndf', MOVE 'WWI_Log' TO '/var/opt/mssql/data/WideWorldImporters.ldf', MOVE 'WWI_InMemory_Data_1' TO '/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1'"
   ```

   Выходные данные должны иметь следующий вид.

   ```
   Processed 1464 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   Processed 33 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   Processed 3862 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Converting database 'WideWorldImporters' from version 852 to the current version 869.
   Database 'WideWorldImporters' running the upgrade step from version 852 to version 853.
   Database 'WideWorldImporters' running the upgrade step from version 853 to version 854.
   Database 'WideWorldImporters' running the upgrade step from version 854 to version 855.
   Database 'WideWorldImporters' running the upgrade step from version 855 to version 856.
   Database 'WideWorldImporters' running the upgrade step from version 856 to version 857.
   Database 'WideWorldImporters' running the upgrade step from version 857 to version 858.
   Database 'WideWorldImporters' running the upgrade step from version 858 to version 859.
   Database 'WideWorldImporters' running the upgrade step from version 859 to version 860.
   Database 'WideWorldImporters' running the upgrade step from version 860 to version 861.
   Database 'WideWorldImporters' running the upgrade step from version 861 to version 862.
   Database 'WideWorldImporters' running the upgrade step from version 862 to version 863.
   Database 'WideWorldImporters' running the upgrade step from version 863 to version 864.
   Database 'WideWorldImporters' running the upgrade step from version 864 to version 865.
   Database 'WideWorldImporters' running the upgrade step from version 865 to version 866.
   Database 'WideWorldImporters' running the upgrade step from version 866 to version 867.
   Database 'WideWorldImporters' running the upgrade step from version 867 to version 868.
   Database 'WideWorldImporters' running the upgrade step from version 868 to version 869.
   RESTORE DATABASE successfully processed 58455 pages in 18.069 seconds (25.273 MB/sec).
   ```

## <a name="verify-the-restored-database"></a>Проверка восстановленной базы данных

Выполните следующий запрос, чтобы отобразить список имен баз данных в контейнере:

```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'SELECT Name FROM sys.Databases'
```

```PowerShell
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "SELECT Name FROM sys.Databases"
```

Вы должны увидеть **WideWorldImporters** в списке баз данных.

## <a name="make-a-change"></a>Внесение изменения

Следующие шаги вносят изменение в базу данных.

1. Выполните запрос, чтобы просмотреть 10 первых элементов в таблице **Warehouse.StockItems**.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID"
   ```

   Вы увидите список идентификаторов и имен элементов:

   ```
   StockItemID StockItemName
   ----------- -----------------
             1 USB missile launcher (Green)
             2 USB rocket launcher (Gray)
             3 Office cube periscope (Black)
             4 USB food flash drive - sushi roll
             5 USB food flash drive - hamburger
             6 USB food flash drive - hot dog
             7 USB food flash drive - pizza slice
             8 USB food flash drive - dim sum 10 drive variety pack
             9 USB food flash drive - banana
            10 USB food flash drive - chocolate bar
   ```

1. Обновите описание первого элемента с помощью следующей инструкции **UPDATE**:

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName="USB missile launcher (Dark Green)" WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName='USB missile launcher (Dark Green)' WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   Выходные данные должны иметь следующий вид:

   ```
   (1 rows affected)
   StockItemID StockItemName
   ----------- ------------------------------------
             1 USB missile launcher (Dark Green)
   ```

## <a name="create-a-new-backup"></a>Создание резервной копии

После восстановления базы данных в контейнере вам может потребоваться регулярно создавать резервные копии базы данных в работающем контейнере. Соответствующие действия выполняются по той же схеме, что и в предыдущих шагах, только в обратном порядке.

1. Используйте команду **BACKUP DATABASE** Transact-SQL, чтобы создать резервную копию базы данных в контейнере. В этом руководстве создается файл резервной копии **wwi_2.bak** в ранее созданном каталоге **/var/opt/mssql/backup**.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   Выходные данные должны иметь следующий вид.

   ```
   10 percent processed.
   20 percent processed.
   30 percent processed.
   40 percent processed.
   50 percent processed.
   60 percent processed.
   70 percent processed.
   Processed 1200 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   80 percent processed.
   Processed 3865 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Processed 938 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   100 percent processed.
   BACKUP DATABASE successfully processed 59099 pages in 25.056 seconds (18.427 MB/sec).
   ```

1. Затем скопируйте файл резервной копии из контейнера на хост-компьютер.

   ```bash
   cd ~
   sudo docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

   ```PowerShell
   cd ~
   docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls wwi*
   ```

## <a name="use-the-persisted-data"></a>Использование хранимых данных

Кроме создания резервных копий базы данных для защиты данных, можно также использовать контейнеры томов данных. В начале этого учебника был создан контейнер **sql1** с параметром `-v sql1data:/var/opt/mssql`. Контейнер томов данных **sql1data** хранит данные **/var/opt/mssql** даже после удаления контейнера. Следующие шаги полностью удаляют контейнер **sql1**, а затем создают новый контейнер — **sql2** — с хранимыми данными.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Остановите контейнер **sql1**.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Удалите контейнер. Это не приводит к удалению ранее созданного контейнера томов данных **sql1data** и хранимых в нем данных.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Создайте новый контейнер **sql2** и повторно используйте контейнера томов данных **sql1data**.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
      -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
      -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

1. Теперь база данных Wide World Importers находится в новом контейнере. Выполните запрос, чтобы проверить внесенное ранее изменение.

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > Пароль системного администратора не является паролем `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`, указанным для контейнера **sql2**. Все данные SQL Server были восстановлены из **sql1**, включая измененный пароль, описанный ранее в этом руководстве. По сути, некоторые параметры, подобные этому, игнорируются из-за восстановления данных в /var/opt/mssql. По этой причине пароль имеет значение `<YourNewStrong!Passw0rd>`, как показано здесь.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Остановите контейнер **sql1**.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Удалите контейнер. Это не приводит к удалению ранее созданного контейнера томов данных **sql1data** и хранимых в нем данных.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Создайте новый контейнер **sql2** и повторно используйте контейнера томов данных **sql1data**.

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04
    ```

1. Теперь база данных Wide World Importers находится в новом контейнере. Выполните запрос, чтобы проверить внесенное ранее изменение.

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > Пароль системного администратора не является паролем `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`, указанным для контейнера **sql2**. Все данные SQL Server были восстановлены из **sql1**, включая измененный пароль, описанный ранее в этом руководстве. По сути, некоторые параметры, подобные этому, игнорируются из-за восстановления данных в /var/opt/mssql. По этой причине пароль имеет значение `<YourNewStrong!Passw0rd>`, как показано здесь.

::: moniker-end

## <a name="next-steps"></a>Дальнейшие действия

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом руководстве вы узнали, как создать резервную копию базы данных в Windows и переместить ее на сервер Linux под управлением SQL Server 2017. Вы ознакомились с выполнением следующих задач:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом руководстве вы узнали, как создать резервную копию базы данных в Windows и переместить ее на сервер Linux под управлением SQL Server 2019. Вы ознакомились с выполнением следующих задач:

::: moniker-end

> [!div class="checklist"]
> * Создание образов контейнеров Linux SQL Server.
> * Копирование резервных копий базы данных SQL Server в контейнер.
> * Выполнение инструкций Transact-SQL в контейнере с помощью **sqlcmd**.
> * Создание файлов резервных копий и извлечение их из контейнера.
> * Использование контейнеров томов данных в Docker для сохранения данных SQL Server.

Затем ознакомьтесь с другими сценариями настройки и устранения неполадок Docker:

> [!div class="nextstepaction"]
>[Настройка SQL Server 2017 в Docker](sql-server-linux-configure-docker.md)
