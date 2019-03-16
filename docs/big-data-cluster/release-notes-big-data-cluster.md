---
title: Заметки о выпуске
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье описываются последние обновления и известные проблемы для кластеров SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4c178c5868789bec2dc80a4b68558f12afbc90d2
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58073230"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Заметки о выпуске для кластеров больших данных в SQL Server

В этой статье перечислены обновления и известные проблемы для последних выпусков кластеров больших данных в SQL Server.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp23"></a> CTP-ВЕРСИИ 2.3 (SQL 2019 Г.)

Февраля 2019 &nbsp; &nbsp;  /  &nbsp; &nbsp; SQL Server 2019 &nbsp; &nbsp;  /  &nbsp; &nbsp; CTP2.3

### <a name="new-features"></a>Новые возможности

| Новая функция | Сведения |
| :---------- | :------ |
| [Отправка заданий Spark на кластерах SQL Server больших данных в IntelliJ](spark-submit-job-intellij-tool-plugin.md). | &nbsp; |
| [Общий интерфейс командной строки для приложения развертывания и управления кластерами](big-data-cluster-create-apps.md). | &nbsp; |
| [Расширение VS Code для развертывания приложений к кластерам больших данных в SQL Server](app-deployment-extension.md). | &nbsp; |
| [Изменения в **mssqlctl** средство использование команды](#mssqlctlctp23). | &nbsp; |
| [Использовать Sparklyr в кластере SQL Server 2019 больших данных](sparklyr-from-RStudio.md). | &nbsp; |
| Подключите внешних HDFS-совместимом хранилище кластера больших данных с помощью **распределение по уровням HDFS**. | См. в разделе [распределение по уровням HDFS](hdfs-tiering.md). |
| Новые возможности единой подключения для главного экземпляра SQL Server и шлюза HDFS или Spark. | См. в разделе [главного экземпляра SQL Server и шлюза HDFS/Spark](connect-to-big-data-cluster.md). |
| При удалении кластера с **удаления кластера mssqlctl** теперь удаляет только объекты в пространстве имен, которые были частью кластера больших данных. | Пространство имен не удаляется. Однако в более ранних выпусках эта команда был удален всего пространства имен. |
| _Безопасность_ имена конечных точек была изменена и консолидации. | _Предыдущий конечные точки:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-security-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-security-nodeport**<br/><br/>_Новая конечная точка:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-security** |
| _Прокси-сервера_ имена конечных точек была изменена и консолидации. | _Предыдущий конечные точки:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-proxy-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-proxy-nodeport**<br/><br/>_Новая конечная точка:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-service-proxy** |
| _Контроллер_ имена конечных точек была изменена и консолидации. | _Предыдущий конечные точки:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-mssql-controller-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-mssql-controller-nodeport**<br/><br/>_Новая конечная точка:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-controller** |
| &nbsp; | &nbsp; |

### <a name="known-issues-deployment"></a>Известные проблемы: Развертывание

- Обновление данных кластерам больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Необходимо создать резервную копию данных и удалите существующего кластера больших данных (с помощью предыдущей версии **mssqlctl**) перед развертыванием в последнем выпуске. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

- **ACCEPT_EULA** переменной среды должен быть «yes» или «Да», чтобы принять условия лицензионного соглашения. Предыдущие выпуски разрешены «y» и «Y», но они больше не принимаются и приведет к сбою развертывания.

- **CLUSTER_PLATFORM** переменные среды не имеет значения по умолчанию, как в предыдущих выпусках.

- После развертывания в AKS, могут появиться следующие два события-предупреждения из развертывания. Оба эти события перечислены известные проблемы, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Если происходит сбой развертывания кластера больших данных, связанное пространство имен не удаляется. В итоге потерянные пространством имен в кластере. Обойти это можно вручную удалить пространство имен перед развертыванием кластера с тем же именем.

### <a name="known-issues-kubeadm-deployments"></a>Известные проблемы: kubeadm развертываний

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

### <a id="mssqlctlctp23"></a> Известные проблемы: mssqlctl

- **Mssqlctl** изменился инструмент из команды глагол существительное, упорядочение с заказом глагол существительное. Например `mssqlctl create cluster` теперь `mssqlctl cluster create`.

- `--name` Теперь является параметр требуется при создании кластера с `mssqlctl cluster create`.

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- Важные сведения об обновлении до последней версии кластеров больших данных и **mssqlctl**, см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

### <a name="known-issues-external-tables"></a>Известные проблемы: Внешние таблицы

- Это позволяет создать внешнюю таблицу пула данных для таблицы, которая имеет неподдерживаемые типы столбцов. При выполнении запроса внешней таблицы, вы получите сообщение следующего вида:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Если базовый файл копируется в HDFS в то же время при выполнении запроса внешней таблицы пула хранения, может появиться ошибка.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы к базе данных Oracle, использовать символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. В результате сбоя в язык DDL внешней таблицы. Измените схемы Oracle для NVARCHAR2 на типе, или вручную создайте инструкций ВНЕШНЕЙ таблицы, укажите NVARCHAR, а не с помощью мастера.

### <a name="known-issues-application-deployment"></a>Известные проблемы: Развертывание приложения

- При вызове приложения R, Python или MLeap из RESTful API, вызов истечет время ожидания в течение 5 минут.

### <a name="known-issues-spark-and-notebooks"></a>Известные проблемы: Spark и записные книжки

- IP-адресом МОДУЛЯ адреса могут измениться в среде Kubernetes, время перезагрузки модулей POD. В сценарии, где перезапускает master-pod, сеанс Spark может произойти сбой с `NoRoteToHostException`. Это связано с виртуальной машины Java кэшей, не обновляется с помощью нового IP-адреса адреса.

- Если у вас есть Jupyter уже установлен и отдельные Python в Windows, записные книжки Spark может завершиться ошибкой. Чтобы обойти эту проблему, обновите Jupyter до последней версии.

- В записной книжке, если щелкнуть **добавить текст** команды ячейку текст добавляется в режиме предварительного просмотра, а не в режиме редактирования. Можно щелкнуть значок предварительного просмотра, чтобы переключиться в режим правки и изменять ячейки.

### <a name="known-issues-hdfs"></a>Известные проблемы: HDFS

- Если щелкнуть правой кнопкой мыши файл в файловой системе HDFS, чтобы сделать это, может появиться следующая ошибка:

   `Error previewing file: File exceeds max size of 30MB`

   В настоящее время нет способа для предварительного просмотра файлов, размер которых превышает 30 МБ студии данных Azure.

- Изменения конфигурации HDFS, влечет за собой изменения hdfs-site.xml не поддерживаются.

### <a name="known-issues-security"></a>Известные проблемы: безопасность

- SA_PASSWORD является частью среды и доступными (например, в файл дампа кабель). После развертывания, необходимо сбросить SA_PASSWORD на основной экземпляр. Это не ошибка, но шаг по обеспечению безопасности. Дополнительные сведения о способах изменения SA_PASSWORD в контейнере Linux, см. в разделе [Смена пароля Администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS журналы могут содержать пароль системного Администратора для развертывания кластера больших данных.

## <a id="ctp22"></a> CTP-версии 2.2 (декабря 2018 г.)

Новые возможности и известные проблемы для больших данных кластеров в SQL Server 2019 CTP-версии 2.2 в следующих разделах.

### <a name="whats-in-the-ctp-22-release"></a>Новые возможности в выпуске CTP-версии 2.2

- Доступ к порталу администрирования кластера с `/portal` (**https://\<ip адрес\>: 30777: портал**).
- Имя службы в главный пул изменено с `service-master-pool-lb` и `service-master-pool-nodeport` для `endpoint-master-pool`.
- Новая версия **mssqlctl** и обновления образов.
- Прочие исправления ошибок и улучшения.

### <a name="known-issues"></a>Известные проблемы

Следующие разделы содержат известные проблемы для больших данных кластеров SQL Server в CTP-версии 2.2.

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

### <a name="whats-in-the-ctp-21-release"></a>Новые возможности в выпуске CTP 2.1

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

### <a name="whats-in-the-ctp-20-release"></a>Новые возможности в выпуске CTP 2.0

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
