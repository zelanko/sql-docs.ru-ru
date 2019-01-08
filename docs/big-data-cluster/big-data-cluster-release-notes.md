---
title: Заметки о выпуске
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье описываются последние обновления и известные проблемы для кластеров SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 8c9c57e641c76f78bf66565cc8e1ce8f67323b7e
ms.sourcegitcommit: 3f19c843b38d3835d07921612f0143620eb9a0e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53709817"
---
# <a name="release-notes-for-sql-server-2019-big-data-clusters"></a>Заметки о выпуске для кластеров SQL Server 2019 больших данных

В этой статье предоставляет последние обновления и известные проблемы для последней версии кластеров больших данных в SQL Server. В следующей таблице представлены ссылки, вы раздел для выпусков, описанном в этой статье.

| Выпуск | Дата |
|---|---|
| [CTP-ВЕРСИИ 2.2](#ctp22) | Декабря 2018 г. |
| [CTP-ВЕРСИИ 2.1](#ctp21) | Ноябрь 2018 г. |
| [CTP-ВЕРСИИ 2.0](#ctp20) | Октября 2018 г. |

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

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
