
## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных к группе доступности

Убедитесь, добавляемого к группе доступности базы данных находится в режиме полного восстановления и резервное копирование журнала допустимым. Если это тестовую базу данных или создать новую базу данных, резервное копирование базы данных. На основном сервере SQL, запустите следующий скрипт Transact SQL для создания и резервного копирования база данных с именем `db1`.

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'var/opt/mssql/data/db1.bak';
```

В первичной реплике SQL Server, запустите следующий скрипт Transact SQL для добавления в базу данных с именем `db1` чтобы группы доступности с именем `ag1`.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Убедитесь, что база данных создается на серверах-получателях

Во вторичной реплике SQL Server, выполните следующий запрос ли `db1` базы данных будет создана и синхронизирована.

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
