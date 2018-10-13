---
title: Настроить службу Azure Kubernetes для развертываний SQL Server 2019 CTP-версии 2.0 | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 6c245365c231264f1aa56e2f1fad8ac17446ec5b
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877937"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-ctp-20"></a>Настройка службы Azure Kubernetes для SQL Server 2019 CTP 2.0

Служба Azure Kubernetes (AKS) позволяет легко создавать, настраивать и администрировать кластер виртуальных машин, настроенных с кластером Kubernetes для запуска контейнерных приложений. 

Это позволяет использовать имеющиеся навыки либо положиться большого и постоянно растущего сообщества опыт, развертывание и управление ими контейнерных приложений в Microsoft Azure.

В этой статье описаны шаги по развертыванию Kubernetes в AKS с помощью Azure CLI. Если у вас нет подписки Azure, создайте бесплатную учетную запись перед началом работы.

## <a name="prerequisites"></a>предварительные требования

- Для среды AKS минимальное требование виртуальной Машины — по крайней мере два агента виртуальных машин (в дополнение к главному узлу) минимального размера [Standard_DS3_v2](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-general#dsv2-series). Минимальные ресурсы, необходимые каждой виртуальной Машины: 4 ЦП и 14 ГБ памяти.
  
   > [!NOTE]
   > Если вы планируете запускать задания с большими данными или нескольких приложений Spark, минимальный размер — [Standard_D8_v3](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-general#dv3-series-sup1sup), и минимальные ресурсы, необходимые каждой виртуальной Машины — 8 процессоров и 32 ГБ памяти.

- В этом разделе необходимо иметь Azure CLI версии 2.0.4 или более поздней версии. Если требуется выполнить установку или обновление, см. в разделе [Установка Azure CLI 2.0](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli). Запустите `az --version` чтобы узнать версию, при необходимости.

- Установка [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Кластера больших данных в SQL Server требуется любой дополнительный номер версии в рамках диапазона 1,10 версий, для Kubernetes, но для сервера и клиента. Чтобы установить определенную версию на клиент kubectl, см. в разделе [установки kubectl двоичных с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Для AKS необходимо использовать `--kubernetes-version` параметр для указания версии отличается от по умолчанию. Обратите внимание на то, что в выпуском CTP2.0 AKS поддерживает только 1.10.7 и 1.10.8 версии. 


> [!NOTE]
Обратите внимание, что это наклон версии клиента и сервера поддерживается +/-1 дополнительный номер версии. В документации по Kubernetes состояния «клиент должен быть неравномерно распределенных не более чем один дополнительный номер версии с главного сервера, что может привести образце, на один дополнительный номер версии. Например, версия 1.3 главной должны работать с версии 1.1, версия 1.2 и версия 1.3 узлов и должны работать с версии 1.2, версия 1.3 и клиентов версии 1.4.» Дополнительные сведения см. в разделе [Kubernetes поддерживаемые выпуски и наклона компонент](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

Кроме того, обратите внимание, что `az aks kubernetes install-cli` установит клиент kubectl с версией, снизить требуется 1.10. Выполните приведенные выше инструкции, чтобы установить правильную версию клиент kubectl.

## <a name="create-a-resource-group"></a>Создайте группу ресурсов

Группа ресурсов Azure — это логическая группа, в какие Azure развертываются и администрируются ресурсы. Следующие действия, вход в Azure и создайте группу ресурсов в кластере AKS.

> [!TIP]
> Если вы используете Windows, используйте PowerShell для дальнейших действий, описанных.

1. В командной строке выполните следующую команду и следуйте инструкциям на экране входа в подписку Azure:

    ```bash
    az login
    ```

1. Если у вас несколько подписок, всех подписок можно просмотреть, выполнив следующую команду:

   ```bash
   az account list
   ```

1. Если вы хотите изменить в другую подписку вы выполните следующую команду:

   ```bash
   az account set --subscription <subscription id>
   ```

1. Создайте группу ресурсов с помощью **Создание группы az** команды. В следующем примере создается группа ресурсов, с именем `sqlbigdatagroup` в `westus2` расположение.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Создание кластера Kubernetes

1. Создание кластера Kubernetes в AKS при помощи [создать az aks](https://docs.microsoft.com/cli/azure/aks) команды. В следующем примере создается кластер Kubernetes с именем *kubcluster* с Linux одного главного узла и двух узлов агентов Linux. Убедитесь, что вы создаете кластер AKS в той же группе ресурсов, который использовался в предыдущих разделах.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_DS3_v2 \
    --node-count 2 \
    --kubernetes-version 1.10.7
    ```

    Можно увеличить или уменьшить количество агентов по умолчанию, изменив `--node-count <n>` где `<n>` — количество узлов агентов, которые вы хотите иметь.

    Через несколько минут команда завершается и возвращает информацию о кластере в формате JSON.

1. Сохранение выходных данных JSON из предыдущей команды для последующего использования.

## <a name="connect-to-the-cluster"></a>Подключитесь к кластеру

1. Чтобы настроить kubectl для подключения к кластеру Kubernetes, выполните [az aks get-credentials](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) команды. Этот шаг скачиваются учетные данные и настройка интерфейса командной строки, чтобы их использовать kubectl.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Чтобы проверить подключение к кластеру, используйте [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) команду, чтобы получить список узлов кластера.  В приведенном ниже примере показаны выходные данные при 1 главный, а 3 узлов агентов.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье настроить кластер Kubernetes в AKS. Следующим шагом является развертывание SQL Server 2019 больших данных в кластере.

[Развертывание кластера SQL Server 2019 больших данных в Kubernetes](quickstart-big-data-cluster-deploy.md)
