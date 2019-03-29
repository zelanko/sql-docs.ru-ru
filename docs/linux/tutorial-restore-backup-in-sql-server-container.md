---
title: Восстановление базы данных SQL Server в Docker | Документация Майкрософт
description: В этом учебнике показано, как восстановить резервную копию базы данных SQL Server в новом контейнере Docker в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 31cf9104ea47bdf8086e8676312d9ac8d8085184
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2019
ms.locfileid: "58566553"
---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Восстановление базы данных SQL Server в контейнере Docker в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Этом руководстве показано, как переместить и восстановите файл резервной копии SQL Server в образ контейнера Linux с SQL Server 2017, запуск в Docker.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Этот учебник посвящен перемещения и восстановления файла резервной копии SQL Server в образ контейнера SQL Server 2019 Предварительная версия Linux под управлением Docker.

::: moniker-end

> [!div class="checklist"]
> * Извлечение и запуск последней версии образа контейнера SQL Server Linux.
> * Скопируйте файл базы данных Wide World Importers в контейнер.
> * Восстановите базу данных в контейнере.
> * Выполнение инструкций Transact-SQL для просмотра и изменения базы данных.
> * Резервное копирование с измененной базой данных.

## <a name="prerequisites"></a>предварительные требования

* Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
* Не менее 2 ГБ места на диске
* Не менее 2 ГБ ОЗУ
* [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Откройте окно терминала bash в Linux или Mac или сеанс PowerShell с повышенными правами в Windows.

1. Извлеките образ контейнера Linux с SQL Server 2017 из центра Docker.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!TIP]
   > В этом руководстве примерах команд docker предоставляется для оболочки bash (Linux или Mac) и PowerShell (Windows).

1. Чтобы запустить образ контейнера с помощью Docker, можно использовать следующую команду:

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

   Эта команда создает контейнер SQL Server 2017 с Developer edition (по умолчанию). Порт SQL Server **1433** предоставляется на узле, что порт **1401**. Необязательный `-v sql1data:/var/opt/mssql` параметр создает контейнер томов данных с именем **sql1ddata**. Это позволяет сохранить данные, созданные SQL Server.

   > [!NOTE]
   > Процесс запуска производственными выпусками SQL Server в контейнерах, немного отличается. Дополнительные сведения см. в разделе [Запуск образов контейнеров с производственными выпусками](sql-server-linux-configure-docker.md#production). Если вы используете те же имена контейнеров и порты, остальной части этого пошагового руководства по-прежнему работает с контейнерами в рабочей среде.

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

1. Откройте окно терминала bash в Linux или Mac или сеанс PowerShell с повышенными правами в Windows.

1. Извлечь предварительной версии SQL Server 2019 образа контейнера Linux из Docker Hub.

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   > [!TIP]
   > В этом руководстве примерах команд docker предоставляется для оболочки bash (Linux или Mac) и PowerShell (Windows).

1. Чтобы запустить образ контейнера с помощью Docker, можно использовать следующую команду:

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql1' -p 1401:1433 \
      -v sql1data:/var/opt/mssql \
      -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql1" -p 1401:1433 `
      -v sql1data:/var/opt/mssql `
      -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   Эта команда создает контейнер предварительной версии SQL Server 2019 с Developer edition (по умолчанию). Порт SQL Server **1433** предоставляется на узле, что порт **1401**. Необязательный `-v sql1data:/var/opt/mssql` параметр создает контейнер томов данных с именем **sql1ddata**. Это позволяет сохранить данные, созданные SQL Server.

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

## <a name="copy-a-backup-file-into-the-container"></a>Скопируйте файл резервной копии в контейнер

В этом руководстве используется [образца базы данных Wide World Importers](../sample/world-wide-importers/wide-world-importers-documentation.md). Следуйте инструкциям ниже, чтобы загрузить и скопировать файл резервной копии базы данных Wide World Importers в контейнер SQL Server.

1. Во-первых, используйте **docker exec** для создания папки резервного копирования. Следующая команда создает **/var/opt/mssql/backup** каталог внутри контейнера SQL Server.

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. Теперь скачайте [WideWorldImporters Full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0) файл хост-компьютер. Следующие команды, перейдите в каталог home/user и загружает файл резервной копии как **wwi.bak**.

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. Используйте **docker cp** для копирования файла резервной копии в контейнер в **/var/opt/mssql/backup** каталога.

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>Восстановление базы данных

Файл резервной копии теперь находится внутри контейнера. Перед восстановлением резервной копии, важно знать логических имен файлов и типов файлов в резервной копии. Следующие команды Transact-SQL, проверять резервную копию и выполнять восстановление, используя **sqlcmd** в контейнере.

> [!TIP]
> В этом руководстве используется **sqlcmd** внутри контейнера, так как контейнер поставляется с предварительно установлено это средство. Тем не менее, также средства можно запустить инструкции Transact-SQL совместно с другими клиентами вне контейнера, такие как [Visual Studio Code](sql-server-linux-develop-use-vscode.md) или [SQL Server Management Studio](sql-server-linux-manage-ssms.md). Чтобы подключиться, используйте порт узла, который был сопоставлен с портом 1433 в контейнере. В этом примере это **localhost, 1401** на хост-компьютере и **Host_IP_Address 1401** удаленно.

1. Запустите **sqlcmd** внутри контейнера, чтобы вывести список логических имен файлов и путей внутри резервной копии. Это делается с помощью **RESTORE FILELISTONLY** инструкции Transact-SQL.

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

   Вы должны увидеть результат, аналогичный приведенному ниже:

   ```
   LogicalName   PhysicalName
   ------------------------------------------
   WWI_Primary   D:\Data\WideWorldImporters.mdf
   WWI_UserData   D:\Data\WideWorldImporters_UserData.ndf
   WWI_Log   E:\Log\WideWorldImporters.ldf
   WWI_InMemory_Data_1   D:\Data\WideWorldImporters_InMemory_Data_1
   ```

1. Вызовите **RESTORE DATABASE** команду, чтобы восстановить базу данных внутри контейнера. Укажите новые пути для каждого из файлов на предыдущем шаге.

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

   Вы должны увидеть результат, аналогичный приведенному ниже:

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

Вы должны увидеть **WideWorldImporters** в список баз данных.

## <a name="make-a-change"></a>Изменения

Следующие шаги внести изменения в базе данных.

1. Выполните запрос, чтобы просмотреть 10 верхних элементов в **Warehouse.StockItems** таблицы.

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

   Вы должны увидеть список имена и идентификаторы элементов:

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

1. Обновите Описание первого элемента со следующими **обновления** инструкции:

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

   Вы должны увидеть результат, аналогичный приведенному ниже:

   ```
   (1 rows affected)
   StockItemID StockItemName
   ----------- ------------------------------------
             1 USB missile launcher (Dark Green)
   ```

## <a name="create-a-new-backup"></a>Создание резервной копии

После восстановления базы данных в контейнер может также потребоваться регулярно создавать резервные копии базы данных внутри запущенного контейнера. Действия имеют схожий шаблон к предыдущим шагам, но в обратном порядке.

1. Используйте **резервное копирование базы данных** команды Transact-SQL для создания резервной копии базы данных в контейнере. Это руководство позволяет создать новый файл резервной копии, **wwi_2.bak**, в ранее созданный **/var/opt/mssql/backup** каталога.

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

   Вы должны увидеть результат, аналогичный приведенному ниже:

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

1. Затем скопируйте файл резервной копии за пределы контейнера, а также на хост-компьютере.

   ```bash
   cd ~
   sudo docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

   ```PowerShell
   cd ~
   docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

## <a name="use-the-persisted-data"></a>Использовать сохраненные данные

В дополнение к создание резервных копий базы данных для защиты данных, можно также использовать контейнеры томов данных. Начало работы с этим руководством создан **sql1** контейнер с `-v sql1data:/var/opt/mssql` параметра. **Sql1data** контейнер томов данных сохранится **/var/opt/mssql** данные даже после удаления контейнера. Следующие шаги полностью удалить **sql1** контейнера, а затем создать новый контейнер, **sql2**, с помощью материализованных данных.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Остановить **sql1** контейнера.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Удалите контейнер. При этом не удаляются ранее созданный **sql1data** контейнер томов данных и сохраненные данные в нем.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Создать контейнер, **sql2**и повторно использовать **sql1data** контейнер томов данных.

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

1. Базы данных Wide World Importers теперь находится в новый контейнер. Выполните запрос для проверки предыдущих внесенные изменения.

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
   > Пароль системного Администратора не пароль, указанный для **sql2** контейнера, `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`. Все данные SQL Server была восстановлена из **sql1**, включая измененные пароли из ранее в этом руководстве. По сути из-за восстановления данных в /var/opt/mssql пропускаются некоторые параметры следующим образом. По этой причине пароль — `<YourNewStrong!Passw0rd>` следующим образом.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Остановить **sql1** контейнера.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Удалите контейнер. При этом не удаляются ранее созданный **sql1data** контейнер томов данных и сохраненные данные в нем.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Создать контейнер, **sql2**и повторно использовать **sql1data** контейнер томов данных.

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
    ```

1. Базы данных Wide World Importers теперь находится в новый контейнер. Выполните запрос для проверки предыдущих внесенные изменения.

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
   > Пароль системного Администратора не пароль, указанный для **sql2** контейнера, `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`. Все данные SQL Server была восстановлена из **sql1**, включая измененные пароли из ранее в этом руководстве. По сути из-за восстановления данных в /var/opt/mssql пропускаются некоторые параметры следующим образом. По этой причине пароль — `<YourNewStrong!Passw0rd>` следующим образом.

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В этом руководстве вы узнали, как резервное копирование базы данных на Windows и переместите его на сервер Linux, под управлением SQL Server 2017. Вы узнали, как для:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В этом руководстве вы узнали, как резервное копирование базы данных на Windows и переместите его на сервер Linux, под управлением предварительной версии SQL Server 2019. Вы узнали, как для:

::: moniker-end

> [!div class="checklist"]
> * Создание образов контейнеров SQL Server Linux.
> * Скопируйте резервные копии базы данных SQL Server в контейнере.
> * Выполните инструкции Transact-SQL внутри контейнера с **sqlcmd**.
> * Создание и извлечение файлов резервных копий из контейнера.
> * Используйте контейнеры томов данных в Docker для сохранения данных SQL Server.

Затем просмотрите другие конфигурации Docker и устранение неполадок в сценариях:

> [!div class="nextstepaction"]
>[Руководство по настройке для SQL Server 2017 в Docker](sql-server-linux-configure-docker.md)
