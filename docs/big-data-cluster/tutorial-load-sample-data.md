---
title: Загрузка примера данных
titleSuffix: SQL Server big data clusters
description: В этом руководстве показано, как загрузить пример данных в кластер больших данных SQL Server. Пример данных включает в себя реляционные данные в основном экземпляре SQL Server. Он также включает в себя данные HDFS в пуле носителей. На этих данных основываются другие руководства в этом разделе.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5b35eccece4df47cb483932386cf6a38e45d2dc8
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419277"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Руководство. Загрузка примера данных в кластер больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Это руководство описывает, как использовать скрипт для загрузки примера данных в кластер больших данных SQL Server 2019 (предварительная версия). Этот пример данных используется во многих других руководствах в этой документации.

> [!TIP]
> Дополнительные примеры для кластера больших данных SQL Server 2019 (предварительная версия) можно найти в репозитории [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) GitHub. Путь к ним: **sql-server-samples/samples/features/sql-big-data-cluster/** .

## <a name="prerequisites"></a>предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a> Загрузка примера данных

В следующих шагах используется скрипт начальной загрузки для скачивания резервной копии базы данных SQL Server и загрузки этих данных в ваш кластер больших данных. Чтобы упростить работу, эти действия были разнесены по разделам для [Windows](#windows) и [Linux](#linux).

## <a id="windows"></a> Windows

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
   | <SQL_MASTER_IP> | IP-адрес основного экземпляра. |
   | <SQL_MASTER_SA_PASSWORD> | Пароль SA для основного экземпляра. |
   | <KNOX_IP> | IP-адрес для шлюза HDFS/Spark. |
   | <KNOX_PASSWORD> | Пароль для шлюза HDFS/Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md), чтобы найти IP-адрес для основного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и просмотрите IP-адреса EXTERNAL для основного экземпляра (**master-svc-external**) и Knox (**gateway-svc-external**). Имя кластера по умолчанию — **mssql-cluster**.

1. Запустите скрипт начальной загрузки.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

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
   | <SQL_MASTER_IP> | IP-адрес основного экземпляра. |
   | <SQL_MASTER_SA_PASSWORD> | Пароль SA для основного экземпляра. |
   | <KNOX_IP> | IP-адрес для шлюза HDFS/Spark. |
   | <KNOX_PASSWORD> | Пароль для шлюза HDFS/Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md), чтобы найти IP-адрес для основного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и просмотрите IP-адреса EXTERNAL для основного экземпляра (**master-svc-external**) и Knox (**gateway-svc-external**). Имя кластера по умолчанию — **mssql-cluster**.

1. Запустите скрипт начальной загрузки.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Следующие шаги

После выполнения скрипта начальной загрузки кластер больших данных будет иметь примеры баз данных и данные HDFS. В следующих руководствах этот пример данных используется для демонстрации возможностей кластера больших данных.

Виртуализация данных

- [Учебник. Запрос данных HDFS в кластере больших данных SQL Server](tutorial-query-hdfs-storage-pool.md)
- [Учебник. Запрос данных Oracle из кластера больших данных SQL Server](tutorial-query-oracle.md)

Прием данных

- [Учебник. Прием данных в пул данных SQL Server с помощью Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Учебник. Прием данных в пул данных SQL Server с помощью заданий Spark](tutorial-data-pool-ingest-spark.md)

Записные книжки

- [Учебник. Запуск примера записной книжки в кластере больших данных SQL Server 2019](tutorial-notebook-spark.md)