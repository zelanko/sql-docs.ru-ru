---
title: Настройка minikube
titleSuffix: SQL Server big data clusters
description: Сведения о настройке minikube для развернутых кластеров (Предварительная версия) SQL Server 2019 больших данных на одном компьютере.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 5b7698cd439461a9ee9280571f49649fb03387a8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803097"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>Настройка minikube, для развертывания кластера больших данных в SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается настройка **minikube** на одном компьютере для развертываний кластеров (Предварительная версия) SQL Server 2019 больших данных. Minikube — это средство, которое позволяет легко запускать Kubernetes на одном компьютере как ноутбук или к рабочему столу. Minikube запускает одноузловой кластер Kubernetes внутри виртуальной Машины на локальном компьютере для пользователей, которые хотят опробовать Kubernetes или разработку, используя его повседневной. 

## <a name="prerequisites"></a>предварительные требования

- 32 ГБ памяти (рекомендуется 64 ГБ).

- Если на компьютере установлена только минимум, рекомендованный объем памяти, затем настройки развертывания кластера могут быть только 1 вычислительный экземпляр пула, 1 экземпляр пула данных и экземпляр пула хранения 1. Эта конфигурация должна использоваться только в тестовых средах где устойчивости и доступности данных не важен. См. в разделе [документации по развертыванию](deployment-guidance.md#configfile) Дополнительные сведения о переменных среды, чтобы задать для настройки числа реплик для данных пулов вычислительных пулов и пулы носителей.

- Виртуализации VT-x или AMD-v необходимо включить в BIOS компьютера.

## <a name="install-dependencies"></a>Установка зависимостей

1. Установка [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Установите Python 3:
   - Если pip не найден, загрузите [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) и запустите `python get-pip.py`.
   - Запрашивает установку пакета с помощью `python -m pip install requests`.

1. Если у вас еще нет установлена низкоуровневая оболочка, установите его сейчас.
   - OS X, установка [драйвер xhyve](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), или [VMware Fusion](https://www.vmware.com/products/fusion).
   - Для Linux, установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [KVM](https://www.linux-kvm.org/).
   - Для Windows, установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Если у вас внешний коммутатор, настроенный в hyper-v, создайте приложение, имеющее доступ внешней сети.  См. в разделе Практическое [создать внешний коммутатор в hyper-v для minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Установка minikube

Установка minikube в соответствии с инструкциями для [v0.28.2 выпуска](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Кластера SQL Server 2019 больших данных (Предварительная версия) работает только в версии v0.24.1 и более.

## <a name="create-a-minikube-cluster"></a>Создание кластера minikube

Следующая команда создает кластер minikube в виртуальной Машине Hyper-V с 8 процессорами, 28 ГБ памяти и диск размером 100 ГБ. Размер диска не зарезервированного пространства.  При необходимости, то его значение роста, размер на диске.  Мы рекомендуем не будет изменен на диске пространства на что-нибудь менее 100 ГБ, как мы столкнулись с проблемами с этим при тестировании. Это также указывает коммутатора hyper-v с внешним доступом явным образом.

Изменить параметры, такие как **--памяти** при необходимости в зависимости от доступного оборудования и который вы используете низкоуровневой оболочки.  Убедитесь, что **--hyper-v** значение параметра виртуального коммутатора совпадает с именем, использованным при создании виртуального коммутатора.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Если вы используете minikube с помощью VirtualBox, команда будет выглядеть следующим образом:

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Отключение автоматической контрольной точки с помощью Hyper-V

В Windows 10 автоматическая контрольная точка включена на виртуальной Машине. Выполните указанную ниже команду в PowerShell для отключения автоматических контрольных точек на виртуальной Машине.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье настроили кластер minikube. Следующим шагом является развертывание кластера SQL Server 2019 больших данных. Инструкции см. следующую статью:

[Развертывание кластеров SQL Server 2019 больших данных в Kubernetes](deployment-guidance.md#deploy)
