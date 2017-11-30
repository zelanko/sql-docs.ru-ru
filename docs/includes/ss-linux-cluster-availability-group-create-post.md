
## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных в группу доступности

Убедитесь, что находится в режиме полного восстановления базы данных, добавляемых в группу доступности и резервное копирование журнала допустимым. Если это тестовую базу данных или вновь созданную базу данных, резервное копирование базы данных. На основном сервере SQL, запустите следующий сценарий Transact-SQL для создания и резервного копирования база данных с именем `db1`:

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

В первичной реплике SQL Server, запустите следующий сценарий Transact-SQL, чтобы добавить базу данных с именем `db1` чтобы группы доступности с именем `ag1`:

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Убедитесь, что база данных создана на вторичных серверах.

Во вторичной реплике SQL Server, выполните следующий запрос ли `db1` база данных была создана и синхронизирована:

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
