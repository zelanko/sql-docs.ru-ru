---
title: Просмотр состояния кластера
titleSuffix: SQL Server big data clusters
description: Эта статья описывает, как просмотреть состояние кластера больших данных с помощью Azure Data Studio, записных книжек и команд azdata.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f5b3b210cb4e20bdf9585a7efdfd0f10aa19f29
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725797"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Просмотр состояния кластера больших данных 

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается, как получить доступ к конечным точкам служб и просмотреть состояние кластера больших данных SQL Server. Вы можете использовать как Azure Data Studio, так и **azdata**, и в этой статье рассмотрены обе методики.

## <a name="use-azure-data-studio"></a><a id="datastudio"></a> Использование Azure Data Studio

После скачивания последней **сборки предварительной оценки**[Azure Data Studio](../azure-data-studio/download-azure-data-studio.md) вы можете просматривать конечные точки служб и состояние кластера больших данных с помощью панели мониторинга кластера больших данных SQL Server. Некоторые из приведенных ниже функций появились в сборке предварительной оценки Azure Data Studio впервые.

1. Сначала создайте подключение к кластеру больших данных в Azure Data Studio. Дополнительные сведения см. в статье [Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши конечную точку кластера больших данных и выберите пункт **Управление**.

   ![щелкните правой кнопкой мыши и выберите "Управление"](media/view-cluster-status/right-click-manage.png)

1. Перейдите на вкладку **SQL Server Big Data Cluster** (Кластер больших данных SQL Server), чтобы открыть панель мониторинга кластера больших данных.

   ![Панель мониторинга кластера больших данных](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Конечные точки служб

Важно иметь возможность легко обращаться к различным службам в кластере больших данных. Панель мониторинга кластера больших данных предоставляет таблицу конечных точек служб, позволяющую просматривать и копировать конечные точки служб.

![конечные точки служб](media/view-cluster-status/service-endpoints.png)

Эти службы выводят список конечных точек, которые можно копировать и вставлять, когда требуется конечная точка для подключения к таким службам. Например, можно щелкнуть значок копирования справа от конечной точки, а затем вставить ее в текстовом окне, запрашивающем эту конечную точку. Конечная точка службы управления кластерами нужна для запуска [записной книжки состояния кластера](#notebook).

### <a name="dashboards"></a>Панели мониторинга

Таблица конечных точек служб также предоставляет несколько панелей мониторинга для наблюдения.

- Метрики (Grafana)
- Журналы (Kibana)
- Мониторинг заданий Spark
- Управление ресурсами Spark

Вы можете напрямую щелкнуть эти ссылки. При доступе к этим панелям мониторинга вам придется пройти проверку подлинности. Для панелей мониторинга метрик и журналов укажите учетные данные администратора контроллера, которые задаются во время развертывания с помощью переменных среды **AZDATA_USERNAME** и **AZDATA_PASSWORD**. Панели мониторинга Spark будут использовать учетные данные шлюза (Knox): либо удостоверение AD в кластере, интегрированном с AD, либо пользователя **AZDATA_USERNAME** и переменную среды **AZDATA_PASSWORD**, если в кластере используется обычная проверка подлинности.

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

### <a name="cluster-status-notebook"></a><a id="notebook"></a> Записная книжка состояния кластера

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

5. Если подключение выполнено успешно, в оставшейся части записной книжки отображаются выходные данные каждого компонента в кластере больших данных. Чтобы повторно запустить определенную ячейку кода, наведите на нее указатель мыши и щелкните значок **Выполнить**.

## <a name="use-azdata"></a>Использование azdata

Для просмотра обеих конечных точек и состояния кластера также можно использовать команды [azdata](../azdata/install/deploy-install-azdata.md).

### <a name="service-endpoints"></a>Конечные точки служб

1. Войдите в кластер больших данных с помощью [azdata login](../azdata/reference/reference-azdata.md). Задайте для параметра **--controller-endpoint** значение внешнего IP-адреса конечной точки контроллера.

   ```bash
   azdata login --endpoint https://<ip-address-of-controller-svc-external>:30080 --username <user-name>
   ```

   Укажите имя пользователя и пароль, настроенные для контроллера (AZDATA_USERNAME и AZDATA_PASSWORD) во время развертывания. 
   Для проверки подлинности AD используется следующая команда:

  ```bash
   azdata login --endpoint https://<control_domain_name>:30080 --auth ad
   ```

1. Выполните команду [`azdata bdc endpoint list`](../azdata/reference/reference-azdata-bdc-endpoint.md), чтобы получить список с описанием каждой конечной точки и соответствующими значениями IP-адреса и порта. 

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

Проверить состояние кластера можно с помощью команды [`azdata bdc status show`](../azdata/reference/reference-azdata-bdc-status.md).

```bash
azdata bdc status show
```

> [!TIP]
> Чтобы выполнить команды состояния, нужно сначала войти в систему с помощью команды **azdata login**, которая была приведена в предыдущем разделе о конечных точках.

Ниже приведен пример выходных данных этой команды.

```output
 Bdc: ready                                                                                                                                                                                                          Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Services: ready                                                                                                                                                                                                     Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Servicename    State    Healthstatus    Details

 spark          ready    healthy         -
 sql            ready    healthy         -
 hdfs           ready    healthy         -
 control        ready    healthy         -
 gateway        ready    healthy         -
 app            ready    healthy         -


 Spark Services: ready                                                                                                                                                                                               Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Sql Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 master          ready    healthy         StatefulSet master is healthy
 compute-0       ready    healthy         StatefulSet compute-0 is healthy
 data-0          ready    healthy         StatefulSet data-0 is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Hdfs Services: ready                                                                                                                                                                                                Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 nmnode-0        ready    healthy         StatefulSet nmnode-0 is healthy
 zookeeper       ready    healthy         StatefulSet zookeeper is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy
 sparkhead       ready    healthy         StatefulSet sparkhead is healthy


 Control Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 controldb       ready    healthy         StatefulSet controldb is healthy
 control         ready    healthy         ReplicaSet control is healthy
 metricsdc       ready    healthy         DaemonSet metricsdc is healthy
 metricsui       ready    healthy         ReplicaSet metricsui is healthy
 metricsdb       ready    healthy         StatefulSet metricsdb is healthy
 logsui          ready    healthy         ReplicaSet logsui is healthy
 logsdb          ready    healthy         StatefulSet logsdb is healthy
 mgmtproxy       ready    healthy         ReplicaSet mgmtproxy is healthy
 controlwd       ready    healthy         ReplicaSet controlwd is healthy


 Gateway Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 gateway         ready    healthy         StatefulSet gateway is healthy


 App Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 appproxy        ready    healthy         ReplicaSet appproxy is healthy
```

### <a name="view-specific-resource-status"></a>Просмотр состояния конкретного ресурса

Состояние конкретного ресурса в кластере можно просмотреть с помощью команды [azdata bdc status show](../azdata/reference/reference-azdata-bdc-status.md). При использовании этой команды можно фильтровать результаты с помощью параметра `--resource`. Ниже приведены некоторые примеры входных данных для параметра `--resource`.

- master
- управляющие
- compute-0
- storage-0
- gateway

Например, следующая команда отображает состояние пула носителей.

```bash
azdata bdc status show --all --resource storage-0
```

Чтобы просмотреть состояние всех компонентов, в которых запущена определенная служба, необходимо использовать соответствующую группу команд `azdata bdc <serviceName> status show`. Пример:

- azdata bdc sql status show --all
- azdata bdc hdfs status show --all
- azdata bdc spark status show --all

Ниже приведен пример выходных данных.

```output
  Storage-0: ready                                                                                                                                                                                                    Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Instances: running                                                                                                                                                                                                  Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 storage-0-0     running  healthy         Pod storage-0-0 is healthy
 storage-0-1     running  healthy         Pod storage-0-1 is healthy


 Dashboards
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Name            Url

 nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/nodemetrics/ui
 sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/sqlmetrics/ui
 logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/logs/ui
 ```

> [!TIP]
> Для получения дополнительных сведений о работоспособности, включая ссылки на панели мониторинга метрик и журналов, соответствующие конкретному экземпляру, выполните команду status с параметрами `--all`. Ниже приведен пример выходных данных при использовании параметров `--all`.

```output
 Spark: ready                                                                                                                                                                                                        Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Resources: ready                                                                                                                                                                                                    Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Sparkhead Resources: running                                                                                                                                                                                        Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 sparkhead-0     running  healthy         Pod sparkhead-0 is healthy
 sparkhead-1     running  healthy         Pod sparkhead-1 is healthy


      Dashboards
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      Name            Url

      nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/nodemetrics/ui
      sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/sqlmetrics/ui
      logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/logs/ui


 Storage-0 Resources: running                                                                                                                                                                                        Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 storage-0-0     running  healthy         Pod storage-0-0 is healthy
 storage-0-1     running  healthy         Pod storage-0-1 is healthy


      Dashboards
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      Name            Url

      nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/nodemetrics/ui
      sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/sqlmetrics/ui
      logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/logs/ui
```

Значение `logsUrl` ссылается на панель мониторинга Kibana:

![Панель мониторинга Kibana](./media/view-cluster-status/kibana-dashboard.png)

> [!NOTE]
> Браузер Microsoft Edge (старый) несовместим с Kibana. Чтобы эта панель мониторинга отображалась корректно, необходимо использовать браузер на базе Chromium. При загрузке панелей мониторинга в неподдерживаемом браузере вы увидите пустую страницу. Поддерживаемые браузеры для Kibana см. здесь.

Значения `nodeMetricsUrl` и `sqlMetricsUrl` ссылаются на панель мониторинга Grafana для мониторинга метрик узла Kubernetes и метрик службы кластеров больших данных.

![Панель мониторинга Grafana](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Просмотр состояния контроллера

Состояние контроллера можно увидеть с помощью команды [`azdata bdc control status show`](../azdata/reference/reference-azdata-bdc-control-status.md). Она предоставляет аналогичные ссылки на панели мониторинга, связанные с компонентами контроллера в кластере больших данных.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).