---
title: Руководство по развертыванию в Active Directory в службах Azure Kubernetes (AKS)
titleSuffix: SQL Server Big Data Cluster
description: Сведения о развертывании кластеров больших данных SQL Server в режиме AD в службах Azure Kubernetes (AKS).
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 11/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b24a83e1647b0e32aff3ce19ad69a0fdc9405b0e
ms.sourcegitcommit: 0f484f32709a414f05562bbaafeca9a9fc57c9ed
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2020
ms.locfileid: "94632957"
---
# <a name="tutorial-deploy-sql-server-big-data-clusters-in-ad-mode-on-azure-kubernetes-services-aks"></a>Руководство по развертыванию кластеров больших данных SQL Server в режиме AD в службах Azure Kubernetes (AKS)

В этой статье объясняется, как развернуть кластер больших данных SQL Server в режиме проверки подлинности Active Directory с использованием эталонной архитектуры. Эталонная архитектура позволяет расширить локальные доменные службы Active Directory (AD DS) в Azure. Ее можно развернуть из [центра архитектуры Azure](https://github.com/mspnp/identity-reference-architectures/tree/master/adds-extend-domain) с использованием [стандартных блоков Azure](https://github.com/mspnp/template-building-blocks/wiki/Install-Azure-Building-Blocks).

## <a name="prerequisites"></a>Предварительные требования

Для развертывания кластера больших данных SQL Server вам потребуется следующее:

* Доступ к виртуальной машине Azure для управления. Для этой виртуальной машины требуется доступ к виртуальной сети Azure, в которой будет развернут кластер больших данных. Она должна находиться либо в той же, либо в [одноранговой](/azure/virtual-network/virtual-network-manage-peering) виртуальной сети.
* [Установка средств обработки больших данных](deploy-big-data-tools.md) на виртуальную машину управления.
* Подготовка к развертыванию кластера в [режиме проверки подлинности Active Directory](active-directory-prerequisites.md) на локальном контроллере AD.

## <a name="create-aks-subnet"></a>Создание подсети AKS

1. Настройка переменных среды

   ```console
   export REGION_NAME=< your Azure Region >
   export RESOURCE_GROUP=<your resource group >
   export SUBNET_NAME=aks-subnet
   export VNet_NAME= adds-vnet
   export AKS_NAME= <your aks cluster name>
   ```

1. Создание подсети AKS

   ```console
   SUBNET_ID=$(az network vnet subnet show \
    --resource-group $RESOURCE_GROUP \
    --vnet-name $VNet_NAME \
    --name $SUBNET_NAME \
    --query id -o tsv)
   ```

На следующем снимке экрана показано, как планируется размещение подсетей в виртуальной сети в архитектуре.

:::image type="content" source="media/active-directory-deployment-aks/ad-in-aks-diagram.png" alt-text="Кластер AKS с AD и кластер больших данных SQL Server":::

## <a name="create-an-aks-private-cluster"></a>Создание частного кластера AKS

Для развертывания частного кластера AKS можно использовать следующую команду. Если частный кластер не требуется, удалите параметр `--enable-private-cluster` из команды. Дополнительные сведения о других требованиях см. в разделе [Развертывание кластера Azure Kubernetes (AKS)](/azure/aks/tutorial-kubernetes-deploy-cluster).

```azurecli
az aks create \
    --resource-group $RESOURCE_GROUP \
    --name $AKS_NAME \
    --load-balancer-sku standard \
    --enable-private-cluster \
    --network-plugin azure \
    --vnet-subnet-id $SUBNET_ID \
    --docker-bridge-address 172.17.0.1/16 \
    --dns-service-ip 10.3.0.10 \
    --service-cidr 10.3.0.0/24 \
    --node-vm-size Standard_D13_v2 \
    --node-count 2 \
    --generate-ssh-keys
```

После развертывания кластера AKS [установите подключение к нему](/azure/aks/tutorial-kubernetes-deploy-cluster#connect-to-cluster-using-kubectl).

## <a name="verify-reverse-dns-entry-for-domain-controller"></a>Проверка обратной DNS-записи для контроллера домена

Перед запуском развертывания кластера больших данных в режиме AD в кластере AKS убедитесь, что в самом контроллере домена есть и **запись типа A**, и **запись типа PTR** (обратная DNS-запись), зарегистрированные на DNS-сервере.

Для проверки этого параметра выполните команду `nslookup` или [скрипт PowerShell](troubleshoot-ad-reverse-lookup-zone.md), чтобы убедиться, что обратная DNS-запись (запись типа PTR) настроена.

## <a name="create-bdc-deployment-profile"></a>Создание профиля для развертывания кластера больших данных

Чтобы создать профиль развертывания, выполните следующую команду:

```console
azdata bdc config init --source kubeadm-prod  --target bdc-ad-aks
```

Следующие команды используются для настройки параметров профиля развертывания.

### <a name="controljson"></a>control.json

```console
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.spec.storage.data.className=default"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.spec.storage.logs.className=default"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.spec.endpoints[1].serviceType=NodePort"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.spec.endpoints[0].dnsName=controller.contoso.com"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.spec.endpoints[1].dnsName=proxys.contoso.com"

# security settings 
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.security.activeDirectory.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=com"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.security.activeDirectory.dnsIpAddresses=[\"192.168.0.4\"]"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.security.activeDirectory.domainControllerFullyQualifiedDns=[\"ad1.contoso.com\"]"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.security.activeDirectory.domainDnsName=contoso.com"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.security.activeDirectory.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -p bdc-ad-aks/control.json -j "$.security.activeDirectory.clusterUsers=[\"bdcusersgroup\"]"
```

### <a name="bdcjson"></a>bdc.json

```console
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=master.contoso.com"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.master.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=mastersec.contoso.com"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.master.spec.endpoints[1].serviceType=NodePort"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=gateway.contoso.com"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=approxy.contoso.com"
azdata bdc config replace -p bdc-ad-aks/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].serviceType=NodePort"
```

## <a name="initiate-deployment"></a>Запуск развертывания

Следующая команда запускает развертывание кластера больших данных:

```console
azdata bdc create --config-profile bdc-ad-aks --accept-eula yes
```

## <a name="next-steps"></a>Дальнейшие шаги

[Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md)

[Руководство. Загрузка примера данных в кластер больших данных SQL Server](tutorial-load-sample-data.md)