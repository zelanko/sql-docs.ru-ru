---
title: Установка azdata с помощью pip
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство azdata для установки кластеров больших данных и управления ими с помощью pip.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 034514c13a65171fca9eb1fc20b6c496329816a1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773635"
---
# <a name="install-azdata-with-pip"></a>Установка `azdata` с помощью `pip`

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается установка средства `azdata` в Windows или Linux с помощью `pip`.

В Windows и Linux (дистрибутив Ubuntu) для простоты можно выполнить установку с помощью [диспетчера пакетов](./deploy-install-azdata-installer.md).

## <a name="prerequisites"></a><a id="prerequisites"></a> Предварительные требования

`azdata` — это служебная программа командной строки на языке Python, которая позволяет администраторам кластера выполнять начальную загрузку кластера больших данных и управлять им с помощью REST API. Минимальная требуемая версия Python — 3.5. Для загрузки и установки средства `azdata` требуется `pip`. В инструкциях ниже приведены примеры для Windows и Ubuntu. Сведения об установке Python на других платформах см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).
Кроме того, нужно также установить и обновить последнюю версию пакета Python `requests`.

```bash
pip3 install -U requests
```

> [!IMPORTANT]
> При установке более новой версии кластеров больших данных создайте резервную копию своих данных и удалите старый кластер, обновив `azdata` и установив новый выпуск. Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

## <a name="windows-azdata-installation"></a><a id="windows"></a> Установка `azdata` в Windows

1. В клиенте Windows скачайте необходимый пакет Python из [https://www.python.org/downloads/](https://www.python.org/downloads/). Для Python 3.5.3 и более поздних версий pip3 устанавливается вместе с Python. 

   > [!TIP] 
   > При установке Python3 добавьте Python в свою переменную `PATH`. Если это не сделано, позднее можно найти расположение pip3 и добавить его в переменную `PATH` вручную.

1. Откройте новый сеанс Windows PowerShell, чтобы он использовал актуальный путь для Python.

1. Если установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии.

   Для CTP 3.2 или RC1 выполните следующую команду.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```
   или диспетчер конфигурации служб
   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Установите `azdata` с помощью следующей команды:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="linux-azdata-installation"></a><a id="linux"></a> Установка `azdata` в Linux

В Linux нужно установить Python 3.5, а затем обновить pip. В следующем примере показаны команды, которые будут работать для Ubuntu. Сведения о других платформах Linux см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Установите необходимые пакеты Python.

   ```bash
   sudo apt-get update && \
   sudo apt-get install -y python3 && \
   sudo apt-get install -y python3-pip && \
   sudo apt-get install -y libkrb5-dev && \
   sudo apt-get install -y libsqlite3-dev && \
   sudo apt-get install -y unixodbc-dev
   ```

1. Обновите pip3.

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Если установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии.

   Для CTP 3.2 или RC1 выполните следующую команду.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```
   или диспетчер конфигурации служб
   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Установите `azdata` с помощью следующей команды:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Параметр `--user` задает установку `azdata` в пользовательский каталог установки Python. В Linux это обычно `~/.local/bin`. Добавьте этот каталог в путь или перейдите в пользовательский каталог установки и запустите `./azdata` оттуда.

## <a name="install-azdata-on-macos-or-os-x"></a><a id="macOSX"></a> Установка `azdata` в macOS или OS X

Чтобы установить `azdata` в macOS или OS X, выполните следующие действия. Для каждого шага запустите пример в окне терминала.

1. На клиенте macOS установите программу [Homebrew](https://brew.sh), если она еще не установлена.

   ```
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

1. Установите Python и pip (минимальная версия 3.0):

   ```
   brew install python3
   ```

1. Установите зависимости:

   ```
   pip3 install -U requests
   brew install freetds
   ```

1. Если установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии. Следующая команда удаляет версию `azdata`.

   ```
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Установите `azdata` с помощью следующей команды:

   ```
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
