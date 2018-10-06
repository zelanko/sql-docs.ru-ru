---
title: Развертывание кластера больших данных в SQL Server в Kubernetes | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 4db726ac3ceab7649b0a3c04b2c4647b83c7e660
ms.sourcegitcommit: 8aecafdaaee615b4cd0a9889f5721b1c7b13e160
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2018
ms.locfileid: "48818072"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>Развертывание кластера больших данных в SQL Server в Kubernetes

Кластер SQL Server больших данных могут развертываться как контейнеры docker в кластере Kubernetes. Это этапы установки и настройки:

- Настройка кластера Kubernetes в одиночной ВМ, кластер виртуальных машин или в службе контейнеров Azure
- Установите средство конфигурации кластера `mssqlctl` на клиентском компьютере
- Развертывание кластера больших данных в SQL Server в кластере Kubernetes

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="kubernetes-prerequisistes"></a>Kubernetes prerequisistes

Кластера больших данных в SQL Server требуется версия минимальное v1.10 для Kubernetes, но для сервера и клиента. Чтобы установить определенную версию на клиент kubectl, см. в разделе [установки kubectl двоичных с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl).  Последние версии minikube и AKS, по крайней мере 1.10. Для AKS необходимо использовать `--kubernetes-version` параметр для указания версии отличается от по умолчанию.

Кроме того Обратите внимание, что версия клиента и сервера Kubernetes наклонить, т. е поддерживается +/-1 дополнительный номер версии. В документации по Kubernetes состояния «клиент должен быть неравномерно распределенных не более чем один дополнительный номер версии с главного сервера, что может привести образце, на один дополнительный номер версии. Например, версия 1.3 главной должны работать с версии 1.1, версия 1.2 и версия 1.3 узлов и должны работать с версии 1.2, версия 1.3 и клиентов версии 1.4.» Дополнительные сведения см. в разделе [Kubernetes поддерживаемые выпуски и наклона компонент](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Настройка кластера Kubernetes

Если у вас уже есть кластер Kubernetes, отвечающий выше необходимые условия, то вы можете сразу переходить к [шаг развертывания](#deploy). В этом разделе требуется понимание основных концепций Kubernetes.  Подробные сведения о Kubernetes см. в разделе [документации по Kubernetes](https://kubernetes.io/docs/home).

Вы можете развернуть Kubernetes в любом из трех способов:

| Развертывание Kubernetes на: | Описание |
|---|---|
| **Minikube** | Кластер Kubernetes одного узла на виртуальной Машине. |
| **Службы Azure Kubernetes (AKS)** | Управляемой службы контейнеров Kubernetes в Azure. |
| **Несколько виртуальных машин** | Кластер Kubernetes, развернутых на виртуальных машинах, с помощью kubeadm |

Руководство по настройке по одному из этих параметров кластер Kubernetes для кластера SQL Server больших данных см. в следующих статьях:

   - [Настройка Minikube](deploy-on-minikube.md)
   - [Настройка Kubernetes в службе Azure Kubernetes](deploy-on-aks.md)

## <a id="deploy"></a> Развертывание кластера больших данных в SQL Server

После настройки кластера Kubernetes, вы можно приступить к развертыванию для кластера SQL Server больших данных. Чтобы развернуть кластер Aris всех конфигурациях по умолчанию для среды разработки и тестирования, следуйте инструкциям в этой статье:

[Краткое руководство по Развертыванию Aris SQL Server в Kubernetes](quickstart-big-data-cluster-deploy.md)

Если вы хотите настроить конфигурацию Aris в соответствии с потребностями рабочей нагрузки, выполните следующий набор инструкций.

## <a name="verify-kubernetes-configuration"></a>Проверка конфигурации kubernetes

Выполните указанную ниже команду kubectl для просмотра конфигурации кластера. Убедитесь, что этот kubectl указывает контекст правильный кластера.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool-for-sql-server-big-data-cluster"></a>Установка средства управления mssqlctl интерфейса командной строки для кластера SQL Server больших данных
`mssqlctl` создается программа командной строки на языке Python, который позволяет администраторам кластера для начальной загрузки и управления кластером больших данных с помощью REST API. Минимальная требуемая версия Python — версии 3.5. Необходимо также иметь `pip` , используемый для загрузки и установки `mssqlctl` средство. На клиенте Windows, можно загрузить необходимые пакеты Python из [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Python3.5.3 и более поздних версий pip3 также устанавливается одновременно с установкой Python. При установке его добавить в путь невозможно выбрать. Затем можно найти, где расположен pip3 и вручную добавить путь.
В Linux (WSL или Ubuntu клиент для примера) эти команды установит 3,5 последнюю версию Python и pip:

```bash
sudo apt-get update
sudo apt-get install python3
sudo apt-get install python3-pip
sudo pip3 install --upgrade pip
```

> [!NOTE]
Если отсутствует установку Python `requests` пакета, необходимо установить `requests` с помощью `python -m pip install requests`. Если у вас уже есть `requests` пакет установлен, убедитесь, что вы используете последнюю версию, выполнив `python -m pip install requests --upgrade`.

Выполните следующую команду, чтобы установить msqlctl:

```bash
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
```

## <a name="define-environment-variables"></a>Определение переменных среды

Конфигурации кластера можно настроить, используя набор переменных среды, которые передаются `mssqlctl create cluster` команды. Большинство переменных среды являются необязательными для avalues по умолчанию, как указано ниже. Обратите внимание, что переменные среды, такие как учетные данные, которые требуют ввода.

| Переменная среды | Обязательно | Значение по умолчанию | Описание |
|---|---|---|---|
| **ACCEPT_EULA** | Да | Недоступно | Примите лицензионное соглашение SQL Server (например, «Y»).  |
| **ИМЯ_КЛАСТЕРА** | Да | Недоступно | Имя пространства имен для развертывания кластера больших данных SQLServer в Kubernetes. |
| **CLUSTER_PLATFORM** | Да | Недоступно | Платформы, на которой развернут кластер Kubernetes. Может быть `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | Нет | 1 | Число реплик пула вычислений, чтобы выстроить. В CTP2.0 только табличные значения разрешено-1. |
| **CLUSTER_DATA_POOL_REPLICAS** | Нет | 2 | Количество данных пула реплик, чтобы выстроить. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | Нет | 2 | Число реплик пула хранения, чтобы выстроить. |
| **DOCKER_REGISTRY** | Да | TBD | Частный реестр, где хранятся образы, используемые для развертывания кластера. |
| **DOCKER_REPOSITORY** | Да | TBD | Частный репозиторий в реестре выше, где хранятся образы.  Он необходим в течение условная общедоступная Предварительная версия. |
| **DOCKER_USERNAME** | Да | Недоступно | Имя пользователя для доступа к образы контейнеров, в случае, если они хранятся в частный репозиторий. Он необходим в течение условная общедоступная Предварительная версия. |
| **DOCKER_PASSWORD** | Да | Недоступно | Пароль для доступа к выше частный репозиторий. Он необходим в течение условная общедоступная Предварительная версия.|
| **DOCKER_EMAIL** | Да | Недоступно | Электронная почта, связанная с выше частный репозиторий. Он необходим в течение неконтролируемые закрытой предварительной версии. |
| **DOCKER_IMAGE_TAG** | Нет | Последние | Метка, использованные для пометки изображений. |
| **DOCKER_IMAGE_POLICY** | Нет | Всегда | Всегда принудительный операции извлечения образов.  |
| **DOCKER_PRIVATE_REGISTRY** | Да | 1 | Для тех же временных рамках условная общедоступная Предварительная версия это значение должно быть установлено в 1. |
| **CONTROLLER_USERNAME** | Да | Недоступно | Имя пользователя администратора кластера. |
| **CONTROLLER_PASSWORD** | Да | Недоступно | Пароль администратора кластера. |
| **KNOX_PASSWORD** | Да | Недоступно | Пароль для пользователя Knox. |
| **MSSQL_SA_PASSWORD** | Да | Недоступно | Пароль для пользователя SA для главного экземпляра SQL. |
| **USE_PERSISTENT_VOLUME** | Нет | true | `true` для использования утверждения постоянного тома Kubernetes для хранения pod.  `false` Использование временных узлов хранилища для хранения pod. См. в разделе [постоянного хранения](concept-data-persistence.md) Дополнительные сведения. |
| **STORAGE_CLASS_NAME** | Нет | значение по умолчанию | Если `USE_PERSISTENT_VOLUME` является `true` это указывает на имя класса хранения Kubernetes для использования. См. в разделе [постоянного хранения](concept-data-persistence.md) Дополнительные сведения. |
| **MASTER_SQL_PORT** | Нет | 31433 | Порт TCP/IP, который ожидает передачи данных master экземпляра SQL в общедоступной сети. |
| **KNOX_PORT** | Нет | 30443 | Порт TCP/IP, который ожидает передачи данных Apache Knox в общедоступной сети. |
| **GRAFANA_PORT** | Нет | 30888 | Порт TCP/IP, который ожидает передачи данных Grafana, наблюдение за приложением в общедоступной сети. |
| **KIBANA_PORT** | Нет | 30999 | Порт TCP/IP, который прослушивает приложение поиска журнала Kibana в общедоступной сети. |



> [!IMPORTANT]
>1. В течение ограниченной закрытой предварительной версии, учетные данные для частного реестра Docker будет предоставляться вам после рассмотрения вашего [регистрации EAP](https://aka.ms/eapsignup).
>1. Для локального кластера, созданного с помощью kubeadm, значение для переменной среды `CLUSTER_PLATFORM` является `kubernetes`. Кроме того, если USE_PERSISTENT_STORAGE = true, необходимо предварительно подготовить класс хранения Kubernetes и передать его с помощью STORAGE_CLASS_NAME.
>1. Убедитесь, что перенос паролей в двойные кавычки, если он содержит специальные символы. Можно присвоить любое MSSQL_SA_PASSWORD, но убедитесь, что они достаточно сложны и не используйте `!`, `&` или `‘` символов. Обратите внимание, что двойные кавычки-разделители работают только в команды bash.
>1. Имя кластера должно быть только буквенно цифровые символы в нижнем регистре, не должно быть пробелов. Все артефакты Kubernetes (контейнеры, модулей, вертикальное наборов, службы) для кластера будет создан в пространство имен с тем же именем, что и кластер указанное имя.
>1. **SA** учетная запись является администратором системы на экземпляре SQL Server Master, которая создается во время установки. После создания контейнера SQL Server, переменную среды MSSQL_SA_PASSWORD, которое вы указали будет обнаружить, выполнив вывод на экран MSSQL_SA_PASSWORD $ в контейнере. В целях безопасности смените пароль SA в соответствии с практическими рекомендациями, описанными [здесь](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Задание переменных среды, необходимые для развертывания Aris кластера отличается в зависимости от того, используете ли вы клиент Windows или Linux.  Выберите следующие действия, в зависимости от того, какая операционная система используется.

Инициализировать следующие переменные среды, которые требуются для развертывания кластера:

### <a name="windows"></a>Windows

С помощью окна командной строки (не PowerShell), настройте следующие переменные среды:

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instances>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username>
SET DOCKER_PASSWORD=<your password>
SET DOCKER_EMAIL=<your Docker email, use same as username provided>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linux"></a>Linux

Инициализируйте следующие переменные среды:

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instances>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username>
export DOCKER_PASSWORD=<your password>
export DOCKER_EMAIL=<your Docker email, use same as username provided>
export DOCKER_PRIVATE_REGISTRY="1"
```

## <a name="deploy-sql-server-big-data-cluster"></a>Развертывание кластера больших данных в SQL Server

API создания кластера используется для инициализации пространств имен Kubernetes и развернуть всех модулях приложения в пространстве имен. Для развертывания кластера больших данных в SQL Server в кластере Kubernetes, выполните следующую команду:

```bash
mssqlctl create cluster <name of your cluster>
```

Во время начальной загрузки кластера командное окно клиента будут выходные данные состояния развертывания. Можно также проверить состояние развертывания, выполнив следующие команды в окне командной строки различные:

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

## <a id="masterip"></a> Получите экземпляр SQL Server Master и IP-адреса кластера больших данных в SQL Server

После успешного выполнения сценария развертывания, можно получить IP-адрес главного экземпляра SQL Server, используя шаги, описанные ниже. Этот IP-адрес и порт номер 31433 будет использовать для подключения к основной экземпляр SQL Server (например:  **\<ip адрес\>, 31433**). Аналогично для IP-адреса кластера больших данных в SQL Server. На вкладке "конечные точки службы" на портале администрирования кластера также описаны все конечные точки кластера. На портале администрирования кластера можно использовать для мониторинга развертывания. Доступны на портале с помощью внешних IP-адрес и порт номер для `service-proxy-lb` (например: **https://\<ip адрес\>: 30777**). Учетные данные для доступа к порталу администрирования являются значениями `CONTROLLER_USERNAME` и `CONTROLLER_PASSWORD` переменные среды, приведенные выше.

### <a name="aks"></a>AKS

Если вы используете AKS, Azure предоставляет службы Azure Подсистема балансировки нагрузки. Выполните следующую команду:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

Найдите **External-IP** значение, присвоенное к службе. Затем подключитесь к основной экземпляр SQL Server с помощью IP-адрес на порте 31433 (например:  **\<ip адрес\>, 31433**) и SQL Server с данными большого размера кластера с помощью external-IP для конечной точки `service-security-lb` службы. 

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

После успешного развертывания SQL Server больших данных кластера Kubernetes, [установите средства работы с большими данными](deploy-big-data-tools.md) и ознакомьтесь с некоторыми новыми возможностями и узнайте [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).
