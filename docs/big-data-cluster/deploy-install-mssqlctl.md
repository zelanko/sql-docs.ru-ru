---
title: Установка mssqlctl для управления кластерами больших данных SQL 2019 | Документация Майкрософт
description: Узнайте, как установить средство mssqlctl по установке и управлению кластерами больших данных SQL Server 2019 (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 5133134a45a4110abc0a1a7a3eebe1c5ac7b6ebd
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432107"
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

2. Установка **mssqlctl** , выполнив следующую команду:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a id="linux"></a> Установка mssqlctl Linux

В Linux необходимо установить Python 3.5 и затем обновить систему pip. В следующем примере показано команды, которые будут работать для Ubuntu. Для других платформ Linux, см. в разделе [документации Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Установите необходимые пакеты Python:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. Установка **mssqlctl** , выполнив следующую команду:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
