---
title: Настройка Kubernetes с использованием kubeadm
titleSuffix: SQL Server Big Data Clusters
description: Сведения о том, как настроить Kubernetes на нескольких компьютерах с Ubuntu 16.04 или 18.04 (физических или виртуальных) для развертываний [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6b5f2c8dac062f147326a0b9fcfb7120f0648729
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74165435"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>Настройка Kubernetes на нескольких компьютерах для развертываний кластера больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья содержит пример использования **kubeadm** для настройки Kubernetes на нескольких компьютерах для развертываний [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. В этом примере целевым объектом являются несколько компьютеров с Ubuntu 16.04 или 18.04 LTS (физических или виртуальных). При развертывании на другой платформе Linux нужно изменить некоторые команды в соответствии с вашей системой.  

> [!TIP] 
> Примеры сценариев, которые настраивают Kubernetes, см. в статье [ Создание кластера Kubernetes с использованием Kubeadm в Ubuntu 16.04 LTS или 18.04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).
Кроме того, в [этом](deployment-script-single-node-kubeadm.md) разделе приведен пример скрипта, который автоматизирует развертывание kubeadm из одного узла на виртуальной машине, а затем поверх него развертывает конфигурацию по умолчанию кластера больших данных.

## <a name="prerequisites"></a>предварительные требования

- Не меньше 3 физических компьютеров или виртуальных машин с Linux
- Рекомендуемая конфигурация отдельного компьютера:
   - 8 ЦП
   - 64 ГБ памяти
   - 100 ГБ хранилища
 
> [!Important] 
> Перед развертыванием кластера больших данных необходимо убедиться, что часы во всех узлах Kubernetes, участвующих в развертывании, синхронизированы. Кластер больших данных имеет встроенные свойства обеспечения работоспособности разных служб, которые зависят от времени, поэтому любые отклонения во времени могут привести к неправильной работе системы.

## <a name="prepare-the-machines"></a>Подготовка компьютеров

На каждом компьютере нужно выполнить несколько предварительных условий. Выполните следующие команды в терминале bash на каждом компьютере:

1. Добавьте текущий компьютер в файл `/etc/hosts`:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Отключите подкачку на всех устройствах.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Импортируйте ключи и зарегистрируйте репозиторий для Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Настройте на компьютере необходимые компоненты Docker и Kubernetes.

   ```bash
   KUBE_DPKG_VERSION=1.15.0-00 #or your other target K8s version, which should be at least 1.13.
   sudo apt-get update && \
   sudo apt-get install -y ebtables ethtool && \
   sudo apt-get install -y docker.io && \
   sudo apt-get install -y apt-transport-https && \
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && \
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Задайте `net.bridge.bridge-nf-call-iptables=1`. В Ubuntu 18.04 выполните указанную ниже команду для включения `br_netfilter`.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Настройка главного узла Kubernetes

После выполнения предыдущих команд на каждом компьютере выберите один из компьютеров в качестве главного узла Kubernetes. Затем выполните на этом компьютере указанные ниже команды.

1. Сначала создайте файл rbac.yaml в текущем каталоге с помощью следующей команды. 

   ```bash
   cat <<EOF > rbac.yaml
   apiVersion: rbac.authorization.k8s.io/v1beta1
   kind: ClusterRoleBinding
   metadata:
     name: default-rbac
   subjects:
   - kind: ServiceAccount
     name: default
     namespace: default
   roleRef:
     kind: ClusterRole
     name: cluster-admin
     apiGroup: rbac.authorization.k8s.io
   EOF
   ```

1. Инициализируйте главный узел Kubernetes на этом компьютере. В приведенном ниже примере сценария указана версия Kubernetes `1.15.0`. Используемая версия зависит от кластера Kubernetes.

   ```bash
   KUBE_VERSION=1.15.0
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

   Вы должны увидеть выходные данные, указывающие на успешную инициализацию главного узла Kubernetes.

1. Обратите внимание на команду `kubeadm join`, которую нужно использовать на других серверах для присоединения к кластеру Kubernetes. Скопируйте ее для последующего использования.

   ![kubeadm join](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Настройте файл конфигурации Kubernetes в домашнем каталоге.

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. Настройте кластер и панель мониторинга Kubernetes.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Настройка агентов Kubernetes

Другие компьютеры будут выступать в качестве агентов Kubernetes в кластере. 

На каждом из остальных компьютеров выполните команду `kubeadm join`, скопированную в предыдущем разделе.

![kubeadm join agents](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Просмотр состояния кластера

Чтобы проверить подключение к кластеру, используйте команду [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) для получения списка узлов кластера.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Дальнейшие действия

Действия, описанные в этой статье, обеспечивают настройку кластера Kubernetes на нескольких компьютерах Ubuntu. Следующим шагом является развертывание кластера больших данных SQL Server 2019. Инструкции см. в следующей статье:

[Развертывание SQL Server в Kubernetes](deployment-guidance.md#deploy)
