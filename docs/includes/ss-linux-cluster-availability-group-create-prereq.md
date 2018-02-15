## <a name="prerequisites"></a>предварительные требования

Перед созданием группы доступности необходимо выполнить следующие действия:

- Задайте среду, чтобы все серверы, которые будут размещаться реплики доступности можно взаимодействовать.
- Установите SQL Server.

>[!NOTE]
>В Linux необходимо создать группу доступности, перед их добавлением в качестве ресурса кластера для управления кластером. В этом документе приводится пример создания группы доступности. Для распространения конкретных инструкций по созданию кластера и добавить группу доступности в качестве ресурса кластера см. по ссылкам в разделе «Дальнейшие действия».

1. Обновите имя компьютера для каждого узла.

   Каждое имя SQL Server должно отвечать следующим требованиям:
   
   - 15 символов или меньше.
   - Уникально в пределах сети.
   
   Чтобы указать имя компьютера, измените файл `/etc/hostname`. Следующий сценарий позволяет редактировать `/etc/hostname` с `vi`:

   ```bash
   sudo vi /etc/hostname
   ```

2. Настройка файла hosts.

    >[!NOTE]
    >Если имена узлов зарегистрированы с их IP-адреса в DNS-сервер, выполните следующие действия не нужно. Проверьте, что все узлы должен входить в состав конфигурации группы доступности может обмениваться данными друг с другом. (Ping для имени узла должны ответить соответствующий IP-адрес). Кроме того убедитесь, что файл/etc/hosts не содержит запись, которая сопоставляет IP-адрес localhost 127.0.0.1 с именем узла узла.
    >

   Файл hosts на каждом сервере содержит IP-адреса и имена всех серверов, которые будут участвовать в группе доступности. 

   Следующая команда возвращает IP-адрес текущего сервера:

   ```bash
   sudo ip addr show
   ```

   Обновите `/etc/hosts`. Следующий сценарий позволяет редактировать `/etc/hosts` с `vi`:

   ```bash
   sudo vi /etc/hosts
   ```

   В следующем примере показан файл `/etc/hosts` на узле **node1** с дополнениями для узлов **node1**, **node2** и **node3**. В этом документе **node1** ссылается на сервер, на котором размещена первичная реплика. И **node2** и **node3** ссылаться на серверы, на которых размещены вторичные реплики.

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>Установка SQL Server

Установите SQL Server. Следующие ссылки указывают на инструкции по установке SQL Server для различных дистрибутивов: 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Включение групп доступности AlwaysOn и перезапустите сервер mssql

Включение групп доступности AlwaysOn на каждом узле, на котором размещается экземпляр SQL Server. Затем перезапустите `mssql-server`. Выполните следующий скрипт:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwaysonhealth-event-session"></a>Включить сеанс событий AlwaysOn_health 

При необходимости можно включить AlwaysOn доступности группы расширенных событий для диагностики причин при устранении неполадок группы доступности. На каждом экземпляре SQL Server, выполните следующую команду: 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Дополнительные сведения об этом сеансе XE см. в разделе [AlwaysOn расширенных событий](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-a-database-mirroring-endpoint-user"></a>Создание пользователя конечной точки зеркального отображения базы данных

Следующий сценарий Transact-SQL создает имя входа `dbm_login` и пользователя с именем `dbm_user`. Обновите сценарий, задав надежный пароль. Чтобы создать пользователя конечной точки зеркального отображения базы данных, выполните следующую команду на всех экземплярах SQL Server:

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Создание сертификата

Служба SQL Server на Linux использует сертификаты для проверки подлинности при обмене данными между конечными точками с зеркальным отображением. 

Следующий сценарий Transact-SQL создает главный ключ и сертификат. Он затем создает резервную копию сертификата, а также обеспечивает защиту файла с закрытым ключом. Обновите сценарий, задав надежные пароли. Подключиться к основным экземпляром SQL Server. Чтобы создать сертификат, выполните следующий сценарий Transact-SQL:

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

На этом этапе первичную реплику SQL Server имеет сертификат на `/var/opt/mssql/data/dbm_certificate.cer` и закрытого ключа at `var/opt/mssql/data/dbm_certificate.pvk`. Скопируйте эти файлы в одно и то же место на всех серверах, где будут размещаться реплики доступности. Используйте mssql пользователя или предоставить разрешение пользователю mssql, чтобы доступ к этим файлам. 

Например на исходном сервере, следующая команда копирует файлы на целевой компьютер. Замените `**<node2>**` значения с именами экземпляров SQL Server, где будут размещены реплики. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

На каждом целевом сервере необходимо предоставьте разрешение пользователю mssql доступ к этому сертификату.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Создание сертификата на серверах-получателях

Следующий сценарий Transact-SQL создает главный ключ и сертификат из резервной копии, созданной в первичной реплике SQL Server. Эта команда также разрешает пользователю доступ к сертификату. Обновите сценарий, задав надежные пароли. Для расшифровки используется тот же пароль, что и при создании PVK-файла в предыдущем шаге. Чтобы создать сертификат, выполните следующий скрипт на всех серверах-получателях:

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Создайте конечные точки на всех репликах зеркального отображения базы данных

Конечные точки зеркального отображения базы данных используется протокол управления передачей (TCP) для отправки и получения сообщений между экземплярами сервера, участвовать в сеансах зеркального отображения базы данных или размещены реплики доступности. Конечная точка зеркального отображения базы данных прослушивает порт TCP с уникальным номером. 

Следующий сценарий Transact-SQL создает конечную точку прослушивания с именем `Hadr_endpoint` для группы доступности. Он запускает конечную точку и дает разрешение на подключение для пользователя, который был создан. Перед выполнением данного сценария замените значения между `**< ... >**`. При необходимости можно включить IP-адрес `LISTENER_IP = (0.0.0.0)`. IP-адрес прослушивателя должен быть адресом IPv4. Можно также использовать `0.0.0.0`. 

Обновите следующий сценарий Transact-SQL для вашей среды, на всех экземплярах SQL Server: 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

>[!NOTE]
>При использовании SQL Server, экспресс-выпуск на одном узле размещается реплика только для конфигурации, единственным допустимым значением для `ROLE` — `WITNESS`. Выполните следующий скрипт в SQL Server Express Edition:

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

TCP-порт в брандмауэре необходимо открыть порт прослушивателя.



>[!IMPORTANT]
>Для выпуска SQL Server 2017 г. — единственного способа проверки подлинности поддерживается для конечной точки зеркального отображения базы данных `CERTIFICATE`. `WINDOWS` Параметр будет включен в будущем выпуске.

Дополнительные сведения см. в разделе [(SQL Server) конечной точки зеркального отображения базы данных](http://msdn.microsoft.com/library/ms179511.aspx).


