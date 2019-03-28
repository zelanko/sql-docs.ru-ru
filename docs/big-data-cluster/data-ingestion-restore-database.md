---
title: Восстановление базы данных
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье показано, как восстановить базу данных на основной экземпляр кластера SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 7b6f37f3e82b48a0c56e42cae63f898c3c1089fb
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513211"
---
# <a name="restore-a-database-into-the-sql-server-2019-big-data-cluster-master-instance"></a>Восстановление базы данных в основной экземпляр кластера SQL Server 2019 больших данных

В этой статье описывается, как восстановить существующую базу данных на основной экземпляр кластера SQL Server 2019 больших данных (Предварительная версия). Рекомендуется использовать резервное копирование, копирование и восстановление подход.

## <a name="backup-your-existing-database"></a>Создать резервную копию существующей базы данных

Во-первых создайте резервную копию существующей базы данных SQL Server из SQL Server на Windows или Linux. Используйте стандартные методики резервного копирования, с помощью Transact-SQL или с помощью средства, такие как SQL Server Management Studio (SSMS).

В этой статье показано, как восстановить базу данных AdventureWorks, но можно использовать любой резервной копии базы данных. 

> [!TIP]
> Резервное копирование AdventureWorks можно загрузить [здесь](https://www.microsoft.com/download/details.aspx?id=49502).

## <a name="copy-the-backup-file"></a>Скопируйте файл резервной копии

Скопируйте файл резервной копии в контейнер SQL Server в pod главного экземпляра кластера Kubernetes.

```bash
kubectl cp <path to .bak file> mssql-master-pool-0:/tmp -c mssql-server -n <name of your cluster>
```

Пример

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n clustertest
```

Затем убедитесь, что файл резервной копии был скопирован в контейнер pod.

```bash
kubectl exec -it mssql-master-pool-0 -n <name of your cluster> -c mssql-server -- bin/bash
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
  WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');

-- Create the SqlStoragePool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
BEGIN
  IF SERVERPROPERTY('ProductLevel') = 'CTP2.3'
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
  ELSE IF SERVERPROPERTY('ProductLevel') = 'CTP2.4'
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
END
GO
```

> [!NOTE]
> Необходимо будет выполнить эти сценарии установки только для базы данных, восстановленные из более ранних версиях SQL Server. При создании новой базы данных master экземпляра SQL Server, данные пула хранилища пула хранилища процедуры и уже настроены для вас.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. в разделе приведены общие:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
