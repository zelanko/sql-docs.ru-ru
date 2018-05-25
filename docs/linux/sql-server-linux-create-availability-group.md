---
title: Создание и настройка группы доступности для SQL Server для Linux | Документы Microsoft
description: Этот учебник демонстрирует создание и Настройка групп доступности для SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 549b34aa918f65da20c3398e1d38491841b5c6fc
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>Создание и настройка группы доступности для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Этот учебник описывает способы создания и настройки группы доступности (AG) для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux. В отличие от [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] и более ранних версий на Windows, можно включить и действий с или без создания базового кластера Pacemaker сначала. Интеграция с кластером, если требуется, не выполняется до более поздней версии.

Учебник включает следующие задачи:
 
> [!div class="checklist"]
> * Включите группы доступности.
> * Создайте конечные точки группы доступности и сертификаты.
> * Используйте [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) или Transact-SQL для создания группы доступности.
> * Создание [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] входа и разрешения для Pacemaker.
> * Создание ресурсов группы доступности в кластере Pacemaker (только для внешнего типа).

## <a name="prerequisite"></a>Предварительные требования
- Развертывание кластера Pacemaker высокий уровень доступности, как описано в [развертывание кластера Pacemaker для SQL Server в Linux](sql-server-linux-deploy-pacemaker-cluster.md).


## <a name="enable-the-availability-groups-feature"></a>Включить группы доступности

В отличие от в Windows, нельзя использовать PowerShell или [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Configuration Manager для обеспечения доступности группы компонентов (AG). Под Linux, следует использовать `mssql-conf` для включения функции. Существует два способа включить группы доступности: использовать `mssql-conf` программы, или изменить `mssql.conf` файл вручную.

> [!IMPORTANT]
> Функция AG должен быть включен для реплик только для конфигурации, даже [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)].

### <a name="use-the-mssql-conf-utility"></a>Используйте служебную программу mssql conf

В строке выполните следующее:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Измените файл mssql.conf

Можно также изменить `mssql.conf` файла, расположенного в `/var/opt/mssql` папке, добавьте следующие строки:

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>Перезагрузка [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
После включения групп доступности, как в Windows, необходимо перезапустить [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Что можно сделать следующие:

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>Создайте конечные точки группы доступности и сертификаты

Группа доступности использует конечные точки TCP для обмена данными. Под Linux конечные точки для группы Доступности поддерживаются только при использовании сертификатов для проверки подлинности. Это означает, что сертификат из одного экземпляра, необходимо восстановить на все остальные экземпляры, которые будут реплик, участвующих в одну группу Доступности. В процессе сертификатов требуется даже для реплик только для конфигурации. 

Создание конечных точек и восстановление сертификатов может выполняться только через Transact-SQL. Можно использовать отличных[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-сертификаты также создан. Необходимо использовать процесс для управления и замените все сертификаты, срок действия.

> [!IMPORTANT]
> Если вы планируете использовать [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] мастера для создания группы Доступности, вы по-прежнему требуется для создания и восстановления сертификатов с помощью Transact-SQL в Linux.

Полное описание синтаксиса на параметры, доступные для различных команд (например, дополнительная защита) см.:

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [СОЗДАНИЕ СЕРТИФИКАТА](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> Несмотря на то, что будет создана группа доступности, использует тип конечной точки *FOR DATABASE_MIRRORING*, так как некоторые аспекты базовых один раз был предоставлен, неподдерживаемые функции.

Этот пример создает сертификаты для настройки трех узлов. Имена экземпляров: LinAGN1, LinAGN2 и LinAGN3.

1.  LinAGN1 для создания главного ключа, сертификат и конечной точки, а также создать резервную копию сертификата, выполните следующее. Например типичный TCP-порт 5022 используется для конечной точки.
    
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
    
3.  Наконец выполните ту же последовательность на LinAGN3:
    
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
    
4.  С помощью `scp` или другую утилиту для копирования резервных копий сертификата на каждом узле, который будет входить в группу доступности.
    
    В этом примере:
    
    - Скопируйте LinAGN1_Cert.cer LinAGN2 и LinAGN3
    - Скопируйте LinAGN2_Cert.cer LinAGN1 и LinAGN3.
    - Скопируйте LinAGN3_Cert.cer LinAGN1 и LinAGN2.
    
5.  Изменить владельца и группа, связанная с файлы копируются сертификатов, чтобы `mssql`.
    
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
    
7.  Восстановление LinAGN2_Cert и LinAGN3_Cert на LinAGN1. Наличие других реплик сертификатов является важным аспектом связи группы Доступности и безопасности.
    
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
    
10.  Восстановление LinAGN1_Cert и LinAGN3_Cert на LinAGN2. 
    
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
    
13.  Восстановление LinAGN1_Cert и LinAGN2_Cert на LinAGN3. 
    
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

В этом разделе описывается использование [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) или Transact-SQL для создания группы доступности для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>Используйте [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)].

В этом разделе показано создание группы Доступности с типом кластера внешних объектов с помощью среды SSMS с помощью мастера создания группы доступности.

1.  В SSMS разверните **высокий уровень доступности AlwaysOn**, щелкните правой кнопкой мыши **группы доступности**и выберите **мастера создания группы доступности**.

2.  В диалоговом окне Общие сведения, нажмите кнопку **Далее**.

3.  В диалоговом окне укажите параметры группы доступности введите имя для группы доступности и выберите тип кластера ВНЕШНИЕ или нет в раскрывающемся списке. Внешние должен использоваться при Pacemaker будет развертываться. NONE — для специализированных сценариев, такие как чтение горизонтальное масштабирование. При выборе параметра для определения работоспособности уровня базы данных является необязательным. Дополнительные сведения об этом параметре см. в разделе [параметра отработки отказа обнаружения работоспособности уровня базы данных группы доступности](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md). Нажмите кнопку **Далее**.

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  В диалоговом окне Выбор баз данных выберите баз данных, который будет участвовать в группе Доступности. Его можно добавить к группе Доступности должны иметь полную резервную копию каждой базы данных. Нажмите кнопку **Далее**.

5.  В диалоговом окне Выбор реплик щелкните **добавления реплики**.

6.  В окне подключения к серверу диалоговое окно, введите имя экземпляра Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] , которые будут вторичная реплика и учетные данные для подключения. Нажмите кнопку **Соединить**.

7.  Повторите два предыдущих шага для экземпляра, который будет содержать только для настройки реплики или другая вторичная реплика.

8.  Теперь все три экземпляра должна быть указана в диалоговом окне Выбор реплик. При использовании кластера разновидность внешних, вторичная реплика, которая будет иметь значение true, получатель, убедитесь, что режим доступности таковыми первичной реплики и внешние задан режим перехода на другой ресурс. Для реплики только для конфигурации выберите только в режиме конфигурации.

    В следующем примере показано группе Доступности с двумя репликами, тип кластера внешних объектов и только для настройки реплики.

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    В следующем примере показано группе Доступности с двумя репликами, типом кластера ни один и только для настройки реплики.

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  Если вы хотите изменить параметры резервного копирования, перейдите на вкладку Параметры резервного копирования. Дополнительные сведения о настройки резервного копирования с помощью групп доступности см. в разделе [Настройка резервного копирования в репликах доступности](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).

10. Если с помощью получателей для чтения или создание группы Доступности в кластере тип None для чтения шкалы, можно создать прослушиватель при выборе вкладки прослушивателя. Также можно позднее добавить прослушиватель. Чтобы создать прослушиватель, выберите вариант **создание прослушивателя группы доступности** и введите имя, порт TCP/IP и следует ли использовать статические или автоматически назначенный IP-адреса DHCP. Помните, что для группы Доступности с типом кластера нет, IP-адрес должен быть статическим и установите на сервере-источнике IP-адрес.

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. Если прослушиватель создан для сценариев для чтения, среда SSMS 17.3 или более поздней версии позволяет создавать маршрутизации только для чтения в мастере. Его можно также добавить позже через SSMS или Transact-SQL. Чтобы добавить теперь маршрутизации только для чтения.

    A.  Перейдите на вкладку маршрутизации только для чтения.

    Б.  Введите URL-адреса для реплик только для чтения. Эти URL-адреса похожи на конечные точки, за исключением того, они используют порт экземпляра, не конечной точки.

    в.  Выберите каждый URL-адрес, а в нижней части выберите реплики для чтения. Для множественный выбор удерживая клавишу SHIFT или щелкните и перетащите.

12. Нажмите кнопку **Далее**.

13. Выберите, каким образом будет инициализирована во вторичные реплики. Значение по умолчанию — использование [автоматического заполнения](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md), которая требует один и тот же путь на всех серверах, участвующих в группе Доступности. Вы также можете мастер резервного копирования, копирования и восстановления (второй вариант); его соединение, если вручную резервного копирования, копирования и восстановления базы данных в реплику (третий параметр); или добавьте базу данных более поздней версии (последний параметр). С помощью сертификатов, если вы вручную выполнять резервное копирование и копирования их разрешения для файлов резервных копий должно быть задано на другие реплики. Нажмите кнопку **Далее**.

14. В диалоговом окне проверки Если все приходит как успех, изучите. Некоторые предупреждения являются допустимым и не критическая ошибка, например, если прослушиватель не создается. Нажмите кнопку **Далее**.

15. В диалоговом окне сводки, щелкните **Готово**. Теперь начнется процесс создания группы Доступности.

16. После завершения создания группы Доступности, нажмите кнопку **закрыть** на результаты. Теперь можно увидеть группой Доступности для реплики в динамических административных представлений, а также в папке высокой доступности AlwaysOn в среде SSMS.

### <a name="use-transact-sql"></a>С помощью Transact-SQL

В этом разделе приведены примеры создания группы Доступности с помощью Transact-SQL. После создания группы Доступности можно настроить прослушиватель и маршрутизации только для чтения. Группы Доступности, сама могут быть изменены с `ALTER AVAILABILITY GROUP`, но изменение типа кластера не может выполняться [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Если вы не собираетесь для создания группы Доступности с типом кластера внешних объектов, необходимо удалить и повторно создать его с типом кластера нет. Дополнительные сведения и другие параметры можно найти по следующим ссылкам:

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [Настройка маршрутизации только для чтения для группы доступности (SQL Server)](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one--two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>Пример одного – двух реплик с репликой только для конфигурации (тип внешнего кластера)

В этом примере показано создание двух реплик группы Доступности, использующей реплику только для конфигурации.

1.  Выполните на узле, который будет первичной реплики, содержащий полностью чтение/запись копии этих баз данных. В этом примере используется автоматического заполнения.

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
    
2.  В окне запроса подключена к другой реплике выполните следующую команду, чтобы присоединить реплику к группе Доступности и инициировать процесс заполнения с сервера-источника на вторичную реплику.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  В окне запроса подключена к реплике только конфигурации присоедините ее к группе Доступности.
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
   ```

#### <a name="example-two--three-replicas-with-read-only-routing-external-cluster-type"></a>Пример двух-трех реплик с маршрутизации (тип внешнего) только для чтения

В этом примере показаны три полной реплики и маршрутизации только для чтения можно настроить как часть первоначальное Создание группы Доступности.

1.  Выполните на узле, который будет первичной реплики, содержащий полностью чтение/запись копии этих баз данных. В этом примере используется автоматического заполнения.

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
    
    Некоторые аспекты замечания об этой конфигурации.
    
    - *AGName* имя группы доступности.
    - *DBName* — имя базы данных, которая будет использоваться с группой доступности. Он также может быть список имен, разделенных запятыми.
    - *ListenerName* — имя, которое отличается от любого из этих базовых серверов или узлов. Она будет зарегистрирована в службе DNS вместе с *IP-адрес*.
    - *IP-адрес* — IP-адрес, который связан с *ListenerName*. Является уникальным и отличным от любого из этих узлов и серверов. Приложения и пользователи будут использовать либо *ListenerName* или *IP-адрес* для подключения к группе Доступности.
    - *Маска подсети* — маска подсети *IP-адрес*; например, 255.255.255.0.

2.  В окне запроса подключена к другой реплике выполните следующую команду, чтобы присоединить реплику к группе Доступности и инициировать процесс заполнения с сервера-источника на вторичную реплику.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Повторите шаг 2 для третьего реплики.

#### <a name="example-three--two-replicas-with-read-only-routing-none-cluster-type"></a>Пример 3 – два реплик с маршрутизации только для чтения (ни один кластер типа)

В этом примере показано создание конфигурации двумя репликами с помощью типом кластера нет. Он используется в сценарии чтения шкалы там, где ожидается отработка отказа. При этом создается прослушиватель, который является фактически первичной реплики, а также маршрутизацию только для чтения, с помощью функции циклического перебора.

1.  Выполните на узле, который будет первичной реплики, содержащий полностью чтение/запись копии этих баз данных. В этом примере используется автоматического заполнения.

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
    - *AGName* имя группы доступности.
    - *DBName* — имя базы данных, которая будет использоваться с группой доступности. Он также может быть список имен, разделенных запятыми.
    - *PortOfEndpoint* — номер порта, используемого конечной точкой создан.
    - *PortOfInstance* — номер порта, используемый экземпляром [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].
    - *ListenerName* — имя, которое отличается от любой основной реплике, но фактически не будет использоваться.
    - *PrimaryReplicaIPAddress* IP-адрес первичной реплики.
    - *Маска подсети* — маска подсети *IP-адрес*. Например, 255.255.255.0.
    
2.  Присоединение вторичной реплики к группе Доступности и инициировать автоматического заполнения.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>Создание [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] входа и разрешения для Pacemaker

Базовый кластер Pacemaker высокого уровня доступности [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux требуется доступ к [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] экземпляра, а также разрешения на саму группу доступности. Эти шаги создают имя входа и разрешениями, вместе с файлом, о том, как войти в Pacemaker [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

1.  В окне запроса подключена к первой реплике выполните следующее:

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
    
    Откроется редактор Emacs.
    
3.  Введите следующие две строки в редактор:

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  Удерживая нажатой клавишу CTRL и нажмите клавишу X, а затем C, чтобы выйти и сохранить файл.

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    для блокировки файла.

6.  Повторите шаги 1-5 на других серверах, которые будет использоваться в качестве реплики.

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>Создайте ресурсов группы доступности в кластере Pacemaker (внешний)

После доступности группа создается в [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], соответствующие ресурсы должны создаваться в Pacemaker, если указан тип кластера внешних объектов. Два ресурса, связанный с группой Доступности: группы Доступности, сама и IP-адрес. Настройка ресурса IP-адреса является обязательным, если вы не используете функцию прослушивателя, но рекомендуется.

Созданного ресурса группы Доступности — это специальный ресурса, называемая клоном. Ресурс группы Доступности по существу имеет копий на каждом узле и имеется один управляющий ресурс, называемый образцом. Master связан с сервером, на котором размещена первичная реплика. Вторичные реплики (обычный или только для конфигурации), считаются подчиненными и может быть повышен до главного при отработке отказа.

1.  Создайте ресурс группы Доступности с помощью следующего синтаксиса:

    **Red Hat Enterprise Linux (RHEL) и Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> --master meta notify=true
    ```

    >[!NOTE]
    >На RHEL 7.4 может появиться предупреждение с использованием--master. Чтобы избежать этого, используйте `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
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
    
    где *NameForAGResource* уникальное имя, присвоенное этому ресурсу кластера для группы Доступности, и *AGName* имя группы Доступности, который был создан.
 
2.  Создайте ресурс IP-адреса для группы Доступности, связанного с помощью функции прослушивателя.

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
    
    где *NameForIPResource* уникальное имя для ресурса IP- и *IP-адрес* статический IP-адрес, назначенные для ресурса. На SLES необходимо также указать сетевую маску. Например, 255.255.255.0 будет иметь значение 24 для *маска сети.*
    
3.  Чтобы убедитесь, что IP-адрес и ресурс группы Доступности работают на одном узле, необходимо настроить ограничение совместного размещения.

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
    
    где *NameForIPResource* имя для ресурса IP- *NameForAGResource* имя ресурса группы Доступности, а на SLES, *NameForConstraint* имя ограничение.

4.  Создайте упорядочения ограничения, что ресурс группы Доступности не будет и выполняется до IP-адрес. Хотя ограничение совместного размещения подразумевает ограничением порядка сортировки, при этом принудительно реализуется его.

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
    
    где *NameForIPResource* имя для ресурса IP- *NameForAGResource* имя ресурса группы Доступности, а на SLES, *NameForConstraint* имя ограничение.

## <a name="next-steps"></a>Следующие шаги

В этом учебнике вы узнали, как создание и настройка группы доступности для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux. Узнать, как для:
> [!div class="checklist"]
> * Включите группы доступности.
> * Создание группы Доступности конечными точками и сертификаты.
> * Используйте [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) или Transact-SQL для создания группы Доступности.
> * Создание [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] входа и разрешения для Pacemaker.
> * Создание группы Доступности ресурсов в кластере Pacemaker.

Большая часть группы Доступности задач администрирования, включая обновления и отработка отказа см.:

> [!div class="nextstepaction"]
> [Работы группы доступности высокого уровня ДОСТУПНОСТИ для SQL Server в Linux](sql-server-linux-availability-group-failover-ha.md)

