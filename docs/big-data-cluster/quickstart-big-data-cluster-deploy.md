---
title: Краткое руководство по развертыванию
titleSuffix: SQL Server 2019 big data clusters
description: Пошаговое руководство по развертыванию кластеров SQL Server 2019 больших данных (Предварительная версия) в службе Azure Kubernetes (AKS).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: quickstart
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: c760bd4c149a63de0335c6d6651036bba56533a0
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246763"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Краткое руководство. Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS)

В этом кратком руководстве вы развернете кластер SQL Server 2019 больших данных (Предварительная версия) в AKS в конфигурации по умолчанию подходит для сред разработки и тестирования.

> [!NOTE]
> AKS — только в одном месте для узлов Kubernetes. Кластерами больших данных могут развертываться в Kubernetes, независимо от базовой инфраструктуры. Дополнительные сведения см. в разделе [развертывание больших данных в SQL Server кластеров Kubernetes](deployment-guidance.md).

Помимо экземпляр SQL Master кластера включает один вычислительный экземпляр пула, один экземпляр пула данных и два экземпляра пула хранения. Данные сохраняются с помощью постоянных томах Kubernetes, использующих классы хранения по умолчанию AKS. Для дальнейшей настройки конфигурации, см. в разделе переменных среды в [руководство по развертыванию](deployment-guidance.md).

Если вы хотите использовать для выполнения скрипта для создания кластера AKS и установить кластер больших данных в то же время, см. в разделе [развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>предварительные требования

В этом кратком руководстве требует, что вы уже настроили кластер AKS с минимальной версии v1.10. Дополнительные сведения см. в разделе [развертывание в AKS](deploy-on-aks.md) руководства.

- [Средства SQL Server 2019 больших данных](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**
   - **mssqlctl**

## <a name="verify-aks-configuration"></a>Проверка конфигурации AKS

После развертывания кластера AKS, можно выполнить следующую команду kubectl, чтобы просмотреть конфигурации кластера. Убедитесь, что этот kubectl указывает контекст правильный кластера.

```bash
kubectl config view
```

## <a name="define-environment-variables"></a>Определение переменных среды

Задание переменных среды, необходимые для развертывания кластера больших данных немного отличается в зависимости от того, используете ли вы клиент Windows или Linux и Mac OS.  Выберите следующие действия, в зависимости от того, какая операционная система используется.

Прежде чем продолжить, обратите внимание, следующие важные моменты:

- В [командное окно](https://docs.microsoft.com/visualstudio/ide/reference/command-window), кавычки включаются в переменных среды. Если используются кавычки программы-оболочки для пароля, кавычки будут включены в пароль.
- В bash кавычки не включаются в переменной. Наши примеры используйте двойные кавычки `"`.
- Пароль можно задать переменные среды на любое другое, но убедитесь, что они достаточно сложны и не используйте `!`, `&`, или `'` символов.
- Для выпуска CTP-версии 2.2 не изменить порты по умолчанию.
- `sa` Учетная запись является администратором системы на экземпляре SQL Server Master, которая создается во время установки. После создания контейнера SQL Server указанную вами переменную среды `MSSQL_SA_PASSWORD` можно обнаружить, запустив `echo $MSSQL_SA_PASSWORD` в контейнере. В целях безопасности измените вашей `sa` пароля в соответствии с практическими рекомендациями, описанными [здесь](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Инициализируйте следующие переменные среды.  Они необходимы для развертывания кластера больших данных:

### <a name="windows"></a>Windows

Используя окно командной строки (не PowerShell), настройте следующие переменные среды:

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
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

export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
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

Чтобы развернуть кластер SQL Server 2019 CTP 2.2 больших данных в кластере Kubernetes, выполните следующую команду:

```bash
mssqlctl create cluster <your-cluster-name>
```

> [!NOTE]
> Имя кластера должно быть только буквенно цифровые символы в нижнем регистре, не должно быть пробелов. Все артефакты Kubernetes для кластера больших данных создается в пространстве имен с тем же именем, что и кластер указанное имя.

Окно командной строки или оболочки возвращает состояние развертывания. Можно также проверить состояние развертывания, выполнив следующие команды в окне командной строки различные:

```bash
kubectl get all -n <your-cluster-name>
kubectl get pods -n <your-cluster-name>
kubectl get svc -n <your-cluster-name>
```

Вы увидите более детализированные состоянии и конфигурации для каждого модуля, выполнив:
```bash
kubectl describe pod <pod name> -n <your-cluster-name>
```

> [!TIP]
> Дополнительные сведения о том, как мониторинг и устранение неполадок развертывания см. в разделе [Устранение неполадок развертывания](deployment-guidance.md#troubleshoot) статьи руководство по развертыванию.

## <a name="open-the-cluster-administration-portal"></a>Откройте портал администрирования кластера

После запуска модуль контроллера на портале администрирования кластера можно использовать для мониторинга развертывания. Доступны на портале с помощью внешних IP-адрес и порт номер для `service-proxy-lb` (например: **https://\<ip адрес\>: 30777: портал**). Учетные данные для доступа к порталу администрирования являются значениями `CONTROLLER_USERNAME` и `CONTROLLER_PASSWORD` переменные среды, приведенные выше.

IP-адрес службы прокси-сервера балансировки нагрузки службы можно получить, выполнив следующую команду в окне bash или cmd:

```bash
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

> [!NOTE]
> Вы увидите предупреждение о безопасности при доступе к веб-страницы, так как мы используем создан SSL-сертификаты. В будущих выпусках мы предоставим возможность предоставлять свои собственные сертификаты со знаком.

## <a name="connect-to-the-big-data-cluster"></a>Подключитесь к кластеру больших данных

После успешного выполнения сценария развертывания, можно получить IP-адрес главного экземпляра SQL Server и конечная точки Spark или HDFS, используя шаги, описанные ниже. Все конечные точки кластера отображаются в разделе конечных точек службы на портал администрирования кластера, а также для удобства.

Azure предоставляет службы Azure Подсистема балансировки нагрузки AKS. Выполните следующую команду в cmd или окне bash:

```bash
kubectl get svc endpoint-master-pool -n <your-cluster-name>
kubectl get svc service-security-lb -n <your-cluster-name>
```

Найдите **External-IP** значение, присвоенное к службам. Подключиться к основной экземпляр SQL Server с помощью IP-адрес для `endpoint-master-pool` на порте 31433 (например:  **\<ip адрес\>, 31433**) и конечную точку кластера больших данных SQL Server, используя external-IP для `service-security-lb` службы.   Что больших данных кластера конечной точки — где можно взаимодействовать с HDFS и отправка заданий Spark через Knox.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда развернут кластер больших данных SQL Server, ознакомьтесь с некоторыми новыми возможностями:

> [!div class="nextstepaction"]
> [Как использовать записные книжки в предварительной версии SQL Server 2019](notebooks-guidance.md)
