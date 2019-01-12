---
title: Загрузка образца данных
titleSuffix: SQL Server 2019 big data clusters
description: Этом руководстве показано, как Загрузка образца данных в кластер SQL Server больших данных. Пример данных содержит реляционные данные в основной экземпляр SQL Server. Она также включает данные из HDFS в пуле носителей. Эти данные поддерживает другие руководства в этом разделе.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: a89b1bec266f590d6e96365436fe5339b9152f92
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241485"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-2019-big-data-cluster"></a>Учебник. Загрузка образца данных в кластере SQL Server 2019 больших данных

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
   | &LT; CLUSTER_NAMESPACE &GT; | Имя присвоенное кластеру больших данных. |
   | &LT; SQL_MASTER_IP &GT; | IP-адрес главного экземпляра. |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | Пароль системного Администратора для главного экземпляра. |
   | &LT; KNOX_IP &GT; | IP-адрес шлюза HDFS или Spark. |
   | &LT; KNOX_PASSWORD &GT; | Пароль для шлюза HDFS или Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md) найти IP-адреса для главного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-cluster-name>` и посмотрите на внешний IP-адреса основной экземпляр (**конечной точки master-pool**) и Knox (**службы безопасности балансировки нагрузки** или **nodeport службы безопасности**).

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
   | &LT; CLUSTER_NAMESPACE &GT; | Имя присвоенное кластеру больших данных. |
   | &LT; SQL_MASTER_IP &GT; | IP-адрес главного экземпляра. |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | Пароль системного Администратора для главного экземпляра. |
   | &LT; KNOX_IP &GT; | IP-адрес шлюза HDFS или Spark. |
   | &LT; KNOX_PASSWORD &GT; | Пароль для шлюза HDFS или Spark. |

   > [!TIP]
   > Используйте [kubectl](cluster-troubleshooting-commands.md) найти IP-адреса для главного экземпляра SQL Server и Knox. Запустите `kubectl get svc -n <your-cluster-name>` и посмотрите на внешний IP-адреса основной экземпляр (**конечной точки master-pool**) и Knox (**службы безопасности балансировки нагрузки** или **nodeport службы безопасности**).

1. Скрипт начальной загрузки.

   ```bash
   ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Следующие шаги

После выполнения начальной загрузки сценария, кластер больших данных содержит образцы баз данных и данные из HDFS. Чтобы приступить к изучению этих данных и кластеры больших данных, см. в разделе [учебники](tutorial-query-hdfs-storage-pool.md) в этом разделе.