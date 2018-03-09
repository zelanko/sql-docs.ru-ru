---
title: "Установка агента SQL Server в Linux | Документы Microsoft"
description: "В этой статье описывается установка агента SQL Server в Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.workload: On Demand
ms.openlocfilehash: bec1837a2e4084d01858815346c5a7563199a220
ms.sourcegitcommit: 57f45ee008141ddf009b1c1195442529e0ea1508
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="install-sql-server-agent-on-linux"></a>Установка агента SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 [Агента SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) выполняет запланированные задания SQL Server. Начиная с SQL Server CU4 2017 г., агент SQL Server входит в состав **mssql server** пакета и отключена по умолчанию. Сведения о функциях, поддерживаемой этим выпуском SQL Server Agent вместе с информацией о версии см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

 Для установки и применения агента SQL Server:
- [Для версий CU4 2017 г. и более поздних версий Включение агента SQL Server](#EnableAgentAfterCU4)
- [Для версий CU3 2017 г. и ниже Установка агента SQL Server](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Для версий CU4 2017 г. и более поздних версий Включение агента SQL Server</a>

 Чтобы включить агент SQL Server, выполните следующие действия.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Если вы обновляете CU3 2017 г. или ниже с агент установлен, агент SQL Server будет автоматически включена и предыдущих пакетов агента будет удален.  

## <a name="InstallAgentBelowCU4">Для версий CU3 2017 г. и ниже Установка агента SQL Server</a>

> [!NOTE]
> Инструкции по установке применяются к SQL Server версии 2017 г CU3 и ниже. Перед установкой агента SQL Server, сначала [установить 2017 г. SQL Server](sql-server-linux-setup.md#platforms). Это настраивает ключи и репозиториев, которые используются при установке **mssql-server-agent** пакета.

Установите агент SQL Server на платформе:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Установите на RHEL</a>

Выполните следующие действия для установки **mssql-server-agent** в Red Hat Enterprise Linux. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Если у вас уже есть **mssql-server-agent** установлены, можно обновить до последней версии с помощью следующих команд:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам требуется автономной установки, найдите загрузки пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

### <a name="ubuntu">Установите на Ubuntu</a>

Выполните следующие действия для установки **mssql-server-agent** на Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Если у вас уже есть **mssql-server-agent** установлены, можно обновить до последней версии с помощью следующих команд:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам требуется автономной установки, найдите загрузки пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

### <a name="SLES">Установите на SLES</a>

Выполните следующие действия для установки **mssql-server-agent** на SUSE Linux Enterprise Server. 

Установка **mssql сервера агента** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Если у вас уже есть **mssql-server-agent** установлены, можно обновить до последней версии с помощью следующих команд:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Если вам требуется автономной установки, найдите загрузки пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о том, как использовать для создания, планирования и запуска заданий агента SQL Server см. в разделе [запуска задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).
