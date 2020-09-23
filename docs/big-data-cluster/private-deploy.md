---
title: Развертывание BDC в частном кластере службы Azure Kubernetes (AKS)
titleSuffix: SQL Server Big Data Cluster
description: Сведения о развертывании кластеров больших данных SQL Server с помощью частного кластера службы Azure Kubernetes (AKS) с расширенными сетевыми возможностями (CNI).
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 08/20/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4a55d7f6c9c55891f8d1a7bf97d8834c9df4a796
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283123"
---
# <a name="deploy-bdc-in-azure-kubernetes-service-aks-private-cluster"></a>Развертывание BDC в частном кластере службы Azure Kubernetes (AKS)

В этой статье объясняется, как развертывать кластеры больших данных SQL Server в частном кластере службы Azure Kubernetes (AKS). Эта конфигурация поддерживает ограниченное использование общедоступных IP-адресов в корпоративной сетевой среде.

Частное развертывание обеспечивает следующие преимущества.

* Ограниченное использование общедоступных IP-адресов
* Сетевой трафик между серверами приложений и пулами узлов кластера остается только в частной сети.
* Настраиваемая конфигурация для обязательного исходящего трафика в соответствии с конкретными требованиями

В этой статье показано, как использовать частный кластер AKS для ограничения использования общедоступных IP-адресов, когда применяются соответствующие строки безопасности.

## <a name="deploy-private-bdc-cluster-with-aks-private-cluster"></a>Развертывание частного кластера BDC с помощью частного кластера AKS

Чтобы приступить к работе, создайте [частный кластер AKS](/azure/aks/private-clusters), чтобы сетевой трафик между сервером API и пулами узлов оставался в частной сети. Уровень управления или сервер API имеют внутренние IP-адреса в частном кластере AKS.

В этом разделе показано, как развернуть кластер BDC в частном кластере службы Azure Kubernetes (AKS) с расширенными сетевыми возможностями (CNI).

## <a name="create-a-private-aks-cluster-with-advanced-networking"></a>Создание частного кластера AKS с расширенными сетевыми возможностями

```console

export REGION_NAME=<your Azure region >
export RESOURCE_GROUP=< your resource group name >
export SUBNET_NAME=aks-subnet
export VNET_NAME=bdc-vnet
export AKS_NAME=< your aks private cluster name >
 
az group create -n $RESOURCE_GROUP -l $REGION_NAME
 
az network vnet create \
    --resource-group $RESOURCE_GROUP \
    --location $REGION_NAME \
    --name $VNET_NAME \
    --address-prefixes 10.0.0.0/8 \
    --subnet-name $SUBNET_NAME \
    --subnet-prefix 10.1.0.0/16
 

SUBNET_ID=$(az network vnet subnet show \
    --resource-group $RESOURCE_GROUP \
    --vnet-name $VNET_NAME \
    --name $SUBNET_NAME \
    --query id -o tsv)
 
echo $SUBNET_ID
## will be displayed something similar as the following: 
/subscriptions/xxxx-xxxx-xxx-xxxx-xxxxxxxx/resourceGroups/your-bdc-rg/providers/Microsoft.Network/virtualNetworks/your-aks-vnet/subnets/your-aks-subnet
```

### <a name="create-aks-private-cluster-with-advanced-networking-cni"></a>Создание частного кластера AKS с расширенными сетевыми возможностями (CNI)

Чтобы перейти к следующему шагу, необходимо подготовить к работе кластер AKS со стандартным средством балансировки нагрузки и включенной функцией частного кластера. Команда будет выглядеть следующим образом: 

```console
az aks create \
    --resource-group $RESOURCE_GROUP \
    --name $AKS_NAME \
    --load-balancer-sku standard \
    --enable-private-cluster \
    --network-plugin azure \
    --vnet-subnet-id $SUBNET_ID \
    --docker-bridge-address 172.17.0.1/16 \
    --dns-service-ip 10.2.0.10 \
    --service-cidr 10.2.0.0/24 \
    --node-vm-size Standard_D13_v2 \
    --node-count 2 \
    --generate-ssh-keys
```

После успешного развертывания можно переходить к группе ресурсов `<MC_yourakscluster>`, после чего обнаружится, что `kube-apiserver` является частной конечной точкой. См., например, следующий раздел.

## <a name="connect-to-an-aks-cluster"></a>Подключение к кластеру AKS

```console
az aks get-credentials -n $AKS_NAME -g $RESOURCE_GROUP
```

## <a name="build-big-data-cluster-bdc-deployment-profile"></a>Создание профиля развертывания для Кластера больших данных (BDC)

После подключения к кластеру AKS можно приступить к развертыванию BDC, а также подготовить переменную среды и запустить развертывание: 

```console
azdata bdc config init --source aks-dev-test --target private-bdc-aks --force
```

Создание и настройка настраиваемого профиля развертывания BDC:

```console
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.docker.imageTag=2019-CU6-ubuntu-16.04"
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.storage.data.className=default"
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.storage.logs.className=default"

azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.endpoints[1].serviceType=NodePort"

azdata bdc config replace -c private-bdc-aks/bdc.json -j "$.spec.resources.master.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -c private-bdc-aks/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -c private-bdc-aks/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].serviceType=NodePort"
```

## <a name="deploy-private-sql-server-big-data-cluster-with-ha"></a>Развертывание частного кластера больших данных SQL Server с высоким уровнем доступности

В случае [развертывания кластера больших данных SQL Server (SQL-BDC) с высокой доступностью](deployment-high-availability.md) будет использоваться профиль развертывания `aks-dev-test-ha`. После успешного развертывания можно использовать ту же команду `kubectl get svc`, чтобы создать дополнительную службу `master-secondary-svc`. Следует настроить `ServiceType` как `NodePort`. Оставшиеся шаги мало отличаются от упомянутых в предыдущем разделе.

В следующем примере `ServiceType` задается как `NodePort`:

```console
azdata bdc config replace -c private-bdc-aks /bdc.json -j "$.spec.resources.master.spec.endpoints[1].serviceType=NodePort"
```

## <a name="deploy-bdc-in-aks-private-cluster"></a>Развертывание BDC в частном кластере AKS

```console
export AZDATA_USERNAME=<your bdcadmin username>
export AZDATA_PASSWORD=< your bdcadmin password>

azdata bdc create --config-profile private-bdc-aks --accept-eula yes
```

## <a name="check-deployment-status"></a>Проверка состояния развертывания

Развертывание займет несколько минут. Для проверки состояния развертывания можно использовать следующую команду: 

```console
kubectl get pods -n mssql-cluster -w
```

## <a name="check-the-service-status"></a>Проверка состояния службы

Используйте следующую команду для проверки служб. Убедитесь, что все они работоспособны без внешних IP-адресов:

```console
kubectl get services -n mssql-cluster
```

См. сведения об [управлении BDC в частном кластере AKS](private-manage.md), а затем приступайте к [подключению к кластеру BDC](connect-to-big-data-cluster.md).

Сведения о скриптах автоматизации для этого сценария см. на странице [репозитория примеров SQL Server на сайте GitHub](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/private-aks).

## <a name="next-steps"></a>Дальнейшие шаги

[Управление частным кластером](private-manage.md)

[Ограничение исходящего трафика частного кластера BDC](private-restrict-egress-traffic.md)

[Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md)
