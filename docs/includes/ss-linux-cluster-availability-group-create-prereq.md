## <a name="prerequisites"></a>Предварительные требования

Перед созданием группы доступности необходимо выполнить следующие действия:

- Настроить среду таким образом, чтобы все серверы, в которых будут находиться группы доступности, могли взаимодействовать между собой.
- Установите SQL Server.

>[!NOTE]
>В Linux группу доступности необходимо создать перед тем, как добавить ее в качестве кластерного ресурса, управляемого кластером. В этом документе приводится пример создания группы доступности. Инструкции по созданию кластера и добавлению группы доступности в качестве кластерного ресурса для конкретных сред см. по ссылкам в разделе "Дальнейшие действия".

1. Обновление имени компьютера для каждого узла.

   Каждое имя SQL Server должно отвечать следующим требованиям:
   
   - 15 символов или меньше;
   - уникальность в пределах сети.
   
   Чтобы указать имя компьютера, измените файл `/etc/hostname`. Следующий сценарий позволяет изменить `/etc/hostname` с помощью `vi`:

   ```bash
   sudo vi /etc/hostname
   ```

2. Настройка файла hosts.

    >[!NOTE]
    >Если имена узлов зарегистрированы с их IP-адресами на DNS-сервере, указанные ниже действия выполнять не нужно. Убедитесь, что все узлы, которые требуется включить в конфигурацию группы доступности, могут взаимодействовать друг с другом. (Команда проверки связи с узлом должна возвращать ответ с соответствующим IP-адресом.) Кроме того, проверьте, не содержит ли файл /etc/hosts запись, которая сопоставляет IP-адрес localhost 127.0.0.1 с именем узла.
    >

   Файл hosts на каждом сервере содержит IP-адреса и имена всех серверов, которые будут участвовать в группе доступности. 

   Следующая команда возвращает IP-адрес текущего сервера:

   ```bash
   sudo ip addr show
   ```

   Обновите `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`:

   ```bash
   sudo vi /etc/hosts
   ```

   В следующем примере показан файл `/etc/hosts` на узле **node1** с дополнениями для узлов **node1**, **node2** и **node3**. В этом документе **node1** относится к серверу, на котором размещается первичная реплика, а **node2** и **node3** относятся к серверам, на которых размещаются вторичные реплики.

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>Установка SQL Server

Установите SQL Server. Инструкции по установке SQL Server для различных сред см. по указанным ниже ссылкам: 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Включение групп доступности AlwaysOn и перезапуск mssql-server

Включите группы доступности Always On на каждом узле с экземпляром SQL Server. Затем перезапустите `mssql-server`. Выполните следующий скрипт:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwayson_health-event-session"></a>Включение сеанса событий AlwaysOn_health 

При необходимости вы можете включить расширенные события групп доступности AlwaysOn, что может помочь в устранении их неполадок. На каждом экземпляре SQL Server выполните следующую команду: 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Дополнительные сведения о сеансах расширенных событий см. в разделе [Расширенные события Always On](https://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-a-certificate"></a>Создание сертификата

Служба SQL Server на Linux использует сертификаты для проверки подлинности при обмене данными между конечными точками с зеркальным отображением. 

Следующий сценарий Transact-SQL создает главный ключ и сертификат. Затем он создает резервную копию сертификата и защищает файл закрытым ключом. Обновите сценарий, задав надежные пароли. Подключение к первичному экземпляру SQL Server. Чтобы создать сертификат, выполните следующий скрипт Transact-SQL:

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

На этом этапе первичная реплика SQL Server имеет сертификат в файле `/var/opt/mssql/data/dbm_certificate.cer` и закрытый ключ в файле `var/opt/mssql/data/dbm_certificate.pvk`. Скопируйте эти файлы в одно и то же место на всех серверах, где будут размещаться реплики доступности. Выберите пользователя mssql или предоставьте пользователю mssql разрешения на доступ к этим файлам. 

Например, на исходном сервере указанная ниже команда копирует файлы на целевой компьютер. Замените значения `**<node2>**` на имена экземпляров SQL Server, где будут размещены реплики. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

На каждом целевом сервере предоставьте пользователю mssql разрешение на доступ к сертификату.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Создание сертификата на серверах-получателях

Следующий сценарий Transact-SQL создает главный ключ и сертификат из резервной копии, созданной в первичной реплике SQL Server. Обновите сценарий, задав надежные пароли. Для расшифровки используется тот же пароль, что и при создании PVK-файла в предыдущем шаге. Выполните следующий скрипт на всех серверах-получателях для создания сертификата:

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Создайте конечные точки на всех репликах зеркального отображения базы данных

Для передачи и получения сообщений между экземплярами серверов, участвующими в сеансах зеркального отображения базы данных или размещающих реплики доступности, в конечных точках зеркального отображения базы данных используется протокол TCP. Конечная точка зеркального отображения базы данных прослушивает порт TCP с уникальным номером. 

Следующий запрос Transact-SQL создает конечную точку прослушивания с именем `Hadr_endpoint` для группы доступности. Он запускает конечную точку и предоставляет созданному вами сертификату разрешение на подключение. Перед выполнением данного сценария замените значения между `**< ... >**`. При необходимости можно включить IP-адрес `LISTENER_IP = (0.0.0.0)`. IP-адрес прослушивателя должен быть IPv4-адресом. Также можно использовать `0.0.0.0`. 

Обновите следующий сценарий Transact-SQL для среды на всех экземплярах SQL Server: 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATABASE_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
```

>[!NOTE]
>Если вы используете выпуск SQL Server Express на одном узле для размещения реплики, поддерживающей только конфигурацию, единственным допустимым значением для `ROLE` является `WITNESS`. Выполните следующий скрипт в выпуске SQL Server Express:

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATABASE_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
```

TCP-порт в брандмауэре должен быть открыт для порта прослушивателя.



>[!IMPORTANT]
>Для выпуска SQL Server 2017 единственный поддерживаемый способ проверки подлинности для конечной точки с зеркальным отображением базы данных — `CERTIFICATE`. Параметр `WINDOWS` будет включен в будущем выпуске.

Дополнительные сведения см. в статье [Конечная точка зеркального отображения базы данных (SQL Server)](https://msdn.microsoft.com/library/ms179511.aspx).


