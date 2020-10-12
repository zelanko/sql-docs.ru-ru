---
title: Установка azdata с помощью pip
titleSuffix: ''
description: Узнайте, как установить средство azdata с помощью pip.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ecf4eaaddf9423bb9a3ae88036b5c3cb2090451b
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725291"
---
# <a name="install-azdata-with-pip"></a>Установка `azdata` с помощью `pip`

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

В этой статье описывается установка средства `azdata` в Windows,Linux или macOS/OS X с помощью `pip`.

> [!TIP]
> Для упрощения задачи `azdata` можно установить с помощью [диспетчера пакетов](./deploy-install-azdata.md) для Windows, Linux (дистрибутивы Ubuntu, Debian, RHEL, CentOS, openSUSE и SLE) и macOS.

## <a name="prerequisites"></a><a id="prerequisites"></a> Предварительные требования

`azdata` — это служебная программа командной строки на языке Python, которая позволяет администраторам кластера выполнять начальную загрузку ресурсов данных и управлять ими с помощью REST API. Минимальная требуемая версия Python — 3.5. Для загрузки и установки средства `azdata` требуется `pip`. В приведенных ниже инструкциях приведены примеры для Windows, Linux (Ubuntu) и macOS/OS X. Сведения об установке Python на других платформах см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download). Кроме того, нужно также установить и обновить последнюю версию пакета Python `requests`.

```bash
pip3 install -U requests
```

## <a name="windows-azdata-installation"></a><a id="windows"></a> Установка `azdata` в Windows

1. В клиенте Windows скачайте необходимый пакет Python из [https://www.python.org/downloads/](https://www.python.org/downloads/). В Python 3.5.3 и более поздних версий pip3 устанавливается вместе с Python.

   > [!TIP]
   > При установке Python3 добавьте Python в свою переменную `PATH`. Если это не сделано, позднее можно найти расположение pip3 и добавить его в переменную `PATH` вручную.

1. Откройте новый сеанс Windows PowerShell, чтобы он использовал актуальный путь для Python.

1. Начиная с выпуска SQL Server 2019 CU5, azdata имеет независимую от сервера семантическую версию. Если до этого были установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии.

   Например, для 2019-cu4 выполните следующую команду:

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-cu4/requirements.txt
   ```

  > [!NOTE]
  > В приведенных выше примерах замените `2019-cu6` на версию и CU вашей установки `azdata`. 

1. Установить службы `azdata`.

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

1. Начиная с выпуска SQL Server 2019 CU5, azdata имеет независимую от сервера семантическую версию. Если до этого были установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии.

   Например, для `2019-cu6` выполните следующую команду:

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-cu6/requirements.txt
   ```

  > [!NOTE]
  > В приведенных выше примерах замените `2019-cu6` на версию и CU вашей установки `azdata`.

1. Установить службы `azdata`.

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Параметр `--user` задает установку `azdata` в пользовательский каталог установки Python. В Linux это обычно `~/.local/bin`. Добавьте этот каталог в путь или перейдите в пользовательский каталог установки и запустите `./azdata` оттуда.

## <a name="install-azdata-on-macos-or-os-x"></a><a id="macOSX"></a> Установка `azdata` в macOS или OS X

Чтобы установить `azdata` в macOS или OS X, выполните следующие действия. Для каждого шага запустите пример в окне терминала.

1. На клиенте macOS установите программу [Homebrew](https://brew.sh), если она еще не установлена.

   ```bash
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

1. Установите Python и pip (минимальная версия 3.0):

   ```bash
   brew install python3
   ```

1. Установите зависимости:

   ```bash
   pip3 install -U requests
   brew install freetds
   ```

1. Начиная с выпуска SQL Server 2019 CU5, azdata имеет независимую от сервера семантическую версию. Если до этого были установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии. Например, следующая команда удаляет версию RC1 `azdata`:

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Установить службы `azdata`.

   ```bash
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Использование azdata со [службами данных с поддержкой Azure Arc](/azure/azure-arc/data/)
