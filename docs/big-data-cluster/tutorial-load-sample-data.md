---
title: Загрузка примера данных
titleSuffix: SQL Server big data clusters
description: Этом руководстве показано, как Загрузка образца данных в кластер SQL Server больших данных. Пример данных содержит реляционные данные в основной экземпляр SQL Server. Она также включает данные из HDFS в пуле носителей. Эти данные поддерживает другие руководства в этом разделе.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d78fd9ecce71e9b7ffb86441fab134b1180d058a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66770825"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Учебник. Загрузка образца данных в кластер SQL Server больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Этом руководстве объясняется, как использовать скрипт для загрузки демонстрационных данных в кластере SQL Server 2019 больших данных (Предварительная версия). Во многих других учебников в документации используется следующий образец данных.

> [!TIP]
> Дополнительные примеры для кластера SQL Server 2019 больших данных (Предварительная версия) можно найти в [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) репозитория GitHub. Они находятся в **sql-server-samples/samples/features/sql-big-data-cluster/** путь.

## <a name="prerequisites"></a>предварительные требования

- [Кластер развернутой больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **mssqlctl**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a> Загрузка образца данных

Далее используется сценарий начальной загрузки для загрузки резервной копии базы данных SQL Server и загрузка данных в кластере больших данных. Для удобства использования, эти действия была выведена в [Windows](#windows) и [Linux](#linux) разделы.

## <a id="windows"></a> Windows

Ниже описано, как использовать клиент Windows для загрузки образца данных в кластере больших данных.

1. Откройте новую командную строку Windows.

   > [!IMPORTANT]
   > Не используйте Windows PowerShell для этих шагов. В PowerShell, скрипт завершится ошибкой, так как он будет использовать версии PowerShell **curl**.

1. Используйте **curl** для загрузки начальной загрузки скрипта для образца данных.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Скачайте **bootstrap пример db.sql** сценарий Transact-SQL. Этот сценарий вызывается с помощью начальной загрузки скрипта.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Загрузочный сценарий требует следующих позиционные параметры для больших данных кластера:

   | Параметр | Описание |
   |---|---|
   | <CLUSTER_NAMESPACE> | Имя присвоенное кластеру больших данных. |
   | <SQL_MASTER_IP> | IP-адрес главного экземпляра. |
   | <SQL_MASTER_SA_PASSWORD> | Пароль системного Администратора для главного экземпляра. |
   | <KNOX_IP> | IP-адрес шлюза HDFS или Spark. |
   | <KNOX_PASSWORD> | Пароль для шлюза HDFS или Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md) найти IP-адреса для главного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и посмотрите на внешний IP-адреса основной экземпляр (**master-svc-external**) и Knox (**шлюз svc-external**). Имя по умолчанию кластера — **mssql-cluster**.

1. Скрипт начальной загрузки.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

Ниже описывается использование клиента Linux для загрузки образца данных в кластере больших данных.

1. Скачайте загрузочный сценарий и назначить ей разрешение.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Скачайте **bootstrap пример db.sql** сценарий Transact-SQL. Этот сценарий вызывается с помощью начальной загрузки скрипта.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Загрузочный сценарий требует следующих позиционные параметры для больших данных кластера:

   | Параметр | Описание |
   |---|---|
   | <CLUSTER_NAMESPACE> | Имя присвоенное кластеру больших данных. |
   | <SQL_MASTER_IP> | IP-адрес главного экземпляра. |
   | <SQL_MASTER_SA_PASSWORD> | Пароль системного Администратора для главного экземпляра. |
   | <KNOX_IP> | IP-адрес шлюза HDFS или Spark. |
   | <KNOX_PASSWORD> | Пароль для шлюза HDFS или Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md) найти IP-адреса для главного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-big-data-cluster-name>` и посмотрите на внешний IP-адреса основной экземпляр (**master-svc-external**) и Knox (**шлюз svc-external**). Имя по умолчанию кластера — **mssql-cluster**.

1. Скрипт начальной загрузки.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Следующие шаги

После выполнения начальной загрузки сценария, кластер больших данных содержит образцы баз данных и данные из HDFS. Следующие учебники использовать образцы данных для демонстрации возможностей кластера больших данных:

Виртуализация данных.

- [Учебник. Запрос HDFS в кластере SQL Server больших данных](tutorial-query-hdfs-storage-pool.md)
- [Учебник. Запрос Oracle из больших данных кластера SQL Server](tutorial-query-oracle.md)

Прием данных:

- [Учебник. Прием данных в пул данных SQL Server с помощью Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Учебник. Прием данных в пул данных SQL Server с помощью заданий Spark](tutorial-data-pool-ingest-spark.md)

Записные книжки:

- [Учебник. Запуск записной книжки образец в кластере SQL Server 2019 больших данных](tutorial-notebook-spark.md)