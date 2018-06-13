## <a name="prerequisites"></a>предварительные требования

Перед созданием группы доступности необходимо выполнить следующие действия:

- Настроить среду таким образом, чтобы все серверы, в которых будут находиться группы доступности, могли взаимодействовать между собой.
- Установить SQL Server. Подробные сведения см. в разделе [Установка SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Включение групп доступности AlwaysOn и перезапуск mssql-server

>[!NOTE]
>В приведенной ниже команде используются командлеты из модуля sqlserver, опубликованного в коллекции PowerShell. Этот модуль можно установить с помощью команды Install-Module.

Включите группы доступности AlwaysOn на каждой реплике с экземпляром SQL Server. Перезапустите службу SQL Server. Чтобы включить и перезапустить службы SQL Server, выполните следующую команду:

```powershell
Enable-SqlAlwaysOn -ServerInstance <server\instance> -Force
```

## <a name="enable-an-alwaysonhealth-event-session"></a>Включение сеанса событий AlwaysOn_health

При необходимости вы можете включить сеанс расширенных событий для групп доступности AlwaysOn, что может помочь в выяснении причин неполадок и их устранении. На каждом экземпляре SQL Server выполните следующую команду:

```sql
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Дополнительные сведения о сеансах расширенных событий см. в статье [Расширенные события для групп доступности AlwaysOn](../database-engine/availability-groups/windows/always-on-extended-events.md).

## <a name="database-mirroring-endpoint-authentication"></a>Проверка подлинности конечной точки зеркального отображения базы данных

Чтобы обеспечить корректную работу синхронизации, реплики, входящие в группу доступности для чтения масштабирования, должны будут пройти проверку подлинности в конечной точке. Ниже приводятся два основных сценария для такой проверки подлинности.

### <a name="service-account"></a>Учетная запись службы

В среде Active Directory, где все вторичные реплики на присоединенном к одному домену SQL Server могут проходить проверку подлинности с помощью учетной записи службы. Потребуется явным образом создать имя входа для учетной записи службы на каждом экземпляре SQL Server:

```sql
CREATE LOGIN [<domain>\service account] FROM WINDOWS;
```

### <a name="sql-login-authentication"></a>Проверка подлинности имени входа SQL

В средах, где вторичные реплики могут быть не присоединены к домену Active Directory, необходимо использовать проверку подлинности SQL. Следующий сценарий Transact-SQL создает имя входа `dbm_login` и пользователя с именем `dbm_user`. Обновите сценарий, задав надежный пароль. Чтобы создать пользователя конечной точки с зеркальным отображением базы данных, выполните следующую команду на всех экземплярах SQL Server:

```sql
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

#### <a name="certificate-authentication"></a>Проверка подлинности на основе сертификата

Если вы используете вторичную реплику, которая требует проверки подлинности SQL, проверку подлинности между конечными точками зеркального отображения следует проводить с помощью сертификата.

Следующий сценарий Transact-SQL создает главный ключ и сертификат. Затем он создает резервную копию сертификата и защищает файл закрытым ключом. Обновите сценарий, задав надежные пароли. Чтобы создать сертификат, выполните следующий сценарий на основном экземпляре SQL Server:

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

На этом этапе первичная реплика SQL Server имеет сертификат в файле `c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer` и закрытый ключ в файле `c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk`. Скопируйте эти файлы в одно и то же место на всех серверах, где будут размещаться реплики доступности.

На каждой вторичной реплике учетная запись службы SQL Server должна иметь разрешения на доступ к этому сертификату.

#### <a name="create-the-certificate-on-secondary-servers"></a>Создание сертификата на серверах-получателях

Следующий сценарий Transact-SQL создает главный ключ и сертификат из резервной копии, созданной в первичной реплике SQL Server. Эта команда также разрешает пользователю доступ к сертификату. Обновите сценарий, задав надежные пароли. Для расшифровки используется тот же пароль, что и при создании `.pvk`-файла на предыдущем шаге. Чтобы создать сертификат, выполните следующий сценарий на всех вторичных репликах:

```sql
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

Для передачи и получения сообщений между экземплярами серверов, участвующими в сеансах зеркального отображения базы данных или размещающих реплики доступности, в конечных точках зеркального отображения базы данных используется протокол TCP. Конечная точка зеркального отображения базы данных прослушивает порт TCP с уникальным номером.

Следующий запрос Transact-SQL создает конечную точку прослушивания с именем `Hadr_endpoint` для группы доступности. Он запускает конечную точку и предоставляет учетной записи службы или имени входа SQL, созданному на предыдущем шаге, разрешение на подключение. Перед выполнением данного сценария замените значения между `**< ... >**`. При необходимости можно включить IP-адрес `LISTENER_IP = (0.0.0.0)`. IP-адрес прослушивателя должен быть IPv4-адресом. Также можно использовать `0.0.0.0`.

Обновите следующий сценарий Transact-SQL для среды на всех экземплярах SQL Server:

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [<service account or user>];
```

TCP-порт в брандмауэре должен быть открыт для порта прослушивателя.

Дополнительные сведения см. в статье [Конечная точка зеркального отображения базы данных (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
