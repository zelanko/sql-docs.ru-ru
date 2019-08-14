---
title: Настройка minikube
titleSuffix: SQL Server big data clusters
description: Сведения о том, как настроить средство minikube для развертываний кластера больших данных SQL Server 2019 (предварительная версия) на отдельном компьютере.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1991176de132062c46f36f30f4f384e483c069f9
ms.sourcegitcommit: 316c25fe7465b35884f72928e91c11eea69984d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "68969412"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>Настройка minikube для развертываний кластера больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья описывает, как настроить на отдельном компьютере средство **minikube** для развертываний кластера больших данных SQL Server 2019 (предварительная версия). Средство Minikube упрощает запуск Kubernetes на отдельном компьютере, например на ноутбуке или на настольной системе. Minikube запускает кластер Kubernetes с одним узлом в виртуальной машине на ноутбуке для пользователей, которые хотят опробовать Kubernetes или работать с ней каждый день. 

## <a name="prerequisites"></a>предварительные требования

- 64 ГБ памяти.

- Если компьютер имеет только минимальный рекомендуемый объем памяти, настройте для развертывания кластера только 1 экземпляр вычислительного пула, 1 экземпляр пула данных и 1 экземпляр пула носителей. Эту конфигурацию следует использовать только для сред оценки, в которых устойчивость и доступность данных несущественны. Дополнительные сведения о переменных среды, которые нужно задать для настройки количества реплик для пулов данных, вычислительных пулов и пулов носителей, см. в [документации по развертыванию](deployment-guidance.md#configfile).

- В BIOS компьютера должна быть включена виртуализация VT-x или AMD-v.

## <a name="install-dependencies"></a>Установка зависимостей

1. Установите [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Если гипервизор еще не установлен, установите его.
   - Для OS X установите [драйвер xhyve](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [VMware Fusion](https://www.vmware.com/products/fusion).
   - Для Linux установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [KVM](https://www.linux-kvm.org/).
   - Для Windows установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Если у вас нет внешнего коммутатора, настроенного в Hyper-V, создайте его, имеющий доступ к внешней сети. Узнайте, как [создать внешний коммутатор в Hyper-V для minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Установка minikube

Установите выпуск minikube в соответствии с инструкциями для [выпуска версии 1.3.0](https://github.com/kubernetes/minikube/releases/tag/v1.3.0). Кластер больших данных SQL Server 2019 (Предварительная версия) работает только с версиями 1.0.0 и выше.

## <a name="create-a-minikube-cluster"></a>Создание кластера minikube

Приведенная ниже команда создает кластер minikube на виртуальной машине Hyper-V с 8 ЦП, 64 ГБ памяти и размером диска в 100 ГБ. Размер диска не является зарезервированным пространством.  При необходимости кластер увеличивается до этого размера на диске.  Не рекомендуется устанавливать место на диске менее 100 ГБ, так как при тестировании в этом случае возникали проблемы. Здесь также указывается коммутатор Hyper-V с внешним доступом явным образом.

При необходимости измените параметры, такие как **--memory**, в зависимости от имеющегося оборудования и используемого гипервизора.  Убедитесь, что значение параметра виртуального коммутатора **--hyper-v** соответствует имени, которое использовалось при создании виртуального коммутатора.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 65536 --disk-size 100g --hyperv-virtual-switch "External"
```

Если вы используете minikube с VirtualBox, команда будет выглядеть следующим образом.

```base
minikube start --cpus 8 --memory 65536 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Отключение автоматической контрольной точки с помощью Hyper-V

В Windows 10 на виртуальной машине включена автоматическая контрольная точка. Выполните приведенную ниже команду в PowerShell, чтобы отключить автоматическую контрольную точку на виртуальной машине и задать статическую память.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false -StaticMemory
```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье, обеспечивают настройку кластера minikube. Следующим шагом является развертывание кластера больших данных SQL Server 2019. Инструкции см. в следующей статье:

[Развертывание кластеров больших данных SQL Server 2019 в Kubernetes](deployment-guidance.md#deploy).
