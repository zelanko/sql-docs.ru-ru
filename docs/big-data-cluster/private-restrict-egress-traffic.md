---
title: Ограничения для исходящего трафика Кластеров больших данных (BDC) в частном кластере Службы Azure Kubernetes (AKS)
titleSuffix: SQL Server Big Data Clusters
description: Узнайте, как ограничить исходящий трафик Кластеров больших данных (BDC) в частном кластере Службы Azure Kubernetes (AKS).
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 08/20/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 962e155b3b0b5906d36fa4d884be2af353cb25a9
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076610"
---
# <a name="restrict-egress-traffic-of-big-data-clusters-bdc-clusters-in-azure-kubernetes-service-aks-private-cluster"></a>Ограничения для исходящего трафика Кластеров больших данных (BDC) в частном кластере Службы Azure Kubernetes (AKS)

По умолчанию AKS подготавливает для настройки и использования для исходящего трафика Load Balancer ценовой категории "Стандартный". Однако настройка по умолчанию может не соответствовать требованиям всех сценариев, если общедоступные IP-адреса запрещены или для исходящего трафика требуются дополнительные прыжки. Идентифицируйте определяемую пользователем таблицу маршрутов, если кластер запрещает использовать общедоступные IP-адреса и находится за сетевым виртуальным модулем (NVA).

По умолчанию кластеры AKS имеют неограниченный исходящий доступ к Интернету для управления и эксплуатации. Рабочим узлам в кластере AKS нужен доступ к определенным портам и полным доменным именам (FQDN), например:

* Для обновления системы безопасности операционной системы рабочего узла кластеру необходимо извлечь образы контейнеров базовой системы из Реестра контейнеров Майкрософт (MCR).
* Если рабочим узлам AKS с поддержкой GPU необходимо получить доступ к некоторым конечным точкам из NVIDIA для установки драйвера.
* В сценарии, в котором клиенты используют AKS для работы в сочетании со службами Azure, такими как политика Azure для обеспечения соответствия корпоративного уровня, мониторинг Azure (с аналитикой для контейнеров). 
* Для включения пространства разработки и других подобных сценариев.

> [!NOTE]
> В настоящее время при развертывании BDC в частном кластере Службы Azure Kubernetes (AKS) в сценарии нет входящих зависимостей, кроме описанных в этой статье. Вы можете найти все исходящие зависимости в статье [Управление исходящим трафиком для узлов кластера в службе Azure Kubernetes (AKS)](/azure/aks/limit-egress-traffic).

В этой статье описывается развертывание BDC в частном кластере AKS с расширенным сетевым взаимодействием и определяемым пользователем маршрутом, а также дальнейшая интеграция с сетевой средой корпоративного класса.

## <a name="use-azure-firewall-to-restrict-egress-traffic"></a>Ограничение исходящего трафика с помощью брандмауэра Azure

В Брандмауэре Azure для упрощения этой конфигурации доступен тег FQDN `(AzureKubernetesService)` Службы Azure Kubernetes.

Полные сведения об этом теге см. в разделе [Ограничение исходящего трафика с помощью брандмауэра Azure](/azure/aks/limit-egress-traffic#restrict-egress-traffic-using-azure-firewall).

На следующем рисунке показано ограничение трафика в частном кластере AKS. 

:::image type="content" source="media/private-cluster-restrict-egress-traffic/aks-azure-firewall-egress.png" alt-text="Исходящий трафик брандмауэра частного кластера AKS":::

Чтобы настроить базовую архитектуру с помощью Брандмауэра Azure, сделайте следующее:

1. Создайте группу ресурсов и виртуальную сеть.
2. Создайте и настройте брандмауэр Azure.
3. Создайте определяемую пользователем таблицу маршрутизации.
4. Настройка правил брандмауэра
5. Создайте субъект-службу (SP).
6. Создайте частный кластер AKS
7. Создайте профиль развертывания BDC
8. Разверните BDC.

В следующих шагах укажите подробные сведения.

## <a name="create-the-resource-group-and-vnet"></a>Создание группы ресурсов и виртуальной сети

1. Определите набор переменных среды для создания ресурсов.

   ```console
   export REGION_NAME=<region>
   export RESOURCE_GROUP=private-bdc-aksudr-rg
   export SUBNET_NAME=aks-subnet
   export VNET_NAME=bdc-vnet
   export AKS_NAME=bdcaksprivatecluster
   ```

1. Создание группы ресурсов

   ```azurecli
   az group create -n $RESOURCE_GROUP -l $REGION_NAME
   ```

1. Создайте виртуальную сеть.

   ```azurecli
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
   ```

## <a name="create-and-set-up-azure-firewall"></a>Создание и настройка Брандмауэра Azure

1. Определите набор переменных среды для создания ресурсов.

   ```console
   export FWNAME=bdcaksazfw
   export FWPUBIP=$FWNAME-ip
   export FWIPCONFIG_NAME=$FWNAME-config

   az extension add --name azure-firewall
   ```

1. Создайте выделенную подсеть для брандмауэра.

   > [!NOTE]
   > После создания имя брандмауэра невозможно изменить.

   ```azurecli
   az network vnet subnet create \
     --resource-group $RESOURCE_GROUP \
     --vnet-name $VNET_NAME \
     --name AzureFirewallSubnet \
     --address-prefix 10.3.0.0/24

    az network firewall create -g $RESOURCE_GROUP -n $FWNAME -l $REGION_NAME --enable-dns-proxy true

    az network public-ip create -g $RESOURCE_GROUP -n $FWPUBIP -l $REGION_NAME --sku "Standard"

    az network firewall ip-config create -g $RESOURCE_GROUP -f $FWNAME -n $FWIPCONFIG_NAME --public-ip-address $FWPUBIP --vnet-name $VNET_NAME
   ```

По умолчанию Azure автоматически направляет трафик между подсетями Azure, виртуальными и локальными сетями. 

## <a name="create-user-defined-route-table"></a>Создание определяемой пользователем таблицы маршрутизации

Создайте определяемую пользователем таблицу маршрутизации (UDR) с прыжком к Брандмауэру Azure.

```azurecli

export SUBID= <your Azure subscription ID>
export FWROUTE_TABLE_NAME=bdcaks-rt
export FWROUTE_NAME=bdcaksroute
export FWROUTE_NAME_INTERNET=bdcaksrouteinet

export FWPUBLIC_IP=$(az network public-ip show -g $RESOURCE_GROUP -n $FWPUBIP --query "ipAddress" -o tsv)
export FWPRIVATE_IP=$(az network firewall show -g $RESOURCE_GROUP -n $FWNAME --query "ipConfigurations[0].privateIpAddress" -o tsv)

# Create UDR and add a route for Azure Firewall

az network route-table create -g $RESOURCE_GROUP --name $FWROUTE_TABLE_NAME

az network route-table route create -g $RESOURCE_GROUP --name $FWROUTE_NAME --route-table-name $FWROUTE_TABLE_NAME --address-prefix 0.0.0.0/0 --next-hop-type VirtualAppliance --next-hop-ip-address $FWPRIVATE_IP --subscription $SUBID

az network route-table route create -g $RESOURCE_GROUP --name $FWROUTE_NAME_INTERNET --route-table-name $FWROUTE_TABLE_NAME --address-prefix $FWPUBLIC_IP/32 --next-hop-type Internet
```

## <a name="set-up-firewall-rules"></a>Настройка правил брандмауэра 

```azurecli
# Add FW Network Rules

az network firewall network-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwnr' -n 'apiudp' --protocols 'UDP' --source-addresses '*' --destination-addresses "AzureCloud.$REGION_NAME" --destination-ports 1194 --action allow --priority 100
az network firewall network-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwnr' -n 'apitcp' --protocols 'TCP' --source-addresses '*' --destination-addresses "AzureCloud.$REGION_NAME" --destination-ports 9000
az network firewall network-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwnr' -n 'time' --protocols 'UDP' --source-addresses '*' --destination-fqdns 'ntp.ubuntu.com' --destination-ports 123

# Add FW Application Rules

az network firewall application-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwar' -n 'fqdn' --source-addresses '*' --protocols 'http=80' 'https=443' --fqdn-tags "AzureKubernetesService" --action allow --priority 100
```

Вы можете связать определяемую пользователем таблицу маршрутизации (UDR) с кластером AKS, в котором ранее развернуты кластеры BDC, с помощью следующей команды:

```azurecli
az network vnet subnet update -g $RESOURCE_GROUP --vnet-name $VNET_NAME --name $SUBNET_NAME --route-table $FWROUTE_TABLE_NAME
```

## <a name="create--configure-service-principal-sp"></a>Создание и настройка субъекта-службы (SP)

На этом шаге необходимо создать субъект-службу и назначить разрешение для виртуальной сети.

См. следующий пример. 

```azurecli
# Create SP and Assign Permission to Virtual Network

az ad sp create-for-rbac -n "bdcaks-sp" --skip-assignment

APPID=<your service principal ID >
PASSWORD=< your service principal password >
VNETID=$(az network vnet show -g $RESOURCE_GROUP --name $VNET_NAME --query id -o tsv)

# Assign SP Permission to VNET

az role assignment create --assignee $APPID --scope $VNETID --role "Network Contributor"


RTID=$(az network route-table show -g $RESOURCE_GROUP -n $FWROUTE_TABLE_NAME --query id -o tsv)
az role assignment create --assignee $APPID --scope $RTID --role "Network Contributor"
```

## <a name="create-aks-cluster"></a>Создание кластера AKS

Затем создайте кластер AKS с `userDefinedRouting` в качестве типа исходящего трафика.

```azurecli
az aks create \
    --resource-group $RESOURCE_GROUP \
    --location $REGION_NAME \
    --name $AKS_NAME \
    --load-balancer-sku standard \
    --outbound-type userDefinedRouting \
    --enable-private-cluster \
    --network-plugin azure \
    --vnet-subnet-id $SUBNET_ID \
    --docker-bridge-address 172.17.0.1/16 \
    --dns-service-ip 10.2.0.10 \
    --service-cidr 10.2.0.0/24 \
    --service-principal $APPID \
    --client-secret $PASSWORD \
    --node-vm-size Standard_D13_v2 \
    --node-count 2 \
    --generate-ssh-keys
```

## <a name="build-big-data-cluster-bdc-deployment-profile"></a>Создание профиля развертывания для Кластера больших данных (BDC)

Кластеры BDC можно создавать с помощью настраиваемого профиля: 

```console
azdata bdc config init --source aks-dev-test --target private-bdc-aks --force
```

## <a name="generate-and-config-bdc-custom-deployment-profile"></a>Создание и настройка настраиваемого профиля развертывания BDC: 
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

## <a name="deploy-bdc-in-aks-private-cluster"></a>Развертывание BDC в частном кластере AKS

```console
export AZDATA_USERNAME=<your bdcadmin username>
export AZDATA_PASSWORD=< your bdcadmin password>

azdata bdc create --config-profile private-bdc-aks --accept-eula yes
```

## <a name="use-third-party-firewall-instead-of-azure-firewall"></a>Использование стороннего брандмауэра вместо Брандмауэра Azure

Используйте сторонний брандмауэр, чтобы ограничить исходящий трафик при развертывании BDC через частный кластер AKS. Пример приведен на странице [брандмауэров в Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps?search=firewall&page=1). Сторонние брандмауэры можно использовать в частных решениях развертывания с более соответствующими конфигурациями. Брандмауэр должен предоставить следующие правила сети:

* Все [необходимые правила исходящей сети и FQDN для кластеров AKS](/azure/aks/limit-egress-traffic#required-outbound-network-rules-and-fqdns-for-aks-clusters), а также все конечные точки и зависимости подстановочного знака протокола HTTP/HTTPS, которые могут отличаться в зависимости от ряда квалификаторов и реальных требований.
* Глобальные обязательные правила сети Azure / полное доменное имя / правила приложения, указанные [здесь](/azure/aks/limit-egress-traffic#azure-global-required-network-rules).
* Дополнительное рекомендуемое полное доменное имя / правила приложения для кластеров AKS, указанные [здесь](/azure/aks/limit-egress-traffic#optional-recommended-fqdn--application-rules-for-aks-clusters). 

Узнайте, как [управлять BDC в частном кластере AKS](private-manage.md), а затем выполните следующий шаг, чтобы [подключиться к кластеру BDC](connect-to-big-data-cluster.md).

Сведения о скриптах автоматизации для этого сценария см. на странице [репозитория примеров SQL Server на сайте GitHub](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/private-aks).

## <a name="next-steps"></a>Дальнейшие шаги

[Управление кластером больших данных в частном кластере AKS](private-manage.md)

[Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md)
