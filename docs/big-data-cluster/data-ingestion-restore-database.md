---
title: Восстановление базы данных
titleSuffix: SQL Server big data clusters
description: В этой статье показано, как восстановить базу данных на главном экземпляре [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bad1a62752dd75e181d30c28485e1c9b707aa888
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652238"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Восстановление базы данных на главном экземпляре кластера больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как восстановить существующую базу данных на главном экземпляре [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Рекомендуется использовать метод резервного копирования, копирования и восстановления.

## <a name="backup-your-existing-database"></a>Создайте резервную копию существующей базы данных.

Сначала создайте резервную копию существующей базы данных SQL Server на Windows или Linux. Используйте стандартные методы резервного копирования с помощью Transact-SQL или с помощью такого средства, как SQL Server Management Studio (SSMS).

В этой статье показано, как восстановить базу данных AdventureWorks, но можно использовать резервную копию любой базы данных. 

> [!TIP]
> Вы можете скачать резервную копию AdventureWorks [здесь](https://www.microsoft.com/download/details.aspx?id=49502).

## <a name="copy-the-backup-file"></a>Копирование файла резервной копии

Скопируйте файл резервной копии в контейнер SQL Server в модуле Pod главного экземпляра кластера Kubernetes.

```bash
kubectl cp <path to .bak file> master-0:/tmp -c mssql-server -n <name of your big data cluster>
```

Пример

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n clustertest
```

Затем убедитесь, что файл резервной копии скопирован в контейнер Pod.

```bash
kubectl exec -it master-0 -n <name of your big data cluster> -c mssql-server -- bin/bash
cd /var/
ls /tmp
exit
```

Пример

```bash
kubectl exec -it master-0 -n clustertest -c mssql-server -- bin/bash
ls /tmp
exit
```

## <a name="restore-the-backup-file"></a>Восстановление файла резервной копии

Затем восстановите резервную копию базы данных в главном экземпляре SQL Server.  При восстановлении резервной копии базы данных, созданной в Windows, необходимо будет получить имена файлов.  В Azure Data Studio установите подключение к главному экземпляру и запустите следующий скрипт SQL:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Пример

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Список файлов резервной копии](media/restore-database/database-restore-file-list.png)

Теперь проведите восстановление базы данных. Следующий скрипт — это пример. При необходимости замените имена и пути в зависимости от вашей резервной копии базы данных.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

## <a name="configure-data-pool-and-hdfs-access"></a>Настройка пула данных и доступа HDFS

Теперь, чтобы главный экземпляр SQL Server обращался к пулам данных и HDFS, запустите хранимые процедуры пула данных и пула носителей. Выполните следующие скрипты Transact-SQL во вновь восстановленной базе данных:

```sql
USE AdventureWorks2016CTP3
GO
-- Create the SqlDataPool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
  CREATE EXTERNAL DATA SOURCE SqlDataPool
  WITH (LOCATION = 'sqldatapool://controller-svc/default');

-- Create the SqlStoragePool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   CREATE EXTERNAL DATA SOURCE SqlStoragePool
   WITH (LOCATION = 'sqlhdfs://controller-svc/default');
GO
```

> [!NOTE]
> Эти скрипты установки требуется выполнять только для баз данных, восстановленных из более старых версий SQL Server. Если вы создаете новую базу данных в главном экземпляре SQL Server, то для вас уже настроены хранимые процедуры пула данных и пула носителей.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующем обзоре:

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
