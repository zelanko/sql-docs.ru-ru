---
title: Настройка репликации SQL Server в Linux | Документация Майкрософт
description: Этом руководстве показано, как настроить репликацию моментальных снимков SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 88fa1c1be8e6506f947fc300b2f26bd865d77622
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715414"
---
# <a name="configure-replication-with-t-sql"></a>Настройка репликации с помощью T-SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)] 

В этом руководстве вы настроите репликации моментальных снимков SQL Server в Linux с использованием 2 экземпляра SQL Server с помощью Transact-SQL. Издатель и распространитель будет являться одним экземпляром, и подписчик будет находиться на отдельном экземпляре.

> [!div class="checklist"]
> * Включение агентов репликации SQL Server в Linux
> * Создание образца базы данных
> * Настройка папки моментальных снимков для доступа к SQL Server агенты
> * Настройка распространителя
> * Настройка издателя
> * Настройка публикации и статьи
> * Настройка подписчика 
> * Выполнение заданий репликации

Все конфигурации репликации можно настроить с помощью [хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

## <a name="prerequisites"></a>предварительные требования  
Для работы с этим руководством вам потребуется:

- два экземпляра SQL Server с помощью последней версии SQL Server в Linux
- Это средство, чтобы отправлять T-SQL-запросы для настройки репликации, например SQLCMD или SSMS

  См. в разделе [управления SQL Server в Linux с помощью среды SSMS](./sql-server-linux-manage-ssms.md).

## <a name="detailed-steps"></a>Подробные инструкции

1. Включение агентов репликации SQL Server на Linux включить агент SQL Server для использования агентов репликации. На обоих компьютерах узла выполните следующие команды в окне терминала. 

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  sudo systemctl restart mssql-server
  ```

1. Настройка экземпляра SQL Server для репликации выполните следующую хранимую процедуру в базе данных msdb для каждого экземпляра CTP1.5, участвующих в репликации SQL Server.

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. Создание образца базы данных и таблицы на издатель Создание образца базы данных и таблицу, которая будет выступать в качестве статьи для публикации.

  ```sql
  CREATE DATABASE Sales
  GO
  USE [SALES]
  GO 
  CREATE TABLE CUSTOMER([CustomerID] [int] NOT NULL, [SalesAmount] [decimal] NOT NULL)
  GO 
  INSERT INTO CUSTOMER (CustomerID, SalesAmount) VALUES (1,100),(2,200),(3,300)
  ```

  На другой экземпляр SQL Server, подписчик, создайте базу данных, для получения статей.

  ```sql
  CREATE DATABASE Sales
  GO
  ```

1. Создать папку моментальных снимков для агентов SQL Server на чтение и запись на распространителе, создать папку моментальных снимков и предоставлять доступ для пользователя «mssql» 

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

1. Настройка распространителя в этом примере, также будет распространителем издателя. Выполните следующие команды на издателе для настройки экземпляра для распространения также.

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

1. Настройка издателя, выполните следующие команды TSQL на издателе.

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

1. Настройте приведенные ниже команды TSQL публикации, задание выполняется на издателе.

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

1. Создание статьи из таблицы продаж выполнения команды TSQL на издателе.

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

1. Настройка подписки выполните следующие команды TSQL на издателе.

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
  @subscriber_login =  @subscriberLogin,
  @subscriber_password =  @subscriberPassword,
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

1. Выполнение заданий агента репликации

  Выполните следующий запрос для получения списка заданий:

  ```sql
  SELECT name, date_modified FROM msdb.dbo.sysjobs order by date_modified desc
  ```

  Запустите задание репликации моментальных снимков для создания моментального снимка:

  ```sql
  USE msdb;  
  --generate snapshot of publications, for example
  EXEC dbo.sp_start_job N'PUBLISHER-PUBLICATION-SnapshotRepl-1'
  GO
  ```

  Запустите задание репликации моментальных снимков для создания моментального снимка:

  ```sql
  USE msdb;  
  --distribute the publication to subscriber, for example
  EXEC dbo.sp_start_job N'DISTRIBUTOR-PUBLICATION-SnapshotRepl-SUBSCRIBER'
  GO
  ```

1. Подключение подписчика и запрос реплицированных данных 

  На подписчике проверьте работоспособность репликации, выполнив следующий запрос:

  ```sql
  SELECT * from [Sales].[dbo].[CUSTOMER]
  ```

В этом руководстве вы настроили репликации моментальных снимков SQL Server в Linux с использованием 2 экземпляра SQL Server с помощью Transact-SQL.

> [!div class="checklist"]
> * Включение агентов репликации SQL Server в Linux
> * Создание образца базы данных
> * Настройка папки моментальных снимков для доступа к SQL Server агенты
> * Настройка распространителя
> * Настройка издателя
> * Настройка публикации и статьи
> * Настройка подписчика 
> * Выполнение заданий репликации

## <a name="see-also"></a>См. также

Подробные сведения о репликации см. в разделе [руководство по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="next-steps"></a>Следующие шаги

[Основные понятия: Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).