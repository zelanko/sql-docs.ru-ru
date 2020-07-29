---
title: Загрузка примера данных
titleSuffix: SQL Server big data clusters
description: В этом руководстве показано, как загрузить пример данных в кластер больших данных SQL Server. Пример данных включает в себя реляционные данные в основном экземпляре SQL Server. Он также включает в себя данные HDFS в пуле носителей. На этих данных основываются другие руководства в этом разделе.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8a4412c5b32b42074d760acbc162d5df56e0976f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772862"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Руководство по Загрузка примера данных в кластер больших данных SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Это руководство описывает, как использовать скрипт для загрузки примера данных в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Этот пример данных используется во многих других руководствах в этой документации.

> [!TIP]
> Дополнительные примеры для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] можно найти в репозитории [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) GitHub. Путь к ним: **sql-server-samples/samples/features/sql-big-data-cluster/** .

## <a name="prerequisites"></a>Предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**
 
## <a name="load-sample-data"></a><a id="sampledata"></a> Загрузка примера данных

В следующих шагах используется скрипт начальной загрузки для скачивания резервной копии базы данных SQL Server и загрузки этих данных в ваш кластер больших данных. Чтобы упростить работу, эти действия были разнесены по разделам для [Windows](#windows) и [Linux](#linux). Если вы хотите использовать простой механизм проверки подлинности по имени пользователя и паролю, настройте переменные среды AZDATA_USERNAME и AZDATA_PASSWORD перед выполнением скрипта. В противном случае скрипт будет использовать для подключения к главному экземпляру SQL Server и шлюзу Knox интегрированную проверку подлинности. Кроме того, для использования встроенной проверки подлинности нужно указать DNS-имена для конечных точек.

## <a name="windows"></a><a id="windows"></a> Windows

Следующие действия описывают использование клиента Windows для загрузки примера данных в кластер больших данных.

1. Откройте новую командную строку Windows.

   > [!IMPORTANT]
   > Не используйте Windows PowerShell для выполнения этих действий. В PowerShell этот скрипт завершится ошибкой, так как он будет использовать версию **curl** для PowerShell.

1. Используйте **curl**, чтобы скачать скрипт начальной загрузки для примера данных.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Скачайте скрипт **bootstrap-sample-db.sql** Transact-SQL. Этот скрипт вызывается скриптом начальной загрузки.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Скрипту начальной загрузки требуются следующие позиционные параметры для кластера больших данных.

   | Параметр | Описание |
   |---|---|
   | <CLUSTER_NAMESPACE> | Имя, присвоенное кластеру больших данных. |
   | <SQL_MASTER_ENDPOINT> | DNS-имя или IP-адрес главного экземпляра. |
   | <KNOX_ENDPOINT> | DNS-имя или IP-адрес шлюза HDFS/Spark. |
   
   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md), чтобы найти IP-адрес для основного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и просмотрите IP-адреса EXTERNAL для основного экземпляра (**master-svc-external**) и Knox (**gateway-svc-external**). Имя кластера по умолчанию — **mssql-cluster**.

1. Запустите скрипт начальной загрузки.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_ENDPOINT> <KNOX_ENDPOINT>
   ```

## <a name="linux"></a><a id="linux"></a> Linux

Следующие действия описывают использование клиента Linux для загрузки примера данных в кластер больших данных.

1. Скачайте скрипт начальной загрузки и назначьте ему разрешения исполняемого файла.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Скачайте скрипт **bootstrap-sample-db.sql** Transact-SQL. Этот скрипт вызывается скриптом начальной загрузки.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Скрипту начальной загрузки требуются следующие позиционные параметры для кластера больших данных.

   | Параметр | Описание |
   |---|---|
   | <CLUSTER_NAMESPACE> | Имя, присвоенное кластеру больших данных. |
   | <SQL_MASTER_ENDPOINT> | DNS-имя или IP-адрес главного экземпляра. |
   | <KNOX_ENDPOINT> | DNS-имя или IP-адрес шлюза HDFS/Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md), чтобы найти IP-адрес для основного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и просмотрите IP-адреса EXTERNAL для основного экземпляра (**master-svc-external**) и Knox (**gateway-svc-external**). Имя кластера по умолчанию — **mssql-cluster**.

1. Запустите скрипт начальной загрузки.

   ```bash
   ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_ENDPOINT> <KNOX_ENDPOINT>
   ```

## <a name="next-steps"></a>Дальнейшие действия

После выполнения скрипта начальной загрузки кластер больших данных будет иметь примеры баз данных и данные HDFS. В следующих руководствах этот пример данных используется для демонстрации возможностей кластера больших данных.

Виртуализация данных

- [Руководство. Запрос данных HDFS в кластере больших данных SQL Server](tutorial-query-hdfs-storage-pool.md)
- [Руководство. Запрос данных Oracle из кластера больших данных SQL Server](tutorial-query-oracle.md)

Прием данных

- [Руководство. Прием данных в пул данных SQL Server с помощью Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Руководство. Прием данных в пул данных SQL Server с помощью заданий Spark](tutorial-data-pool-ingest-spark.md)

Записные книжки

- [Руководство. Запуск примера записной книжки в кластере больших данных SQL Server 2019](notebooks-tutorial-spark.md)
