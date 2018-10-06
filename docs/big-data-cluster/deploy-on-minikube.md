---
title: Настройка Minikube для развертываний SQL Server 2019 CTP-версии 2.0 | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 1f20f2adc916a456e4a1975804fac1640ee95f69
ms.sourcegitcommit: 8aecafdaaee615b4cd0a9889f5721b1c7b13e160
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2018
ms.locfileid: "48818052"
---
# <a name="configure-minikube-for-sql-server-2019-ctp-20"></a>Настройка Minikube для SQL Server 2019 CTP 2.0

Minikube — это средство, которое позволяет легко запускать Kubernetes на одном компьютере как ноутбук или к рабочему столу. Minikube запускает одноузловой кластер Kubernetes внутри виртуальной Машины на локальном компьютере для пользователей, которые хотят опробовать Kubernetes или разработку, используя его повседневной. 

## <a name="prerequisites"></a>предварительные требования

- Чтобы запустить Minikube кластер для SQL Server 2019 CTP 2.0 в конфигурации кластера больших данных SQL, рекомендуется наличие по крайней мере 32 ГБ ОЗУ на компьютере.

   > [!TIP] 
   > Если на компьютере недостаточно памяти, измените конфигурацию кластера таким образом, создаются только 3 экземпляра: один основной экземпляр и два вычислительных экземпляров.

- Виртуализации VT-x или AMD-v необходимо включить в BIOS компьютера.

## <a name="install-dependencies"></a>Установка зависимостей

1. Если еще не установлен, установите локально на устройстве git [Windows](https://git-for-windows.github.io/), [Linux или Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

1. Установка [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Установите Python 3:
   - Если pip не найден, загрузите [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) и запустите `python get-pip.py`.
   - Запрашивает установку пакета с помощью `python -m pip install requests`.

1. Если у вас еще нет установлена низкоуровневая оболочка, установите его сейчас.
   - OS X, установка [драйвер xhyve](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), или [VMware Fusion](https://www.vmware.com/products/fusion).
   - Для Linux, установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [KVM](http://www.linux-kvm.org/).
   - Для Windows, установите [VirtualBox](https://www.virtualbox.org/wiki/Downloads) или [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Если у вас внешний коммутатор, настроенный в hyper-v, создайте приложение, имеющее доступ внешней сети.  См. в разделе Практическое [создать внешний коммутатор в hyper-v для minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Установка Minikube

Установка Minikube в соответствии с инструкциями для [v0.28.2 выпуска](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Большие данные кластера SQL Server 2019 CTP 2.0 работает только в том случае, в версии v0.24.1 и более.

## <a name="create-a-minikube-cluster"></a>Создание кластера Minikube

Следующая команда создает кластер minikube в виртуальной Машине Hyper-V с 8 процессорами, 28 ГБ памяти и диск размером 100 ГБ. Размер диска не зарезервированного пространства.  При необходимости, то его значение роста, размер на диске.  Мы рекомендуем не будет изменен на диске пространства на что-нибудь менее 100 ГБ, как мы столкнулись с проблемами с этим при тестировании. Это также указывает коммутатора hyper-v с внешним доступом явным образом.

Изменить параметры, такие как **--памяти** при необходимости в зависимости от доступного оборудования и который вы используете низкоуровневой оболочки.  Убедитесь, что **--hyper-v** значение параметра виртуального коммутатора совпадает с именем, использованным при создании виртуального коммутатора.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Если вы используете Minikube с помощью VirtualBox, команда будет выглядеть следующим образом:

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Отключение автоматической контрольной точки с помощью Hyper-V

В Windows 10 автоматическая контрольная точка включена на виртуальной Машине. Выполните указанную ниже команду в PowerShell для отключения автоматических контрольных точек на виртуальной Машине.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье настроили кластер Minikube. Следующим шагом является развертывание в кластере SQL Server 2019 CTP 2.0.

[Развертывание SQL Server 2019 CTP 2.0 в Kubernetes](deployment-guidance.md#deploy)
