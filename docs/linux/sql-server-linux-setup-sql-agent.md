---
title: Установка агента SQL Server в Linux | Документация Майкрософт
description: В этой статье описывается установка агента SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: 1cb2a630dab67875db8a9731fe98895599f3290a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705061"
---
# <a name="install-sql-server-agent-on-linux"></a>Установка агента SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 [Агента SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) выполняет запланированные задания SQL Server. Начиная с накопительным пакетом обновления 4 для SQL Server 2017, агента SQL Server входит в состав **mssql-server** упаковки и отключен по умолчанию. Сведения о функциях, поддерживаемых для этого выпуска агента SQL Server, а также сведения о версии, см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

 Установка и включение агента SQL Server:
- [Для версии 2017 CU4 и более поздних версий включите агент SQL Server](#EnableAgentAfterCU4)
- [Для версии 2017 CU3 и ниже Установка агента SQL Server](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Для версии 2017 CU4 и более поздних версий включите агент SQL Server</a>

 Чтобы включить агент SQL Server, выполните следующие действия.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Если вы обновляете 2017 с накопительным пакетом обновления 3 или ниже агент установлен, агент SQL Server будет автоматически включена и предыдущих пакетов агента будет удален.  

## <a name="InstallAgentBelowCU4">Для версии 2017 CU3 и ниже Установка агента SQL Server</a>

> [!NOTE]
> Приведенные ниже инструкции установки применяются к SQL Server версии 2017 CU3 и ниже. Перед установкой агента SQL Server, сначала [Установка SQL Server](sql-server-linux-setup.md#platforms). Это позволит настроить ключи и репозитории, которые можно использовать при установке **mssql-server-agent** пакета.

Установка агента SQL Server для вашей платформы:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Установка в RHEL</a>

Выполните следующие действия для установки **mssql-server-agent** в Red Hat Enterprise Linux. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Если у вас уже есть **mssql-server-agent** установлен, можно обновить до последней версии, выполнив следующие команды:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам нужна автономной установки, найдите то загрузка пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

### <a name="ubuntu">Установка в Ubuntu</a>

Выполните следующие действия для установки **mssql-server-agent** в Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Если у вас уже есть **mssql-server-agent** установлен, можно обновить до последней версии, выполнив следующие команды:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам нужна автономной установки, найдите то загрузка пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

### <a name="SLES">Установка в SLES</a>

Выполните следующие действия для установки **mssql-server-agent** в SUSE Linux Enterprise Server. 

Установка **mssql-server-agent** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Если у вас уже есть **mssql-server-agent** установлен, можно обновить до последней версии, выполнив следующие команды:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам нужна автономной установки, найдите то загрузка пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о том, как использовать для создания, планирования и запуска заданий агента SQL Server см. в разделе [выполнение задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).
