---
title: Управление кластерами больших данных (BDC) в частном кластере службы Azure Kubernetes (AKS)
titleSuffix: SQL Server Big Data Cluster
description: Сведения об управлении кластерами больших данных SQL Server в частном кластере службы Azure Kubernetes (AKS).
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 08/20/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 442f5def7e1378b750460cfc6860e780b1dcfd80
ms.sourcegitcommit: fe5dedb2a43516450696b754e6fafac9f5fdf3cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2020
ms.locfileid: "89202230"
---
# <a name="manage-big-data-cluster-in-aks-private-cluster"></a>Управление кластером больших данных в частном кластере AKS

В этой статье объясняется, как управлять частным кластером службы Azure Kubernetes (AKS) с развернутыми в Azure кластерами больших данных (BDC) SQL Server.

Как описано в разделе [Создание частного кластера](/azure/aks/private-clusters/), конечная точка сервера API частного кластера AKS не имеет общедоступного IP-адреса. Для управления сервером API следует использовать виртуальную машину, имеющую доступ к виртуальной сети Azure кластера AKS.

## <a name="azure-vm---same-vnet"></a>Виртуальная машина Azure — это виртуальная сеть

Самый простой способ — развернуть виртуальную машину Azure в той же виртуальной сети, что и кластер AKS.

1. Разверните виртуальную машину Azure в одной виртуальной сети с кластером AKS. Иногда ее называют *Jumpbox*.
1. Подключитесь к этой виртуальной машине и [установите средства для работы с большими данными SQL Server 2019](deployment-guidance.md#install-sql-server-2019-big-data-tools).

В целях безопасности можно использовать функции AKS для IP-адресов, разрешенных сервером API, чтобы ограничить доступ к серверу API (на уровне управления AKS). Ограниченный доступ позволяет использовать определенные IP-адреса, такие как виртуальная машина Jumpbox или виртуальная машина управления, или диапазон IP-адресов для группы разработчиков, а также общедоступный интерфейсный IP-адрес брандмауэра.

## <a name="other-options"></a>Другие варианты

Ниже перечислены альтернативные варианты использования Jumpbox.

* Использовать виртуальную машину в отдельной сети и настроить [пиринг виртуальных сетей](/azure/virtual-network/virtual-network-peering-overview) для виртуальной сети.

* Подключение [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) или [VPN-шлюза](/azure/vpn-gateway/vpn-gateway-about-vpngateways).

   [Варианты подключения к частному кластеру](/azure/aks/private-clusters#options-for-connecting-to-the-private-cluster) предусматривают каждый из этих методов, названных выше.

* Если служба работает за [стандартной подсистемой балансировки нагрузки Azure](/azure/aks/load-balancer-standard) ее можно включить для [Приватного канала Azure](/azure/private-link/private-link-service-overview#limitations). С помощью частного канала Azure можно включить частный доступ из других виртуальных сетей Azure.

* В гибридном сценарии можно также настроить подключения [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) или [VPN-шлюз](/azure/vpn-gateway/vpn-gateway-about-vpngateways).

## <a name="next-steps"></a>Дальнейшие шаги

[Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md)