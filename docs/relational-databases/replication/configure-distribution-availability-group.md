---
title: Настройка базы данных распространителя SQL Server в группе доступности | Документы Майкрософт
ms.custom: ''
ms.date: 04/19/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- remote Distributors [SQL Server replication]
- transactional replication, configuring distribution
- distribution databases [SQL Server replication], sizing
- Distributors [SQL Server replication], configuring
- distribution databases [SQL Server replication], about distribution databases
- distribution databases [SQL Server replication]
- merge replication [SQL Server replication], configuring distribution
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
caps.latest.revision: 44
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 762ccf4bbae20c465db8515336dc2995be17bc12
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-replication-distribution-database-in-always-on-availability-group"></a>Настройка базы данных распространителя репликации в группе доступности AlwaysOn

В этой статье описывается настройка баз данных распространителя репликации SQL Server в группе доступности AlwaysOn.

В SQL Server 2017 с накопительным обновлением 6 реализована поддержка базы данных распространителя репликации в группе доступности с применением следующих механизмов:

- Группа доступности для базы данных распространителя должна иметь прослушиватель. При добавлении распространителя издатель использует в качестве имени распространителя имя прослушивателя.
- При создании заданий репликации имя прослушивателя также используется в качестве имени распространителя.
- Новое задание отслеживает состояние (первичное или вторичное в группе доступности) баз данных распространителя и в зависимости от этого состояния отключает или включает задания репликации.

После настройки базы данных распространителя в группе доступности с применением описываемых ниже действий задания настройки репликации и реального времени могут корректно выполняться до и после отработки отказа в группе доступности базы данных распространителя.

## <a name="supported-scenarios"></a>Поддерживаемые сценарии

- Настройка базы данных распространителя, которая будет включена в группу доступности.
- Настройка репликации, в том числе публикаций и подписок до и после отработки отказа в группе доступности.
- Задания репликации, выполняемые до и после отработки отказа.
- Удаление репликации на стороне распространителя и издателя, когда база данных распространителя находится в группе доступности.
- Добавление или удаление узлов для существующей группы доступности базы данных распространителя.
- Распространитель может иметь несколько баз данных распространителя. Каждая база данных распространителя может входить в собственную группу доступности или не принадлежать ни одной такой группе. Несколько баз данных распространителя могут использовать одну группу доступности.
- Издатель и распространитель должны размещаться на отдельных экземплярах SQL Server.

## <a name="limitations-or-exclusions"></a>Ограничения или исключения

- Не поддерживаются локальные распространители. Например, в качестве издателя и распространителя должны выступать разные экземпляры SQL Server. Издатель, который сам выступает в качестве распространителя (т. е. локальный распространитель) не поддерживает базы данных распространителя в группе доступности.
- Не поддерживаются издатели Oracle.
- Репликация слиянием не поддерживается.
- Не поддерживается репликация транзакций с обновлением подписчика напрямую или посредством очереди.
- Не поддерживается одноранговая репликация.
- Все экземпляры SQL Server, на которых размещаются реплики баз данных распространителя, должны использовать версию SQL Server 2017 с накопительным обновлением 6 или более позднюю. 
- Все экземпляры SQL Server, на которых размещаются реплики баз данных распространителя, должны иметь одну и ту же версию, за исключением коротких промежутков времени, связанных с обновлением.
- База данных распространителя должна находиться в режиме полного восстановления.
- Чтобы обеспечить восстановление и усечение журнала транзакций, следует настроить резервное копирование полного журнала и журнала транзакций.
- Для группы доступности базы данных распространителя должен быть настроен прослушиватель.
- Вторичные реплики в группе доступности базы данных распространителя могут быть как синхронными, так и асинхронными. Рекомендуемым и предпочтительным является синхронный режим.
- Двунаправленная репликация транзакций не поддерживается.


   >[!NOTE]
   >Прежде чем выполнять какие-либо хранимые процедуры репликации (например, `sp_dropdistpublisher`, `sp_dropdistributiondb`, `sp_dropdistributor`, `sp_adddistributiondb` или `sp_adddistpublisher`) для вторичной реплики, убедитесь, что эта реплика полностью синхронизирована.

- Все вторичные реплики в группе доступности базы данных распространителя должны быть доступны для чтения.
- Все узлы в группе доступности базы данных распространителя должны использовать одну и ту же учетную запись домена для выполнения агента SQL Server. Этой учетной записи домена должны быть назначены одинаковые разрешения на каждом узле.
- Если какой-либо из агентов репликации выполняется с использованием учетной записи-посредника, такая учетная запись-посредник должна существовать на каждом узле в группе доступности базы данных распространителя и иметь одинаковые разрешения на каждом узле.
- Вносить изменения в свойства распространителя или базы данных распространителя необходимо для всех реплик, участвующих в группе доступности базы данных распространителя.
- Вносить изменения в задания репликации с использованием хранимых процедур msdb или SQL Server Management Studio необходимо для всех реплик, участвующих в группе доступности базы данных распространителя.
- Настройка распространителя на издателе должна осуществляться с помощью скриптов. Использование мастера репликации не поддерживается. При этом можно использовать мастеры репликации и страницы свойств репликации для других целей.
- Начиная с версии SQL Server 2017 с накопительным обновлением 6 не поддерживаются монитор репликации, а также другие компоненты пользовательского интерфейса репликации, которые осуществляют подключение с использованием имени прослушивателя группы доступности. Для администрирования агентов репликации, связанных с базой данных распространителя в группе доступности, следует использовать свойство и журнал задания.
- Настройка группы доступности для баз данных распространителя может осуществляться только с помощью скриптов.
- Настройка баз данных распространителя в группе доступности должна осуществляться только в рамках новой конфигурации репликации. Переключение существующей базы данных распространителя в группу доступности не поддерживается. Кроме того, после исключения базы данных распространителя из группы доступности она больше не может использоваться в качестве действительной базы данных распространителя и должна быть удалена.

## <a name="configuration-architecture"></a>Архитектура конфигурации

В приведенных в этой статье примерах используются следующие имена серверов и параметры.

- DIST1, DIST2, DIST3 — это серверы распространителя;
- PUB — это сервер издателя;
- после формирования группы доступности для базы данных распространителя прослушиватель получает имя DISTLISTENER;
- DIST1 выступает в качестве первичной реплики группы доступности для базы данных распространителя.

## <a name="configure-distributor-distribution-database-and-publisher"></a>Настройка распространителя, базы данных распространителя и издателя

В этом примере выполняется настройка нового распространителя и издателя, а также добавление базы данных распространителя в группу доступности.

### <a name="distributors-workflow"></a>Рабочий процесс распространителя

1. Настройте DIST1, DIST2 и DIST3 в качестве распространителя с использованием `sp_adddistributor @@servername`. Укажите пароль для `distributor_admin` с помощью `@password`. Значения `@password` должны быть одинаковыми для DIST1, DIST2 и DIST3.
2. Создайте базу данных распространителя на сервере DIST1 с использованием `sp_adddistributiondb`. База данных распространителя имеет имя `distribution`. Измените режим восстановления базы данных `distribution` с простого на полный.
3. Создайте группу доступности для базы данных `distribution` с репликами на серверах DIST1, DIST2 и DIST3. Рекомендуется сделать все реплики синхронными. Настройте вторичные реплики как доступные для чтения. На этот момент для группы доступности базы данных распространителя DIST1 является первичной репликой, а DIST2 и DIST3 — вторичными репликами.
4. Настройте прослушиватель с именем `DISTLISTENER` для группы доступности.
5. Чтобы обеспечить восстановление и усечение журнала транзакций, следует настроить резервное копирование полного журнала и журнала транзакций.
6. На серверах DIST2 и DIST3 выполните команду:

   ```sql
   sp_adddistributiondb 'distribution'
   ```

1. Чтобы добавить `PUB` в качестве издателя на сервер DIST1, выполните команду:
   
   ```sql
   sp_adddistpublisher @publisher= 'PUB', @distribution_db= 'distribution', @working_directory= '<network path>'
   ```

   Значение `@working_directory` не должно зависеть от сетевого пути к серверам DIST1, DIST2 и DIST3.

1. На серверах DIST2 и DIST3 выполните команду:  

   ```sql
   sp_adddistpublisher @publisher= 'PUB', @distribution_db= 'distribution', @working_directory= '<network path>'
   ```

   Значение `@working_directory` должно быть таким же, как и на предыдущем шаге.

### <a name="publisher-workflow"></a>Рабочий процесс издателя

Чтобы добавить прослушиватель группы доступности для базы данных `distribution` в качестве распространителя, на сервере PUB выполните команду: 

   ```sql
   sp_adddistributor @distributor = 'DISTLISTENER', @password = <distributor_admin password> 
   ```

   Значение @password должно быть таким же, как указанное при настройке распространителей в рамках рабочего процесса распространителя.

## <a name="remove-distributor-and-publisher"></a>Удаление издателя и распространителя

В этом примере из находящейся в группе доступности базы данных распространителя удаляются издатель и распространитель.

### <a name="publisher-workflow"></a>Рабочий процесс издателя

На сервере PUB удалите все подписки и публикации для этого издателя, после чего вызовите `sp_dropdistributor`.

### <a name="distributors-workflow"></a>Рабочий процесс распространителя

В этом примере сервер DIST1 является текущей первичной репликой для группы доступности базы данных `distribution`. Серверы DIST2 и DIST3 являются вторичными репликами.

1. На серверах DIST2 и DIST3 выполните команду:

   ```sql
   sp_dropdistpublisher 'PUB',  @no_checks = 1
   ```

1. На DIST1 выполните следующую команду:

   ```sql
   sp_dropdistpublisher 'PUB'
   ```

1. Удалите группу доступности.
2. На серверах DIST2 и DIST3 переведите базу данных `distribution` в режим read_write, выполнив ее восстановление.
   
   ```sql
   RESTORE DATABASE distribution WITH RECOVERY, KEEP_REPLICATION
   ```

1. Чтобы удалить базу данных `distribution` и сохранить каталог моментальных снимков, выполните команду: 

   ```sql
   sp_dropdistributiondb 'distribution' , @former_ag_secondary=1
   ```

  Эта процедура удаляет все несвязанные задания в этой реплике.

1. Чтобы удалить базу данных `distribution` на сервере DIST1, выполните команду:

   ```sql
   sp_dropdistributiondb 'distribution'
   ``` 

1. Если в группе доступности нет других баз данных распространителя, выполните `sp_dropdistributor` на серверах DIST1, DIST2 и DIST3.

## <a name="add-a-replica-to-distribution-database-ag"></a>Добавление реплики в группу доступности базы данных распространителя

В этом примере добавляется новый распространитель в существующую конфигурацию репликации с базой данных распространителя в группе доступности. В этом примере существующая база данных распространителя находится в группе доступности. Серверы DIST1 и DIST2 являются распространителями, `distribution` — это база данных распространителя в группе доступности, а PUB — это издатель. Добавьте сервер DIST3 в качестве реплики в группу доступности.

### <a name="distributors-workflow"></a>Рабочий процесс распространителя

1. Сервер DIST3 должен быть настроен в качестве распространителя с использованием `sp_adddistributor @@servername`. Пароль `distributor_admin` необходимо задавать с использованием параметра @password. Пароль должен совпадать с указанным для серверов DIST1 и DIST2.
2. Добавьте сервер DIST3 в группу доступности для текущей базы данных распространителя.
3. На сервере DIST3 выполните команду:

   ```sql
   sp_adddistributiondb 'distribution'
   ```

1. На сервере DIST3 выполните команду: 

   ```sql
   sp_adddistpublisher @publisher= 'PUB', @distribution_db= 'distribution', @working_directory= '<network path>'
   ```

   Значение `@working_directory` должно совпадать с указанным для серверов DIST1 и DIST2.

## <a name="remove-a-replica-from-distribution-database-ag"></a>Удаление реплики из группы доступности базы данных распространителя

В этом примере распространитель удаляется из текущей группы доступности базы данных распространителя и при этом не затрагиваются другие реплики в этой группе. В этом примере база данных распространителя находится в группе доступности. Серверы DIST1, DIST2 и DIST3 являются распространителями, `distribution` — это база данных распространителя в группе доступности, а PUB — это издатель. Удалите сервер DIST3 из группы доступности.

### <a name="distributors-workflow"></a>Рабочий процесс распространителя

1. Убедитесь, что в группе доступности базы данных `distribution` сервер DIST3 является вторичным.
2. Удалите сервер DIST3 из группы доступности базы данных `distribution`.
3. На сервере DIST3 переведите базу данных `distribution` в режим read_write, выполнив ее восстановление. Например, выполните следующую команду:  
   
   ```sql
   RESTORE DATABASE distribution WITH RECOVERY, KEEP_REPLICATION.
   ```
   
1. Чтобы удалить все несвязанные задания на сервере DIST3, выполните команду: 

   ```sql
   sp_dropdistpublisher 'PUB', @no_checks = 1
   ```

1. На сервере DIST3 выполните команду:

   ```sql
   sp_dropdistributiondb 'distribution', @former_ag_secondary=1
   ```

1. На сервере DIST3 выполните команду: 

   ```sql
   sp_dropdistributor
   ```

## <a name="remove-a-publisher-from-distribution-database-ag"></a>Удаление издателя из группы доступности базы данных распространителя

В этом примере издатель удаляется из текущей группы доступности базы данных распространителя для распространителя, и при этом не затрагиваются другие издатели, обслуживаемые этой группой. В этом примере в существующей конфигурации база данных распространителя находится в группе доступности. Серверы DIST1, DIST2 и DIST3 являются распространителями, `distribution` — это база данных распространителя в группе доступности, а PUB1 и PUB2 — это издатели, обслуживаемые базой данных `distribution`. В этом примере удаляется издатель PUB1.

### <a name="publisher-workflow"></a>Рабочий процесс издателя

На сервере PUB1 удалите все подписки и публикации для этого издателя, после чего вызовите `sp_dropdistributor`.

### <a name="distributor-workflow"></a>Рабочий процесс распространителя

Сервер DIST1 является текущей первичной репликой для группы доступности базы данных `distribution`.

1. На серверах DIST2 и DIST3 выполните команду:

   ```sql
   sp_dropdistpublisher 'PUB1',  @no_checks = 1
   ```

1. На DIST1 выполните следующую команду:

   ```sql
   sp_dropdistpublisher 'PUB1'
   ```

1. На этом этапе могут возникать несвязанные задания, относящиеся к издателю PUB1 на серверах DIST2 или DIST3. При выполнении отработки отказа на серверы DIST2 и DIST3 такие несвязанные задания, относящиеся ко всем публикациям сервера PUB1, будут удалены заданием `Monitor and sync replication agent jobs`.

## <a name="add-subscription"></a>Добавление подписки

В этом примере описывается настройка сведения о подписчике на распространителях. В этом примере добавляется подписчик. DIST1 является первичной репликой базы данных распространителя в группе доступности, а DIST2 и DIST3 — ее вторичные реплики. SUB — это имя подписчика.

### <a name="publisher-workflow"></a>Рабочий процесс издателя

На сервере PUB добавьте подписку для подписчика `SUB` обычным образом.

### <a name="distributor-workflow"></a>Рабочий процесс распространителя

На серверах DIST2 и DIST3 добавьте связанный сервер для SUB, если он еще не был зарегистрирован для DIST2 или DIST3. Ниже приводится пример кода TSQL для создания связанного сервера:

   ```sql 
   EXEC master.dbo.sp_addlinkedserver@server =N'SUB', @srvproduct=N'SQL Server'
   /* For security reasons the linked server remote logins password is changed with ######## */
   EXEC master.dbo.sp_addlinkedsrvlogin@rmtsrvname=N'SUB', @useself=N'True',@locallogin=NULL,@rmtuser=NULL,@rmtpassword=NULL
   ```

## <a name="add-a-pull-subscription"></a>Добавление подписки по запросу

### <a name="subscriber-workflow"></a>Рабочий процесс подписчика

Чтобы добавить подписку по запросу для публикации в базе данных распространителя в группе доступности, используйте имя прослушивателя группы доступности в параметре `@distributor` хранимой процедуры `sp_addpullsubscription_agent`.

## <a name="sample-t-sql-create-distribution-db-in-ag"></a>Пример кода T-SQL для создания базы данных распространителя в группе доступности

Следующий скрипт включает базу данных распространителя в группе доступности. 

```sql
--- WorkFlow to Enable Distribution Database In AG.

-- SECTION 1 ---- CONFIGURE THE DISTRIBUTOR SERVERS

-- Step1 - Configure the Distribution DB nodes (AG Replicas) to act as a distributor
:Connect SQLNode1
sp_adddistributor @distributor = @@ServerName, @password = 'Pass@word1'
Go 
:Connect SQLNode2
sp_adddistributor @distributor = @@ServerName, @password = 'Pass@word1'
Go

-- Step2 - Configure the Distribution Database
:Connect SQLNode1
USE master
EXEC sp_adddistributiondb @database = 'DistributionDB', @security_mode = 1;
GO
Alter Database [DistributionDB] Set Recovery Full
Go
Backup Database [DistributionDB] to Disk = 'Nul'
Go
-- Step 3 - Create AG for the Distribution DB.
:Connect SQLNode1
USE [master]
GO
CREATE ENDPOINT [Hadr_endpoint] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)   
    FOR DATA_MIRRORING (ROLE = ALL, AUTHENTICATION = WINDOWS NEGOTIATE
, ENCRYPTION = REQUIRED ALGORITHM AES)
GO

:Connect SQLNode2
USE [master]
GO
CREATE ENDPOINT [Hadr_endpoint] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)   
    FOR DATA_MIRRORING (ROLE = ALL, AUTHENTICATION = WINDOWS NEGOTIATE
, ENCRYPTION = REQUIRED ALGORITHM AES)
GO

:Connect SQLNode1
-- Create the Availability Group
CREATE AVAILABILITY GROUP [DistributionDB_AG]
FOR DATABASE [DistributionDB]
REPLICA ON 'SQLNode1'
WITH (ENDPOINT_URL = N'TCP://SQLNode1.contoso.com:5022', 
         FAILOVER_MODE = AUTOMATIC, 
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
         BACKUP_PRIORITY = 50, 
         SECONDARY_ROLE(ALLOW_CONNECTIONS = ALL), 
         SEEDING_MODE = AUTOMATIC),
N'SQLNode2' WITH (ENDPOINT_URL = N'TCP://SQLNode2.contoso.com:5022', 
     FAILOVER_MODE = AUTOMATIC, 
     AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
     BACKUP_PRIORITY = 50, 
     SECONDARY_ROLE(ALLOW_CONNECTIONS = ALL), 
     SEEDING_MODE = AUTOMATIC);
 GO


:Connect SQLNode2
ALTER AVAILABILITY GROUP [DistributionDB_AG] JOIN
GO  
ALTER AVAILABILITY GROUP [DistributionDB_AG] GRANT CREATE ANY DATABASE
Go

--STEP4 - Create the Listener for the Availability Group. This is very important.
:Connect SQLNode1

USE [master]
GO
ALTER AVAILABILITY GROUP [DistributionDB_AG]
ADD LISTENER N'DistributionDBList' (
WITH IP
((N'10.0.0.8', N'255.255.255.0')) , PORT=1500);
GO

-- STEP 5 - Enable SQLNode1 also as a Distributor
:CONNECT SQLNODE2
EXEC sp_adddistributiondb @database = 'DistributionDB', @security_mode = 1;
GO

--STEP 6 - On all Distributor Nodes Configure the Publisher Details 
:CONNECT SQLNODE1
EXEC sp_addDistPublisher @publisher = 'SQLNode4', @distribution_db = 'DistributionDB', 
    @working_directory = '\\sqlfileshare\Dist_Work_Directory\'
GO
:CONNECT SQLNODE2
EXEC sp_addDistPublisher @publisher = 'SQLNode4', @distribution_db = 'DistributionDB', 
    @working_directory = '\\sqlfileshare\Dist_Work_Directory\'
GO

-- SECTION 2 ---- CONFIGURE THE PUBLISHER SERVER
:CONNECT SQLNODE4
EXEC sp_addDistributor @distributor = 'DistributionDBList', -- Listener for the Distribution DB.    
    @password = 'Pass@word1'
Go

-- SECTION 3 ---- CONFIGURE THE SUBSCRIBERS 
-- On Publisher, create the publication as one would normally do.
-- On the Secondary replicas of the Distribution DB, add the Subscriber as a linked server.
:CONNECT SQLNODE2
EXEC master.dbo.sp_addlinkedserver @server = N'SQLNODE5', @srvproduct=N'SQL Server'
 /* For security reasons the linked server remote logins password is changed with ######## */
EXEC master.dbo.sp_addlinkedsrvlogin @rmtsrvname=N'SQLNODE5',@useself=N'True',@locallogin=NULL,@rmtuser=NULL,@rmtpassword=NULL 
```

## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Защита распространителя](../../relational-databases/replication/security/secure-the-distributor.md)  
  
## <a name="next-steps"></a>Следующие шаги
 [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md)  
 [Отключение публикации и распространения](disable-publishing-and-distribution.md)  
 [Разрешение применения репликации для базы данных (среда SQL Server Management Studio)](enable-a-database-for-replication-sql-server-management-studio.md) 
