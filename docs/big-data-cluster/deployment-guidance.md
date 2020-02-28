---
title: Руководства по развертыванию
titleSuffix: SQL Server Big Data Clusters
description: Узнайте, как развертывать кластеры больших данных SQL Server в Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9e2204000400c06ea0fd884dbf4db6c08085d495
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256887"
---
# <a name="how-to-deploy-big-data-clusters-2019-on-kubernetes"></a>Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Кластер больших данных SQL Server развертывается в виде контейнеров Docker в кластере Kubernetes. Здесь описаны этапы настройки.

- Настройте кластер Kubernetes на одной виртуальной машине, в кластере виртуальных машин или в службе Azure Kubernetes (AKS).
- Установите средство настройки кластера `azdata` на клиентском компьютере.
- Разверните кластер больших данных SQL Server в кластере Kubernetes.

## <a name="install-sql-server-2019-big-data-tools"></a>Установка средств для работы с большими данными SQL Server 2019

Перед развертыванием кластера больших данных SQL Server 2019 [установите средства для работы с большими данными](deploy-big-data-tools.md).

- `azdata`
- `kubectl`
- Azure Data Studio
- [Расширение Data Virtualization](../azure-data-studio/data-virtualization-extension.md) для Azure Data Studio

## <a id="prereqs"></a> Предварительные требования для Kubernetes

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] требуется минимальная версия Kubernetes не ниже 1.13 для сервера и клиента (kubectl).

> [!NOTE]
> Обратите внимание, что версии клиента и сервера Kubernetes должны находиться в пределах +/– 1 от дополнительного номера версии. Дополнительные сведения см. в [заметках о выпуске Kubernetes и описании политики в отношении отклонения версий SKU](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a> Настройка кластера Kubernetes

Если у вас уже есть кластер Kubernetes, соответствующий приведенным выше предварительным требованиям, можно сразу перейти к [этапу развертывания](#deploy). В этом разделе предполагается базовое понимание концепций Kubernetes.  Подробные сведения о Kubernetes см. в [документации по Kubernetes](https://kubernetes.io/docs/home).

Вы можете развернуть Kubernetes любым из трех способов.

| Расположение развертывания Kubernetes | Описание | Ссылка |
|---|---|---|
| **Службы Azure Kubernetes (AKS)** | Управляемая служба контейнеров Kubernetes в Azure. | [Инструкции](deploy-on-aks.md) |
| **Один или несколько компьютеров (`kubeadm`)** | Кластер Kubernetes, развернутый на физических компьютерах или виртуальных машинах с помощью `kubeadm` | [Инструкции](deploy-with-kubeadm.md) |

> [!TIP]
> Вы также можете создать скрипт для развертывания AKS и кластера больших данных за один шаг. Дополнительные сведения о том, как это сделать, см. в [скрипте Python](quickstart-big-data-cluster-deploy.md) или в [записной книжке](deploy-notebooks.md) Azure Data Studio.

### <a name="verify-kubernetes-configuration"></a>Проверка конфигурации Kubernetes

Выполните команду `kubectl`, чтобы просмотреть конфигурацию кластера. Убедитесь, что kubectl указывает на правильный контекст кластера.

```bash
kubectl config view
```

> [!Important] 
> При развертывании в кластере Kubernetes с несколькими узлами, начальная загрузка которого выполняется с помощью `kubeadm`, перед развертыванием кластера больших данных необходимо убедиться, что часы во всех узлах Kubernetes, участвующих в развертывании, синхронизированы. Кластер больших данных имеет встроенные свойства обеспечения работоспособности разных служб, которые зависят от времени, поэтому любые отклонения во времени могут привести к неправильной работе системы.

После настройки кластера Kubernetes можно перейти к развертыванию нового кластера больших данных SQL Server. Если вы обновляете предыдущий выпуск, см. статью [Обновление[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deployment-upgrade.md).

## <a name="ensure-you-have-storage-configured"></a>Убедитесь, что хранилище настроено

В большинстве случаев развертывания кластеров больших данных должны иметь постоянное хранилище. В настоящее время необходимо убедиться, как именно вы собираетесь подготовить постоянное хранилище в кластере Kubernetes перед развертыванием BDC.

При развертывании в AKS настройка хранилища не требуется. AKS предоставляет встроенные классы хранения с динамической подготовкой. Вы можете настроить класс хранения (`default` или `managed-premium`) в файле конфигурации развертывания. Встроенные профили используют класс хранения `default`. При развертывании в кластере Kubernetes, развернутом с помощью `kubeadm`, необходимо убедиться в наличии достаточного объема хранилища для кластера, доступного для требуемого масштабирования и настроенного для использования. Если вы хотите настроить использование хранилища, сделайте это перед продолжением. См. раздел [Сохраняемость данных при использовании кластера больших данных SQL Server в Kubernetes](concept-data-persistence.md).

## <a id="deploy"></a> Общие сведения о развертывании

Большинство параметров кластера больших данных определяется в файле конфигурации развертывания JSON. Вы можете использовать профиль развертывания по умолчанию для кластеров AKS и Kubernetes, созданных с помощью `kubeadm`, или настроить собственный файл конфигурации развертывания для использования во время установки. По соображениям безопасности параметры проверки подлинности передаются через переменные среды.

Следующие разделы содержат дополнительные сведения о настройке развертываний кластера больших данных, а также примеры распространенных настроек. Кроме того, вы всегда можете изменить пользовательский файл конфигурации развертывания в редакторе, таком как VS Code.

## <a id="configfile"></a> Конфигурации по умолчанию

Параметры развертывания кластера больших данных определяются в файлах конфигурации JSON. Можно начать пользовательскую настройку развертывания кластеров с встроенных профилей развертывания, которые доступны в `azdata`. 

> [!NOTE]
> Образы контейнеров, необходимые для развертывания кластера больших данных, размещаются в реестре контейнеров Microsoft (`mcr.microsoft.com`) в репозитории `mssql/bdc`. По умолчанию эти параметры уже включены в файл конфигурации `control.json` в каждом из профилей развертывания, включенных в `azdata`. Кроме того, тег образа контейнера для каждого выпуска также предварительно заполняется в том же файле конфигурации. Если необходимо извлечь образы контейнеров в собственный частный реестр контейнеров и изменить параметры реестра контейнеров или репозитория, следуйте инструкциям в статье [Автономная установка](deploy-offline.md).

Выполните следующую команду, чтобы найти доступные шаблоны:

```
azdata bdc config list -o table 
```

Так, для служебного обновления (GDR1) RTM-версии SQL Server 2019 возвращается следующее:

```
Result
----------------
aks-dev-test
aks-dev-test-ha
kubeadm-dev-test
kubeadm-prod
```

| Профиль развертывания | Среда Kubernetes |
|---|---|
| `aks-dev-test` | Развертывание кластера больших данных SQL Server в службе Azure Kubernetes Service (AKS)|
| `aks-dev-test-ha` | Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS). Критически важные службы, такие как основной экземпляр SQL Server и узел имен HDFS, настроены для обеспечения высокой доступности.|
| `kubeadm-dev-test` | Развертывание кластера больших данных SQL Server в кластере Kubernetes, созданном с помощью kubeadm на одной или нескольких физических или виртуальных машинах.|
| `kubeadm-prod`| Развертывание кластера больших данных SQL Server в кластере Kubernetes, созданном с помощью kubeadm на одной или нескольких физических или виртуальных машинах. Используйте этот шаблон, чтобы включить интеграцию служб кластеров больших данных с Active Directory. Критически важные службы, такие как основной экземпляр SQL Server и узел имен HDFS, настроены для обеспечения высокой доступности.  |

Кластер больших данных можно развернуть, выполнив команду `azdata bdc create`. Вам будет предложено выбрать одну из конфигураций по умолчанию, а затем выполнить развертывание, следуя указаниям.

При первом запуске `azdata` нужно включить `--accept-eula=yes`, чтобы принять условия лицензионного соглашения (EULA).

```bash
azdata bdc create --accept-eula=yes
```

В этом сценарии вам будет предложено ввести параметры, не входящие в конфигурацию по умолчанию, например пароли. 

> [!IMPORTANT]
> Имя кластера больших данных по умолчанию — `mssql-cluster`. Это важно знать, чтобы выполнить любую из команд `kubectl`, задающих пространство имен Kubernetes с параметром `-n`.

## <a id="customconfig"></a> Пользовательские конфигурации

Кроме того, можно настроить развертывание специально для выполнения нужных вам рабочих нагрузок. Обратите внимание, что нельзя изменить масштаб (число реплик) или параметры хранилища для служб кластеров больших данных после развертывания, поэтому необходимо тщательно спланировать конфигурацию развертывания, чтобы избежать проблем с емкостью. Чтобы настроить развертывание, выполните следующие действия:

1. Начните с одного из стандартных профилей развертывания, соответствующих вашей среде Kubernetes. Для их перечисления можно использовать команду `azdata bdc config list`:

   ```bash
   azdata bdc config list
   ```

1. Чтобы настроить развертывание, создайте копию профиля развертывания с помощью команды `azdata bdc config init`. Например, следующая команда создает копию файлов конфигурации развертывания `aks-dev-test` в целевом каталоге `custom`:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

   >[!TIP]
   >`--target` указывает каталог, содержащий файлы конфигурации `bdc.json` и `control.json`, на основе параметра `--source`.

1. Чтобы настроить параметры в профиле конфигурации развертывания, можно изменить этот файл в средстве, которое подходит для редактирования JSON-файлов, например VS Code. Для автоматизации на основе скриптов можно также изменить пользовательский профиль развертывания с помощью команды `azdata bdc config`. Например, следующая команда изменяет пользовательский профиль развертывания, чтобы изменить имя развернутого кластера с используемого по умолчанию (`mssql-cluster`) на `test-cluster`.  

   ```bash
   azdata bdc config replace --config-file custom/bdc.json --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > Вы также можете передать имя кластера во время развертывания с помощью параметра *--name* для команды *azdata create bdc*. Параметры в команде имеют приоритет над значениями в файлах конфигурации.
   >
   > Полезным инструментом для поиска путей JSON является [JSONPath Online Evaluator](https://jsonpath.com/).
   >
   Кроме передачи пар "ключ — значение", можно также указать встроенные значения JSON или передать файлы исправлений JSON. Дополнительные сведения см. в статье [Настройка параметров развертывания для кластеров больших данных](deployment-custom-configuration.md).

1. Передайте пользовательский файл конфигурации в `azdata bdc create`. Обратите внимание, что требуется задать необходимые [переменные среды](#env), в противном случае терминал предложит ввести эти значения:

   ```bash
   azdata bdc create --config-profile custom --accept-eula yes
   ```

> Дополнительные сведения о структуре файла конфигурации развертывания см. в [справочнике по файлу конфигурации развертывания](reference-deployment-config.md). Дополнительные примеры конфигурации см. в статье [Настройка параметров развертывания для кластеров больших данных](deployment-custom-configuration.md).

## <a id="env"></a> Переменные среды

Указанные ниже переменные среды используются для параметров безопасности, которые не хранятся в файле конфигурации развертывания. Обратите внимание, что параметры Docker, за исключением учетных данных, можно задать в файле конфигурации.

| Переменная среды | Требование |Описание |
|---|---|---|
| `AZDATA_USERNAME` | Обязательно |Имя пользователя администратора кластера больших данных SQL Server. Данные для входа sysadmin с тем же именем создаются в основном экземпляре SQL Server. В целях безопасности учетная запись `sa` отключена. |
| `AZDATA_PASSWORD` | Обязательно |Пароль для учетной записи пользователя, созданной выше. Для пользователя `root` используется тот же пароль, что и для защиты шлюза Knox и HDFS. |
| `ACCEPT_EULA`| Требуется для первого использования `azdata`.| Выберите "Да". При задании в качестве переменной среды применяет лицензионное соглашение как к SQL Server, так и к `azdata`. Если параметр не задан в качестве переменной среды, можно включить `--accept-eula=yes` при первом использовании команды `azdata`.|
| `DOCKER_USERNAME` | Необязательно | Имя пользователя для доступа к образам контейнера в случае, если они хранятся в частном репозитории. Дополнительные сведения о том, как использовать частный репозиторий Docker для развертывания кластеров больших данных, см. в разделе [Автономные развертывания](deploy-offline.md).|
| `DOCKER_PASSWORD` | Необязательно |Пароль для доступа к указанному выше частному репозиторию. |

Эти переменные среды необходимо задать до вызова команду `azdata bdc create`. Если какая-либо из переменных не задана, вам будет предложено ввести ее.

В следующем примере показано, как задать переменные среды для Linux (bash) и Windows (PowerShell).

```bash
export AZDATA_USERNAME=admin
export AZDATA_PASSWORD=<password>
export ACCEPT_EULA=yes
```

```PowerShell
SET AZDATA_USERNAME=admin
SET AZDATA_PASSWORD=<password>
```

> [!NOTE]
> Используйте пользователя `root` для шлюза Knox с паролем выше. `root` — это единственный пользователь, поддерживаемый этим методом обычной проверки подлинности (имя пользователя и пароль).
> Чтобы подключиться к SQL Server с обычной проверкой подлинности, используйте те же значения, что и для [переменных среды](#env) AZDATA_USERNAME и AZDATA_PASSWORD. 


После задания переменных среды нужно запустить `azdata bdc create`, чтобы активировать развертывание. В этом примере используется профиль конфигурации кластера, созданный ранее.

```bash
azdata bdc create --config-profile custom --accept-eula yes
```

Нужно учитывать следующее.

- Заключите пароль в двойные кавычки, если он содержит специальные символы. Вы можете задать для `AZDATA_PASSWORD` любое значение, но убедитесь, что пароль достаточно сложен и не содержит символы `!`, `&` или `'`. Обратите внимание, что разделители в виде двойных кавычек работают только в командах bash.
- Учетная запись `AZDATA_USERNAME` обладает правами системного администратора на главном экземпляре SQL Server, создаваемом во время установки. После создания контейнера SQL Server указанную вами переменную среды `AZDATA_PASSWORD` можно обнаружить, запустив `echo $AZDATA_PASSWORD` в контейнере. В целях безопасности измените пароль.

## <a id="unattended"></a> Автоматическая установка

Для автоматического развертывания нужно задать все необходимые переменные среды, использовать файл конфигурации и вызвать команду `azdata bdc create` с параметром `--accept-eula yes`. Примеры в предыдущем разделе демонстрируют синтаксис для автоматической установки.

## <a id="monitor"></a> Мониторинг развертывания

Во время начальной загрузки кластера командное окно клиента возвращает состояние развертывания. В процессе развертывания вы увидите ряд сообщений об ожидании pod контроллера.

```output
Waiting for cluster controller to start.
```

В течение 15–30 минут вы должны получить уведомление о том, что pod контроллера работает.

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> Полное развертывание может занять много времени из-за временных затрат на скачивание образов контейнеров для компонентов кластера больших данных. Однако это не должно занять несколько часов. При возникновении проблем с развертыванием см. статью [Мониторинг и устранение неполадок [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](cluster-troubleshooting-commands.md).

После завершения развертывания выходные данные указывают на успешное выполнение.

```output
Cluster deployed successfully.
```

> [!TIP]
> Именем по умолчанию для развернутого кластера больших данных является `mssql-cluster`, если только оно не изменено в пользовательской конфигурации.

## <a id="endpoints"></a> Получение конечных точек

После успешного завершения скрипта развертывания можно получить адреса внешних конечных точек для кластера больших данных, выполнив указанные ниже действия.

1. После развертывания найдите IP-адрес конечной точки контроллера либо в стандартных выходных данных развертывания, либо в выходных данных EXTERNAL-IP следующей команды `kubectl`.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Если вы не изменили имя по умолчанию во время развертывания, используйте `-n mssql-cluster` в предыдущей команде. `mssql-cluster` — это имя по умолчанию для кластера больших данных.

1. Войдите в кластер больших данных с помощью [azdata login](reference-azdata.md). Задайте для параметра `--endpoint` значение внешнего IP-адреса конечной точки контроллера.

   ```bash
   azdata login --endpoint https://<ip-address-of-controller-svc-external>:30080 --username <user-name>
   ```

   Укажите имя пользователя и пароль, настроенные для администратора кластера больших данных (AZDATA_USERNAME и AZDATA_PASSWORD) во время развертывания.

   > [!TIP]
   > Если вы являетесь администратором кластера Kubernetes и имеете доступ к файлу конфигурации кластера (файл конфигурации kube), можно настроить текущий контекст так, чтобы он указывал на целевой кластер Kubernetes. В этом случае можно выполнить вход с помощью `azdata login -n <namespaceName>`, где `namespace` — имя кластера больших данных. Вам будет предложено ввести учетные данные, если они не указаны в команде login.
   
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

Вы также можете получить все конечные точки службы, развернутые для кластера, выполнив следующую команду `kubectl`.

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

## <a id="status"></a> Проверка состояния кластера

После развертывания можно проверить состояние кластера с помощью команды [azdata bdc status show](reference-azdata-bdc-status.md).

```bash
azdata bdc status show
```

> [!TIP]
> Чтобы выполнить команды состояния, нужно сначала войти в систему с помощью команды `azdata login`, которая была приведена в предыдущем разделе о конечных точках.

Ниже приведен пример выходных данных этой команды.

```output
Bdc: ready                                                                                                                                                                                                          Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Services: ready                                                                                                                                                                                                     Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Servicename    State    Healthstatus    Details

 sql            ready    healthy         -
 hdfs           ready    healthy         -
 spark          ready    healthy         -
 control        ready    healthy         -
 gateway        ready    healthy         -
 app            ready    healthy         -


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
 storage-0       ready    healthy         StatefulSet storage-0 is healthy
 sparkhead       ready    healthy         StatefulSet sparkhead is healthy


 Spark Services: ready                                                                                                                                                                                               Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Control Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 controldb       ready    healthy         -
 control         ready    healthy         -
 metricsdc       ready    healthy         DaemonSet metricsdc is healthy
 metricsui       ready    healthy         ReplicaSet metricsui is healthy
 metricsdb       ready    healthy         StatefulSet metricsdb is healthy
 logsui          ready    healthy         ReplicaSet logsui is healthy
 logsdb          ready    healthy         StatefulSet logsdb is healthy
 mgmtproxy       ready    healthy         ReplicaSet mgmtproxy is healthy


 Gateway Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 gateway         ready    healthy         StatefulSet gateway is healthy


 App Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 appproxy        ready    healthy         ReplicaSet appproxy is healthy
```

Можно также получить более подробные сведения о состоянии с помощью следующих команд.

- Команда [azdata bdc control status show](reference-azdata-bdc-control-status.md) возвращает состояние работоспособности для всех компонентов, связанных со службой управления.
```
azdata bdc control status show
```
Образец вывода:
```output
Control: ready                                                                                                                                                                                                      Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Resources: ready                                                                                                                                                                                                    Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 controldb       ready    healthy         -
 control         ready    healthy         -
 metricsdc       ready    healthy         DaemonSet metricsdc is healthy
 metricsui       ready    healthy         ReplicaSet metricsui is healthy
 metricsdb       ready    healthy         StatefulSet metricsdb is healthy
 logsui          ready    healthy         ReplicaSet logsui is healthy
 logsdb          ready    healthy         StatefulSet logsdb is healthy
 mgmtproxy       ready    healthy         ReplicaSet mgmtproxy is healthy
```

- `azdata bdc sql status show` возвращает состояние работоспособности для всех ресурсов со службой SQL Server
```
azdata bdc sql status show
```
Образец вывода:
```output
Sql: ready                                                                                                                                                                                                          Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Resources: ready                                                                                                                                                                                                    Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 master          ready    healthy         StatefulSet master is healthy
 compute-0       ready    healthy         StatefulSet compute-0 is healthy
 data-0          ready    healthy         StatefulSet data-0 is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy
```

> [!IMPORTANT]
> При использовании параметра `--all` выходные данные этих команд содержат URL-адреса панелей мониторинга Kibana и Grafana для более подробного анализа.

В дополнение к использованию `azdata` можно также использовать Azure Data Studio для поиска конечных точек и сведений о состоянии. Дополнительные сведения о просмотре состояния кластера с помощью `azdata` и Azure Data Studio см. в статье [Просмотр состояния кластера больших данных](view-cluster-status.md).

## <a id="connect"></a> Подключение к кластеру

Дополнительные сведения о подключении к кластеру больших данных см. в статье [Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о развертывании кластера больших данных см. в следующих статьях.

- [Настройка параметров развертывания для кластеров больших данных](deployment-custom-configuration.md)
- [Выполнение автономного развертывания кластера больших данных SQL Server](deploy-offline.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
