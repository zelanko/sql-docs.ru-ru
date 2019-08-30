---
title: Установка аздата с помощью PIP
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство аздата для установки и управления [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Предварительная версия) с помощью PIP.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a72e2ab39a17adef6c330f1ae17dcdc8a5dd8ddf
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160735"
---
# <a name="install-azdata-for-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-using-pip"></a>Установить `azdata` для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] использования`pip`

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как установить `azdata` средство для версии-кандидата в Windows или Linux `pip`с помощью.

## <a id="prerequisites"></a> Предварительные требования

`azdata`— это служебная программа командной строки, написанная на языке Python, которая позволяет администраторам кластера выполнять начальную загрузку и управление кластером больших данных с помощью интерфейсов API. Минимальная требуемая версия Python — 3.5. Кроме того `pip` , для загрузки и установки `azdata` средства необходимо использовать именно этот инструмент. В инструкциях ниже приведены примеры для Windows и Ubuntu. Сведения об установке Python на других платформах см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).
Кроме того, нужно также установить и обновить последнюю версию пакета Python *requests*.
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> При установке более новой версии кластеров больших данных необходимо создать резервную копию данных и удалить старый кластер *перед* обновлением `azdata` и установкой нового выпуска. Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

## <a id="windows"></a>Установка `azdata` Windows

1. В клиенте Windows скачайте необходимый пакет Python из [https://www.python.org/downloads/](https://www.python.org/downloads/). Для Python 3.5.3 и более поздних версий pip3 устанавливается вместе с Python. 

   > [!TIP] 
   > При установке Python3 добавьте Python в свою переменную **PATH**. Если этого не сделать, позже можно будет найти расположение pip3 и добавить его в **PATH** вручную.

1. Откройте новый сеанс Windows PowerShell, чтобы он использовал актуальный путь для Python.

1. Если установлены предыдущие версии средства (до CTP-версии 3,2, это средство было называлось **мссклктл**), прежде чем устанавливать последнюю версию `azdata`, необходимо сначала удалить его. Следующая команда удаляет версию **мссклктл**для CTP-версии 3,1.

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Если у вас есть предыдущие выпуски `azdata` , важно сначала удалить ее перед установкой последней версии.

   Для CTP-версии 3,2 выполните следующую команду.

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

1. Установите `azdata` с помощью следующей команды:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Установка `azdata` Linux

В Linux нужно установить Python 3.5, а затем обновить pip. В следующем примере показаны команды, которые будут работать для Ubuntu. Сведения о других платформах Linux см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Установите необходимые пакеты Python.

   ```bash
   sudo apt-get update && \
   sudo apt-get install -y python3 && \
   sudo apt-get install -y python3-pip
   ```

1. Обновите pip3.

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Если установлены предыдущие версии средства (до CTP-версии 3,2, это средство было называлось **мссклктл**), прежде чем устанавливать последнюю версию `azdata`, необходимо сначала удалить его. Следующая команда удаляет версию **мссклктл**для CTP-версии 3,1.

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Если у вас есть предыдущие выпуски `azdata` , важно сначала удалить ее перед установкой последней версии.

   Для CTP-версии 3,2 выполните следующую команду.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

1. Установите `azdata` с помощью следующей команды:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > `--user` Параметр устанавливается`azdata` в каталог установки пользователя Python. В Linux это обычно `~/.local/bin`. Добавьте этот каталог в путь или перейдите в пользовательский каталог установки и запустите `./azdata` оттуда.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]что такое?](big-data-cluster-overview.md).
