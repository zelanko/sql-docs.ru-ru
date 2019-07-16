---
title: Просмотр состояния кластера
titleSuffix: SQL Server big data clusters
description: В этой статье объясняется, как просмотреть состояние кластера больших данных с помощью Azure Data Studio, записные книжки и mssqlctl команды.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 06/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1a8d04ab43adac77a534a82626cc4a018c24b68f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957670"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Как просмотреть состояние кластера больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как для доступа к конечным точкам службы и просмотреть состояние кластера больших данных SQL Server (Предварительная версия). Вы можете использовать оба Studio данных Azure и **mssqlctl**, и в этой статье рассматриваются оба способа.

## <a id="datastudio"></a> С помощью Studio данных Azure

После загрузки последней версии **сборка программы предварительной оценки** из [Azure Data Studio](https://aka.ms/azdata-insiders), можно просмотреть конечные точки службы, и состояние больших данных кластера с помощью панели мониторинга кластера больших данных в SQL Server. Обратите внимание на то, что некоторые из функций, описанных ниже доступны только сначала в сборки программы предварительной оценки студии данных Azure.

1. Во-первых создаете подключение к кластеру больших данных в Azure Data Studio. Дополнительные сведения см. в разделе [соединиться с сервером SQL кластера больших данных с помощью Azure Data Studio](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши на конечную точку кластера больших данных, а затем нажмите кнопку **управление**.

   ![Щелкните правой кнопкой мыши Управление](media/view-cluster-status/right-click-manage.png)

1. Выберите **кластера больших данных SQL Server** tab, чтобы получить доступ к панели мониторинга кластера больших данных.

   ![Панель мониторинга кластера больших данных](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Конечные точки службы

Очень важно иметь возможность легко получить доступ к различным службам в кластере больших данных. Панель мониторинга кластера больших данных предоставляет таблицу конечные точки службы, которая позволяет см. в разделе и скопируйте конечные точки службы.

![Конечные точки службы](media/view-cluster-status/service-endpoints.png)

Первые несколько строк предоставлять следующие службы:

- Прокси приложения
- Cluster Management Service
- HDFS и Spark
- Прокси-сервер управления

Эти службы перечислены конечные точки, которые можно скопировать и вставить, когда требуется конечная точка для подключения к этим службам. Например можно щелкните значок копирования справа от конечной точки и вставьте его в текстовое окно, запрашивает эту конечную точку. Конечная точка Cluster Management Service необходимо запускать [записной книжки состояние кластера](#notebook).

### <a name="dashboards"></a>Информационные панели

В таблице конечных точек службы также предоставляет несколько панелей мониторинга для мониторинга:

- Метрики (Grafana)
- Журналы (Kibana)
- Отслеживание заданий Spark
- Управление ресурсами Spark

Можно напрямую щелкнуть эти ссылки. Вам требуется дважды ввести свое имя пользователя и пароль перед подключением к службе.

### <a id="notebook"></a> Записная книжка состояния кластера

1. Можно также просмотреть состояние кластера больших данных кластера, запустив записную книжку состояние кластера. Чтобы запустить записную книжку, нажмите кнопку **состояние кластера** задачи.

    ![запустить](media/view-cluster-status/cluster-status-launch.png)

2. Перед началом работы требуется следующее:

    - Имя кластера больших данных
    - Имя пользователя контроллера
    - Пароля для контроллера
    - Конечные точки контроллера

    Имя кластера больших данных по умолчанию — **mssql-cluster** Если вы настроили во время развертывания. Конечная точка контроллера, из панели мониторинга кластера больших данных можно найти в таблице конечных точек службы. Конечная точка указана как **Cluster Management Service**. Если вы не знаете учетные данные, попросите администратора, который развернут кластер.

3. Нажмите кнопку **запуска ячеек** на верхней панели инструментов.

4. Следуйте указаниям для учетных данных. Нажмите клавишу ВВОД после того как вы введите каждых учетных данных для имени кластера больших данных, контроллер имени пользователя и пароля для контроллера.

    > [!Note]
    > Если у вас нет настройки файла конфигурации с большими данными, вам нужно будет для конечной точки контроллера. Введите или вставьте его и нажмите клавишу ВВОД, чтобы продолжить.

5. Если подключение успешно установлено, остальная часть записной книжки будут показаны выходные данные каждого компонента кластера больших данных. Если вы хотите повторно выполнить определенные ячейку кода, наведите указатель мыши на ячейку кода и нажмите кнопку **запуска** значок.

## <a name="use-mssqlctl"></a>Использование mssqlctl

Можно также использовать [mssqlctl](deploy-install-mssqlctl.md) команды, чтобы просмотреть конечные точки и состояние кластера.

### <a name="service-endpoints"></a>Конечные точки службы

Вы можете получить IP-адреса внешних конечных точек для больших данных кластера, выполнив следующие действия.

1. Найти IP-адрес конечной точки контроллера на внешний IP-данными, полученными следующей **kubectl** команды:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Если вы не изменяли имя по умолчанию во время развертывания, используйте `-n mssql-cluster` в предыдущей команде. **MSSQL-cluster** является именем по умолчанию для кластера больших данных.

1. Войдите кластер больших данных с [mssqlctl входа](reference-mssqlctl.md). Задайте **--конечной точки контроллера** параметр внешний IP-адрес конечной точки контроллера.

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Укажите имя пользователя и пароль, настроенный для контроллера (CONTROLLER_USERNAME и CONTROLLER_PASSWORD) во время развертывания.

1. Запустите [списка конечных точек bdc mssqlctl](reference-mssqlctl-bdc-endpoint.md) для получения списка с описанием каждой конечной точки и соответствующих IP адрес и порт. 

   ```bash
   mssqlctl bdc endpoint list -o table
   ```

   В следующем списке приведены пример выходных данных этой команды:

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

### <a name="view-cluster-status"></a>Просмотр состояния кластера

Можно просмотреть состояние кластера с [Показать состояние bdc mssqlctl](reference-mssqlctl-bdc-status.md) команды.

```bash
mssqlctl bdc status show -o table
```

> [!TIP]
> Для выполнения команд состояние, необходимо сначала войти в систему **mssqlctl входа** команды, который был показан в предыдущем разделе конечных точек.

Ниже приведен пример выходных данных этой команды.

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

### <a name="view-pool-status"></a>Просмотр состояния пула

Можно просмотреть состояние пулов в кластер с [Показать состояние пула bdc mssqlctl](reference-mssqlctl-bdc-pool-status.md) команды. Чтобы использовать эту команду, укажите тип пула с `--kind` параметра. Ниже приведены типы пула.

- Вычислений
- data
- master
- Spark
- Хранилища

Например следующая команда отображает состояние пула, пула носителей:

```bash
mssqlctl bdc pool status show --kind storage
```

Вы должны увидеть текст, аналогичный приведенному ниже:

```output
[
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/logs/ui",
    "name": "storage-0-0",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/sqlmetrics/ui",
    "state": "Running"
  },
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/logs/ui",
    "name": "storage-0-1",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/sqlmetrics/ui",
    "state": "Running"
  }
]
```

`logsUrl` Значение ссылки на панели мониторинга kibana с информацией журнала:

![панель мониторинга kibana](./media/view-cluster-status/kibana-dashboard.png)

`nodeMetricsUrl` И `sqlMetricsUrl` значения связи на панели мониторинга grafana для мониторинга состояния работоспособности узла и метрики SQL:

![Панели мониторинга Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Просмотр состояния контроллера

Можно просмотреть состояние контроллера с [Показать состояние управления bdc mssqlctl](reference-mssqlctl-bdc-control-status.md) команды. Также предоставляет аналогичные ссылки на панелей мониторинга, связанных с узлами контроллера кластера больших данных.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server с большими данными](big-data-cluster-overview.md).
