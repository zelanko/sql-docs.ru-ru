---
title: Заметки о выпуске
titleSuffix: SQL Server big data clusters
description: В этой статье описываются последние обновления и известные проблемы для кластеров SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/28/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 3c999d82df4e8b73e290456ad5d3601712747ef9
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860534"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Заметки о выпуске для кластеров больших данных в SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье перечислены обновления и известные проблемы для последних выпусков кластеров больших данных в SQL Server.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp24"></a> CTP 2.4 (март)

Новые возможности и известные проблемы с кластерами больших данных в SQL Server 2019 CTP 2.4 в следующих разделах.

### <a name="whats-new"></a>What's New

| Новые средства или обновления | Сведения |
|:---|:---|
| Руководство по использованию GPU для выполнения глубокого обучения с помощью библиотеки TensorFlow в Spark. | [Развертывание кластера больших данных с поддержкой GPU и запустите TensorFlow](spark-gpu-tensorflow.md). |
| **SqlDataPool** и **SqlStoragePool** источники данных больше не создаются по умолчанию. | Создайте их вручную, при необходимости. См. в разделе [известные проблемы](#externaltablesctp24). |
| Поддержка `INSERT INTO SELECT` для пула данных. | Например, см. в разделе [руководства: Прием данных в пул данных SQL Server с помощью Transact-SQL](tutorial-data-pool-ingest-sql.md). |
| `FORCE SCALEOUTEXECUTION` и `DISABLE SCALEOUTEXECUTION` параметр. | Принудительно или отключает использование вычислительных ресурсов пула для запросов во внешних таблицах. Например, `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`. |
| Обновленные рекомендации по развертыванию AKS. | В ходе анализа больших данных кластеров в AKS, теперь рекомендуется использовать один узел размера **Standard_L8s**. |
| Обновление среды выполнения Spark до версии Spark 2.4. | |

### <a name="known-issues"></a>Известные проблемы

Известные проблемы и ограничения в выпуске в следующих разделах.

#### <a name="deployment"></a>Развертывание

- Обновление данных кластерам больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Необходимо создать резервную копию данных и удалите существующего кластера больших данных (с помощью предыдущей версии **mssqlctl**) перед развертыванием в последнем выпуске. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

- После развертывания в AKS, могут появиться следующие два события-предупреждения из развертывания. Оба эти события перечислены известные проблемы, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Если происходит сбой развертывания кластера больших данных, связанное пространство имен не удаляется. В итоге потерянные пространством имен в кластере. Обойти это можно вручную удалить пространство имен перед развертыванием кластера с тем же именем.

#### <a name="kubeadm-deployments"></a>kubeadm развертываний

Если вы используете kubeadm для развертывания Kubernetes на нескольких компьютерах, на портале администрирования кластера отображаться неправильно конечные точки, необходимые для подключения к кластеру больших данных. При возникновении этой проблемы, воспользуйтесь следующей решение проблемы, чтобы узнать IP-адреса конечной точки службы.

- Если вы подключаетесь из кластера, запрашивать IP-адрес службы для конечной точки, которую вы хотите подключиться к Kubernetes. Например, следующая **kubectl** команда отображает IP-адрес главного экземпляра SQL Server:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Если вы подключаетесь из за пределов кластера, следуйте инструкциям ниже для подключения:

   1. Получить IP-адрес узла под управлением главного экземпляра SQL Server: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Подключитесь к экземпляру SQL Server master, используя этот IP-адрес.

   1. Запрос **cluster_endpoint_table** в базе данных master для других внешних конечных точек.

      Если время ожидания подключения, возможна брандмауэр соответствующем узле. В этом случае необходимо обратитесь к администратору кластера Kubernetes и попросить для IP-адреса узла, который предоставляется наружу. Это может быть любой узел. Затем можно использовать этот IP-адрес и соответствующий порт для подключения к различным службам, запущенных в кластере. Например администратор может найти этот IP-адрес, выполнив:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Удаление кластера происходит сбой

При попытке удалить кластер с **mssqlctl**, она завершается сбоем со следующей ошибкой:

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

Новый клиент Python Kubernetes (версия 9.0.0) изменен удаления пространства имен API, который в данный момент запрещает **mssqlctl**. Это происходит только при наличии более новой версии клиента python Kubernetes установлен. Эту проблему можно обойти, непосредственно удалив кластер с помощью **kubectl** (`kubectl delete ns <ClusterName>`), или можно установить более старой версией с помощью `sudo pip install kubernetes==8.0.1`.

#### <a id="externaltablesctp24"></a> Внешние таблицы

- Развертывание кластера больших данных больше не создает **SqlDataPool** и **SqlStoragePool** внешних источников данных. Можно создать эти источники данных вручную для поддержки виртуализации данных к пулу данных и пула носителей.

   ```sql
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
   ```

- Это позволяет создать внешнюю таблицу пула данных для таблицы, которая имеет неподдерживаемые типы столбцов. При выполнении запроса внешней таблицы, вы получите сообщение следующего вида:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Если базовый файл копируется в HDFS в то же время при выполнении запроса внешней таблицы пула хранения, может появиться ошибка.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы к базе данных Oracle, использовать символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. В результате сбоя в язык DDL внешней таблицы. Измените схемы Oracle для NVARCHAR2 на типе, или вручную создайте инструкций ВНЕШНЕЙ таблицы, укажите NVARCHAR, а не с помощью мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из RESTful API, вызов истечет время ожидания в течение 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адресом МОДУЛЯ адреса могут измениться в среде Kubernetes, время перезагрузки модулей POD. В сценарии, где перезапускает master-pod, сеанс Spark может произойти сбой с `NoRoteToHostException`. Это связано с виртуальной машины Java кэшей, не обновляется с помощью нового IP-адреса адреса.

- Если у вас есть Jupyter уже установлен и отдельные Python в Windows, записные книжки Spark может завершиться ошибкой. Чтобы обойти эту проблему, обновите Jupyter до последней версии.

- В записной книжке, если щелкнуть **добавить текст** команды ячейку текст добавляется в режиме предварительного просмотра, а не в режиме редактирования. Можно щелкнуть значок предварительного просмотра, чтобы переключиться в режим правки и изменять ячейки.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в файловой системе HDFS, чтобы сделать это, может появиться следующая ошибка:

   `Error previewing file: File exceeds max size of 30MB`

   В настоящее время нет способа для предварительного просмотра файлов, размер которых превышает 30 МБ студии данных Azure.

- Изменения конфигурации HDFS, влечет за собой изменения hdfs-site.xml не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и доступными (например, в файл дампа кабель). После развертывания, необходимо сбросить SA_PASSWORD на основной экземпляр. Это не ошибка, но шаг по обеспечению безопасности. Дополнительные сведения о способах изменения SA_PASSWORD в контейнере Linux, см. в разделе [Смена пароля Администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS журналы могут содержать пароль системного Администратора для развертывания кластера больших данных.

## <a id="ctp23"></a> CTP-версии 2.3 (февраль)

Новые возможности и известные проблемы с кластерами больших данных в SQL Server 2019 CTP 2.3 в следующих разделах.

### <a name="whats-new"></a>What's New

| Новые средства или обновления | Сведения |
| :---------- | :------ |
| Отправка заданий Spark в кластерах больших данных в IntelliJ. | [Отправка заданий Spark в кластерах больших данных SQL Server в IntelliJ](spark-submit-job-intellij-tool-plugin.md) |
| Общий интерфейс командной строки для приложения развертывания и управления кластерами. | [Развертывание приложения в кластере SQL Server 2019 больших данных (Предварительная версия)](big-data-cluster-create-apps.md) |
| Расширение VS Code для развертывания приложений в кластер больших данных. | [Как использовать VS Code для развертывания приложений к кластерам больших данных в SQL Server](app-deployment-extension.md) |
| Изменения в **mssqlctl** средство об использовании команды. | Дополнительные сведения см. [известные проблемы для mssqlctl](#mssqlctlctp23). |
| Использовать Sparklyr в кластере больших данных | [Использовать Sparklyr в кластере SQL Server 2019 больших данных](sparklyr-from-RStudio.md) |
| Подключение внешнего HDFS-совместимого хранилища к кластеру больших данных с **распределением HDFS по уровням**. | См. в разделе [распределение по уровням HDFS](hdfs-tiering.md). |
| Новые возможности единой подключения для главного экземпляра SQL Server и шлюза HDFS или Spark. | См. в разделе [главного экземпляра SQL Server и шлюза HDFS/Spark](connect-to-big-data-cluster.md). |
| При удалении кластера с **удаления кластера mssqlctl** теперь удаляет только объекты в пространстве имен, которые были частью кластера больших данных. | Пространство имен не удаляется. Однако в более ранних выпусках эта команда был удален всего пространства имен. |
| _Безопасность_ имена конечных точек была изменена и консолидации. | **службы безопасности балансировки нагрузки** и **службы безопасности nodeport** были объединены в **безопасности конечных точек** конечной точки. |
| _Прокси-сервера_ имена конечных точек была изменена и консолидации. | **Служба прокси-сервер балансировки нагрузки** и **службы, прокси-сервера, nodeport** были объединены в **конечная точка службы прокси-сервера** конечной точки. |
| _Контроллер_ имена конечных точек была изменена и консолидации. | **Служба mssql контроллера lb** и **служба mssql контроллера nodeport** были объединены в **конечной точки контроллера** конечную точку. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Известные проблемы

Известные проблемы и ограничения в выпуске в следующих разделах.

#### <a name="deployment"></a>Развертывание

- Обновление данных кластерам больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Необходимо создать резервную копию данных и удалите существующего кластера больших данных (с помощью предыдущей версии **mssqlctl**) перед развертыванием в последнем выпуске. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

- **ACCEPT_EULA** переменной среды должен быть «yes» или «Да», чтобы принять условия лицензионного соглашения. Предыдущие выпуски разрешены «y» и «Y», но они больше не принимаются и приведет к сбою развертывания.

- **CLUSTER_PLATFORM** переменные среды не имеет значения по умолчанию, как в предыдущих выпусках.

- После развертывания в AKS, могут появиться следующие два события-предупреждения из развертывания. Оба эти события перечислены известные проблемы, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Если происходит сбой развертывания кластера больших данных, связанное пространство имен не удаляется. В итоге потерянные пространством имен в кластере. Обойти это можно вручную удалить пространство имен перед развертыванием кластера с тем же именем.

#### <a name="kubeadm-deployments"></a>kubeadm развертываний

Если вы используете kubeadm для развертывания Kubernetes на нескольких компьютерах, на портале администрирования кластера отображаться неправильно конечные точки, необходимые для подключения к кластеру больших данных. При возникновении этой проблемы, воспользуйтесь следующей решение проблемы, чтобы узнать IP-адреса конечной точки службы.

- Если вы подключаетесь из кластера, запрашивать IP-адрес службы для конечной точки, которую вы хотите подключиться к Kubernetes. Например, следующая **kubectl** команда отображает IP-адрес главного экземпляра SQL Server:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Если вы подключаетесь из за пределов кластера, следуйте инструкциям ниже для подключения:

   1. Получить IP-адрес узла под управлением главного экземпляра SQL Server: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Подключитесь к экземпляру SQL Server master, используя этот IP-адрес.

   1. Запрос **cluster_endpoint_table** в базе данных master для других внешних конечных точек.

      Если время ожидания подключения, возможна брандмауэр соответствующем узле. В этом случае необходимо обратитесь к администратору кластера Kubernetes и попросить для IP-адреса узла, который предоставляется наружу. Это может быть любой узел. Затем можно использовать этот IP-адрес и соответствующий порт для подключения к различным службам, запущенных в кластере. Например администратор может найти этот IP-адрес, выполнив:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="mssqlctlctp23"></a> mssqlctl

- **Mssqlctl** изменился инструмент из команды глагол существительное, упорядочение с заказом глагол существительное. Например `mssqlctl create cluster` теперь `mssqlctl cluster create`.

- `--name` Теперь является параметр требуется при создании кластера с `mssqlctl cluster create`.

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- Важные сведения об обновлении до последней версии кластеров больших данных и **mssqlctl**, см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

#### <a name="external-tables"></a>Внешние таблицы

- Это позволяет создать внешнюю таблицу пула данных для таблицы, которая имеет неподдерживаемые типы столбцов. При выполнении запроса внешней таблицы, вы получите сообщение следующего вида:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Если базовый файл копируется в HDFS в то же время при выполнении запроса внешней таблицы пула хранения, может появиться ошибка.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы к базе данных Oracle, использовать символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. В результате сбоя в язык DDL внешней таблицы. Измените схемы Oracle для NVARCHAR2 на типе, или вручную создайте инструкций ВНЕШНЕЙ таблицы, укажите NVARCHAR, а не с помощью мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из RESTful API, вызов истечет время ожидания в течение 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адресом МОДУЛЯ адреса могут измениться в среде Kubernetes, время перезагрузки модулей POD. В сценарии, где перезапускает master-pod, сеанс Spark может произойти сбой с `NoRoteToHostException`. Это связано с виртуальной машины Java кэшей, не обновляется с помощью нового IP-адреса адреса.

- Если у вас есть Jupyter уже установлен и отдельные Python в Windows, записные книжки Spark может завершиться ошибкой. Чтобы обойти эту проблему, обновите Jupyter до последней версии.

- В записной книжке, если щелкнуть **добавить текст** команды ячейку текст добавляется в режиме предварительного просмотра, а не в режиме редактирования. Можно щелкнуть значок предварительного просмотра, чтобы переключиться в режим правки и изменять ячейки.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в файловой системе HDFS, чтобы сделать это, может появиться следующая ошибка:

   `Error previewing file: File exceeds max size of 30MB`

   В настоящее время нет способа для предварительного просмотра файлов, размер которых превышает 30 МБ студии данных Azure.

- Изменения конфигурации HDFS, влечет за собой изменения hdfs-site.xml не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и доступными (например, в файл дампа кабель). После развертывания, необходимо сбросить SA_PASSWORD на основной экземпляр. Это не ошибка, но шаг по обеспечению безопасности. Дополнительные сведения о способах изменения SA_PASSWORD в контейнере Linux, см. в разделе [Смена пароля Администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS журналы могут содержать пароль системного Администратора для развертывания кластера больших данных.

## <a id="ctp22"></a> CTP-версии 2.2 (декабря 2018 г.)

Новые возможности и известные проблемы для больших данных кластеров в SQL Server 2019 CTP-версии 2.2 в следующих разделах.

### <a name="new-features"></a>Новые возможности

- Доступ к порталу администрирования кластера с `/portal` (**https://\<ip адрес\>: 30777: портал**).
- Имя службы в главный пул изменено с `service-master-pool-lb` и `service-master-pool-nodeport` для `endpoint-master-pool`.
- Новая версия **mssqlctl** и обновления образов.
- Прочие исправления ошибок и улучшения.

### <a name="known-issues"></a>Известные проблемы

Известные проблемы и ограничения в выпуске в следующих разделах.

#### <a name="deployment"></a>Развертывание

- Обновление данных кластерам больших данных с предыдущего выпуска не поддерживается. Необходимо создать резервную копию и удаление любого существующего кластера больших данных перед развертыванием в последнем выпуске. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

- После развертывания в AKS, могут появиться следующие два события-предупреждения из развертывания. Оба эти события перечислены известные проблемы, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Если происходит сбой развертывания кластера больших данных, связанное пространство имен не удаляется. В итоге потерянные пространством имен в кластере. Обойти это можно вручную удалить пространство имен перед развертыванием кластера с тем же именем.

#### <a name="cluster-administration-portal"></a>Портал администрирования кластера

На портале администрирования кластера не содержит конечную точку для главного экземпляра SQL Server. Чтобы найти IP-адрес и порт для главного экземпляра, воспользуйтесь следующим **kubectl** команды:

```
kubectl get svc endpoint-master-pool -n <your-cluster-name>
```

#### <a name="external-tables"></a>Внешние таблицы

- Это позволяет создать внешнюю таблицу пула данных для таблицы, которая имеет неподдерживаемые типы столбцов. При выполнении запроса внешней таблицы, вы получите сообщение следующего вида:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Если базовый файл копируется в HDFS в то же время при выполнении запроса внешней таблицы пула хранения, может появиться ошибка.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адресом МОДУЛЯ адреса могут измениться в среде Kubernetes, время перезагрузки модулей POD. В сценарии, где перезапускает master-pod, сеанс Spark может произойти сбой с `NoRoteToHostException`. Это связано с виртуальной машины Java кэшей, не обновляется с помощью нового IP-адреса адреса.

- Если у вас есть Jupyter уже установлен и отдельные Python в Windows, записные книжки Spark может завершиться ошибкой. Чтобы обойти эту проблему, обновите Jupyter до последней версии.

- В записной книжке, если щелкнуть **добавить текст** команды ячейку текст добавляется в режиме предварительного просмотра, а не в режиме редактирования. Можно щелкнуть значок предварительного просмотра, чтобы переключиться в режим правки и изменять ячейки.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в файловой системе HDFS, чтобы сделать это, может появиться следующая ошибка:

   `Error previewing file: File exceeds max size of 30MB`

   В настоящее время нет способа для предварительного просмотра файлов, размер которых превышает 30 МБ студии данных Azure.

- Изменения конфигурации HDFS, влечет за собой изменения hdfs-site.xml не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и доступными (например, в файл дампа кабель). После развертывания, необходимо сбросить SA_PASSWORD на основной экземпляр. Это не ошибка, но шаг по обеспечению безопасности. Дополнительные сведения о способах изменения SA_PASSWORD в контейнере Linux, см. в разделе [Смена пароля Администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS журналы могут содержать пароль системного Администратора для развертывания кластера больших данных.

## <a id="ctp21"></a> CTP-версии 2.1 (ноября 2018 г.)

Новые возможности и известные проблемы с кластерами больших данных в SQL Server 2019 CTP-версии 2.1 в следующих разделах.

### <a name="new-features"></a>Новые возможности

- [Развертывание приложений Python и R](big-data-cluster-create-apps.md) в кластере больших данных.
- Новая версия **mssqlctl** и обновления образов. 
- Прочие исправления ошибок и улучшения.

### <a name="known-issues"></a>Известные проблемы

Следующие разделы содержат известные проблемы для больших данных кластеров SQL Server в CTP 2.1.

#### <a name="deployment"></a>Развертывание

- Обновление данных кластерам больших данных с предыдущего выпуска не поддерживается. Необходимо создать резервную копию и удаление любого существующего кластера больших данных перед развертыванием в последнем выпуске. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

- После развертывания в AKS, могут появиться следующие два события-предупреждения из развертывания. Оба эти события перечислены известные проблемы, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Если происходит сбой развертывания кластера больших данных, связанное пространство имен не удаляется. В итоге потерянные пространством имен в кластере. Обойти это можно вручную удалить пространство имен перед развертыванием кластера с тем же именем.

#### <a name="admin-portal"></a>Портал администрирования

- Когда вы [приложение создается с помощью команды msqlctl ctp](big-data-cluster-create-apps.md) и развернуть ее на SQL Server, больших данных кластера, на портале администрирования кластера показано модулей POD развернуто приложение «Неизвестно» в разделе контроллера область администратора.

#### <a name="external-tables"></a>Внешние таблицы

- Это позволяет создать внешнюю таблицу пула данных для таблицы, которая имеет неподдерживаемые типы столбцов. При выполнении запроса внешней таблицы, вы получите сообщение следующего вида:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Если базовый файл копируется в HDFS в то же время при выполнении запроса внешней таблицы пула хранения, может появиться ошибка.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адресом МОДУЛЯ адреса могут измениться в среде Kubernetes, время перезагрузки модулей POD. В сценарии, где перезапускает master-pod, сеанс Spark может произойти сбой с `NoRoteToHostException`. Это связано с виртуальной машины Java кэшей, не обновляется с помощью нового IP-адреса адреса.

- Если у вас есть Jupyter уже установлен и отдельные Python в Windows, записные книжки Spark может завершиться ошибкой. Чтобы обойти эту проблему, обновите Jupyter до последней версии.

- В записной книжке, если щелкнуть **добавить текст** команды ячейку текст добавляется в режиме предварительного просмотра, а не в режиме редактирования. Можно щелкнуть значок предварительного просмотра, чтобы переключиться в режим правки и изменять ячейки.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в файловой системе HDFS, чтобы сделать это, может появиться следующая ошибка:

   `Error previewing file: File exceeds max size of 30MB`

   В настоящее время нет способа для предварительного просмотра файлов, размер которых превышает 30 МБ студии данных Azure.

- Изменения конфигурации HDFS, влечет за собой изменения hdfs-site.xml не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и доступными (например, в файл дампа кабель). После развертывания, необходимо сбросить SA_PASSWORD на основной экземпляр. Это не ошибка, но шаг по обеспечению безопасности. Дополнительные сведения о способах изменения SA_PASSWORD в контейнере Linux, см. в разделе [Смена пароля Администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS журналы могут содержать пароль системного Администратора для развертывания кластера больших данных.

## <a id="ctp20"></a> CTP-версии 2.0 (октября 2018 г.)

Новые возможности и известные проблемы с кластерами больших данных в SQL Server 2019 CTP 2.0 в следующих разделах.

### <a name="new-features"></a>Новые возможности

- Простое развертывание качества с помощью средства управления mssqlctl
- Собственный записная книжка студии данных Azure
- Файлы запросов HDFS с помощью хранилища экземпляра SQL Server
- Виртуализации данных через master для SQL Server, Oracle, MongoDB и HDFS
- Мастер виртуализации данных для SQL Server и Oracle в Azure Data Studio
- Службы машинного Обучения на хозяине
- Портал администрирования кластера, который можно использовать для мониторинга и устранения неполадок
- Отправка задания Spark в Azure Data Studio 
- Пользовательский Интерфейс Spark на портале администрирования кластера
- Тома, подключении к классы хранения
- Запросов за пулы данных с основного сервера
- Показать план для распределенных запросов в среде SSMS
- Пакет PIP для средства управления mssqlctl
- Модуль встроенных развертывания с помощью службы контроллера

### <a name="known-issues"></a>Известные проблемы

Следующие разделы содержат известные проблемы для больших данных кластеров SQL Server в CTP 2.0.

#### <a name="deployment"></a>Развертывание

- Если вы используете службы Azure Kubernetes (AKS), рекомендуется версию Kubernetes является 1.10. *, который не поддерживает изменение размера диска. Следует убедиться в том, соответствующим образом размеры хранилища во время развертывания. Дополнительные сведения о том, как настроить размеры хранилища, см. в разделе [постоянного хранения](concept-data-persistence.md) статьи. Для Kubernetes, развернутом на виртуальных машинах рекомендуемая версия — 1.11.

- После развертывания в AKS, могут появиться следующие два события-предупреждения из развертывания. Оба эти события перечислены известные проблемы, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Если происходит сбой развертывания кластера больших данных, связанное пространство имен не удаляется. В итоге потерянные пространством имен в кластере. Обойти это можно вручную удалить пространство имен перед развертыванием кластера с тем же именем.

#### <a name="external-tables"></a>Внешние таблицы

- Это позволяет создать внешнюю таблицу пула данных для таблицы, которая имеет неподдерживаемые типы столбцов. При выполнении запроса внешней таблицы, вы получите сообщение следующего вида:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Если базовый файл копируется в HDFS в то же время при выполнении запроса внешней таблицы пула хранения, может появиться ошибка.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адресом МОДУЛЯ адреса могут измениться в среде Kubernetes, время перезагрузки модулей POD. В сценарии, где перезапускает master-pod, сеанс Spark может произойти сбой с `NoRoteToHostException`. Это связано с виртуальной машины Java кэшей, не обновляется с помощью нового IP-адреса адреса.

- Если у вас есть Jupyter уже установлен и отдельные Python в Windows, записные книжки Spark может завершиться ошибкой. Чтобы обойти эту проблему, обновите Jupyter до последней версии.

- В записной книжке, если щелкнуть **добавить текст** команды ячейку текст добавляется в режиме предварительного просмотра, а не в режиме редактирования. Можно щелкнуть значок предварительного просмотра, чтобы переключиться в режим правки и изменять ячейки.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в файловой системе HDFS, чтобы сделать это, может появиться следующая ошибка:

   `Error previewing file: File exceeds max size of 30MB`

   В настоящее время нет способа для предварительного просмотра файлов, размер которых превышает 30 МБ студии данных Azure.

- Изменения конфигурации HDFS, влечет за собой изменения hdfs-site.xml не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и доступными (например, в файл дампа кабель). После развертывания, необходимо сбросить SA_PASSWORD на основной экземпляр. Это не ошибка, но шаг по обеспечению безопасности. Дополнительные сведения о способах изменения SA_PASSWORD в контейнере Linux, см. в разделе [Смена пароля Администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS журналы могут содержать пароль системного Администратора для развертывания кластера больших данных.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о больших данных кластеров SQL Server, см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
