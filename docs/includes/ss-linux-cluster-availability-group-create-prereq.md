## <a name="prerequisites"></a>Предварительные требования

Перед созданием группы доступности, необходимо:

- Задать среды, чтобы все серверы, которые будут размещаться реплики доступности можно взаимодействовать
- Установка SQL Server

>[!NOTE]
>В Linux необходимо создать группу доступности перед добавлением его в качестве ресурса кластера для управления кластером. Этот документ содержит пример, в котором создается группа доступности. Для распространения конкретных инструкций по созданию кластера и добавить группу доступности в качестве ресурса кластера, см. по ссылкам в разделе [дальнейшие действия](#next-steps).

1. **Обновить имя компьютера для каждого узла**

   Каждое имя SQL Server должно быть:
   
   - 15 символов или меньше
   - Уникальный в пределах сети
   
   Чтобы указать имя компьютера, изменить `/etc/hostname`. Следующий сценарий позволяет редактировать `/etc/hostname` с `vi`.

   ```bash
   sudo vi /etc/hostname
   ```

1. **Настройка файла hosts**

>[!NOTE]
>Если имена узлов зарегистрированы с их IP-адреса в DNS-сервере, нет необходимости выполнить указанные ниже действия. Проверьте, что все узлы, которые будут входить в состав конфигурации группы доступности может обмениваться данными друг с другом (проверка связи, имя узла должно возвращать соответствующие IP-адреса). Кроме того убедитесь, что этот файл/etc/hosts не содержит запись, которая сопоставляет IP-адрес localhost 127.0.0.1 с именем узла узла.


   Файл hosts на каждом сервере содержит IP-адреса и имена всех серверов, которые будут участвовать в группе доступности. 

   Следующая команда возвращает IP-адрес текущего сервера:

   ```bash
   sudo ip addr show
   ```

   Обновление `/etc/hosts`. Следующий сценарий позволяет редактировать `/etc/hosts` с `vi`.

   ```bash
   sudo vi /etc/hosts
   ```

   Следующий пример показывает `/etc/hosts` на **node1** с дополнениями **node1**, **node2** и **node3**. В этом документе **node1** относится к серверу, на котором размещается первичная реплика, а **node2** и **node3** относятся к серверам, на которых размещаются вторичные реплики.


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.12 node1
   10.128.16.77 node2
   10.128.15.33 node3
   ```

### <a name="install-sql-server"></a>Установка SQL Server

Установка SQL Server. Следующие ссылки указывают на инструкции по установке SQL Server для различных дистрибутивов. 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)

- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)

- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Включение групп доступности AlwaysOn и перезапустите sqlserver

Включите группы доступности AlwaysOn на каждом узле размещения экземпляра SQL Server, а затем перезапустите `mssql-server`.  Выполните следующий скрипт:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-alwaysonhealth-event-session"></a>Включить AlwaysOn_health сеанса событий 

При необходимости вы можете включить расширенные события групп доступности AlwaysOn, что может помочь в устранении их неполадок. Выполните на каждом экземпляре SQL Server следующую команду. 

```Transact-SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Дополнительные сведения об этом сеансе XE см. в разделе [всегда на расширенных событий](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-db-mirroring-endpoint-user"></a>Создание пользователя конечной точки зеркального отображения базы данных

Следующий сценарий Transact-SQL создает имя входа `dbm_login`и пользователя с именем `dbm_user`. Обновите сценарий с надежным паролем. Выполните следующую команду на всех экземплярах SQL Server, чтобы создать пользователя конечной точки с зеркальным отображением базы данных.

```Transact-SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Создание сертификата

Служба SQL Server на Linux использует сертификаты для проверки подлинности при обмене данными между конечными точками с зеркальным отображением. 

Следующий сценарий Transact-SQL создает главный ключ и сертификат. Затем резервная копия сертификата и защищает файл с закрытым ключом. Сценарий можно обновите с помощью надежных паролей. Подключитесь к основному экземпляру SQL Server и запустите следующий код Transact-SQL, чтобы создать сертификат:

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

На этом этапе первичную реплику SQL Server имеет сертификат на `/var/opt/mssql/data/dbm_certificate.cer` и закрытого ключа at `var/opt/mssql/data/dbm_certificate.pvk`. Скопируйте эти файлы в то же расположение на всех серверах, на которых будут размещаться реплики доступности. Используйте mssql user или предоставление разрешения для mssql пользователю доступ к этим файлам. 

Например на исходном сервере, следующая команда копирует файлы на целевой компьютер. Замените  **<node2>**  значения с именами экземпляров SQL Server, где будут размещены реплики. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

На каждом целевом сервере предоставьте пользователю mssql разрешение на доступ к сертификату.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Создание сертификата на серверах-получателях

Следующий сценарий Transact-SQL создает главный ключ и сертификат из резервной копии, созданной в первичной реплике SQL Server. Команда также разрешают пользователю доступ к сертификату. Сценарий можно обновите с помощью надежных паролей. Пароль для дешифрования имеет тот же пароль, который использовался для создания PVK-файл в предыдущем шаге. Выполните следующий скрипт на всех серверах-получателях для создания сертификата.

```Transact-SQL
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

Следующий запрос Transact-SQL создает конечную точку прослушивания с именем `Hadr_endpoint` для группы доступности. Он запускает конечную точку, и дает разрешение connect для пользователя, который был создан. Перед выполнением скрипта замените значения между `**< ... >**`.

>[!NOTE]
>В этом выпуске не следует использовать другой IP-адрес для прослушивателя IP-адреса. Мы работаем над решением этой проблемы, но только допустимые значения сейчас: "0.0.0.0».

Обновление следующий запрос Transact-SQL для вашей среды, на всех экземплярах SQL Server: 

```Transact-SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

>[!IMPORTANT]
>TCP-порт в брандмауэре должен быть открыт порт прослушивателя.

>[!IMPORTANT]
>Для выпуска SQL Server 2017 единственный поддерживаемый способ проверки подлинности для конечной точки с зеркальным отображения базы данных — `CERTIFICATE`. Параметр `WINDOWS` будет включен в будущем выпуске.

Дополнительные сведения см. в разделе [базы данных конечной точки зеркального отображения (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
