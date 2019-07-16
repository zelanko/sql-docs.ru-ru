---
title: Установка mssqlctl
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство mssqlctl по установке и управлению кластерами больших данных SQL Server 2019 (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3be1987baed27aeb49b03942ca3c4f07c2b0ce0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958527"
---
# <a name="install-mssqlctl-to-manage-sql-server-big-data-clusters"></a>Установка mssqlctl для управления кластерами больших данных в SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается установка **mssqlctl** средство для CTP-версии 3.1 в Windows или Linux.

**mssqlctl** — программа командной строки, написанный на Python, что позволяет кластера администраторов для начальной загрузки и управления кластером больших данных с помощью REST API. Минимальная требуемая версия Python — версии 3.5. Необходимо также иметь `pip` , используемый для загрузки и установки **mssqlctl** средство. В инструкциях ниже приведены примеры для Windows и Ubuntu. Установка Python на других платформах, см. в разделе [документации Python](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> При установке новой версии кластеров больших данных, необходимо создать резервную копию данных и удалить старый кластер *перед* обновление **mssqlctl** и установки новой версии. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-upgrade.md).

## <a id="windows"></a> Mssqlctl установки Windows

1. На клиенте Windows, скачайте необходимые пакеты Python из [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Python3.5.3 и более поздних версий pip3 также устанавливается одновременно с установкой Python. 

   > [!TIP] 
   > При установке Python3, выберите, чтобы добавить код Python вашей **путь**. Если этого не сделать, можно позже найти расположение pip3 и вручную добавить его к вашей **путь**.

1. Откройте новый сеанс Windows PowerShell, чтобы он возвращает последнюю путь с Python в нем.

1. Если у вас есть все предыдущие выпуски **mssqlctl** установлен, очень важно удалить **mssqlctl** перед установкой последней версии.

   Если вы удаляете **mssqlctl** до CTP-версии 2.2 или ниже версии запуска:

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Для CTP-версия 2.3 или более поздней версии выполните следующую команду. Замените `ctp3.0` в команде с версией **mssqlctl** , при удалении. Если версия до версии CTP 3.0, добавить дефис перед номер версии (например, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

## <a id="linux"></a> Установка mssqlctl Linux

В Linux необходимо установить Python 3.5 и затем обновить систему pip. В следующем примере показано команды, которые будут работать для Ubuntu. Для других платформ Linux, см. в разделе [документации Python](https://wiki.python.org/moin/BeginnersGuide/Download).

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

1. Если у вас есть все предыдущие выпуски **mssqlctl** установлен, очень важно удалить **mssqlctl** перед установкой последней версии.

   Если вы удаляете **mssqlctl** до CTP-версии 2.2 или ниже версии запуска:

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Для CTP-версия 2.3 или более поздней версии выполните следующую команду. Замените `ctp3.0` в команде с версией **mssqlctl** , при удалении. Если версия до версии CTP 3.0, добавить дефис перед номер версии (например, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt --user
   ```

   > [!NOTE]
   > `--user` Служит для установки mssqlctl в каталог установки Python пользователя. Обычно это `~/.local/bin` в Linux. Добавьте этот каталог в путь, перейдите в каталог установки пользователя и выполняться `./mssqlctl` оттуда.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
