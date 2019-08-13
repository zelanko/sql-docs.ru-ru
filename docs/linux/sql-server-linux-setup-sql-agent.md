---
title: Установка агента SQL Server в Linux
description: В этой статье описывается установка агента SQL Server в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: c27a31a5e6b9ed771df82e942087d7be88270038
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032471"
---
# <a name="install-sql-server-agent-on-linux"></a>Установка агента SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 [Агент SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) выполняет запланированные задания SQL Server. Начиная с версии SQL Server 2017 с накопительным пакетом обновления 4 агент SQL Server включается в пакет **mssql-server** и по умолчанию отключен. Сведения о функциях, поддерживаемых в этом выпуске агента SQL Server, а также сведения о версии см. в [заметках о выпуске](sql-server-linux-release-notes.md).

 Установите или включите агент SQL Server:
- [Включение агента SQL Server в версии 2017 с накопительным пакетом обновления 4 и более поздних](#EnableAgentAfterCU4)
- [Установка агента SQL Server в версии 2017 с накопительным пакетом обновления 3 и более ранних](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Включение агента SQL Server в версии 2017 с накопительным пакетом обновления 4 и более поздних</a>

 Чтобы включить агент SQL Server, выполните указанные ниже действия.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Если вы производите обновление с версии 2017 с накопительным пакетом обновления 3 или более ранней с установленным агентом, агент SQL Server включается автоматически, а предыдущие версии пакета агента удаляются.  

## <a name="InstallAgentBelowCU4">Установка агента SQL Server в версии 2017 с накопительным пакетом обновления 3 и более ранних</a>

> [!NOTE]
> Приведенные ниже инструкции относятся к версии SQL Server 2017 с накопительным пакетом обновления 3 и более ранним. Перед установкой агента SQL Server сначала [установите SQL Server](sql-server-linux-setup.md#platforms). Это позволит настроить ключи и репозитории, которые следует использовать при установке пакета **mssql-server-agent**.

Установите агент SQL Server для своей платформы:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Установка в RHEL</a>

Чтобы установить **mssql-server-agent** в Red Hat Enterprise Linux, выполните указанные ниже действия. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Если пакет **mssql-server-agent** уже установлен, можно обновить его до последней версии, выполнив следующие команды:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам нужна автономная установка, найдите скачиваемый пакет агента SQL Server в разделе [Заметки о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

### <a name="ubuntu">Установка в Ubuntu</a>

Чтобы установить **mssql-server-agent** в Ubuntu, выполните указанные ниже действия. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Если пакет **mssql-server-agent** уже установлен, можно обновить его до последней версии, выполнив следующие команды:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам нужна автономная установка, найдите скачиваемый пакет агента SQL Server в разделе [Заметки о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

### <a name="SLES">Установка в SLES</a>

Чтобы установить **mssql-server-agent** в SUSE Linux Enterprise Server, выполните указанные ниже действия. 

Установка **mssql-server-agent** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Если пакет **mssql-server-agent** уже установлен, можно обновить его до последней версии, выполнив следующие команды:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам нужна автономная установка, найдите скачиваемый пакет агента SQL Server в разделе [Заметки о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об использовании агента SQL Server для создания, планирования и выполнения заданий см. в статье [Создание и запуск задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).
