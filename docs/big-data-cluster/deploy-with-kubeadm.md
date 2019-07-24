---
title: Настройка Kubernetes с помощью кубеадм
titleSuffix: SQL Server big data clusters
description: Узнайте, как настроить Kubernetes на нескольких компьютерах Ubuntu 16,04 или 18,04 (физических или виртуальных) для развертываний кластера больших данных SQL Server 2019 (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ea79503869e7d403e4d3f4f960de9c95760eda0f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419449"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>Настройка Kubernetes на нескольких компьютерах для SQL Server развертываний кластера больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье приведен пример использования **кубеадм** для настройки Kubernetes на нескольких компьютерах для развертываний кластера больших данных SQL Server 2019 (Предварительная версия). В этом примере целевым объектом являются несколько компьютеров Ubuntu 16,04 или 18,04 LTS (физический или виртуальный). При развертывании на другой платформе Linux необходимо изменить некоторые команды в соответствии с вашей системой.  

> [!TIP] 
> Примеры сценариев, которые настраивают Kubernetes, см. в статье [Создание кластера Kubernetes с помощью кубеадм в Ubuntu 16,04 LTS или 18,04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>предварительные требования

- Минимум 3 физических компьютера Linux или виртуальных машин
- Рекомендуемая конфигурация для каждого компьютера:
   - 8 ЦП
   - 64 ГБ памяти
   - 100 ГБ хранилища

## <a name="prepare-the-machines"></a>Подготовка компьютеров

На каждом компьютере есть несколько обязательных предварительных условий. В терминале Bash выполните следующие команды на каждом компьютере:

1. Добавьте текущий компьютер в `/etc/hosts` файл:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Отключите переключение на всех устройствах.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Импортируйте ключи и зарегистрируйте репозиторий для Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Настройте на компьютере необходимые компоненты DOCKER и Kubernetes.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Задайте `net.bridge.bridge-nf-call-iptables=1`. В Ubuntu 18,04 сначала включается `br_netfilter`Следующая команда.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Настройка главного сервера Kubernetes

После выполнения предыдущих команд на каждом компьютере выберите один из компьютеров в качестве главного Kubernetes. Затем выполните следующие команды на этом компьютере.

1. Сначала создайте файл RBAC. YAML в текущем каталоге с помощью следующей команды. 

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

1. Инициализируйте мастер Kubernetes на этом компьютере. Вы должны увидеть выходные данные, которые мастер Kubernetes успешно инициализировал.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Обратите внимание на команду, которую необходимо использовать на других серверах для приподключения к кластеру Kubernetes. `kubeadm join` Скопируйте его для последующего использования.

   ![кубеадм соединение](./media/deploy-with-kubeadm/kubeadm-join.png)

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
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Настройка агентов Kubernetes

Другие компьютеры будут действовать как агенты Kubernetes в кластере. 

На каждом из остальных компьютеров выполните `kubeadm join` команду, скопированную в предыдущем разделе.

![агенты кубеадм Join](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Просмотр состояния кластера

Чтобы проверить подключение к кластеру, используйте команду [kubectl Get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) , чтобы получить список узлов кластера.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье, настроили кластер Kubernetes на нескольких компьютерах Ubuntu. Следующим шагом является развертывание кластера больших данных SQL Server 2019. Инструкции см. в следующей статье:

[Развертывание SQL Server в Kubernetes](deployment-guidance.md#deploy)
