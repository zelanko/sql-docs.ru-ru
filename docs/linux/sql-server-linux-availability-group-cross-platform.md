---
title: Настройка группы доступности Always On SQL Server в Windows и Linux
description: Настройка группы доступности SQL Server с использованием реплик в Windows и Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 651467463e0563c9da00e23115ffb7bc4f151d23
ms.sourcegitcommit: cebf41506a28abfa159a5dd871b220630c4c4504
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77479682"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Настройка группы доступности Always On SQL Server в Windows и Linux (кроссплатформенная конфигурация)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

В этой статье описаны действия по созданию группы доступности Always On с одной репликой на сервере Windows Server и другой репликой на сервере Linux. Такая конфигурация является кроссплатформенной, так как реплики находятся в разных операционных системах. Используйте эту конфигурацию для миграции с одной платформы на другую или аварийного восстановления. Такая конфигурация не поддерживает высокую доступность, так как отсутствуют решения кластера для управления кроссплатформенной конфигурацией. 

![Гибридный режим None](./media/sql-server-linux-availability-group-overview/image1.png)

Прежде чем продолжить, нужно ознакомиться с установкой и настройкой экземпляров SQL Server в Windows и Linux. 

## <a name="scenario"></a>Сценарий

В этом сценарии два сервера находятся в разных операционных системах. На сервере Windows Server 2016 с именем `WinSQLInstance` размещается первичная реплика. На сервере Linux с именем `LinuxSQLInstance` размещается вторичная реплика.

## <a name="configure-the-ag"></a>Настройка группы доступности 

Действия по созданию группы доступности аналогичны действиям по созданию группы доступности для рабочих нагрузок с масштабированием для чтения. Тип кластера группы доступности — NONE, так как отсутствует диспетчер кластеров. 

   >[!NOTE]
   >Для скриптов в этой статье угловые скобки `<` и `>` обозначают значения, которые нужно заменить для вашей среды. Сами угловые скобки в скриптах не требуются. 

1. Установите SQL Server 2017 в Windows Server 2016, включите группы доступности Always On из диспетчера конфигурации SQL Server и установите смешанный режим проверки подлинности. 

   >[!TIP]
   >Если вы проверяете это решение в Azure, разместите оба сервера в одной группе доступности, чтобы обеспечить их разделение в центре обработки данных. 

   **Включение групп доступности**

   Инструкции см. в статье [Включение и отключение групп доступности Always On (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

   ![Включение групп доступности](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   Диспетчер конфигурации SQL Server отмечает, что компьютер не является узлом отказоустойчивого кластера. 

   После включения групп доступности перезапустите SQL Server.

   **Настройка смешанного режима проверки подлинности**

   Инструкции см. в статье [Изменение режима проверки подлинности сервера](../database-engine/configure-windows/change-server-authentication-mode.md#change-authentication-mode-with-ssms).

1. Установите SQL Server 2017 в Linux. Инструкции см. в статье [Установка SQL Server](sql-server-linux-setup.md). Включите `hadr` через mssql-conf.

   Чтобы включить `hadr` с помощью mssql-conf из командной строки оболочки, выполните следующую команду.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   После включения `hadr` перезапустите экземпляр SQL Server.  

   На следующем рисунке показан этот шаг целиком.

   ![Включение групп доступности в Linux](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. Настройте файл hosts на обоих серверах или зарегистрируйте имена серверов в DNS.

1. Откройте порты брандмауэра для TPC 1433 и 5022 в Windows и Linux.

1. На первичной реплике создайте имя для входа и пароль базы данных.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. На первичной реплике создайте главный ключ и сертификат, а затем создайте резервную копию сертификата с закрытым ключом.

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

1. Скопируйте сертификат и закрытый ключ на сервер Linux (вторичная реплика) по адресу `/var/opt/mssql/data`. Можно использовать `pscp` для копирования файлов на сервер Linux. 

1. Задайте для группы и владельца закрытого ключа и сертификата значение `mssql:mssql`.

   Следующий скрипт задает группу и владение для файлов. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   На следующей схеме владение и группа заданы правильно для сертификата и ключа.

   ![Включение групп доступности в Linux](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. На вторичной реплике создайте имя для входа и пароль базы данных, а также главный ключ.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. На вторичной реплике восстановите сертификат, скопированный в `/var/opt/mssql/data`. 

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

1. Создайте конечную точку на первичной реплике.

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
   >TCP-порт прослушивателя в брандмауэре должен быть открыт. В приведенном выше сценарии это порт 5022. Используйте любой доступный TCP-порт. 

1. На вторичной реплике создайте конечную точку. Повторите предыдущий скрипт на вторичной реплике, чтобы создать конечную точку. 

1. На первичной реплике создайте группу доступности с помощью `CLUSTER_TYPE = NONE`. Этот пример скрипта использует `SEEDING_MODE = AUTOMATIC` для создания группы доступности. 

   >[!NOTE]
   >Если в экземпляре SQL Server на базе Windows используются разные пути для файлов данных и журналов, автоматическое заполнение с ошибкой переходит на экземпляр SQL Server на базе Linux, так как эти пути не существуют во вторичной реплике. Чтобы использовать следующий скрипт для кроссплатформенной группы доступности, базе данных требуется одинаковый путь для файлов данных и журналов на сервере Windows Server. Кроме того, можно обновить скрипт, чтобы задать `SEEDING_MODE = MANUAL`, а затем выполнить резервное копирование и восстановление базы данных с помощью `NORECOVERY`, чтобы заполнить ее. 
   >
   >Это поведение применяется к образам Azure Marketplace. 
   >
   >Дополнительные сведения об автоматическом заполнении см. в разделе [Автоматическое заполнение — разметка диска](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout). 

   Перед выполнением скрипта обновите значения для своих групп доступности.

      * Замените `<WinSQLInstance>` на имя сервера для экземпляра SQL Server первичной реплики.

      * Замените `<LinuxSQLInstance>` на имя сервера для экземпляра SQL Server вторичной реплики. 

   Чтобы создать группу доступности, обновите значения и выполните скрипт на первичной реплике.  

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

1. На вторичной реплике присоедините группу доступности.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. Создайте базу данных для группы доступности. В примерах шагов используется база данных `<TestDB>`. Если вы используете автоматическое заполнение, задайте один путь для файлов данных и журналов. 

   Перед выполнением скрипта обновите значения для своей базы данных.

      * Замените `<TestDB>` на имя вашей базы данных.

      * Замените `<F:\Path>` на путь к вашей базе данных и файлам журнала. Используйте одинаковый путь для файлов журнала и базы данных. 

      Можно также использовать пути по умолчанию. 

    Чтобы создать базу данных, запустите скрипт. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. Создайте полную резервную копию базы данных. 

1. Если автоматическое заполнение не используется, восстановите базу данных на сервере вторичной реплики (Linux). [Перенесите базу данных SQL Server из Windows в Linux с помощью резервного копирования и восстановления](sql-server-linux-migrate-restore-database.md). Восстановите базу данных `WITH NORECOVERY` на вторичной реплике. 

1. Добавьте базу данных в группу доступности. Измените пример скрипта. Замените `<TestDB>` на имя вашей базы данных. На первичной реплике выполните SQL-запрос, чтобы добавить базу данных в группу доступности.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. Убедитесь, что заполняется база данных на вторичной реплике. 

## <a name="fail-over-the-primary-replica"></a>Отработка отказа первичной реплики

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

В этой статье рассмотрены действия по созданию кроссплатформенной группы доступности для поддержки миграции или рабочих нагрузок с масштабированием для чтения. Ее можно использовать для ручного аварийного восстановления. Также объяснено, как выполнить отработку отказа группы доступности. Кроссплатформенная группа доступности использует тип кластера `NONE` и не поддерживает высокую доступность из-за отсутствия кроссплатформенного средства управления кластерами. 

## <a name="next-steps"></a>Дальнейшие действия

[Обзор групп доступности Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Основные сведения о доступности SQL Server для развертываний Linux](sql-server-linux-ha-basics.md)
