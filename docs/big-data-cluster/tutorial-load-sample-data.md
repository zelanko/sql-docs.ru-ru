---
title: Загрузка примера данных
titleSuffix: SQL Server big data clusters
description: В этом руководстве показано, как загрузить демонстрационные данные в SQL Server кластер больших данных. Образец данных включает в себя реляционные данные в экземпляре SQL Server master. Он также включает в себя данные HDFS в пуле носителей. Эти данные поддерживают другие учебники в этом разделе.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5b35eccece4df47cb483932386cf6a38e45d2dc8
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419277"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Учебник. Загрузка демонстрационных данных в SQL Server кластер больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом учебнике объясняется, как использовать сценарий для загрузки демонстрационных данных в кластер больших данных SQL Server 2019 (Предварительная версия). Многие другие учебники в документации используют этот образец данных.

> [!TIP]
> Дополнительные примеры для кластера больших данных SQL Server 2019 (Предварительная версия) можно найти в репозитории GitHub [SQL-Server-Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) . Они находятся в папке **SQL-Server-Samples/Samples/Features/SQL-Big-Data-Cluster/** Path.

## <a name="prerequisites"></a>предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Инструменты для обработки больших данных](deploy-big-data-tools.md)
   - **аздата**
   - **kubectl**
   - **sqlcmd**
   - **листывания**

## <a id="sampledata"></a>Загрузить образец данных

Следующие шаги используются для загрузки резервной копии базы данных SQL Server и загрузки данных в кластер больших данных с помощью скрипта начальной загрузки. Чтобы упростить использование, эти действия были разбиты на разделы [Windows](#windows) и [Linux](#linux) .

## <a id="windows"></a>Windows

Следующие шаги описывают использование клиента Windows для загрузки образца данных в кластер больших данных.

1. Откройте новую командную строку Windows.

   > [!IMPORTANT]
   > Не используйте Windows PowerShell для выполнения этих действий. В PowerShell выполнение скрипта завершится ошибкой, так как в нем будет использоваться версия, используемая в **PowerShell.**

1. Используйте **фигурную скобку** , чтобы скачать скрипт начальной загрузки для образца данных.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Скачайте скрипт Transact-SQL **бутстрап-сампле-дБ. SQL** . Этот скрипт вызывается скриптом начальной загрузки.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Для скрипта начальной загрузки требуются следующие параметры для кластера больших данных:

   | Параметр | Описание |
   |---|---|
   | < CLUSTER_NAMESPACE > | Имя, присвоенное кластеру больших данных. |
   | < SQL_MASTER_IP > | IP-адрес главного экземпляра. |
   | <SQL_MASTER_SA_PASSWORD> | Пароль SA для главного экземпляра. |
   | <KNOX_IP> | IP-адрес шлюза HDFS/Spark. |
   | < KNOX_PASSWORD > | Пароль для шлюза HDFS/Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md) , чтобы найти IP-адреса для экземпляра SQL Server master и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и просмотрите внешние IP-адреса для главного экземпляра (**master-SVC-External**) и Knox (**шлюз-SVC-External**). Имя кластера по умолчанию — **MSSQL-Cluster**.

1. Запустите скрипт начальной загрузки.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a>Linux

Следующие шаги описывают использование клиента Linux для загрузки образца данных в кластер больших данных.

1. Скачайте скрипт начальной загрузки и назначьте ему разрешения исполняемого файла.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Скачайте скрипт Transact-SQL **бутстрап-сампле-дБ. SQL** . Этот скрипт вызывается скриптом начальной загрузки.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Для скрипта начальной загрузки требуются следующие параметры для кластера больших данных:

   | Параметр | Описание |
   |---|---|
   | < CLUSTER_NAMESPACE > | Имя, присвоенное кластеру больших данных. |
   | < SQL_MASTER_IP > | IP-адрес главного экземпляра. |
   | <SQL_MASTER_SA_PASSWORD> | Пароль SA для главного экземпляра. |
   | <KNOX_IP> | IP-адрес шлюза HDFS/Spark. |
   | < KNOX_PASSWORD > | Пароль для шлюза HDFS/Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md) , чтобы найти IP-адреса для экземпляра SQL Server master и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и просмотрите внешние IP-адреса для главного экземпляра (**master-SVC-External**) и Knox (**шлюз-SVC-External**). Имя кластера по умолчанию — **MSSQL-Cluster**.

1. Запустите скрипт начальной загрузки.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Следующие шаги

После запуска скрипта начальной загрузки кластер больших данных будет иметь образцы баз данных и данные HDFS. В следующих учебниках используются образцы данных для демонстрации возможностей кластера больших данных.

Виртуализация данных:

- [Учебник. Запрос HDFS в SQL Server кластере больших данных](tutorial-query-hdfs-storage-pool.md)
- [Учебник. Запрос Oracle из SQL Server кластера больших данных](tutorial-query-oracle.md)

Прием данных:

- [Учебник. Прием данных в пул данных SQL Server с помощью Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Учебник. Прием данных в пул данных SQL Server с помощью заданий Spark](tutorial-data-pool-ingest-spark.md)

Компьютеры

- [Учебник. Запуск примера записной книжки в кластере больших данных SQL Server 2019](tutorial-notebook-spark.md)