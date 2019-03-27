---
title: Развертывание
titleSuffix: SQL Server 2019 big data clusters
description: Дополнительные сведения о развертывании кластеров SQL Server 2019 больших данных (Предварительная версия) на платформе Kubernetes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: fb09a5b13adc7f673c83a91635451435e4a8c945
ms.sourcegitcommit: 715683b5fc7a8e28a86be8949a194226b72ac915
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477699"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Развертывание кластеров больших данных SQL Server в Kubernetes

Кластер SQL Server больших данных могут развертываться как контейнеры docker в кластере Kubernetes. Это этапы установки и настройки:

- Настройка кластера Kubernetes в одной виртуальной Машине кластера виртуальных машин или в службе Azure Kubernetes (AKS).
- Установите средство конфигурации кластера **mssqlctl** на клиентском компьютере.
- Развертывание кластера больших данных SQL Server в кластере Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Необходимые условия для кластера Kubernetes

Кластерами больших данных SQL Server требуется по меньшей мере минимальной версии Kubernetes v1.10 для сервера и клиента (kubectl).

> [!NOTE]
> Обратите внимание на то, что Kubernetes версии клиента и сервера должны быть + 1 или -1, дополнительный номер версии. Дополнительные сведения см. в разделе [Kubernetes поддерживаемые выпуски и наклона компонент](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Настройка кластера Kubernetes

Если у вас уже есть кластер Kubernetes, отвечающий выше необходимые условия, то вы можете сразу переходить к [шаг развертывания](#deploy). В этом разделе требуется понимание основных концепций Kubernetes.  Подробные сведения о Kubernetes см. в разделе [документации по Kubernetes](https://kubernetes.io/docs/home).

Вы можете развернуть Kubernetes в любом из трех способов:

| Развертывание Kubernetes на: | Описание | Ссылка |
|---|---|---|
| **Minikube** | Кластер Kubernetes одного узла на виртуальной Машине. | [Инструкции](deploy-on-minikube.md) |
| **Службы Azure Kubernetes (AKS)** | Управляемой службы контейнеров Kubernetes в Azure. | [Инструкции](deploy-on-aks.md) |
| **Несколько компьютеров** | Кластер Kubernetes, развернутых на физических компьютерах или виртуальных машин с помощью **kubeadm** | [Инструкции](deploy-with-kubeadm.md) |
  
> [!TIP]
> Пример скрипта python, выполняющий развертывание больших данных кластера AKS и SQL Server, см. в разделе [развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="deploy-sql-server-2019-big-data-tools"></a>Развертывание средств SQL Server 2019 больших данных

Перед развертыванием кластера SQL Server 2019 больших данных, сначала [установите средства работы с большими данными](deploy-big-data-tools.md):
- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **Расширение SQL Server 2019**

## <a id="deploy"></a> Развертывание кластера больших данных в SQL Server

После настройки кластера Kubernetes, вы можно приступить к развертыванию для больших данных кластера SQL Server. 

> [!NOTE]
> Если при обновлении с предыдущей версии, ознакомьтесь с разделом [обновления этой статьи](#upgrade).

Чтобы развернуть кластер больших данных в Azure с помощью всех конфигураций по умолчанию для среды разработки и тестирования, следуйте инструкциям в этой статье:

[Краткое руководство. Развертывание кластера больших данных SQL Server в Kubernetes](quickstart-big-data-cluster-deploy.md)

Если вы хотите настроить развертывание кластера больших данных в соответствии с вашей рабочей нагрузки потребности, следуйте указаниям в оставшейся части этой статьи.

## <a name="verify-kubernetes-configuration"></a>Проверка конфигурации kubernetes

Запустите **kubectl** команду, чтобы просмотреть конфигурацию кластера. Убедитесь, что этот kubectl указывает контекст правильный кластера.

```bash
kubectl config view
```

## <a id="env"></a> Определение переменных среды

Конфигурации кластера можно настроить, используя набор переменных среды, которые передаются `mssqlctl create cluster` команды. Большинство переменных среды являются необязательными, со значениями по умолчанию, как указано ниже. Обратите внимание, что переменные среды, такие как учетные данные, которые требуют ввода.

| Переменная среды | Обязательно | Значение по умолчанию | Описание |
|---|---|---|---|
| **ACCEPT_EULA** | Да | Н/Д | Примите лицензионное соглашение SQL Server (например, «Да»).  |
| **CLUSTER_NAME** | Да | Н/Д | Имя пространства имен Kubernetes для развертывания кластера больших данных в SQLServer. |
| **CLUSTER_PLATFORM** | Да | Н/Д | Платформы, на которой развернут кластер Kubernetes. Может быть `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | Нет | 1 | Число реплик пула вычислений, чтобы выстроить. В CTP-версии 2.3 только табличные значения допускается-1. |
| **CLUSTER_DATA_POOL_REPLICAS** | Нет | 2 | Количество данных пула реплик, чтобы выстроить. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | Нет | 2 | Число реплик пула хранения, чтобы выстроить. |
| **DOCKER_REGISTRY** | Да | TBD | Частный реестр, где хранятся образы, используемые для развертывания кластера. |
| **DOCKER_REPOSITORY** | Да | TBD | Частный репозиторий в реестре выше, где хранятся образы.  Он необходим в течение условная общедоступная Предварительная версия. |
| **DOCKER_USERNAME** | Да | Н/Д | Имя пользователя для доступа к образы контейнеров, в случае, если они хранятся в частный репозиторий. Он необходим в течение условная общедоступная Предварительная версия. |
| **DOCKER_PASSWORD** | Да | Н/Д | Пароль для доступа к выше частный репозиторий. Он необходим в течение условная общедоступная Предварительная версия.|
| **DOCKER_EMAIL** | Да | Н/Д | Адрес электронной почты. |
| **DOCKER_IMAGE_TAG** | Нет | Последние | Метка, используемая для добавлять теги к изображениям. |
| **DOCKER_IMAGE_POLICY** | Нет | Всегда | Всегда принудительный операции извлечения образов.  |
| **DOCKER_PRIVATE_REGISTRY** | Да | Н/Д | Для тех же временных рамках условная общедоступная Предварительная версия необходимо задать это значение «1». |
| **CONTROLLER_USERNAME** | Да | Н/Д | Имя пользователя администратора кластера. |
| **CONTROLLER_PASSWORD** | Да | Н/Д | Пароль администратора кластера. |
| **KNOX_PASSWORD** | Да | Н/Д | Пароль для пользователя Knox. |
| **MSSQL_SA_PASSWORD** | Да | Н/Д | Пароль пользователя SA для главного экземпляра SQL. |
| **USE_PERSISTENT_VOLUME** | Нет | true | `true` для использования утверждения постоянного тома Kubernetes для хранения pod.  `false` Использование временных узлов хранилища для хранения pod. См. в разделе [постоянного хранения](concept-data-persistence.md) Дополнительные сведения. При развертывании SQL Server, большие данные кластера в minikube и USE_PERSISTENT_VOLUME = true, необходимо задать значение для `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | Нет | значение по умолчанию | Если `USE_PERSISTENT_VOLUME` является `true` это указывает на имя класса хранения Kubernetes для использования. См. в разделе [постоянного хранения](concept-data-persistence.md) Дополнительные сведения. При развертывании SQL Server, большие данные кластера в minikube, имя класса для хранения по умолчанию отличается, и его необходимо переопределить, задав `STORAGE_CLASS_NAME=standard`. |
| **CONTROLLER_PORT** | Нет | 30080 | Порт TCP/IP, который прослушивает служба контроллера в общедоступной сети. |
| **MASTER_SQL_PORT** | Нет | 31433 | Порт TCP/IP, который ожидает передачи данных master экземпляра SQL в общедоступной сети. |
| **KNOX_PORT** | Нет | 30443 | Порт TCP/IP, который ожидает передачи данных Apache Knox в общедоступной сети. |
| **PROXY_PORT** | Нет | 30777 | Порт TCP/IP, служба прокси-сервер ожидает передачи данных в общедоступной сети. Это порт, используемый для вычисления на портале URL-адрес. |
| **GRAFANA_PORT** | Нет | 30888 | Порт TCP/IP, который ожидает передачи данных Grafana, наблюдение за приложением в общедоступной сети. |
| **KIBANA_PORT** | Нет | 30999 | Порт TCP/IP, который прослушивает приложение поиска журнала Kibana в общедоступной сети. |


> [!IMPORTANT]
>1. В течение ограниченной закрытой предварительной версии, учетные данные для частного реестра Docker будет предоставляться вам после рассмотрения вашего [регистрации EAP](https://aka.ms/eapsignup).
>1. Для созданного локального кластера с помощью **kubeadm**, значение для переменной среды `CLUSTER_PLATFORM` является `kubernetes`. Кроме того, когда `USE_PERSISTENT_VOLUME=true`, необходимо предварительно подготовить класс хранения Kubernetes и передать его с помощью `STORAGE_CLASS_NAME`.
>1. Убедитесь, что перенос паролей в двойные кавычки, если он содержит специальные символы. Можно присвоить любое MSSQL_SA_PASSWORD, но убедитесь, что они достаточно сложны и не используйте `!`, `&` или `'` символов. Обратите внимание, что двойные кавычки-разделители работают только в команды bash.
>1. Имя кластера должно быть только буквенно цифровые символы в нижнем регистре, не должно быть пробелов. Все артефакты Kubernetes (контейнеры, модулей, вертикальное наборов, службы) для кластера будет создан в пространство имен с тем же именем, что и кластер указанное имя.
>1. **SA** учетная запись является администратором системы на экземпляре SQL Server Master, которая создается во время установки. После создания контейнера SQL Server, переменную среды MSSQL_SA_PASSWORD, которое вы указали будет обнаружить, выполнив вывод на экран MSSQL_SA_PASSWORD $ в контейнере. В целях безопасности смените пароль SA в соответствии с практическими рекомендациями, описанными [здесь](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Задание переменных среды, необходимые для развертывания кластера больших данных, зависит от ли вы используете клиент Windows или Linux.  Выберите следующие действия, в зависимости от того, какая операционная система используется.

Инициализировать следующие переменные среды, которые требуются для развертывания кластера:

### <a name="windows"></a>Windows

С помощью окна командной строки (не PowerShell), настройте следующие переменные среды. Не используйте кавычки вокруг значений.

```cmd
SET ACCEPT_EULA=yes
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your email address>
SET DOCKER_PRIVATE_REGISTRY=1
```

### <a name="linux"></a>Linux

Инициализируйте следующие переменные среды. В bash можно использовать кавычки вокруг каждого значения.

```bash
export ACCEPT_EULA="yes"
export CLUSTER_PLATFORM="<minikube or aks or kubernetes>"

export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your email address>"
export DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="minikube-settings"></a>Параметры Minikube

Если развертывается в minikube и `USE_PERSISTENT_VOLUME=true` (по умолчанию), необходимо также переопределить значение по умолчанию для `STORAGE_CLASS_NAME` переменной среды.

Для развертываний minikube, используйте следующую команду на Windows:

```cmd
SET STORAGE_CLASS_NAME=standard
```

Для развертываний minikube, используйте следующую команду в Linux:

```bash
export STORAGE_CLASS_NAME=standard
```

Кроме того, можно отключить использование постоянных томов на minikube, установив `USE_PERSISTENT_VOLUME=false`.

### <a name="kubadm-settings"></a>Параметры Kubadm

При развертывании с kubeadm на собственных физических или виртуальных машин, необходимо предварительно подготовить класс хранения Kubernetes и передать его с помощью `STORAGE_CLASS_NAME`. Кроме того, можно отключить использование постоянных томов, установив `USE_PERSISTENT_VOLUME=false`. Дополнительные сведения о постоянном хранилище, см. в разделе [сохранение данных с SQL Server, большие данные кластера в Kubernetes](concept-data-persistence.md).

## <a name="deploy-sql-server-big-data-cluster"></a>Развертывание кластера больших данных SQL Server

API создания кластера используется для инициализации пространств имен Kubernetes и развернуть всех модулях приложения в пространстве имен. Чтобы развернуть кластер больших данных SQL Server в кластере Kubernetes, выполните следующую команду:

```bash
mssqlctl cluster create --name <your-cluster-name>
```

Во время начальной загрузки кластера командное окно клиента будет выводить состояние развертывания. Во время развертывания вы увидите ряд сообщений где ожидает pod контроллера:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Через 10 – 20 минут вы должны быть уведомлены выполняющийся модуль контроллера:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> Всего развертывание может занять много времени из-за время, необходимое для загрузки образов контейнеров для компонентов кластера больших данных. Тем не менее он должен занять несколько часов. При возникновении проблем с развертыванием, см. в разделе [Устранение неполадок](#troubleshoot) этой статьи, чтобы узнать, как отслеживать и проверить развертывания.

После завершения развертывания, уведомляет о выходных данных успеха.

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

## <a id="masterip"></a> Получение конечных точек кластера больших данных

После успешного выполнения сценария развертывания, можно получить IP-адрес главного экземпляра SQL Server, используя шаги, описанные ниже. Этот IP-адрес и порт номер 31433 будет использовать для подключения к основной экземпляр SQL Server (например:  **\<ip-address-of-endpoint-master-pool\>, 31433**). Аналогичным образом, можно подключиться к SQL Server, IP-адреса кластера (шлюз HDFS или Spark) больших данных связанные с **безопасности конечных точек** службы.

Следующие команды kubectl Получение общих конечных точек для больших данных кластера:

```bash
kubectl get svc endpoint-master-pool -n <your-cluster-name>
kubectl get svc endpoint-security -n <your-cluster-name>
kubectl get svc endpoint-service-proxy -n <your-cluster-name>
```

Найдите **External-IP** значение, назначенное для каждой службы.

Кроме того, здесь все конечные точки кластера в **конечные точки службы** на портале администрирования кластера. Доступны на портале с помощью внешних IP-адрес и порт номер для `endpoint-service-proxy` (например: **https://\<ip-address-of-endpoint-service-proxy\>: 30777: портал**). Учетные данные для доступа к порталу администрирования являются значениями `CONTROLLER_USERNAME` и `CONTROLLER_PASSWORD` переменные среды, приведенные выше. На портале администрирования кластера также можно отслеживать развертывание.

Дополнительные сведения о подключении см. в разделе [соединиться с сервером SQL кластера больших данных с помощью Azure Data Studio](connect-to-big-data-cluster.md).

### <a name="minikube"></a>Minikube

Если вы используете Minikube, необходимо выполнить следующую команду, чтобы получить IP-адрес, необходимые для подключения к. В дополнение к IP-адрес укажите порт для конечной точки, необходимые для подключения к. Чтобы получить все конечные точки службы для 

```bash
minikube ip
```

Независимо от платформы запуске кластера Kubernetes, чтобы получить все конечные точки служб, развернутых для кластера, выполните следующую команду:
```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="upgrade"></a> Обновление до нового выпуска

В настоящее время единственный способ обновления до нового выпуска кластерам больших данных — вручную удаления и повторного создания кластера. Каждый выпуск содержит уникальной версии **mssqlctl** , не совместим с предыдущей версией. Кроме того Если кластер старых нужно было загрузить изображения на новый узел, последний образ может оказаться несовместимым с старые образы в кластере. Чтобы обновить до последней версии, следуйте инструкциям ниже:

1. Перед удалением старого кластера, резервное копирование данных на экземпляре SQL Server master и в HDFS. Для главного экземпляра SQL Server, можно использовать [Архивация и восстановление SQL Server](data-ingestion-restore-database.md). Для HDFS вы [можно скопировать данные с **curl**](data-ingestion-curl.md).

1. Удалите старый кластер с `mssqlctl delete cluster` команды.

   ```bash
    mssqlctl cluster delete --name <old-cluster-name>
   ```

   > [!Important]
   > Используйте версию **mssqlctl** , соответствующий кластер. Не удаляйте кластер старых с новой версией **mssqlctl**.

1. Удалите все старые версии **mssqlctl**.

   ```bash
   pip3 uninstall mssqlctl
   ```

   > [!IMPORTANT]
   > Не следует устанавливать новую версию **mssqlctl** не удалив сначала все более ранние версии.

1. Установите последнюю версию **mssqlctl**. 

   **Windows:**

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

   **Linux:**

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt --user
   ```

   > [!IMPORTANT]
   > Для каждого выпуска, путь к **mssqlctl** изменения. Даже если вы ранее установили **mssqlctl**, необходимо переустановить из последней пути перед созданием нового кластера.

1. Установите последнюю версию, следуя инструкциям из раздела [развернуть раздел](#deploy) этой статьи. 

## <a id="troubleshoot"></a> Мониторинг и устранение неполадок

Чтобы отслеживать или устранения проблемы развертывания, используйте **kubectl** проверке состояния кластера и для выявления потенциальных проблем. В любое время, во время развертывания можно открыть другой командное окно, чтобы выполнить следующие тесты.

1. Проверьте статус POD, содержащихся в кластере.

   ```cmd
   kubectl get pods -n <your-cluster-name>
   ```

   Во время развертывания модулей с **состояние** из **ContainerCreating** по-прежнему в ближайшее время. Если развертывание перестает отвечать на запросы по любой причине, это может послужить идею где проблема может быть. Также рассмотрим **ГОТОВЫ** столбца. Это означает, сколько контейнеров начали в pod. Обратите внимание на то, что развертывание может занять 30 минут или более в зависимости от вашей конфигурации и сети. Основная часть этого времени расходуется загрузки образов контейнеров для различных компонентов. В следующей таблице показаны изменить пример выходных данных два контейнера во время развертывания:

   ```output
   PS C:\> kubectl get pods -n sbdc8
   NAME                                     READY   STATUS              RESTARTS   AGE
   mssql-controller-h79ft                   4/4     Running             0          13m
   mssql-storage-pool-default-0             0/7     ContainerCreating   0          6m
   ```

1. Описания отдельных pod для получения дополнительных сведений. Следующая команда проверяет `mssql-storage-pool-default-0` pod.

   ```cmd
   kubectl describe pod mssql-storage-pool-default-0 -n <your-cluster-name>
   ```

   Это выводит подробные сведения о pod, включая последние события. Если произошла ошибка, иногда можно найти здесь ошибку.

1. Получить журналы для контейнеров, запущенных в модуле. Следующая команда извлекает журналы для всех контейнеров, запущенных в модуль с именем `mssql-storage-pool-default-0` и выводит их в файл с именем `pod-logs.txt`:

   ```cmd
   kubectl logs mssql-storage-pool-default-0 --all-containers=true -n <your-cluster-name> > pod-logs.txt
   ```

1. Просмотрите службы кластеров, во время и после развертывания с помощью следующей команды:

   ```cmd
   kubectl get svc -n <your-cluster-name>
   ```

   Эти службы поддерживают внутренние и внешние подключения к кластеру больших данных. Для внешних подключений используются следующие службы:

   | Служба | Описание |
   |---|---|
   | **endpoint-master-pool** | Предоставляет доступ к основной экземпляр.<br/>(**EXTERNAL-IP, 31433** и **SA** пользователя) |
   | **Конечная точка контроллер** | Поддержка средств и клиентов, управления кластером. |
   | **endpoint-service-proxy** | Предоставляет доступ к [портал администрирования кластера](cluster-admin-portal.md).<br/>(https://**EXTERNAL-IP**: 30777: портал)|
   | **endpoint-security** | Предоставляет доступ к шлюзу HDFS или Spark.<br/>(**EXTERNAL-IP** и **корневой** пользователя) |

1. Используйте [портал администрирования кластера](cluster-admin-portal.md) мониторинге развертывания на **развертывания** вкладки. Вам придется ждать для **конечная точка службы прокси-сервера** службы для запуска до доступа к этому порталу, поэтому он не будет доступен в начале развертывания.

> [!TIP]
> Дополнительные сведения об устранении неполадок кластера см. в разделе [команды Kubectl для наблюдения и диагностики кластеров SQL Server с большими данными](cluster-troubleshooting-commands.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. следующие ресурсы:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
- [Семинар: Кластерами больших данных Microsoft SQL Server архитектуры](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)