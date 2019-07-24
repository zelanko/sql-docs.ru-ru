---
title: Просмотр состояния кластера
titleSuffix: SQL Server big data clusters
description: В этой статье объясняется, как просмотреть состояние кластера больших данных с помощью Azure Data Studio, записных книжек и команд аздата.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c6dca94b8bd7547222394d7809cb003b9e936982
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419288"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Просмотр состояния кластера больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как получить доступ к конечным точкам службы и просмотреть состояние SQL Server кластера больших данных (Предварительная версия). Можно использовать как Azure Data Studio, так и **аздата**, и в этой статье рассматриваются обе методики.

## <a id="datastudio"></a>Использование Azure Data Studio

После **загрузки последних версий** [Azure Data Studio](https://aka.ms/azdata-insiders)можно просмотреть конечные точки службы и состояние кластера больших данных с помощью панели мониторинга кластера больших данных SQL Server. Обратите внимание, что некоторые функции, приведенные ниже, доступны только в сборке "предварительные оценки" Azure Data Studio.

1. Сначала создайте подключение к кластеру больших данных в Azure Data Studio. Дополнительные сведения см. в статье [Подключение к SQL Server кластеру больших данных с помощью Azure Data Studio](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши конечную точку кластера больших данных и выберите пункт **Управление**.

   ![Щелкните правой кнопкой мыши Управление](media/view-cluster-status/right-click-manage.png)

1. Перейдите на вкладку **SQL Server большой кластер данных** , чтобы открыть панель мониторинга кластера больших данных.

   ![Панель мониторинга кластера больших данных](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Конечные точки службы

Очень важно иметь возможность легко обращаться к различным службам в кластере больших данных. Панель мониторинга кластера больших данных предоставляет таблицу конечных точек службы, которая позволяет просматривать и копировать конечные точки службы.

![конечные точки службы](media/view-cluster-status/service-endpoints.png)

Первые несколько строк предоставляют следующие службы:

- Прокси приложения
- Служба управления кластерами
- HDFS и Spark
- Прокси-сервер управления

Эти службы выводит список конечных точек, которые можно копировать и вставлять, когда требуется конечная точка для подключения к этим службам. Например, можно щелкнуть значок копирования справа от конечной точки, а затем вставить его в текстовое окно, запрашивающее эту конечную точку. Конечная точка службы управления кластером необходима для запуска [записной книжки состояния кластера](#notebook).

### <a name="dashboards"></a>Информационные панели

Таблица конечных точек службы также предоставляет несколько панелей мониторинга для мониторинга:

- Метрики (Grafana)
- Журналы (Kibana)
- Мониторинг заданий Spark
- Управление ресурсами Spark

Вы можете напрямую щелкнуть эти ссылки. Прежде чем подключиться к службе, вам будет предложено дважды указать имя пользователя и пароль.

### <a id="notebook"></a>Записная книжка состояния кластера

1. Вы также можете просмотреть состояние кластера больших данных, запустив записную книжку "состояние кластера". Чтобы запустить записную книжку, щелкните задачу " **состояние кластера** ".

    ![Перехода](media/view-cluster-status/cluster-status-launch.png)

2. Прежде чем начать, вам потребуются следующие элементы:

    - Имя кластера больших данных
    - Имя пользователя контроллера
    - Пароль контроллера
    - Конечные точки контроллера

    Имя кластера больших данных по умолчанию — **MSSQL-Cluster** , если оно не настроено во время развертывания. Конечную точку контроллера можно найти на панели мониторинга кластера больших данных в таблице конечные точки службы. Конечная точка указана как **Служба управления кластерами**. Если вы не знакомы с учетными данными, обратитесь к администратору, который развернул ваш кластер.

3. Нажмите кнопку **Run Cells (запустить ячейки** ) на верхней панели инструментов.

4. Следуйте указаниям в запросе на ввод учетных данных. Нажмите клавишу ВВОД после ввода всех учетных данных для имени кластера больших данных, имени пользователя контроллера и пароля контроллера.

    > [!Note]
    > Если у вас нет настройки файла конфигурации с большими данными, вам будет предложено ввести конечную точку контроллера. Введите или вставьте его, а затем нажмите клавишу ВВОД для продолжения.

5. Если вы успешно подключились к сети, в оставшейся части записной книжки отобразятся выходные данные каждого компонента кластера больших данных. Если вы хотите повторно запустить определенную ячейку кода, наведите указатель мыши на ячейку кода и щелкните значок **выполнить** .

## <a name="use-azdata"></a>Использование аздата

Вы также можете использовать команды [аздата](deploy-install-azdata.md) для просмотра обеих конечных точек и состояния кластера.

### <a name="service-endpoints"></a>Конечные точки службы

Вы можете получить IP-адреса внешних конечных точек для кластера больших данных, выполнив следующие действия.

1. Найдите IP-адрес конечной точки контроллера, просмотрев выходные данные внешнего IP-адреса следующей команды **kubectl** :

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Если вы не изменили имя по умолчанию во время развертывания `-n mssql-cluster` , используйте в предыдущей команде. **MSSQL-Cluster** — это имя по умолчанию для кластера больших данных.

1. Войдите в кластер больших данных с помощью [аздата login](reference-azdata.md). Задайте для параметра **--Controller-Endpoint** значение внешнего IP-адреса конечной точки контроллера.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Укажите имя пользователя и пароль, настроенные для контроллера (CONTROLLER_USERNAME и CONTROLLER_PASSWORD) во время развертывания.

1. Запустите [список конечных точек BDC аздата](reference-azdata-bdc-endpoint.md) , чтобы получить список с описанием каждой конечной точки и соответствующими значениями IP-адреса и порта. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   В следующем списке показан пример выходных данных этой команды:

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

Просмотреть состояние кластера можно с помощью команды [аздата BDC Status Показать](reference-azdata-bdc-status.md) .

```bash
azdata bdc status show -o table
```

> [!TIP]
> Чтобы выполнить команды состояния, необходимо сначала войти в систему с помощью команды **аздата login** , которая была показана в разделе предыдущих конечных точек.

Ниже приведен пример выходных данных этой команды:

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

Вы можете просмотреть состояние пулов в кластере, выполнив команду [аздата BDC Pool Status Показать](reference-azdata-bdc-pool-status.md) . Чтобы использовать эту команду, укажите тип пула с `--kind` параметром. Типы пулов:

- Вычисляющий
- data
- master
- Spark
- Объема

Например, следующая команда отображает состояние пула пула носителей:

```bash
azdata bdc pool status show --kind storage
```

Должен отобразиться текст, аналогичный приведенному ниже:

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

`logsUrl` Значение ссылается на панель мониторинга kibana с данными журнала:

![Панель мониторинга Kibana](./media/view-cluster-status/kibana-dashboard.png)

Значения `nodeMetricsUrl` и`sqlMetricsUrl` связаны с панелью мониторинга grafana для мониторинга работоспособности узла и метрик SQL.

![Панель мониторинга Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Просмотр состояния контроллера

Состояние контроллера можно просмотреть с помощью команды " [Показать состояние" для элемента управления BDC аздата](reference-azdata-bdc-control-status.md) . Он предоставляет аналогичные ссылки на панели мониторинга, относящиеся к узлам контроллера кластера больших данных.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [что такое SQL Server кластерами больших данных](big-data-cluster-overview.md).
