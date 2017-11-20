---
title: "Установка агента SQL Server в Linux | Документы Microsoft"
description: "В этом разделе описывается установка агента SQL Server в Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 83f6e12a38d5fef4ab27cc39257906c4263aa846
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="install-sql-server-agent-on-linux"></a>Установка агента SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Следующие шаги установки агента SQL Server (**mssql-server-agent**) в Linux. [Агента SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) выполняет запланированные задания SQL Server. Сведения о функции, поддерживаемые для этого выпуска агента SQL Server см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

> [!NOTE]
> Перед установкой агента SQL Server, сначала [установить 2017 г. SQL Server](sql-server-linux-setup.md#platforms). Это настраивает ключи и репозиториев, которые используются при установке **mssql-server-agent** пакета.

Установите агент SQL Server на платформе:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Установите на RHEL</a>

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

Если вам требуется автономной установки, найдите загрузки пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанную в разделе [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="ubuntu">Установите на Ubuntu</a>

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

Если вам требуется автономной установки, найдите загрузки пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанную в разделе [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Установите на SLES</a>

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

Если вам требуется автономной установки, найдите загрузки пакета агента SQL Server в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанную в разделе [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о том, как использовать для создания, планирования и запуска заданий агента SQL Server см. в разделе [запуска задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).

