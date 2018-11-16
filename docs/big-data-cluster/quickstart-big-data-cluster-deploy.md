---
title: Развертывание кластера больших данных в SQL Server | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: c25474a30ace6ed6e1ab0560f1b3746a071690ef
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51697042"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Краткое руководство по Развертыванию кластера больших данных SQL Server в службе Azure Kubernetes (AKS)

Установка кластера больших данных в SQL Server в AKS в конфигурации по умолчанию подходит для сред разработки и тестирования. Помимо экземпляр SQL Master кластера включает один вычислительный экземпляр пула, один экземпляр пула данных и два экземпляра пула хранения. Данные сохраняются с помощью постоянных томах Kubernetes, использующих классы хранения по умолчанию AKS. Для дальнейшей настройки конфигурации, см. в разделе переменных среды в [руководство по развертыванию](deployment-guidance.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>предварительные требования

В этом кратком руководстве требует, что вы уже настроили кластер AKS с минимальной версии v1.10. Дополнительные сведения см. в разделе [развертывание в AKS](deploy-on-aks.md) руководства.

На компьютере, вы используете для выполнения команд для установки кластера больших данных SQL Server, установите [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Большие данные кластера SQL Server требуется 1,10 ОС, Kubernetes, для сервера и клиента (kubectl). Чтобы установить kubectl, см. в разделе [установки kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). 

Чтобы установить **mssqlctl** инструмента интерфейса командной строки для управления SQL Server на больших данных кластера на клиентском компьютере, необходимо сначала установить [Python](https://www.python.org/downloads/) версии не ниже версии 3.0 и [pip3](https://pip.pypa.io/en/stable/installing/). `pip` уже установлен, если вы используете версию Python по крайней мере 3.4, загруженные из [python.org](https://www.python.org/).

## <a name="verify-aks-configuration"></a>Проверка конфигурации AKS

После развертывания кластера AKS, можно выполнить следующую команду kubectl, чтобы просмотреть конфигурации кластера. Убедитесь, что этот kubectl указывает контекст правильный кластера.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Установка средства управления mssqlctl интерфейса командной строки

Выполните следующую команду, чтобы установить **mssqlctl** средство на клиентском компьютере. Команда выполняется из Windows и клиента Linux, но убедитесь, что вы используете его из окна командной строки, под управлением Windows с правами администратора или перед ними `sudo` в Linux:

```
pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl  
```

> [!IMPORTANT]
> Если вы установили предыдущего выпуска, необходимо удалить кластер *перед* обновление **mssqlctl** и установки новой версии. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

> [!TIP]
> Если **mssqlctl** не правильную установку, просмотрите действия по готовности к установке в статье [установить mssqlctl](deployment-guidance.md#mssqlctl).

## <a name="define-environment-variables"></a>Определение переменных среды

Задание переменных среды, необходимые для развертывания кластера больших данных немного отличается в зависимости от того, используете ли вы клиент Windows или Linux и Mac OS.  Выберите следующие действия, в зависимости от того, какая операционная система используется.

Прежде чем продолжить, обратите внимание, следующие важные моменты:

- В [командное окно](https://docs.microsoft.com/visualstudio/ide/reference/command-window), кавычки включаются в переменных среды. Если используются кавычки программы-оболочки для пароля, кавычки будут включены в пароль.
- В bash кавычки не включаются в переменной. Наши примеры используйте двойные кавычки `"`.
- Пароль можно задать переменные среды на любое другое, но убедитесь, что они достаточно сложны и не используйте `!`, `&`, или `'` символов.
- Для выпуска CTP 2.1 не изменить порты по умолчанию.
- `sa` Учетная запись является администратором системы на экземпляре SQL Server Master, которая создается во время установки. После создания контейнера SQL Server указанную вами переменную среды `MSSQL_SA_PASSWORD` можно обнаружить, запустив `echo $MSSQL_SA_PASSWORD` в контейнере. В целях безопасности измените вашей `sa` пароля в соответствии с практическими рекомендациями, описанными [здесь](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Инициализируйте следующие переменные среды.  Они необходимы для развертывания кластера больших данных:

### <a name="windows"></a>Windows

Используя окно командной строки (не PowerShell), настройте следующие переменные среды:

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

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

### <a name="linuxmacos"></a>Linux и Mac OS

Инициализируйте следующие переменные среды:

```bash
export ACCEPT_EULA="Y"
export CLUSTER_PLATFORM="aks"

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

> [!NOTE]
> Во время ограниченной общедоступной предварительной версии Docker учетные данные для загрузки изображений кластера больших данных SQL Server предоставляются корпорацией Майкрософт для каждого клиента. Чтобы запросить доступ, зарегистрируйте [здесь](https://aka.ms/eapsignup)и укажите ваш интерес к попробуйте кластеры больших данных в SQL Server.

## <a name="deploy-a-big-data-cluster"></a>Развертывание кластера больших данных

Чтобы развернуть кластер SQL Server 2019 CTP 2.1 больших данных в кластере Kubernetes, выполните следующую команду:

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> Имя кластера должно быть только буквенно цифровые символы в нижнем регистре, не должно быть пробелов. Все артефакты Kubernetes для кластера больших данных создается в пространстве имен с тем же именем, что и кластер указанное имя.


Окно командной строки или оболочки возвращает состояние развертывания. Можно также проверить состояние развертывания, выполнив следующие команды в окне командной строки различные:

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

Вы увидите более детализированные состоянии и конфигурации для каждого модуля, выполнив:
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

После запуска модуль контроллера на портале администрирования кластера можно использовать для мониторинга развертывания. Доступны на портале с помощью внешних IP-адрес и порт номер для `service-proxy-lb` (например: **https://\<ip адрес\>: 30777**). Учетные данные для доступа к порталу администрирования являются значениями `CONTROLLER_USERNAME` и `CONTROLLER_PASSWORD` переменные среды, приведенные выше.

IP-адрес службы прокси-сервера балансировки нагрузки службы можно получить, выполнив следующую команду в окне bash или cmd:

```bash
kubectl get svc service-proxy-lb -n <name of your cluster>
```

> [!NOTE]
> Вы увидите предупреждение о безопасности при доступе к веб-страницы, так как мы используем создан SSL-сертификаты. В будущих выпусках мы предоставим возможность предоставлять свои собственные сертификаты со знаком.
 

## <a name="connect-to-the-big-data-cluster"></a>Подключитесь к кластеру больших данных

После успешного выполнения сценария развертывания, можно получить IP-адрес главного экземпляра SQL Server и конечная точки Spark или HDFS, используя шаги, описанные ниже. Все конечные точки кластера отображаются в разделе конечных точек службы на портал администрирования кластера, а также для удобства.

Azure предоставляет службы Azure Подсистема балансировки нагрузки AKS. Выполните следующую команду в cmd или окне bash:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
```

Найдите **External-IP** значение, присвоенное к службам. Подключиться к основной экземпляр SQL Server с помощью IP-адрес для `service-master-pool-lb` на порте 31433 (например:  **\<ip адрес\>, 31433**) и конечную точку кластера больших данных SQL Server, используя external-IP для `service-security-lb` службы.   Что больших данных кластера конечной точки — где можно взаимодействовать с HDFS и отправка заданий Spark через Knox.

## <a name="sample-deployment-script"></a>Пример сценария развертывания

Пример скрипта python, выполняющий развертывание больших данных кластера AKS и SQL Server, см. в разделе [развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="next-steps"></a>Следующие шаги

Теперь, когда развернут кластер больших данных SQL Server, ознакомьтесь с некоторыми новыми возможностями:

> [!div class="nextstepaction"]
> [Как использовать записные книжки в предварительной версии SQL Server 2019](notebooks-guidance.md)
