---
title: Восстановление базы данных в кластер SQL Server больших данных | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 04514fb0184fa28e0ba959f3dd33cb2e1ec945cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796444"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Восстановление базы данных в основной экземпляр кластера SQL Server больших данных

Для переноса существующей базы данных SQL Server в основной экземпляр, мы рекомендуем использовать резервное копирование, копирование и восстановление подход.  В этом примере будет показано, как для восстановления базы данных AdventureWorks, но можно использовать любой резервной копии базы данных, у вас.  Резервное копирование AdventureWorks можно загрузить [здесь](https://www.microsoft.com/en-us/download/details.aspx?id=49502).

Во-первых создайте резервную копию существующей базы данных SQL Server в SQL Server на Windows или Linux, с помощью обычных методов создания резервной копии базы данных.

Скопируйте файл резервной копии в контейнер SQL Server в pod главного экземпляра кластера Kubernetes.

```bash
kubectl cp <path to .bak file> mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n <name of your cluster>
```

Пример

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n clustertest
```

Затем убедитесь, что файл резервной копии был скопирован в контейнер pod.

```bash
kubectl exec -it mssql-data-pool-master-0 -n <name of your cluster> -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
root@mssql-data-pool-master-0:/# exit
```

Пример

```bash
kubectl exec -it mssql-data-pool-master-0 -n clustertest -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
```

Затем восстановите резервную копию базы данных master экземпляра SQL Server.  При восстановлении резервной копии базы данных, который был создан в Windows, необходимо будет получить имена файлов.  В Ops Studio, подключенной к основной экземпляр выполните следующий сценарий SQL:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Пример

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Список резервных копий файлов](media/restore-database/database-restore-file-list.png)

Теперь восстановите базу данных с помощью сценария следующим образом, заменив при необходимости в зависимости от вашей резервной копии базы данных имена и пути.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

Теперь если требуется, чтобы базы данных большое значение иметь возможность доступа к пулы данных, необходимые для настройки пула данных хранимые процедуры, открыв и выполнив эти сценарии из репозитория GitHub.

Выполнение **высоким значением db configuration\data_pool_ddl_install. SQL** скрипта.

- Настройка поддержки хранимых процедур

Выполнение **высоким значением db configuration\supportability. SQL** скрипта.
