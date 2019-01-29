---
title: Установка mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Узнайте, как установить средство mssqlctl по установке и управлению кластерами больших данных SQL Server 2019 (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/15/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d3ee1a0d2b6f3ec2c395b2c318aaf4b151497562
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087613"
---
# <a name="install-mssqlctl-to-manage-sql-server-2019-big-data-clusters"></a>Установка mssqlctl для управления кластерами SQL Server 2019 больших данных

В этой статье описывается установка **mssqlctl** средства в Windows или Linux.

**mssqlctl** — программа командной строки, написанный на Python, что позволяет кластера администраторов для начальной загрузки и управления кластером больших данных с помощью REST API. Минимальная требуемая версия Python — версии 3.5. Необходимо также иметь `pip` , используемый для загрузки и установки **mssqlctl** средство. В инструкциях ниже приведены примеры для Windows и Ubuntu. Установка Python на других платформах, см. в разделе [документации Python](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> Если вы установили предыдущую версию **mssqlctl**, необходимо удалить кластер *перед* обновление **mssqlctl** и установки новой версии. Дополнительные сведения см. в разделе [обновление до нового выпуска](deployment-guidance.md#upgrade).

## <a id="windows"></a> Mssqlctl установки Windows

1. На клиенте Windows, скачайте необходимые пакеты Python из [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Python3.5.3 и более поздних версий pip3 также устанавливается одновременно с установкой Python. 

   > [!TIP] 
   > При установке Python3, выберите, чтобы добавить код Python вашей **путь**. Если этого не сделать, можно позже найти расположение pip3 и вручную добавить его к вашей **путь**.

1. Откройте новый сеанс Windows PowerShell, чтобы он возвращает последнюю путь с Python в нем.

1. Если у вас есть все предыдущие выпуски **mssqlctl** установлен, очень важно удалить **mssqlctl** перед установкой последней версии.

   ```powershell
   pip3 uninstall mssqlctl
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```powershell
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
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

   ```bash
   pip3 uninstall mssqlctl
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl --user
   ```

   > [!NOTE]
   > `--user` Служит для установки mssqlctl в каталог установки Python пользователя. Обычно это `~/.local/bin` в Linux. Добавьте этот каталог в путь, перейдите в каталог установки пользователя и выполняться `./mssqlctl` оттуда.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
