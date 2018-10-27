---
title: Развертывание SQL Server больших данных кластеров Kubernetes | Документация Майкрософт
description: Дополнительные сведения о развертывании кластеров SQL Server 2019 больших данных (Предварительная версия) на платформе Kubernetes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: de19577b4a83bc10875bf56f4c0f2924828a00ea
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051186"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>Развертывание сервера SQL, большие данные кластера в Kubernetes

Кластер SQL Server больших данных могут развертываться как контейнеры docker в кластере Kubernetes. Это этапы установки и настройки:

- Настройка кластера Kubernetes в одной виртуальной Машине кластера виртуальных машин или в службе Azure Kubernetes (AKS).
- Установите средство конфигурации кластера **mssqlctl** на клиентском компьютере.
- Развертывание кластера больших данных SQL Server в кластере Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Необходимые условия для кластера Kubernetes

Кластера больших данных в SQL Server требуется версия минимальное v1.10 для Kubernetes, но для сервера и клиента. Чтобы установить определенную версию на клиент kubectl, см. в разделе [установки kubectl двоичных с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl).  Последние версии minikube и AKS, по крайней мере 1.10. Для AKS, необходимо использовать `--kubernetes-version` параметр для указания версии отличается от по умолчанию.

> [!NOTE]
> Обратите внимание на то, что Kubernetes версии клиента и сервера должны быть + 1 или -1, дополнительный номер версии. Дополнительные сведения см. в разделе [Kubernetes поддерживаемые выпуски и наклона компонент](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Настройка кластера Kubernetes

Если у вас уже есть кластер Kubernetes, отвечающий выше необходимые условия, то вы можете сразу переходить к [шаг развертывания](#deploy). В этом разделе требуется понимание основных концепций Kubernetes.  Подробные сведения о Kubernetes см. в разделе [документации по Kubernetes](https://kubernetes.io/docs/home).

Вы можете развернуть Kubernetes в любом из трех способов:

| Развертывание Kubernetes на: | Описание |
|---|---|
| **Minikube** | Кластер Kubernetes одного узла на виртуальной Машине. |
| **Службы Azure Kubernetes (AKS)** | Управляемой службы контейнеров Kubernetes в Azure. |
| **Несколько компьютеров** | Кластер Kubernetes, развернутых на физических компьютерах или виртуальных машин с помощью **kubeadm** |

Руководство по настройке по одному из этих параметров кластер Kubernetes для больших данных кластера SQL Server см. в следующих статьях:

   - [Настройка Minikube](deploy-on-minikube.md)
   - [Настройка Kubernetes в службе Azure Kubernetes](deploy-on-aks.md)
   - [Настройка Kubernetes на нескольких компьютерах с kubeadm](deploy-with-kubeadm.md)
   
> [!TIP]
> Пример скрипта python, выполняющий развертывание больших данных кластера AKS и SQL Server, см. в разделе [развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a id="deploy"></a> Развертывание кластера больших данных в SQL Server

После настройки кластера Kubernetes, вы можно приступить к развертыванию для больших данных кластера SQL Server. Чтобы развернуть кластер больших данных в Azure с помощью всех конфигураций по умолчанию для среды разработки и тестирования, следуйте инструкциям в этой статье:

[Краткое руководство: Развертывание кластера больших данных SQL Server в Kubernetes](quickstart-big-data-cluster-deploy.md)

Если вы хотите настроить конфигурацию кластера больших данных в соответствии с потребностями рабочей нагрузки, выполните следующий набор инструкций.

## <a name="verify-kubernetes-configuration"></a>Проверка конфигурации kubernetes

Запустите **kubectl** команду, чтобы просмотреть конфигурацию кластера. Убедитесь, что этот kubectl указывает контекст правильный кластера.

```bash
kubectl config view
```

## <a id="mssqlctl"></a> Установка mssqlctl

**mssqlctl** — программа командной строки, написанный на Python, что позволяет кластера администраторов для начальной загрузки и управления кластером больших данных с помощью REST API. Минимальная требуемая версия Python — версии 3.5. Необходимо также иметь `pip` , используемый для загрузки и установки **mssqlctl** средство. 

### <a name="windows-mssqlctl-installation"></a>Mssqlctl установки Windows

1. На клиенте Windows, скачайте необходимые пакеты Python из [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Python3.5.3 и более поздних версий pip3 также устанавливается одновременно с установкой Python. 

   > [!TIP] 
   > При установке Python3 выберите добавляемый путь к Python. Если этого не сделать, можно позже найти расположение pip3 и вручную добавить его в нужный путь.

1. Убедитесь, что у вас есть последнюю версию **запросы** пакета.

   ```cmd
   python -m pip install requests
   python -m pip install requests --upgrade
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```bash
   pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
   ```

### <a name="linux-mssqlctl-installation"></a>Установка mssqlctl Linux

В Linux, необходимо установить **python3** и **python3-pip** пакетов, а затем запустите `sudo pip3 install --upgrade pip`. Это устанавливает 3,5 последнюю версию Python и pip. В следующем примере показано, как эти команды будет работать для Ubuntu (Если вы используете другую платформу, измените команды для диспетчера пакетов):

1. Установите необходимые пакеты Python:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. Убедитесь, что у вас есть последнюю версию **запросы** пакета.

   ```bash
   sudo -H python3 -m pip install requests
   sudo -H python3 -m pip install requests --upgrade
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```bash
   pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
   ```

## <a name="define-environment-variables"></a>Определение переменных среды

Конфигурации кластера можно настроить, используя набор переменных среды, которые передаются `mssqlctl create cluster` команды. Большинство переменных среды являются необязательными, со значениями по умолчанию, как указано ниже. Обратите внимание, что переменные среды, такие как учетные данные, которые требуют ввода.

| Переменная среды | Обязательно | Значение по умолчанию | Описание |
|---|---|---|---|
| **ACCEPT_EULA** | Да | Недоступно | Примите лицензионное соглашение SQL Server (например, «Y»).  |
| **ИМЯ_КЛАСТЕРА** | Да | Недоступно | Имя пространства имен Kubernetes для развертывания кластера больших данных в SQLServer. |
| **CLUSTER_PLATFORM** | Да | Недоступно | Платформы, на которой развернут кластер Kubernetes. Может быть `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | Нет | 1 | Число реплик пула вычислений, чтобы выстроить. В CTP2.0 только табличные значения разрешено-1. |
| **CLUSTER_DATA_POOL_REPLICAS** | Нет | 2 | Количество данных пула реплик, чтобы выстроить. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | Нет | 2 | Число реплик пула хранения, чтобы выстроить. |
| **DOCKER_REGISTRY** | Да | TBD | Частный реестр, где хранятся образы, используемые для развертывания кластера. |
| **DOCKER_REPOSITORY** | Да | TBD | Частный репозиторий в реестре выше, где хранятся образы.  Он необходим в течение условная общедоступная Предварительная версия. |
| **DOCKER_USERNAME** | Да | Недоступно | Имя пользователя для доступа к образы контейнеров, в случае, если они хранятся в частный репозиторий. Он необходим в течение условная общедоступная Предварительная версия. |
| **DOCKER_PASSWORD** | Да | Недоступно | Пароль для доступа к выше частный репозиторий. Он необходим в течение условная общедоступная Предварительная версия.|
| **DOCKER_EMAIL** | Да | Недоступно | Электронная почта, связанная с выше частный репозиторий. Он необходим в течение неконтролируемые закрытой предварительной версии. |
| **DOCKER_IMAGE_TAG** | Нет | Последние | Метка, используемая для добавлять теги к изображениям. |
| **DOCKER_IMAGE_POLICY** | Нет | Всегда | Всегда принудительный операции извлечения образов.  |
| **DOCKER_PRIVATE_REGISTRY** | Да | 1 | Для тех же временных рамках условная общедоступная Предварительная версия это значение должно быть установлено в 1. |
| **CONTROLLER_USERNAME** | Да | Недоступно | Имя пользователя администратора кластера. |
| **CONTROLLER_PASSWORD** | Да | Недоступно | Пароль администратора кластера. |
| **KNOX_PASSWORD** | Да | Недоступно | Пароль для пользователя Knox. |
| **MSSQL_SA_PASSWORD** | Да | Недоступно | Пароль пользователя SA для главного экземпляра SQL. |
| **USE_PERSISTENT_VOLUME** | Нет | true | `true` для использования утверждения постоянного тома Kubernetes для хранения pod.  `false` Использование временных узлов хранилища для хранения pod. См. в разделе [постоянного хранения](concept-data-persistence.md) Дополнительные сведения. При развертывании SQL Server, большие данные кластера в minikube и USE_PERSISTENT_VOLUME = true, необходимо задать значение для `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | Нет | значение по умолчанию | Если `USE_PERSISTENT_VOLUME` является `true` это указывает на имя класса хранения Kubernetes для использования. См. в разделе [постоянного хранения](concept-data-persistence.md) Дополнительные сведения. При развертывании SQL Server, большие данные кластера в minikube, имя класса для хранения по умолчанию отличается, и его необходимо переопределить, задав `STORAGE_CLASS_NAME=standard`. |
| **MASTER_SQL_PORT** | Нет | 31433 | Порт TCP/IP, который ожидает передачи данных master экземпляра SQL в общедоступной сети. |
| **KNOX_PORT** | Нет | 30443 | Порт TCP/IP, который ожидает передачи данных Apache Knox в общедоступной сети. |
| **GRAFANA_PORT** | Нет | 30888 | Порт TCP/IP, который ожидает передачи данных Grafana, наблюдение за приложением в общедоступной сети. |
| **KIBANA_PORT** | Нет | 30999 | Порт TCP/IP, который прослушивает приложение поиска журнала Kibana в общедоступной сети. |

> [!IMPORTANT]
>1. В течение ограниченной закрытой предварительной версии, учетные данные для частного реестра Docker будет предоставляться вам после рассмотрения вашего [регистрации EAP](https://aka.ms/eapsignup).
>1. Для созданного локального кластера с помощью **kubeadm**, значение для переменной среды `CLUSTER_PLATFORM` является `kubernetes`. Кроме того, когда `USE_PERSISTENT_VOLUME=true`, необходимо предварительно подготовить класс хранения Kubernetes и передать его с помощью `STORAGE_CLASS_NAME`.
>1. Убедитесь, что перенос паролей в двойные кавычки, если он содержит специальные символы. Можно присвоить любое MSSQL_SA_PASSWORD, но убедитесь, что они достаточно сложны и не используйте `!`, `&` или `‘` символов. Обратите внимание, что двойные кавычки-разделители работают только в команды bash.
>1. Имя кластера должно быть только буквенно цифровые символы в нижнем регистре, не должно быть пробелов. Все артефакты Kubernetes (контейнеры, модулей, вертикальное наборов, службы) для кластера будет создан в пространство имен с тем же именем, что и кластер указанное имя.
>1. **SA** учетная запись является администратором системы на экземпляре SQL Server Master, которая создается во время установки. После создания контейнера SQL Server, переменную среды MSSQL_SA_PASSWORD, которое вы указали будет обнаружить, выполнив вывод на экран MSSQL_SA_PASSWORD $ в контейнере. В целях безопасности смените пароль SA в соответствии с практическими рекомендациями, описанными [здесь](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Задание переменных среды, необходимые для развертывания кластера больших данных, зависит от ли вы используете клиент Windows или Linux.  Выберите следующие действия, в зависимости от того, какая операционная система используется.

Инициализировать следующие переменные среды, которые требуются для развертывания кластера:

### <a name="windows"></a>Windows

С помощью окна командной строки (не PowerShell), настройте следующие переменные среды. Не используйте кавычки вокруг значений.

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linux"></a>Linux

Инициализируйте следующие переменные среды. В bash можно использовать кавычки вокруг каждого значения.

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME="<controller_admin_name – can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password – can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password – can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your Docker email, use the username provided by Microsoft>"
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
mssqlctl create cluster <name of your cluster>
```

Во время начальной загрузки кластера командное окно клиента будет выводить состояние развертывания. Можно также проверить состояние развертывания, выполнив следующие команды в окне командной строки различные:

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

Вы увидите более детализированные состоянии и конфигурации для каждого модуля, выполнив:
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

После запуска контроллера pod можно использовать вкладку "Развертывание" на портале администрирования кластера для мониторинга развертывания.

## <a id="masterip"></a> Получите экземпляр SQL Server Master и IP-адреса кластера больших данных SQL Server

После успешного выполнения сценария развертывания, можно получить IP-адрес главного экземпляра SQL Server, используя шаги, описанные ниже. Этот IP-адрес и порт номер 31433 будет использовать для подключения к основной экземпляр SQL Server (например:  **\<ip адрес\>, 31433**). Аналогичным образом, для больших объемов данных SQL Server IP-адрес кластера. На вкладке "конечные точки службы" на портале администрирования кластера также описаны все конечные точки кластера. На портале администрирования кластера можно использовать для мониторинга развертывания. Доступны на портале с помощью внешних IP-адрес и порт номер для `service-proxy-lb` (например: **https://\<ip адрес\>: 30777**). Учетные данные для доступа к порталу администрирования являются значениями `CONTROLLER_USERNAME` и `CONTROLLER_PASSWORD` переменные среды, приведенные выше.

### <a name="aks"></a>AKS

Если вы используете AKS, Azure предоставляет службы Azure Подсистема балансировки нагрузки. Выполните следующую команду:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

Найдите **External-IP** значение, присвоенное к службе. Затем подключитесь к основной экземпляр SQL Server с помощью IP-адрес на порте 31433 (например:  **\<ip адрес\>, 31433**) и SQL Server конечную точку кластера больших данных с помощью external-IP для `service-security-lb` службы. 

### <a name="minikube"></a>Minikube

Если вы используете Minikube, необходимо выполнить следующую команду, чтобы получить IP-адрес, необходимые для подключения к. В дополнение к IP-адрес укажите порт для конечной точки, необходимые для подключения к. Чтобы получить все конечные точки службы для 

```bash
minikube ip
```

Независимо от платформы запуске кластера Kubernetes, чтобы получить все конечные точки служб, развернутых для кластера, выполните следующую команду:
```bash
kubectl get svc -n <name of your cluster>
```

## <a name="next-steps"></a>Следующие шаги

После успешного развертывания SQL Server, больших данных кластера Kubernetes, [установите средства работы с большими данными](deploy-big-data-tools.md) и ознакомьтесь с некоторыми новыми возможностями и узнайте [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).
