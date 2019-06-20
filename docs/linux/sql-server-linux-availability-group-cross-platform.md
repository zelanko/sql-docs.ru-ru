---
title: Настройка SQL Server AlwaysOn группы доступности в Windows и Linux | Документация Майкрософт
description: Настройка группы доступности SQL Server с репликами в Windows и Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 520866e80cd3526d7c039cd98e08f5cc8fc52798
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713383"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Настройка SQL Server группы доступности AlwaysOn в Windows и Linux (для нескольких платформ)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

В этой статье описывается создание всегда в группе доступности (AG) с одной реплики на сервере Windows и другой реплики на сервере Linux. Эта конфигурация является кроссплатформенной, так как реплики находятся в разных операционных системах. Используйте эту конфигурацию для миграции с одной платформы на другую или аварийное восстановление (DR). Эта конфигурация не поддерживает высокого уровня доступности, поскольку нет доступных решений для управления конфигурацией кросс платформенных кластера. 

![Гибридные None](./media/sql-server-linux-availability-group-overview/image1.png)

Прежде чем продолжить, необходимо ознакомиться с установки и настройки для экземпляров SQL Server в Windows и Linux. 

## <a name="scenario"></a>Сценарий

В этом сценарии два сервера находятся в разных операционных системах. Windows Server 2016 с именем `WinSQLInstance` размещена основная реплика. Сервер Linux с именем `LinuxSQLInstance` размещаться вторичная реплика.

## <a name="configure-the-ag"></a>Настройка группы Доступности 

Шаги по созданию группы Доступности будут так же, как действия, чтобы создать группу Доступности для рабочих нагрузок чтения и масштабирования. Тип кластера группы Доступности нет, так как отсутствует диспетчер кластера. 

   >[!NOTE]
   >Для сценариев, в этой статье, в угловые скобки `<` и `>` определить значения, необходимые для замены для вашей среды. Угловые скобки, сами не являются обязательными для сценариев. 

1. Установка SQL Server 2017 на Windows Server 2016, включите группы доступности AlwaysOn из диспетчера конфигурации SQL Server и задайте режим смешанной проверки подлинности. 

   >[!TIP]
   >При проверке этого решения в Azure, поместите оба сервера в одной группе доступности, чтобы убедиться, что они размещены в центре обработки данных. 

   **Включите группы доступности**

   Инструкции см. в разделе [Включение и отключение всегда групп доступности (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

   ![Включите группы доступности](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   Диспетчер конфигурации SQL Server отмечает, что компьютер не является узлом в отказоустойчивом кластере. 

   После включения групп доступности, перезапустите SQL Server.

   **Набор смешанного режима проверки подлинности**

   Инструкции см. в разделе [изменение режима проверки подлинности сервера](../database-engine/configure-windows/change-server-authentication-mode.md#SSMSProcedure).

1. Установка SQL Server 2017 в Linux. Инструкции см. в разделе [Установка SQL Server](sql-server-linux-setup.md). Включить `hadr` через mssql-conf.

   Чтобы включить `hadr` через mssql-conf из командной строки, выполните следующую команду:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   После включения `hadr`, перезапустите экземпляр SQL Server.  

   На следующем рисунке показана этот шаг завершения.

   ![Включить Linux группы доступности](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. Настройка файла hosts на обоих серверах или регистрация имена серверов DNS.

1. Откройте порты брандмауэра для TPC 1433 и 5022 на Windows и Linux.

1. На первичной реплике создайте имя входа базы данных и пароль.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. В первичной реплике создать главный ключ и сертификат, а затем резервную копию сертификата с закрытым ключом.

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

1. Скопируйте сертификат и закрытый ключ на сервер Linux (вторичной реплики) в `/var/opt/mssql/data`. Можно использовать `pscp` для копирования файлов на сервер Linux. 

1. Группе и владение закрытый ключ и сертификат, `mssql:mssql`.

   Следующий скрипт задает группы и владельца файлов. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   На следующей схеме владельца и группу устанавливаются корректно сертификат и ключ.

   ![Включить Linux группы доступности](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. На вторичной реплике создайте имя входа базы данных и пароль и создайте главный ключ.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. На вторичной реплике восстановите сертификат, скопированный `/var/opt/mssql/data`. 

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
   >Брандмауэр должен быть открыт для TCP-порт прослушивателя. В предыдущем скрипте номер порта — 5022. Используйте любой доступный порт TCP. 

1. На вторичной реплике создайте конечную точку. Повторите приведенный выше сценарий на вторичной реплике для создания конечной точки. 

1. В первичной реплике, создание группы Доступности с `CLUSTER_TYPE = NONE`. В примере сценария использует `SEEDING_MODE = AUTOMATIC` для создания группы Доступности. 

   >[!NOTE]
   >Если Windows экземпляра SQL Server использует разные пути для файлов данных и журналов, автоматическое заполнение завершается сбоем для экземпляра SQL Server, Linux, так как эти пути не существуют во вторичной реплике. Чтобы использовать следующий сценарий для группы Доступности кросс платформенных, база данных требует тот же путь для файлов данных и журналов на сервере Windows. Кроме того, вы можете обновить сценарий для установки `SEEDING_MODE = MANUAL` и затем резервное копирование и восстановление базы данных `NORECOVERY` заполнить базу данных. 
   >
   >Это поведение применяется к образам Azure Marketplace. 
   >
   >Дополнительные сведения о автоматического заполнения, см. в разделе [автоматического заполнения - разметка диска](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout). 

   Прежде чем выполнять скрипт, обновите значения для групп доступности.

      * Замените `<WinSQLInstance>` на имя экземпляра SQL Server первичной реплики.

      * Замените `<LinuxSQLInstance>` на имя экземпляра SQL Server вторичной реплики. 

   Чтобы создать группу Доступности, обновите значения и запустите сценарий на первичной реплике.  

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

1. На вторичной реплике присоединиться к группе Доступности.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. Создание базы данных для группы Доступности. Примеры действий использовать базу данных с именем `<TestDB>`. При использовании автоматического заполнения, задайте один и тот же путь для данных и файлы журнала. 

   Прежде чем выполнять скрипт, обновите значения для своей базы данных.

      * Замените `<TestDB>` с именем базы данных.

      * Замените `<F:\Path>` путь для файлов базы данных и журнала. Используйте тот же путь для файлов базы данных и журнала. 

      Можно также использовать пути по умолчанию. 

    Чтобы создать базу данных, запустите скрипт. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. Создание полной резервной копии базы данных. 

1. Если вы не используете автоматического заполнения, восстановите базу данных на сервере вторичной реплики (Linux). [Перенос базы данных SQL Server из Windows для Linux с помощью резервного копирования и восстановления](sql-server-linux-migrate-restore-database.md). Восстановите базу данных `WITH NORECOVERY` на вторичной реплике. 

1. Добавьте базу данных к группе Доступности. Обновите в примере сценария. Замените `<TestDB>` с именем базы данных. В первичной реплике, выполните запрос SQL, чтобы добавить базу данных к группе Доступности.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. Убедитесь, что базы данных является заполняются во вторичной реплике. 

## <a name="fail-over-the-primary-replica"></a>Отработка отказа первичной реплики

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

В этой статье просмотреть действия по созданию кроссплатформенных AG для поддержки миграции или чтения и масштабирования рабочих нагрузок. Его можно использовать для ручного аварийного восстановления. Он также объяснил, как выполнять отработку отказа группы Доступности. AG кросс платформенных использует тип кластера `NONE` и не поддерживает высокий уровень доступности, так как нет кластера средство на платформах. 

## <a name="next-steps"></a>Следующие шаги

[Обзор групп доступности AlwaysOn](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Основные сведения о доступности SQL Server для Linux развертываний](sql-server-linux-ha-basics.md)
