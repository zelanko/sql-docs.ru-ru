---
title: Установка azdata
titleSuffix: SQL Server big data clusters
description: Сведения об установке средства azdata для установки кластеров больших данных SQL Server 2019 и управления ими (предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9444842081456563f411ad618f32b8dbd59f7513
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426444"
---
# <a name="install-azdata-to-manage-sql-server-big-data-clusters"></a>Установка azdata для управления кластерами больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья описывает установку средства **azdata** для CTP 3.2 в Windows или Linux.

## <a id="prerequisites"></a> Предварительные требования

**azdata** — это служебная программа командной строки на языке Python, которая позволяет администраторам кластера провести начальную загрузку кластера больших данных и управлять им с помощью интерфейсов REST API. Минимальная требуемая версия Python — 3.5. Кроме того, требуется `pip`, используемый для скачивания и установки средства **azdata**. В инструкциях ниже приведены примеры для Windows и Ubuntu. Сведения об установке Python на других платформах см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).
Кроме того, нужно также установить и обновить последнюю версию пакета Python *requests*.
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> При установке более новой версии кластеров больших данных нужно создать резервную копию данных и удалить старый кластер *перед* обновлением **azdata** и установкой нового выпуска. Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

## <a id="windows"></a> Установка azdata в Windows

1. В клиенте Windows скачайте необходимый пакет Python из [https://www.python.org/downloads/](https://www.python.org/downloads/). Для Python 3.5.3 и более поздних версий pip3 устанавливается вместе с Python. 

   > [!TIP] 
   > При установке Python3 добавьте Python в свою переменную **PATH**. Если этого не сделать, позже можно будет найти расположение pip3 и добавить его в **PATH** вручную.

1. Откройте новый сеанс Windows PowerShell, чтобы он использовал актуальный путь для Python.

1. Если установлены какие-либо предыдущие выпуски средства (которое ранее называлось **mssqlctl**), нужно обязательно удалить их перед установкой последней версии **azdata**.

   Для CTP 3.1 выполните следующую команду. Замените `ctp3.1` в команде на удаляемую версию **mssqlctl**. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Если установлены какие-либо предыдущие выпуски **azdata**, нужно обязательно удалить их перед установкой последней версии.

   Для CTP 3.2 или более поздней версии выполните приведенную ниже команду. Замените `ctp3.2` в команде на удаляемую версию **azdata**.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Установите **azdata** с помощью следующей команды.

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a> Установка azdata в Linux

В Linux нужно установить Python 3.5, а затем обновить pip. В следующем примере показаны команды, которые будут работать для Ubuntu. Сведения о других платформах Linux см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Установите необходимые пакеты Python.

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Обновите pip3.

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Если установлены какие-либо предыдущие выпуски средства (которое ранее называлось **mssqlctl**), нужно обязательно удалить их перед установкой последней версии **azdata**.

   Для CTP 3.1 выполните следующую команду. Замените `ctp3.1` в команде на удаляемую версию **mssqlctl**. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Если установлены какие-либо предыдущие выпуски **azdata**, нужно обязательно удалить их перед установкой последней версии.

   Для CTP 3.2 или более поздней версии выполните приведенную ниже команду. Замените `ctp3.2` в команде на удаляемую версию **azdata**.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Установите **azdata** с помощью следующей команды.

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Параметр `--user` устанавливает installs в пользовательский каталог установки Python. В Linux это обычно `~/.local/bin`. Добавьте этот каталог в путь или перейдите в пользовательский каталог установки и запустите `./azdata` оттуда.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в статье [Что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md)
