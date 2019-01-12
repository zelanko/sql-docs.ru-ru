---
title: Настройка службы Azure Kubernetes
titleSuffix: SQL Server 2019 big data clusters
description: Сведения о настройке службы Azure Kubernetes (AKS) для развернутых кластеров (Предварительная версия) SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 8e6e91836b3daf0392da082df1f4ec806e9faf94
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241245"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-big-data-cluster-preview-deployments"></a>Настройка службы Azure Kubernetes для развертывания кластера (Предварительная версия) SQL Server 2019 больших данных

В этой статье описывается настройка службы Azure Kubernetes (AKS) для развертывания кластера (Предварительная версия) SQL Server 2019 больших данных.

AKS позволяет легко создавать, настраивать и администрировать кластер виртуальных машин, настроенных с кластером Kubernetes для запуска контейнерных приложений. Это позволяет использовать имеющиеся навыки либо положиться большого и постоянно растущего сообщества опыт, развертывание и управление ими контейнерных приложений в Microsoft Azure.

В этой статье описаны шаги по развертыванию Kubernetes в AKS с помощью Azure CLI. Если у вас нет подписки Azure, создайте бесплатную учетную запись перед началом работы.

> [!TIP] 
> Пример скрипта python, выполняющий развертывание больших данных кластера AKS и SQL Server, см. в разделе [развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="prerequisites"></a>предварительные требования

- [Развертывание средств работы с большими данными SQL Server 2019](deploy-big-data-tools.md):
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **Azure CLI**

- Минимальная 1.10 версия для сервера Kubernetes. Для AKS, необходимо использовать `--kubernetes-version` параметр, чтобы указать версию стандарта не по умолчанию.

- Для среды AKS для оптимальной производительности при проверке основных сценариев мы рекомендуем по крайней мере три агента виртуальных машин с по крайней мере 4 виртуальных ЦП и оставить 32 ГБ памяти каждая. Инфраструктура Azure предлагает несколько вариантов размера для виртуальных машин, см. в разделе [здесь](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) для выбранных элементов в регионе, который вы планируете развернуть.

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

1. Создание кластера Kubernetes в AKS при помощи [создать az aks](https://docs.microsoft.com/cli/azure/aks) команды. В следующем примере создается кластер Kubernetes с именем *kubcluster* с тремя узлами агентов Linux. Убедитесь, что вы создаете кластер AKS в той же группе ресурсов, который использовался в предыдущих разделах.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_L4s \
    --node-count 3 \
    --kubernetes-version 1.10.8
    ```

   Можно увеличить или уменьшить количество узлов агентов Kubernetes, изменив `--node-count <n>` где `<n>` — количество узлов агентов, которые вы хотите использовать. Сюда не входят главном узле Kubernetes, который управляется в фоновом AKS. Поэтому в примере выше, существуют **3** виртуальных машин размера **Standard_L4s** используемые для узлов агента из кластера AKS.

   Через несколько минут команда завершается и возвращает информацию о кластере в формате JSON.

1. Сохранение выходных данных JSON из предыдущей команды для последующего использования.

## <a name="connect-to-the-cluster"></a>Подключитесь к кластеру

1. Чтобы настроить kubectl для подключения к кластеру Kubernetes, выполните [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) команды. Этот шаг скачиваются учетные данные и настройка интерфейса командной строки, чтобы их использовать kubectl.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Чтобы проверить подключение к кластеру, используйте [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) команду, чтобы получить список узлов кластера.  В приведенном ниже примере показаны выходные данные при 1 главный, а 3 узлов агентов.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье настроить кластер Kubernetes в AKS. Следующим шагом является развертывание SQL Server 2019 больших данных в кластере.

[Краткое руководство. Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
