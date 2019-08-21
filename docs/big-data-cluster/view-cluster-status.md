---
title: Просмотр состояния кластера
titleSuffix: SQL Server big data clusters
description: Эта статья описывает, как просмотреть состояние кластера больших данных с помощью Azure Data Studio, записных книжек и команд azdata.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 028864712658e35913fa04fb1a85e4ca960ad573
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653274"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Просмотр состояния кластера больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья описывает, как получить доступ к конечным точкам служб и просмотреть состояние кластера больших данных SQL Server (предварительная версия). Вы можете использовать как Azure Data Studio, так и **azdata**, и в этой статье рассмотрены обе методики.

## <a id="datastudio"></a> Использование Azure Data Studio

После скачивания последней **сборки предварительной оценки** [Azure Data Studio](https://aka.ms/azdata-insiders) вы можете просматривать конечные точки служб и состояние кластера больших данных с помощью панели мониторинга кластера больших данных SQL Server. Обратите внимание, что некоторые из приведенных ниже функций появились в сборке предварительной оценки Azure Data Studio впервые.

1. Сначала создайте подключение к кластеру больших данных в Azure Data Studio. Дополнительные сведения см. в статье [Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши конечную точку кластера больших данных и выберите пункт **Управление**.

   ![щелкните правой кнопкой мыши и выберите "Управление"](media/view-cluster-status/right-click-manage.png)

1. Перейдите на вкладку **SQL Server Big Data Cluster** (Кластер больших данных SQL Server), чтобы открыть панель мониторинга кластера больших данных.

   ![Панель мониторинга кластера больших данных](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Конечные точки служб

Важно иметь возможность легко обращаться к различным службам в кластере больших данных. Панель мониторинга кластера больших данных предоставляет таблицу конечных точек служб, позволяющую просматривать и копировать конечные точки служб.

![конечные точки служб](media/view-cluster-status/service-endpoints.png)

Первые несколько строк предоставляют следующие службы.

- Прокси приложения
- Служба управления кластерами
- HDFS и Spark
- Прокси управления

Эти службы выводят список конечных точек, которые можно копировать и вставлять, когда требуется конечная точка для подключения к таким службам. Например, можно щелкнуть значок копирования справа от конечной точки, а затем вставить ее в текстовом окне, запрашивающем эту конечную точку. Конечная точка службы управления кластерами нужна для запуска [записной книжки состояния кластера](#notebook).

### <a name="dashboards"></a>Панели мониторинга

Таблица конечных точек служб также предоставляет несколько панелей мониторинга для наблюдения.

- Метрики (Grafana)
- Журналы (Kibana)
- Мониторинг заданий Spark
- Управление ресурсами Spark

Вы можете напрямую щелкнуть эти ссылки. Перед подключением к службе вам будет дважды предложено указать имя пользователя и пароль.

### <a id="notebook"></a> Записная книжка состояния кластера

1. Вы также можете просмотреть состояние кластера больших данных, запустив записную книжку состояния кластера. Чтобы запустить ее, щелкните задачу **Состояние кластера**.

    ![запуск](media/view-cluster-status/cluster-status-launch.png)

2. Перед началом работы вам потребуется следующее.

    - Имя кластера больших данных
    - Имя пользователя контроллера
    - Пароль контроллера
    - Конечные точки контроллера

    Имя кластера больших данных по умолчанию — **mssql-cluster**, если только оно не было настроено во время развертывания. Конечную точку контроллера можно найти на панели мониторинга кластера больших данных в таблице конечных точек служб. Конечная точка указана как **Служба управления кластерами**. Если вы не знаете учетные данные, обратитесь к администратору, развернувшему ваш кластер.

3. Щелкните элемент **Запустить ячейки** на верхней панели инструментов.

4. Следуйте указаниям в запросе на ввод учетных данных. Нажмите клавишу ВВОД после ввода всех учетных данных для имени кластера больших данных, имени пользователя контроллера и пароля контроллера.

    > [!Note]
    > Если у вас нет файла конфигурации, настроенного для больших данных, вам будет предложено указать конечную точку контроллера. Введите или вставьте ее, а затем нажмите клавишу ВВОД для продолжения.

5. Если подключение выполнено успешно, в оставшейся части записной книжки отображаются выходные данные каждого компонента в кластере больших данных. Если вы хотите повторно запустить определенную ячейку кода, наведите на нее указатель мыши и щелкните значок **Выполнить**.

## <a name="use-azdata"></a>Использование azdata

Для просмотра обеих конечных точек и состояния кластера также можно использовать команды [azdata](deploy-install-azdata.md).

### <a name="service-endpoints"></a>Конечные точки служб

Вы можете получить IP-адреса внешних конечных точек для кластера больших данных, выполнив указанные ниже действия.

1. Найдите IP-адрес конечной точки контроллера в выходных данных EXTERNAL-IP следующей команды **kubectl**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Если вы не изменили имя по умолчанию во время развертывания, используйте `-n mssql-cluster` в предыдущей команде. **mssql-cluster** — это имя по умолчанию для кластера больших данных.

1. Войдите в кластер больших данных с помощью [azdata login](reference-azdata.md). Задайте для параметра **--controller-endpoint** значение внешнего IP-адреса конечной точки контроллера.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Укажите имя пользователя и пароль, настроенные для контроллера (CONTROLLER_USERNAME и CONTROLLER_PASSWORD) во время развертывания.

1. Выполните команду [azdata bdc endpoint list](reference-azdata-bdc-endpoint.md), чтобы получить список с описанием каждой конечной точки и соответствующими значениями IP-адреса и порта. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   Следующий список содержит пример выходных данных этой команды.

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

Вы можете проверить состояние кластера с помощью команды [azdata bdc status show](reference-azdata-bdc-status.md).

```bash
azdata bdc status show -o table
```

> [!TIP]
> Чтобы выполнить команды состояния, нужно сначала войти в систему с помощью команды **azdata login**, которая была приведена в предыдущем разделе о конечных точках.

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

Вы можете проверить состояние пулов в кластере с помощью команды [azdata bdc pool status show](reference-azdata-bdc-pool-status.md). Чтобы использовать эту команду, укажите тип пула с помощью параметра `--kind`. Типы пулов:

- вычислительные;
- data
- master
- spark;
- носителей.

Например, следующая команда отображает состояние пула носителей.

```bash
azdata bdc pool status show --kind storage
```

Должен отобразиться текст, аналогичный приведенному ниже.

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

Значение `logsUrl` ссылается на панель мониторинга kibana со сведениями журнала.

![Панель мониторинга Kibana](./media/view-cluster-status/kibana-dashboard.png)

Значения `nodeMetricsUrl` и `sqlMetricsUrl` ссылаются на панель мониторинга grafana для отслеживания работоспособности узла и метрик SQL.

![Панель мониторинга Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Просмотр состояния контроллера

Вы можете просмотреть состояние контроллера с помощью команды [azdata bdc control status show](reference-azdata-bdc-control-status.md). Она предоставляет аналогичные ссылки на панели мониторинга, связанные с узлами контроллера в кластере больших данных.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](big-data-cluster-overview.md).
