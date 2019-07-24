---
title: Установка аздата
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство аздата для установки и управления кластерами больших данных SQL Server 2019 (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9444842081456563f411ad618f32b8dbd59f7513
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426444"
---
# <a name="install-azdata-to-manage-sql-server-big-data-clusters"></a>Установка аздата для управления кластерами больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как установить средство **аздата** для CTP-версии 3,2 в Windows или Linux.

## <a id="prerequisites"></a> Предварительные требования

**аздата** — это служебная программа командной строки, написанная на языке Python, которая позволяет администраторам кластера выполнять начальную загрузку и управление кластером больших данных с помощью интерфейсов API. Минимальная требуемая версия Python — v 3.5. Кроме того `pip` , необходимо использовать это средство для загрузки и установки средства **аздата** . В приведенных ниже инструкциях приведены примеры для Windows и Ubuntu. Сведения об установке Python на других платформах см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).
Кроме того, необходимо также установить и обновить последнюю версию *запроса* пакета Python:
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> При установке более новой версии кластеров больших данных необходимо создать резервную копию данных и удалить старый кластер *перед* обновлением **аздата** и установкой нового выпуска. Дополнительные сведения см. [в разделе Обновление до новой версии](deployment-upgrade.md).

## <a id="windows"></a>Установка аздата Windows

1. В клиенте Windows Скачайте необходимый пакет Python из [https://www.python.org/downloads/](https://www.python.org/downloads/). Для Python 3.5.3 и более поздних версий pip3 также устанавливается при установке Python. 

   > [!TIP] 
   > При установке Python3 выберите, чтобы добавить Python в **путь**. Если этого не сделать, позже можно будет найти место расположения pip3 и добавить его в свой **путь**вручную.

1. Откройте новый сеанс Windows PowerShell, чтобы он получит последний путь с Python в нем.

1. При наличии предыдущих выпусков средства (превиосли с именем **мссклктл**) необходимо сначала удалить его перед установкой последней версии **аздата**.

   Для CTP-версии 3,1 или более ранней выполните следующую команду. Замените `ctp3.1` в команде на версию **мссклктл** , которую вы удаляете. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Если у вас есть предыдущие выпуски **аздата** , важно сначала удалить ее перед установкой последней версии.

   Для CTP-версии 3,2 или более поздней выполните следующую команду. Замените `ctp3.2` в команде на версию **аздата** , которую вы удаляете.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Установите **аздата** с помощью следующей команды:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Установка аздата для Linux

В Linux необходимо установить Python 3,5, а затем обновить PIP. В следующем примере показаны команды, которые будут работать для Ubuntu. Другие платформы Linux см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Установите необходимые пакеты Python:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Обновление pip3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. При наличии предыдущих выпусков средства (ранее именуемых **мссклктл**) перед установкой последней версии **аздата**необходимо сначала удалить его.

   Для CTP-версии 3,1 или более ранней выполните следующую команду. Замените `ctp3.1` в команде на версию **мссклктл** , которую вы удаляете. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Если у вас есть предыдущие выпуски **аздата** , важно сначала удалить ее перед установкой последней версии.

   Для CTP-версии 3,2 или более поздней выполните следующую команду. Замените `ctp3.2` в команде на версию **аздата** , которую вы удаляете.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Установите **аздата** с помощью следующей команды:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > `--user` Параметр устанавливает аздата в каталог установки пользователя Python. Обычно `~/.local/bin` это происходит в Linux. Добавьте этот каталог в путь или перейдите к каталогу установки пользователя и запустите `./azdata` его.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md).
