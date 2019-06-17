---
title: Восстановление базы данных
titleSuffix: SQL Server big data clusters
description: В этой статье показано, как восстановить базу данных на основной экземпляр кластера SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d69476548d405ff9b04a010c76241c1f15934778
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66797951"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Восстановление базы данных в основной экземпляр кластера SQL Server больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как восстановить существующую базу данных на основной экземпляр кластера SQL Server 2019 больших данных (Предварительная версия). Рекомендуется использовать резервное копирование, копирование и восстановление подход.

## <a name="backup-your-existing-database"></a>Создать резервную копию существующей базы данных

Во-первых создайте резервную копию существующей базы данных SQL Server из SQL Server на Windows или Linux. Используйте стандартные методики резервного копирования, с помощью Transact-SQL или с помощью средства, такие как SQL Server Management Studio (SSMS).

В этой статье показано, как восстановить базу данных AdventureWorks, но можно использовать любой резервной копии базы данных. 

> [!TIP]
> Резервное копирование AdventureWorks можно загрузить [здесь](https://www.microsoft.com/download/details.aspx?id=49502).

## <a name="copy-the-backup-file"></a>Скопируйте файл резервной копии

Скопируйте файл резервной копии в контейнер SQL Server в pod главного экземпляра кластера Kubernetes.

```bash
kubectl cp <path to .bak file> mssql-master-pool-0:/tmp -c mssql-server -n <name of your big data cluster>
```

Пример

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n clustertest
```

Затем убедитесь, что файл резервной копии был скопирован в контейнер pod.

```bash
kubectl exec -it mssql-master-pool-0 -n <name of your big data cluster> -c mssql-server -- bin/bash
cd /var/
ls /tmp
exit
```

Пример

```bash
kubectl exec -it mssql-master-pool-0 -n clustertest -c mssql-server -- bin/bash
ls /tmp
exit
```

## <a name="restore-the-backup-file"></a>Восстановить файл резервной копии

Затем восстановите резервную копию базы данных master экземпляра SQL Server.  При восстановлении резервной копии базы данных, который был создан в Windows, необходимо будет получить имена файлов.  В Azure Data Studio подключитесь к основной экземпляр и запустите этот скрипт SQL:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Пример

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Список резервных копий файлов](media/restore-database/database-restore-file-list.png)

Теперь восстановите базу данных. Следующий сценарий является примером. Замените имена и пути при необходимости в зависимости от вашей резервной копии базы данных.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

## <a name="configure-data-pool-and-hdfs-access"></a>Настроить пул данных и доступа к HDFS

Теперь для экземпляра SQL Server master пулы данных access и HDFS, выполните данных пул и дисковое пула хранимой процедуры. Выполните следующие скрипты Transact-SQL в только что восстановленной базе данных:

```sql
USE AdventureWorks2016CTP3
GO
-- Create the SqlDataPool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
  CREATE EXTERNAL DATA SOURCE SqlDataPool
  WITH (LOCATION = 'sqldatapool://controller-svc:8080/datapools/default');

-- Create the SqlStoragePool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   CREATE EXTERNAL DATA SOURCE SqlStoragePool
   WITH (LOCATION = 'sqlhdfs://controller-svc:8080/default');
GO
```

> [!NOTE]
> Необходимо будет выполнить эти сценарии установки только для базы данных, восстановленные из более ранних версиях SQL Server. При создании новой базы данных master экземпляра SQL Server, данные пула хранилища пула хранилища процедуры и уже настроены для вас.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. в разделе приведены общие:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
