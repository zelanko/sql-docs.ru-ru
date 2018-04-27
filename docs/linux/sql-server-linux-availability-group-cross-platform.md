---
title: Настройка SQL Server AlwaysOn группы доступности в Windows и Linux | Документы Microsoft
description: Настройка группы доступности SQL Server с репликами в Windows и Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/31/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: e2294549df8bca9fc21d7a72a26a59839fea9022
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Настройка SQL Server группы доступности AlwaysOn в Windows и Linux (кросс платформенных)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

В этой статье описывается порядок создания всегда в группе доступности (AG) с одной реплики на сервере Windows server и другой реплики на сервере Linux. Такая настройка является кросс платформенных, поскольку реплики находятся на разных операционных систем. Используйте эту конфигурацию для перехода с одной платформы на другую или аварийного восстановления (DR). Эта конфигурация не поддерживает высокого уровня доступности, поскольку решения нет кластера для управления конфигурацией между различными платформами. 

![Гибридные None](./media/sql-server-linux-availability-group-overview/image1.png)

Прежде чем продолжить, необходимо ознакомиться с установки и настройки для экземпляров SQL Server в Windows и Linux. 

## <a name="scenario"></a>Сценарий

В этом случае два сервера находятся в различных операционных системах. Windows Server 2016 с именем `WinSQLInstance` размещена первичная реплика. Сервер Linux с именем `LinuxSQLInstance` размещена вторичная реплика.

## <a name="configure-the-ag"></a>Настройка группы Доступности 

Инструкции по созданию группы Доступности одинаковы шаги по созданию группы Доступности для рабочих нагрузок чтения шкалы. Тип кластера группы Доступности нет, так как отсутствует диспетчер кластера. 

   >[!NOTE]
   >Для сценариев, в этой статье, угловые скобки `<` и `>` определить значения, которые необходимо заменить для вашей среды. Сами угловые скобки не требуются для скриптов. 

1. Установить 2017 г. SQL Server в Windows Server 2016, включите группы доступности AlwaysOn из диспетчера конфигурации SQL Server и задайте режим смешанной проверки подлинности. 

   >[!TIP]
   >При проверке этого решения в Azure, установите оба сервера в той же группе, чтобы убедиться, что они должны быть разделены в центре обработки данных доступности. 

   **Включение групп доступности**

   Инструкции см. в разделе [Включение и отключение всегда групп доступности (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

   ![Включение групп доступности](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   Диспетчер конфигурации SQL Server отметка о том, что компьютер не является узлом в отказоустойчивом кластере. 

   После включения групп доступности, перезапустите SQL Server.

   **Набор смешанного режима проверки подлинности**

   Инструкции см. в разделе [изменение режима проверки подлинности сервера](../database-engine/configure-windows/change-server-authentication-mode.md#SSMSProcedure).

1. Установка SQL Server 2017 г. в Linux. Инструкции см. в разделе [установить SQL Sever](sql-server-linux-setup.md). Включить `hadr` через mssql конфигурацией

   Чтобы включить `hadr` через mssql conf из командной строки, выполните следующую команду:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   После включения `hadr`, перезапустите экземпляр SQL Server.  

   На следующем рисунке показана этот шаг завершения.

   ![Включить Linux группы доступности](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. Настройка файла hosts на обоих серверах или зарегистрировать имена серверов DNS.

1. Откройте порты брандмауэра для TPC 1433 и 5022 на Windows и Linux.

1. В первичной реплике создайте имя входа базы данных и пароль.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. В первичной реплике создайте главный ключ и сертификат, а затем создайте резервную копию сертификата с закрытым ключом.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
   BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
       );
   GO
   ```

1. Скопируйте сертификат и закрытый ключ на сервер Linux (вторичной репликой) как `/var/opt/mssql/data`. Можно использовать `pscp` для копирования файлов на сервер Linux. 

1. Задайте группы и принадлежность закрытый ключ и сертификат для `mssql:mssql`.

   Следующий скрипт задает группы и владельца файлов. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   На следующей схеме, владельцем группы правильность установки и сертификата и ключа.

   ![Включить Linux группы доступности](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. На вторичной реплике создайте имя входа и пароль и создайте главный ключ.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. На вторичной реплике восстановить сертификат, который вы скопировали `/var/opt/mssql/data`. 

   ```sql
   CREATE CERTIFICATE dbm_certificate   
       AUTHORIZATION dbm_user
       FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
       WITH PRIVATE KEY (
       FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
       DECRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
   )
   GO
   ```

1. В первичной реплике создайте конечную точку.

   ```sql
   CREATE ENDPOINT [Hadr_endpoint]
       AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = 5022)
       FOR DATA_MIRRORING (
           ROLE = ALL,
           AUTHENTICATION = CERTIFICATE dbm_certificate,
           ENCRYPTION = REQUIRED ALGORITHM AES
           );
   ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
   GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login]
   GO
   ```

   >[!IMPORTANT]
   >Брандмауэр должен быть открыт для TCP-порт прослушивателя. В предыдущем сценарии порт — 5022. Используйте любой доступный порт TCP. 

1. На вторичной реплике создайте конечную точку. Повторите предыдущий сценарий во вторичной реплике, чтобы создать конечную точку. 

1. На первичной реплике создайте AG с `CLUSTER_TYPE = NONE`. В примере сценария использует `SEEDING_MODE = AUTOMATIC` для создания группы Доступности. 

   >[!NOTE]
   >Если Windows экземпляра SQL Server использует разные пути для файлов данных и журналов, автоматическое заполнение Linux экземпляра SQL Server не удается, так как эти пути не существуют во вторичной реплике. Чтобы использовать следующий скрипт для AG кросс платформенных, база данных требует тот же путь для файлов данных и журналов на сервере Windows. Также можно обновить сценарий для установки `SEEDING_MODE = MANUAL` и затем выполните резервное копирование и восстановление базы данных `NORECOVERY` для инициализации базы данных. 
   >
   >Это поведение применяется к образы Azure Marketplace. 
   >
   >Дополнительные сведения о автоматического заполнения см. в разделе [автоматического заполнения - структура диска](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout). 

   Прежде чем запустить скрипт, обновите значения для вашей и действий.

      * Замените `<WinSQLInstance>` на имя сервера экземпляра SQL Server первичной реплики.

      * Замените `<LinuxSQLInstance>` на имя сервера SQL Server экземпляра вторичной реплики. 

   Для создания группы Доступности, обновите значения и запустите сценарий на первичной реплике.  

   ```sql
   CREATE AVAILABILITY GROUP [ag1]
       WITH (CLUSTER_TYPE = NONE)
       FOR REPLICA ON
           N'<WinSQLInstance>' 
        WITH (
           ENDPOINT_URL = N'tcp://<WinSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            SEEDING_MODE = AUTOMATIC,
            FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
           N'<LinuxSQLInstance>' 
       WITH (
            ENDPOINT_URL = N'tcp://<LinuxSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
           SEEDING_MODE = AUTOMATIC,
           FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
           )
   GO
   ```
   
   Дополнительные сведения см. в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md).

1. На вторичную реплику присоедините группой Доступности.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. Создайте базу данных для группы Доступности. Примеры действий использовать базу данных с именем `<TestDB>`. При использовании автоматического заполнения, задайте один и тот же путь для данных и файлов журнала. 

   Прежде чем запустить скрипт, обновите значения для базы данных.

      * Замените `<TestDB>` с именем базы данных.

      * Замените `<F:\Path>` по пути для файлов базы данных и журнала. Используйте тот же путь для файлов базы данных и журнала. 

      Можно также использовать пути по умолчанию. 

    Создание базы данных, запустите скрипт. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. Создайте полную резервную копию базы данных. 

1. Если вы не используете автоматического заполнения, восстановите базу данных на сервере вторичной реплики (Linux). [Миграция базы данных SQL Server с Windows и Linux с помощью резервного копирования и восстановления](sql-server-linux-migrate-restore-database.md). Восстановите базу данных `WITH NORECOVERY` во вторичной реплике. 

1. Добавление базы данных в группе Доступности. Обновление в примере сценария. Замените `<TestDB>` с именем базы данных. В первичной реплике, выполнить SQL-запрос для добавления в группу Доступности базы данных.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. Проверьте, получение, базы данных заполняется во вторичной реплике. 

## <a name="fail-over-the-primary-replica"></a>При сбое основной реплики

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

В этой статье проверить действия по созданию кросс платформенных AG для поддержки рабочих нагрузок миграции или чтения шкалы. Он может использоваться для ручного аварийного восстановления. Он также описаны способы отработки отказа группой Доступности. Тип кластера использует AG кросс платформенных `NONE` и не поддерживает высокий уровень доступности, поскольку кластер средство через платформы не. 

## <a name="next-steps"></a>Следующие шаги

[Обзор групп доступности](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Основные сведения о доступности SQL Server для Linux развертываний](sql-server-linux-ha-basics.md)
