---
title: Настройка Kubernetes с помощью kubeadm для SQL Server 2019 развертываний | Документация Майкрософт
description: Сведения о настройке Kubernetes на несколько Ubuntu 16.04 или 18.04 компьютеров (физических или виртуальных) для развертывания кластера (Предварительная версия) SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/23/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 70ba143bf01336dbd77718007ccd0fb61acc21bb
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051395"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-2019-deployments"></a>Настройка Kubernetes на нескольких компьютерах, для развертываний SQL Server 2019

В этой статье приведен пример использования **kubeadm** Настройка Kubernetes на несколько компьютеров для развертывания кластера (Предварительная версия) SQL Server 2019 больших данных. В этом примере несколько Ubuntu 16.04 или 18.04 LTS компьютеров (физических или виртуальных) являются целью. При развертывании на другую платформу Linux, необходимо изменить некоторые из команд в соответствии с вашей системы.  

> [!TIP] 
> Примеры сценариев, которые настроить Kubernetes, см. в разделе [создание кластера Kubernetes с помощью Kubeadm на Ubuntu 16.04 LTS или 18.04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>предварительные требования

- Несколько Linux физические компьютеры или виртуальные машины для использования для кластера
- Рекомендуемая конфигурация: 8 процессоров, 32 ГБ памяти и по крайней мере 100 ГБ хранилища для каждой машины
- Минимум три машины в кластере

## <a name="prepare-the-machines"></a>Подготовка компьютеров

На каждом компьютере существует несколько необходимых компонентов. В терминале bash выполните следующие команды на каждом компьютере:

1. Добавить текущий компьютер `/etc/hosts` файла:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Отключите подкачку на всех устройствах.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Импортируйте ключи и зарегистрировать репозиторий для Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Настройка docker и Kubernetes необходимых компонентов на компьютере.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Задайте `net.bridge.bridge-nf-call-iptables=1`. На Ubuntu 18.04, сначала включите следующие команды `br_netfilter`.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Настройка главного Kubernetes

После выполнения предыдущей команды на каждом компьютере, выберите один из компьютеров вашей главную Kubernetes. Затем вы следующие команды на этом компьютере.

1. Во-первых создайте файл rbac.yaml в текущем каталоге с помощью следующей команды. 

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

1. Инициализация главного Kubernetes на этом компьютере. Вы должны увидеть результат, что Kubernetes master успешно инициализирована.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Примечание `kubeadm join` команды, что необходимо использовать на других серверах для присоединения к кластеру Kubernetes. Скопируйте этот для последующего использования.

   ![kubeadm соединения](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Настройте файл конфигурации Kubernetes свой домашний каталог.

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. Настройка кластера и панели мониторинга Kubernetes.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Настройка агентов Kubernetes

Других машин будет выступать в качестве агентов Kubernetes в кластере. 

На каждом из остальных компьютеров, запустите `kubeadm join` команду, скопированную в предыдущем разделе.

![kubeadm соединения агентов](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Просмотр состояния кластера

Чтобы проверить подключение к кластеру, используйте [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) команду, чтобы получить список узлов кластера.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье настроить кластер Kubernetes на нескольких компьютерах Ubuntu. Следующим шагом является развертывание кластера SQL Server 2019 больших данных. Инструкции см. следующую статью:

[Развертывание SQL Server 2019 CTP 2.0 в Kubernetes](deployment-guidance.md#deploy)
