---
title: "SQL Server принудительной отработки отказа для группы доступности"
description: "Принудительная отработка отказа для группы доступности с кластера тип NONE"
services: 
author: MikeRayMSFT
ms.service: 
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: 10a2af2cb5bc9e98605a3ee988439e3c3be60c1e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
Каждой группы Доступности имеется только одна первичная реплика. Первичная реплика позволяет выполнять операции чтения и записи. Чтобы изменить реплику, которая является основным, можно выполнить переход. В группе Доступности для обеспечения высокой доступности диспетчера кластеров автоматизирует процесс перехода на другой ресурс. В группе Доступности с кластера типа NONE процесс перехода на другой ресурс вручную. 

Отработку отказа первичной реплики в группе Доступности кластера типа NONE двумя способами.

- Принудительная отработка отказа вручную с потерей данных
- Отработка отказа вручную без потери данных

### <a name="forced-manual-failover-with-data-loss"></a>Принудительная отработка отказа вручную с потерей данных

Используйте этот метод, если первичная реплика недоступна и не может быть восстановлена. 

Принудительное переключение с потерей данных, подключитесь к экземпляру SQL Server, на котором размещается целевая вторичная реплика выполнения:

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-failover-without-data-loss"></a>Отработка отказа вручную без потери данных

Это метод можно использовать, если первичная реплика доступна, но необходимо временно или навсегда изменить конфигурацию и изменить экземпляр SQL Server, на котором размещена первичная реплика. Перед выполнением отработки отказа вручную, убедитесь в наличии в актуальном состоянии, чтобы избежать потенциальной потери данных в целевой вторичной реплике. 

Отработка отказа вручную без потери данных:

1. Убедитесь в целевой вторичной реплике `SYNCHRONOUS_COMMIT`.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Выполните следующий запрос, чтобы определить, что активные транзакции фиксируются для первичной реплики и по крайней мере одна реплика вторичной. 

   ```SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

   Вторичная реплика синхронизируется, если `synchronization_state_desc` имеет значение `SYNCHRONIZED`.

3. Обновление `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` значение 1.

   Следующий скрипт задает `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` в 1 группе Доступности с именем `ag1`. Прежде чем запускать следующий скрипт, замените `ag1` на имя вашей группы Доступности:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   Этот параметр обеспечивает стремится первичная реплика и хотя бы одна реплика вторичной каждой активной транзакции. 

4. Понижение роли первичной реплики на вторичную реплику. После понижения роли первичной реплики, он доступен только для чтения. Выполните следующую команду на экземпляре SQL Server, на котором размещена первичная реплика, для обновления роли `SECONDARY`:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

5. Повысьте уровень целевой вторичной реплики до первичной. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Чтобы удалить группу Доступности, используйте [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Введите для группы Доступности, созданных с помощью кластера нет или ВНЕШНИХ, команда должна выполняться на всех репликах, которые входят в группу доступности.