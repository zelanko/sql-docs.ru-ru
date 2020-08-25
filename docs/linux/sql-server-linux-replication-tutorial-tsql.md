---
title: Руководство по Настройка репликации (T-SQL)
description: Узнайте, как настроить репликацию моментального снимка SQL Server на Linux для двух экземпляров SQL Server с помощью Transact-SQL (T-SQL).
ms.custom: seo-dt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
titleSuffix: SQL Server on Linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: cc1a6ab577a471b69394cf35149f457972aece68
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088861"
---
# <a name="configure-replication-with-t-sql"></a>Настройка репликации с помощью T-SQL

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)] 

В этом руководстве вы настроите репликацию моментального снимка SQL Server на Linux для двух экземпляров SQL Server с помощью Transact-SQL. Издатель и распространитель будут одним экземпляром, а подписчик — отдельным экземпляром.

> [!div class="checklist"]
> * Включение агентов репликации SQL Server в Linux
> * Создание образца базы данных
> * Настройка папки моментальных снимков для доступа со стороны агентов SQL Server
> * Настройка распространителя
> * Настройка издателя
> * Настройка публикации и статей
> * Настройка подписчика 
> * Выполнение заданий репликации

Настройку репликации можно полностью произвести с помощью [хранимых процедур репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

## <a name="prerequisites"></a>Предварительные требования
Для выполнения этого руководства потребуется следующее:

- два экземпляра SQL Server с последней версией SQL Server на Linux;
- средство для отправки запросов T-SQL, предназначенных для настройки репликации, например SQLCMD или SSMS.

   См. статью [Управление SQL Server на Linux с помощью SSMS](./sql-server-linux-manage-ssms.md).

   >[!NOTE]
   >В версии [!INCLUDE[SQL Server 2017](../includes/sssqlv14-md.md)] ([накопительный пакет обновления 18](https://support.microsoft.com/help/4527377)) и более поздних реализована возможность репликации SQL Server для экземпляров SQL Server на Linux.

## <a name="detailed-steps"></a>Подробные инструкции

1. Включите агенты репликации SQL Server на Linux. На обоих хост-компьютерах выполните приведенные ниже команды в терминале. 

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   sudo systemctl restart mssql-server
   ```

1. Создайте образцы базы данных и таблицы. Создайте образцы базы данных и таблицы в издателе, которые будут служить статьями для публикации.

   ```sql
   CREATE DATABASE Sales
   GO
   USE [SALES]
   GO 
   CREATE TABLE CUSTOMER([CustomerID] [int] NOT NULL, [SalesAmount] [decimal] NOT NULL)
   GO 
   INSERT INTO CUSTOMER (CustomerID, SalesAmount) VALUES (1,100),(2,200),(3,300)
   ```

   В другом экземпляре SQL Server (подписчике) создайте базу данных для получения статей.

   ```sql
   CREATE DATABASE Sales
   GO
   ```

1. Создайте папку моментальных снимков, из которой будут производить чтение и в которую будут производить запись агенты SQL Server. В распространителе создайте папку моментальных снимков и предоставьте доступ к ней пользователю mssql. 

   ```bash
   sudo mkdir /var/opt/mssql/data/ReplData/
   sudo chown mssql /var/opt/mssql/data/ReplData/
   sudo chgrp mssql /var/opt/mssql/data/ReplData/
   ```

1. Настройте распространитель. В этом примере издатель также будет распространителем. Выполните приведенные ниже команды в издателе, чтобы также настроить экземпляр для распространения.

   ```sql
   DECLARE @distributor AS sysname
   DECLARE @distributorlogin AS sysname
   DECLARE @distributorpassword AS sysname
   -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
   SET @distributor = N'<distributor instance name>'--in this example, it will be the name of the publisher
   SET @distributorlogin = N'<distributor login>'
   SET @distributorpassword = N'<distributor password>'
   -- Specify the distribution database. 
   
   use master
   exec sp_adddistributor @distributor = @distributor -- this should be the hostname

   -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
   exec sp_adddistributiondb @database = N'distribution', @log_file_size = 2, @deletebatchsize_xact = 5000, @deletebatchsize_cmd = 2000, @security_mode = 0, @login = @distributorlogin, @password = @distributorpassword
   GO

   DECLARE @snapshotdirectory AS nvarchar(500)
   SET @snapshotdirectory = N'/var/opt/mssql/data/ReplData/'

   -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
   use [distribution] 
   if (not exists (select * from sysobjects where name = 'UIProperties' and type = 'U ')) 
          create table UIProperties(id int) 
   if (exists (select * from ::fn_listextendedproperty('SnapshotFolder', 'user', 'dbo', 'table', 'UIProperties', null, null))) 
          EXEC sp_updateextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties' 
   else 
         EXEC sp_addextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties'
   GO
   ```

1. Настройте издатель. Выполните приведенные ниже команды T-SQL в издателе.

   ```sql
   DECLARE @publisher AS sysname
   DECLARE @distributorlogin AS sysname
   DECLARE @distributorpassword AS sysname
   -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
   SET @publisher = N'<instance name>' 
   SET @distributorlogin = N'<distributor login>'
   SET @distributorpassword = N'<distributor password>'
   -- Specify the distribution database. 

   -- Adding the distribution publishers
   exec sp_adddistpublisher @publisher = @publisher, 
   @distribution_db = N'distribution', 
   @security_mode = 0, 
   @login = @distributorlogin, 
   @password = @distributorpassword, 
   @working_directory = N'/var/opt/mssql/data/ReplData', 
   @trusted = N'false', 
   @thirdparty_flag = 0, 
   @publisher_type = N'MSSQLSERVER'
   GO
   ```

1. Настройте задание публикации. Выполните приведенные ниже команды T-SQL в издателе.

   ```sql
   DECLARE @replicationdb AS sysname
   DECLARE @publisherlogin AS sysname
   DECLARE @publisherpassword AS sysname
   SET @replicationdb = N'Sales'
   SET @publisherlogin = N'<Publisher login>'
   SET @publisherpassword = N'<Publisher Password>'

   use [Sales]
   exec sp_replicationdboption @dbname = N'Sales', @optname = N'publish', @value = N'true'
   
   -- Add the snapshot publication
   exec sp_addpublication 
   @publication = N'SnapshotRepl', 
   @description = N'Snapshot publication of database ''Sales'' from Publisher ''<PUBLISHER HOSTNAME>''.',
   @retention = 0, 
   @allow_push = N'true', 
   @repl_freq = N'snapshot', 
   @status = N'active', 
   @independent_agent = N'true'

   exec sp_addpublication_snapshot @publication = N'SnapshotRepl', 
   @frequency_type = 1, 
   @frequency_interval = 1, 
   @frequency_relative_interval = 1, 
   @frequency_recurrence_factor = 0, 
   @frequency_subday = 8, 
   @frequency_subday_interval = 1, 
   @active_start_time_of_day = 0,
   @active_end_time_of_day = 235959, 
   @active_start_date = 0, 
   @active_end_date = 0, 
   @publisher_security_mode = 0, 
   @publisher_login = @publisherlogin, 
   @publisher_password = @publisherpassword
   ```

1. Настройте задание публикации. Выполните приведенные ниже команды T-SQL в издателе.

   ```sql
   use [Sales]
   exec sp_addarticle 
   @publication = N'SnapshotRepl', 
   @article = N'customer', 
   @source_owner = N'dbo', 
   @source_object = N'customer', 
   @type = N'logbased', 
   @description = null, 
   @creation_script = null, 
   @pre_creation_cmd = N'drop', 
   @schema_option = 0x000000000803509D,
   @identityrangemanagementoption = N'manual', 
   @destination_table = N'customer', 
   @destination_owner = N'dbo', 
   @vertical_partition = N'false'
   ```

1. Настройте подписку. Выполните приведенные ниже команды T-SQL в издателе.

   ```sql
   DECLARE @subscriber AS sysname
   DECLARE @subscriber_db AS sysname
   DECLARE @subscriberLogin AS sysname
   DECLARE @subscriberPassword AS sysname
   SET @subscriber = N'<Instance Name>' -- for example, MSSQLSERVER
   SET @subscriber_db = N'Sales'
   SET @subscriberLogin = N'<Subscriber Login>'
   SET @subscriberPassword = N'<Subscriber Password>'

   use [Sales]
   exec sp_addsubscription 
   @publication = N'SnapshotRepl', 
   @subscriber = @subscriber,
   @destination_db = @subscriber_db, 
   @subscription_type = N'Push', 
   @sync_type = N'automatic', 
   @article = N'all', 
   @update_mode = N'read only', 
   @subscriber_type = 0

   exec sp_addpushsubscription_agent 
   @publication = N'SnapshotRepl', 
   @subscriber = @subscriber,
   @subscriber_db = @subscriber_db, 
   @subscriber_security_mode = 0, 
   @subscriber_login = @subscriberLogin,
   @subscriber_password = @subscriberPassword,
   @frequency_type = 1,
   @frequency_interval = 0, 
   @frequency_relative_interval = 0, 
   @frequency_recurrence_factor = 0, 
   @frequency_subday = 0, 
   @frequency_subday_interval = 0, 
   @active_start_time_of_day = 0, 
   @active_end_time_of_day = 0, 
   @active_start_date = 0, 
   @active_end_date = 19950101
   GO
   ```

1. Выполните задания агента репликации. Выполните следующий запрос, чтобы получить список заданий:

   ```sql
   SELECT name, date_modified FROM msdb.dbo.sysjobs order by date_modified desc
   ```

   Выполните задание репликации моментального снимка, чтобы создать моментальный снимок:

   ```sql
   USE msdb;   
   --generate snapshot of publications, for example
   EXEC dbo.sp_start_job N'PUBLISHER-PUBLICATION-SnapshotRepl-1'
   GO
   ```

   Выполните задание репликации моментального снимка, чтобы создать моментальный снимок:

   ```sql
   USE msdb;
   --distribute the publication to subscriber, for example
   EXEC dbo.sp_start_job N'DISTRIBUTOR-PUBLICATION-SnapshotRepl-SUBSCRIBER'
   GO
   ```

1. Подключите подписчик и запросите реплицированные данные.    

   В подписчике проверьте, работает ли репликация, выполнив следующий запрос:

   ```sql
   SELECT * from [Sales].[dbo].[CUSTOMER]
   ```

В этом руководстве вы настроили репликацию моментального снимка SQL Server в Linux для двух экземпляров SQL Server с помощью Transact-SQL.

> [!div class="checklist"]
> * Включение агентов репликации SQL Server в Linux
> * Создание образца базы данных
> * Настройка папки моментальных снимков для доступа со стороны агентов SQL Server
> * Настройка распространителя
> * Настройка издателя
> * Настройка публикации и статей
> * Настройка подписчика 
> * Выполнение заданий репликации

## <a name="see-also"></a>См. также раздел

Дополнительные сведения о репликации см. в разделе [Документация по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="next-steps"></a>Дальнейшие действия

[Основные понятия. Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
