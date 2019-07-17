---
ms.openlocfilehash: 0cdc343bf4ea6866d1a55672187451a3b6d95ec1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215569"
---

## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных в группу доступности

Убедитесь, что база данных, добавляемая в группу доступности, находится в режиме полного восстановления и имеет действительную резервную копию журналов. Если база данных тестовая или только что создана, сделайте ее резервную копию. На первичной реплике SQL Server выполните следующий сценарий Transact-SQL, чтобы создать базу данных с именем `db1` и ее резервную копию.

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

На первичной реплике SQL Server выполните следующий сценарий Transact-SQL, чтобы добавить базу данных с именем `db1` в группу доступности с именем `ag1`.

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Убедитесь, что база данных создана на вторичных серверах.

На каждой вторичной реплике SQL Server выполните следующий запрос, чтобы убедиться, что база данных `db1` создана и синхронизирована.

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
