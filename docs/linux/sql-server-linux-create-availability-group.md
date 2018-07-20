---
title: Создание и настройка группы доступности для SQL Server в Linux | Документация Майкрософт
description: Этом руководстве показано, как создать и настроить группы доступности для SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/28/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 21ca1eea093121107b2e04cff40b6f749a6c6bda
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083496"
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>Создание и настройка группы доступности для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это руководство содержит сведения о создания и настройки группы доступности (AG) для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux. В отличие от [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] и ранее на Windows, вы можете включить группы доступности с или без сначала создать базовый кластер Pacemaker. Интеграция с кластером, если требуется, не выполняется до более поздней версии.

Учебник включает следующие задачи:
 
> [!div class="checklist"]
> * Включите группы доступности.
> * Создайте конечные точки группы доступности и сертификаты.
> * Используйте [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) или Transact-SQL для создания группы доступности.
> * Создание [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] имя входа и разрешения для Pacemaker.
> * Создание ресурсов группы доступности в кластере Pacemaker (только для внешнего типа).

## <a name="prerequisite"></a>Предварительные требования
- Развертывание кластера Pacemaker высокий уровень доступности, как описано в разделе [развернуть кластер Pacemaker для SQL Server в Linux](sql-server-linux-deploy-pacemaker-cluster.md).


## <a name="enable-the-availability-groups-feature"></a>Включите компонент групп доступности

В отличие от на Windows, вы не сможете использовать PowerShell или [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Configuration Manager для обеспечения доступности группирует функции (AG). Под Linux, необходимо использовать `mssql-conf` для включения функции. Существует два способа включения функции групп доступности: использовать `mssql-conf` служебная программа или редактировать `mssql.conf` файл вручную.

> [!IMPORTANT]
> Необходимо включить функцию групп Доступности для реплик только для конфигурации, даже на [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)].

### <a name="use-the-mssql-conf-utility"></a>Используйте служебную программу mssql-conf

В строке выполните следующее:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Измените файл mssql.conf

Вы также можете изменить `mssql.conf` файла, расположенного в `/var/opt/mssql` папки, чтобы добавить следующие строки:

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>Перезапустите [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
После включения групп доступности, так как на Windows, необходимо перезапустить [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Это можно сделать, следующие:

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>Создайте конечные точки группы доступности и сертификаты

Группа доступности использует конечные точки TCP для обмена данными. Под Linux конечные точки для группы Доступности поддерживаются только в случае использования сертификатов для проверки подлинности. Это означает, что сертификат из одного экземпляра должна быть восстановлена на всех экземплярах, которые будут реплик, участвующих в той же группе Доступности. Время сертификата является обязательным, даже для реплики только для конфигурации. 

Создание конечных точек и восстановление сертификатов можно только с помощью Transact-SQL. Можно использовать отличных[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-созданные сертификаты также. Необходимо использовать процесс для управления и замените все сертификаты, срок действия.

> [!IMPORTANT]
> Если вы планируете использовать [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] мастер для создания группы Доступности, вам все равно нужно создать и восстановить сертификаты с помощью Transact-SQL в Linux.

Полный синтаксис на параметры, доступные для различных команд (например, дополнительная безопасность) см.:

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [СОЗДАНИЕ СЕРТИФИКАТА](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> Несмотря на то, что вы создадите группу доступности, использует тип конечной точки *FOR DATABASE_MIRRORING*, так как некоторые базовые параметры один раз был предоставлен этот компонент уже устаревшего.

В этом примере будет создавать сертификаты для конфигурации с тремя узлами. Имена экземпляров являются LinAGN1 LinAGN2 и LinAGN3.

1.  На LinAGN1 создайте главный ключ, сертификат и конечной точки, а также резервную копию сертификата, выполните указанные ниже команды. Например типичный TCP-порт 5022 используется для конечной точки.
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN1_Cert
    WITH SUBJECT = 'LinAGN1 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN1_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN1_Cert,
        ROLE = ALL);
    
    GO
    ```
    
2.  Сделайте то же самое, на LinAGN2:
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    WITH SUBJECT = 'LinAGN2 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN2_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN2_Cert,
        ROLE = ALL);
    
    GO
    ```
    
3.  Наконец выполните ту же последовательность на LinAGN3.
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    WITH SUBJECT = 'LinAGN3 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN3_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN3_Cert,
        ROLE = ALL);
    
    GO
    ```
    
4.  С помощью `scp` или другой служебной программы, скопируйте резервные копии сертификата для каждого узла, который будет частью группы Доступности.
    
    Для этого примера:
    
    - Скопируйте LinAGN1_Cert.cer LinAGN2 и LinAGN3
    - Скопируйте LinAGN2_Cert.cer LinAGN1 и LinAGN3.
    - Скопируйте LinAGN3_Cert.cer LinAGN1 и LinAGN2.
    
5.  Изменить владельца и группу, связанную с файлы копируются сертификатов, чтобы `mssql`.
    
    ```bash
    sudo chown mssql:mssql <CertFileName>
    ```
    
6.  Создание уровня экземпляра имена входа и пользователи, связанные с LinAGN2 и LinAGN3 на LinAGN1.
    
    ```SQL
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
7.  Восстановите LinAGN2_Cert и LinAGN3_Cert на LinAGN1. Наличие других реплик сертификатов является важным аспектом взаимодействия группы Доступности и безопасности.
    
    ```SQL
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
8.  Grant the logins associated with LinAG2 and LinAGN3 permission to connect to the endpoint on LinAGN1.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
9.  Создание уровня экземпляра имена входа и пользователи, связанные с LinAGN1 и LinAGN3 на LinAGN2.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
10.  Восстановите LinAGN1_Cert и LinAGN3_Cert на LinAGN2. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
11.  Grant the logins associated with LinAG1 and LinAGN3 permission to connect to the endpoint on LinAGN2.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
12.  Создание уровня экземпляра имена входа и пользователи, связанные с LinAGN1 и LinAGN2 на LinAGN3.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    ```
    
13.  Восстановите LinAGN1_Cert и LinAGN2_Cert на LinAGN3. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
14.  Grant the logins associated with LinAG1 and LinAGN2 permission to connect to the endpoint on LinAGN3.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    ```

## <a name="create-the-availability-group"></a>Создание группы доступности

В этом разделе описывается, как использовать [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) или Transact-SQL, чтобы создать группу доступности для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>Используйте [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)].

В этом разделе показано, как создать группу Доступности с типом кластера внешних объектов с помощью среды SSMS с помощью мастера создания группы доступности.

1.  В SSMS разверните **высокий уровень доступности AlwaysOn**, щелкните правой кнопкой мыши **групп доступности**и выберите **мастера создания групп доступности**.

2.  В диалоговом окне «введение» нажмите кнопку **Далее**.

3.  В диалоговом окне укажите параметры группы доступности введите имя для группы доступности и выберите тип кластера EXTERNAL или NONE в раскрывающемся списке. Внешние следует использовать, когда Pacemaker будут развернуты. Нет для специализированных сценариев, такие как чтение горизонтальное масштабирование. Выбрав параметр для определения уровня работоспособности базы данных является необязательным. Дополнительные сведения об этом параметре см. в разделе [параметр отработки отказа определения уровня работоспособности базы данных доступности группа](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md). Нажмите кнопку **Далее**.

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  В диалоговом окне Выбор баз данных выберите в качестве баз данных, который будет участвовать в группе Доступности. Каждая база данных должна иметь полной резервной копии, прежде чем его можно добавить в группу доступности. Нажмите кнопку **Далее**.

5.  В диалоговом окне «Выбор реплик» щелкните **добавления реплики**.

6.  В диалоговом окне подключения к серверу, введите имя экземпляра Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] , которые будут вторичная реплика и учетные данные для подключения. Нажмите кнопку **Соединить**.

7.  Повторите два предыдущих шага для экземпляра, который будет содержать реплики только для конфигурации или другая вторичная реплика.

8.  Все три экземпляра должны появиться в диалоговом окне Выбор реплик. При использовании типа кластера External, для вторичной реплики, которые будет иметь значение true, получатель, убедитесь, что режим доступности совпадает с первичной репликой и внешние задан режим отработки отказа. Только для настройки реплики выберите режим доступности конфигурации только.

    В следующем примере показано группе Доступности с двумя репликами, тип кластера External и реплики только для конфигурации.

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    В следующем примере показано группе Доступности с двумя репликами, типа кластера None и реплики только для конфигурации.

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  Если вы хотите изменить параметры резервного копирования, перейдите на вкладку Параметры резервного копирования. Дополнительные сведения о настройки резервного копирования с группами доступности, см. в разделе [Настройка резервного копирования в репликах доступности](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).

10. Если с помощью считываемые вторичные базы данных или создание группы Доступности в кластере тип для чтения и масштабирования — нет, можно создать прослушиватель, выбрав вкладку прослушивателя. Также можно позже добавить прослушиватель. Чтобы создать прослушиватель, выбрать вариант **создание прослушивателя группы доступности** и введите имя, порт TCP/IP и следует ли использовать статические или автоматически назначаемый IP-адреса DHCP. Помните, что для группы Доступности с типом кластера нет IP-адрес должен быть статическим и задайте для основной IP-адрес.

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. Если прослушиватель создан для сценариев для чтения, SSMS 17.3 или более поздней версии позволяет создавать маршрутизации только для чтения в мастере. Его можно также добавить позже с помощью SSMS или Transact-SQL. Чтобы добавить теперь маршрутизации только для чтения:

    A.  Перейдите на вкладку маршрутизации только для чтения.

    Б.  Введите URL-адреса для реплик только для чтения. Эти URL-адресов похожи на конечные точки, за исключением того, они используют порт экземпляра, а не конечной точки.

    в.  Выберите каждый URL-адрес, а в нижней части выберите реплики для чтения. Множественный выбор удерживайте нажатой клавишу SHIFT или щелкните и перетащите.

12. Нажмите кнопку **Далее**.

13. Выберите, каким образом будет инициализирована во вторичные реплики. Значение по умолчанию является использование [автоматического заполнения](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md), что требует один и тот же путь на всех серверах, участвующих в группе Доступности. Также возможно мастер резервного копирования, копирования и восстановления (второй параметр); его соединение, если вручную резервного копирования, копирования и восстановления базы данных на репликах (третий параметр); или добавьте базу данных более поздней версии (последние параметр). Как с помощью сертификатов, если вы вручную выполнять резервное копирование и их копирования, разрешения для файлов резервных копий необходимо установить на других репликах. Нажмите кнопку **Далее**.

14. В диалоговом окне проверки Если все, что не возвращаются как успех, изучите. Некоторые предупреждения допустимым и не является критической ошибкой, например, если прослушиватель не создается. Нажмите кнопку **Далее**.

15. В диалоговом окне сводки нажмите кнопку **Готово**. Теперь начнется процесс создания группы Доступности.

16. После завершения создания группы Доступности, нажмите кнопку **закрыть** на результаты. Теперь вы видите группы Доступности на репликах в динамических административных представлений, а также в папке высокий уровень доступности AlwaysOn в среде SSMS.

### <a name="use-transact-sql"></a>С помощью Transact-SQL

В этом разделе показаны примеры создания группы Доступности с помощью Transact-SQL. После создания группы Доступности можно настроить прослушиватель и маршрутизация только для чтения. Группы Доступности, сам можно изменить при помощи `ALTER AVAILABILITY GROUP`, но изменение типа кластера невозможно выполнить в [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Если вы не собираетесь создать группу Доступности с типом кластера внешних объектов, необходимо удалить и повторно создать его с типом кластера нет. Дополнительные сведения и другие параметры можно найти по следующим ссылкам:

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [Настройка маршрутизации только для чтения для группы доступности (SQL Server)](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one--two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>Пример 1 – 2 реплики с репликой только для настройки (внешнего типа)

В этом примере показано, как создать группы двумя репликами Доступности, использующей реплику только для конфигурации.

1.  Выполните на узле, на котором будет размещаться первичная реплика, содержащий полностью чтения и записи копию базы данных. В этом примере используется автоматическое заполнение.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1' WITH (
       ENDPOINT_URL = N' TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       SEEDING_MODE = AUTOMATIC),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       AVAILABILITY_MODE = CONFIGURATION_ONLY);
       
    GO
    ```
    
2.  В окно запроса, подключенное к другой реплики выполните следующую команду, чтобы присоединить реплику к группе Доступности и инициировать процесс заполнения с первичной на вторичную реплику.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  В окно запроса, подключенное к реплике только конфигурации присоедините ее к группе Доступности.
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
   ```

#### <a name="example-two--three-replicas-with-read-only-routing-external-cluster-type"></a>Пример 2 – 3 реплик с (тип внешнего) маршрутизации только для чтения

В этом примере показаны три полный реплик и маршрутизация как доступный только для чтения можно настроить в процессе начального создания группы Доступности.

1.  Выполните на узле, на котором будет размещаться первичная реплика, содержащий полностью чтения и записи копию базы данных. В этом примере используется автоматическое заполнение.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN2.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:1433')),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN2.FullyQualified.Name:1433')),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN3.FullyQualified.Name:1433'))
    LISTENER '<ListenerName>' (WITH IP = ('<IPAddress>', '<SubnetMask>'), Port = 1433);
    
    GO
    ```
    
    Несколько замечаний относительно этой конфигурации:
    
    - *AGName* — это имя группы доступности.
    - *DBName* — это имя базы данных, который будет использоваться с группой доступности. Он также может быть список имен, разделенных запятыми.
    - *ListenerName* — это имя, которое отличается от любой из базовых серверов или узлов. Оно будет зарегистрировано в DNS, вместе с *IPAddress*.
    - *IP-адрес* является IP-адресом, с которым связан *ListenerName*. Он уникален и не таким, как любой из серверов или узлов. Приложения и конечные пользователи будут использовать либо *ListenerName* или *IPAddress* для подключения к группе Доступности.
    - *Маска подсети* — это маска подсети *IPAddress*; например, 255.255.255.0.

2.  В окно запроса, подключенное к другой реплики выполните следующую команду, чтобы присоединить реплику к группе Доступности и инициировать процесс заполнения с первичной на вторичную реплику.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Повторите шаг 2 для третья реплика.

#### <a name="example-three--two-replicas-with-read-only-routing-none-cluster-type"></a>Пример 3 — две реплики с маршрутизации только для чтения (ни один тип кластера)

В этом примере показано создание конфигурации двумя репликами с помощью типа кластера None. Он используется для сценария масштаба чтения где ожидается отработка отказа не указано. При этом создается прослушиватель, который является фактически первичной реплики, а также маршрутизацию только для чтения, используя функцию циклический перебор.

1.  Выполните на узле, на котором будет размещаться первичная реплика, содержащий полностью чтения и записи копию базы данных. В этом примере используется автоматическое заполнение.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = NONE)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name: <PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name'.'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:<PortOfInstance>'));
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:<PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL =N'TCP://LinAGN2.FullyQualified.Name:<PortOfInstance>'));
    LISTENER '<ListenerName>' (WITH IP = ('<PrimaryReplicaIPAddress>', '<SubnetMask>'), Port = <PortOfListener>);
    
    GO
    ```
    
    Where
    - *AGName* — это имя группы доступности.
    - *DBName* — это имя базы данных, который будет использоваться с группой доступности. Он также может быть список имен, разделенных запятыми.
    - *PortOfEndpoint* — номер порта, используемого конечной точкой создан.
    - *PortOfInstance* — номер порта, используемого экземпляром [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].
    - *ListenerName* — это имя, которое отличается от любой из базовых реплик, но фактически не будет использоваться.
    - *PrimaryReplicaIPAddress* IP-адрес первичной реплики.
    - *Маска подсети* — это маска подсети *IPAddress*. Например, 255.255.255.0.
    
2.  Присоедините вторичную реплику к группе Доступности и инициировать автоматическое заполнение.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>Создание [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] имя входа и разрешения для Pacemaker

Базовый кластер Pacemaker высокого уровня доступности [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux требуется доступ к [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] экземпляра, а также разрешения на саму группу доступности. Эти шаги создают имя входа и соответствующими разрешениями, вместе с файлом, сообщающий о входе Pacemaker [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

1.  В окно запроса, подключенное к первой реплике выполните следующее:

    ```SQL
    CREATE LOGIN PMLogin WITH PASSWORD '<StrongPassword>';
    
    GO
    
    GRANT VIEW SERVER STATE TO PMLogin;
    
    GO
    
    GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::<AGThatWasCreated> TO PMLogin;
    
    GO
    ```
    
2.  На узле 1 введите команду 
    ```bash
    sudo emacs /var/opt/mssql/secrets/passwd
    ```
    
    Откроется в редакторе Emacs.
    
3.  Введите следующие две строки в редактор:

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  Удерживайте нажатой клавишу CTRL и нажмите клавишу X, затем C, чтобы выйти и сохранить файл.

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    для блокировки файла.

6.  Повторите шаги 1 – 5 на других серверах, на которые будет использоваться в качестве реплики.

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>Создание ресурсов группы доступности в кластере Pacemaker (внешний)

После доступности группа создается в [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], соответствующие ресурсы должны создаваться в Pacemaker, если указанный тип кластера External. Существуют два ресурса, сопоставленный группе Доступности: самой группе Доступности и IP-адресом. Настройка ресурса IP-адреса является обязательным, если вы не используете функцию прослушивателя, но рекомендуется.

Ресурс группы Доступности, которая создается — это особый тип ресурса, вызывается клон. Ресурс группы Доступности по существу имеет копий на каждом узле и есть один ресурс управления с именем master. Master, связанный с сервером, на котором размещена первичная реплика. Вторичные реплики (обычный или только для настройки), считаются подчиненными и может быть повышен до главного для отработки отказа.

1.  Создайте ресурс группы Доступности со следующим синтаксисом:

    **Red Hat Enterprise Linux (RHEL) и Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failure-timeout=30s --master meta notify=true
    ```

    >[!NOTE]
    >На RHEL 7.4 может появиться предупреждение с использованием--master. Чтобы избежать этого, используйте `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failover-timeout=30s master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
    meta failure-timeout=60s \
    op start timeout=60s \
    op stop timeout=60s \
    op promote timeout=60s \
    op demote timeout=10s \
    op monitor timeout=60s interval=10s \
    op monitor timeout=60s interval=11s role="Master" \
    op monitor timeout=60s interval=12s role="Slave" \
    op notify timeout=60s
    ms ms-ag_cluster <NameForAGResource> \
    meta master-max="1" master-node-max="1" clone-max="3" \
    clone-node-max="1" notify="true" \
    commit
    ```
    
    где *NameForAGResource* — уникальное имя, присвоенное этому ресурсу кластера для группы Доступности, и *AGName* — имя группы Доступности, который был создан.
 
2.  Создайте ресурс IP-адреса для группы Доступности, который будет связан с помощью функции прослушивателя.

    **RHEL и Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForIPResource> ocf:heartbeat:IPaddr2 ip=<IPAddress> cidr_netmask=<Netmask>
    ```

    **SLES**
    
    ```bash
    crm configure \
    primitive <NameForIPResource> \
       ocf:heartbeat:IPaddr2 \
       params ip=<IPAddress> \
          cidr_netmask=<Netmask>
    ```
    
    где *NameForIPResource* — уникальное имя для ресурса IP-адрес, и *IPAddress* статический IP-адрес, назначенный ресурсу. В SLES необходимо также указать маску подсети. Например, 255.255.255.0 обладает значением 24 для *маску подсети.*
    
3.  Чтобы убедиться, что IP-адрес и ресурс группы Доступности, запущены на одном узле, необходимо настроить ограничение совместного размещения.

    **RHEL и Ubuntu**
    
    ```bash
    sudo pcs constraint colocation add <NameForIPResource> <NameForAGResource>-master INFINITY with-rsc-role=Master
    ```

    **SLES**
    
    ```bash
    crm configure <NameForConstraint> inf: \
    <NameForIPResource> <NameForAGResource>:Master 
    commit
    ```
    
    где *NameForIPResource* — это имя для ресурса IP-адрес, *NameForAGResource* — это имя для ресурса группы Доступности, а также в SLES, *NameForConstraint* имя ограничение.

4.  Создайте ограничение, чтобы убедиться, что ресурс группы Доступности работает порядка и перед IP-адрес. Хотя ограничение совместное размещение подразумевает ограничения упорядочивания, это принудительно применяет ее.

    **RHEL и Ubuntu**
    
    ```bash
    sudo pcs constraint order promote <NameForAGResource>-master then start <NameForIPResource>
    ```
    
    **SLES**
    
    ```bash
    crm configure \
    order <NameForConstraint> inf: <NameForAGResource>:promote <NameForIPResource>:start
    commit
    ```
    
    где *NameForIPResource* — это имя для ресурса IP-адрес, *NameForAGResource* — это имя для ресурса группы Доступности, а также в SLES, *NameForConstraint* имя ограничение.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как создать и настроить группы доступности для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux. Вы узнали, как для:
> [!div class="checklist"]
> * Включите группы доступности.
> * Создание группы Доступности конечные точки и сертификаты.
> * Используйте [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) или Transact-SQL, чтобы создать группу Доступности.
> * Создание [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] имя входа и разрешения для Pacemaker.
> * Создание группы Доступности ресурсов в кластере Pacemaker.

Большая часть группы Доступности задач администрирования, включая обновления и отработки отказа см. в разделе:

> [!div class="nextstepaction"]
> [Работы группы доступности высокого уровня ДОСТУПНОСТИ для SQL Server в Linux](sql-server-linux-availability-group-failover-ha.md)

