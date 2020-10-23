---
title: Устранение неполадок с записной книжкой `pyspark`
titleSuffix: SQL Server Big Data Cluster
description: Устранение неполадок с записной книжкой `pyspark`
author: DaniBunny
ms.author: dacoelho
ms.reviewer: mikeray
ms.date: 06/01/2020
ms.topic: how-to
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d631a74bc71c814a70ef0ecfa33485ee4631ccd4
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257082"
---
# <a name="troubleshoot-pyspark-notebook"></a>Устранение неполадок с записной книжкой `pyspark`

В этой статье показано, как устранить неполадки с записной книжкой `pyspark`.

## <a name="architecture-of-a-pyspark-job-under-azure-data-studio"></a>Архитектура задания PySpark в Azure Data Studio

Azure Data Studio взаимодействует с конечной точкой `livy` в кластере больших данных SQL Server. 

Конечная точка `livy` выдает команды `spark-submit` в кластере больших данных. Каждая команда `spark-submit` имеет параметр, указывающий YARN в качестве диспетчера кластерных ресурсов.

Чтобы эффективно устранять неполадки в сеансе PySpark, вы будете собирать и просматривать журналы в каждом слое: Livy, YARN и Spark.

Для выполнения действий по устранению неполадок необходимо следующее.

1. Установленная программа командной строки [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)] с конфигурацией для вашего кластера.
2. Знакомство с выполнением команд Linux и навыки устранения неполадок с помощью журналов.

## <a name="troubleshooting-steps"></a>Действия по устранению неполадок

1. Проверьте стек и сообщения об ошибках в `pyspark`.

   Извлеките идентификатор приложения из первой ячейки записной книжки. Используйте этот идентификатор приложения, чтобы изучить журналы `livy`, YARN и Spark. `SparkContext` использует этот идентификатор приложения YARN.

   :::image type="content" source="../big-data-cluster/media/troubleshoot-pyspark-notebook/1-failed-cell.png" alt-text="Ошибка в ячейке":::

1. Получите журналы.

   Изучите их с помощью команды `azdata bdc debug copy-logs`.

   В следующем примере выполняется подключение конечной точки кластера больших данных для копирования журналов. Перед выполнением обновите следующие значения в примере.
   - `<ip_address>`: конечная точка кластера больших данных.
   - `<username>`: имя пользователя кластера больших данных.
   - `<namespace>`: пространство имен Kubernetes для кластера.
   - `<folder_to_copy_logs>`: путь к локальной папке, в которую нужно скопировать журналы.

   ```console
   azdata login --auth basic --username <username> --endpoint https://<ip_address>:30080
   azdata bdc debug copy-logs -n <namespace> -d <folder_to_copy_logs>
   ```

   Пример выходных данных

   ```output
   <user>@<server>:~$ azdata bdc debug copy-logs -n <namespace> -d copy_logs
   Collecting the logs for cluster '<namespace>'.
   Collecting logs for containers...
   Creating an archive from logs-tmp/<namespace>.
   Log files are archived in /home/<user>/copy_logs/debuglogs-<namespace>-YYYYMMDD-HHMMSS.tar.gz.
   Creating an archive from logs-tmp/dumps.
   Log files are archived in /home/<user>/copy_logs/debuglogs-<namespace>-YYYYMMDD-HHMMSS-dumps.tar.gz.
   Collecting the logs for cluster 'kube-system'.
   Collecting logs for containers...
   Creating an archive from logs-tmp/kube-system.
   Log files are archived in /home/<user>/copy_logs/debuglogs-kube-system-YYYYMMDD-HHMMSS.tar.gz.
   Creating an archive from logs-tmp/dumps.
   Log files are archived in /home/<user>/copy_logs/debuglogs-kube-system-YYYYMMDD-HHMMSS-dumps.tar.gz.
   ```

1. Просмотрите журналы Livy. Журналы Livy находятся в папке `<namespace>\sparkhead-0\hadoop-livy-sparkhistory\supervisor\log`.

   - Найдите идентификатор приложения YARN из первой ячейки записной книжки pyspark.
   - Найдите состояние `ERR`.
   
   Пример журнала Livy с состоянием `YARN ACCEPTED` Livy отправляет приложение Yarn.

   ```output
   HH:MM:SS INFO utils.LineBufferedStream: YYY-MM-DD HH:MM:SS INFO impl.YarnClientImpl: Submitted application application_<application_id>
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream: YYY-MM-DD HH:MM:SS INFO yarn.Client: Application report for application_<application_id> (state: ACCEPTED)
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream: YYY-MM-DD HH:MM:SS INFO yarn.Client: 
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      client token: N/A
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      diagnostics: N/A
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      ApplicationMaster host: N/A
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      ApplicationMaster RPC port: -1
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      queue: default
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      start time: ############
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      final status: UNDEFINED
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      tracking URL: https://sparkhead-1.fnbm.corp:8090/proxy/application_<application_id>/
   YY/MM/DD HH:MM:SS INFO utils.LineBufferedStream:      user: <account>
   ```

1. Изучите пользовательский интерфейс YARN

   Получите URL-адрес конечной точки YARN из панели мониторинга кластера больших данных Azure Data Studio или запустите `azdata bdc endpoint list –o table`.

   Пример:

   ```console
   azdata bdc endpoint list -o table
   ```

   Результаты

   ```output
   Description                                             Endpoint                                                          Name                        Protocol
   ------------------------------------------------------  ----------------------------------------------------------------  --------------------------  ----------
   Gateway to access HDFS files, Spark                     https://knox.<namespace-value>.local:30443                               gateway                     https
   Spark Jobs Management and Monitoring Dashboard          https://knox.<namespace-value>.local:30443/gateway/default/sparkhistory  spark-history               https
   Spark Diagnostics and Monitoring Dashboard              https://knox.<namespace-value>.local:30443/gateway/default/yarn          yarn-ui                     https
   Application Proxy                                       https://proxy.<namespace-value>.local:30778                              app-proxy                   https
   Management Proxy                                        https://bdcmon.<namespace-value>.local:30777                             mgmtproxy                   https
   Log Search Dashboard                                    https://bdcmon.<namespace-value>.local:30777/kibana                      logsui                      https
   Metrics Dashboard                                       https://bdcmon.<namespace-value>.local:30777/grafana                     metricsui                   https
   Cluster Management Service                              https://bdcctl.<namespace-value>.local:30080                             controller                  https
   SQL Server Master Instance Front-End                    sqlmaster.<namespace-value>.local,31433                                  sql-server-master           tds
   SQL Server Master Readable Secondary Replicas           sqlsecondary.<namespace-value>.local,31436                               sql-server-master-readonly  tds
   HDFS File System Proxy                                  https://knox.<namespace-value>.local:30443/gateway/default/webhdfs/v1    webhdfs                     https
   Proxy for running Spark statements, jobs, applications  https://knox.<namespace-value>.local:30443/gateway/default/livy/v1       livy                        https
   ```

1. Проверьте идентификатор приложения и отдельные журналы application_master и журналы контейнеров.

   :::image type="content" source="media/troubleshoot-pyspark-notebook/15-hadoop-dashboard.png" alt-text="Ошибка в ячейке":::

1. Просмотрите журналы приложения YARN.

   Получите журнал приложения. Используйте `kubectl` для подключения к модулю pod `sparkhead-0`, например:
   
   ```console
   kubectl exec -it sparkhead-0 -- /bin/bash
   ```
      
   Затем выполните следующую команду в этой оболочке, указав правильное значение `application_id`.

   ```console
   yarn logs -applicationId application_<application_id>
   ```

1. Поищите ошибки или стеки.

   Пример ошибки разрешений для HDFS. В стеке Java найдите элемент `Caused by:`.

   ```output
   YYYY-MM-DD HH:MM:SS,MMM ERROR spark.SparkContext: Error initializing SparkContext.
   org.apache.hadoop.security.AccessControlException: Permission denied: user=<account>, access=WRITE, inode="/system/spark-events":sph:<bdc-admin>:drwxr-xr-x
        at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.check(FSPermissionChecker.java:399)
        at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkPermission(FSPermissionChecker.java:255)
        at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkPermission(FSPermissionChecker.java:193)
        at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:1852)
        at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:1836)
        at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkAncestorAccess(FSDirectory.java:1795)
        at org.apache.hadoop.hdfs.server.namenode.FSDirWriteFileOp.resolvePathForStartFile(FSDirWriteFileOp.java:324)
        at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.startFileInt(FSNamesystem.java:2504)
        at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.startFileChecked(FSNamesystem.java:2448)
   
   Caused by: org.apache.hadoop.ipc.RemoteException(org.apache.hadoop.security.AccessControlException): Permission denied: user=<account>, access=WRITE, inode="/system/spark-events":sph:<bdc-admin>:drwxr-xr-x
   ```

1. Изучите пользовательский интерфейс SPARK.

   :::image type="content" source="media/troubleshoot-pyspark-notebook/30-spark-ui.png" alt-text="Ошибка в ячейке":::

   Детализируйте задачи этапов в поисках ошибок.

## <a name="next-steps"></a>Дальнейшие действия

[Устранение неполадок при интеграции кластера больших данных SQL Server с Active Directory](troubleshoot-active-directory.md)