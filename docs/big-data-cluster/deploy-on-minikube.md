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
ms.openlocfilehash: 6c2261b5cfbbe590c76ce410da4b95ee678a20b5
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958476"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>Настройка minikube для развертываний кластера больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья описывает, как настроить на отдельном компьютере средство **minikube** для развертываний кластера больших данных SQL Server 2019 (предварительная версия). Средство Minikube упрощает запуск Kubernetes на отдельном компьютере, например на ноутбуке или на настольной системе. Minikube запускает кластер Kubernetes с одним узлом в виртуальной машине на ноутбуке для пользователей, которые хотят опробовать Kubernetes или работать с ней каждый день. 

## <a name="prerequisites"></a>предварительные требования

- 32 ГБ памяти (рекомендуется 64 ГБ).

- Если компьютер имеет только минимальный рекомендуемый объем памяти, настройте для развертывания кластера только 1 экземпляр вычислительного пула, 1 экземпляр пула данных и 1 экземпляр пула носителей. Эту конфигурацию следует использовать только для сред оценки, в которых устойчивость и доступность данных несущественны. Дополнительные сведения о переменных среды, которые нужно задать для настройки количества реплик для пулов данных, вычислительных пулов и пулов носителей, см. в [документации по развертыванию](deployment-guidance.md#configfile).

- В BIOS компьютера должна быть включена виртуализация VT-x или AMD-v.

## <a name="install-dependencies"></a>Установка зависимостей

1. Установите [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Установите Python 3:
   - если pip отсутствует, скачайте [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) и запустите `python get-pip.py`.
   - Установите пакет запросов с помощью `python -m pip install requests`.

1. Если гипервизор еще не установлен, установите его.
   - Для OS X установите [драйвер xhyve](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [VMware Fusion](https://www.vmware.com/products/fusion).
   - Для Linux установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [KVM](https://www.linux-kvm.org/).
   - Для Windows установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Если у вас нет внешнего коммутатора, настроенного в Hyper-V, создайте его с доступом к внешней сети.  См. описание [создания внешнего коммутатора в Hyper-V для minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Установка minikube

Установите minikube в соответствии с инструкциями для [выпуска 0.28.2](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Кластер больших данных SQL Server 2019 (предварительная версия) работает только с версией 0.24.1 и выше.

## <a name="create-a-minikube-cluster"></a>Создание кластера minikube

Приведенная ниже команда создает кластер minikube в виртуальной машине Hyper-V с 8 ЦП, с 28 ГБ памяти и размером диска 100 ГБ. Размер диска не является зарезервированным пространством.  При необходимости кластер увеличивается до этого размера на диске.  Не рекомендуется устанавливать место на диске менее 100 ГБ, так как при тестировании в этом случае возникали проблемы. Здесь также явно задается коммутатор Hyper-V с внешним доступом.

При необходимости измените параметры, такие как **--memory**, в зависимости от имеющегося оборудования и используемого гипервизора.  Убедитесь, что значение параметра виртуального коммутатора **--hyper-v** соответствует имени, которое использовалось при создании виртуального коммутатора.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Если вы используете minikube с VirtualBox, команда будет выглядеть следующим образом.

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Отключение автоматической контрольной точки с помощью Hyper-V

В Windows 10 на виртуальной машине включена автоматическая контрольная точка. Выполните приведенную ниже команду в PowerShell, чтобы отключить автоматическую контрольную точку на виртуальной машине.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье, обеспечивают настройку кластера minikube. Следующим шагом является развертывание кластера больших данных SQL Server 2019. Инструкции см. в следующей статье:

[Развертывание кластеров больших данных SQL Server 2019 в Kubernetes](deployment-guidance.md#deploy).
