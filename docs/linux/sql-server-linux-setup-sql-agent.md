---
title: Настройка агента SQL Server в Linux
description: В этой статье описывается включение или установка агента SQL Server в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 12/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: b281c60248d86daba36a2cf5628e1ae729d227fe
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75258392"
---
# <a name="install-sql-server-agent-on-linux"></a>Установка агента SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается включение или установка агента SQL Server в Linux.

[Агент SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) выполняет запланированные задания SQL Server. Начиная с версии SQL Server 2017 с накопительным пакетом обновления 4, агент SQL Server включается в пакет **mssql-server** и по умолчанию отключен. Сведения о функциях, поддерживаемых в этом выпуске агента SQL Server, а также сведения о версии см. в [заметках о выпуске](sql-server-linux-release-notes.md).

## <a name="instructions"></a>Instructions

Прежде чем использовать агент SQL Server в Linux, выполните следующие действия, чтобы включить или установить его.

1. Добавьте имя узла (с доменом или без него) в файлы `/etc/hosts`. Ниже приведен пример формата таких записей:

   ```bash
   "IP Address" "hostname"
   "IP Address" "hostname.domain.com"
   ```

1. Следуйте инструкциям в одном из следующих разделов в зависимости от используемой версии SQL Server:

   | Версии | Instructions |
   |---|---|
   | SQL Server 2017 CU4 и более поздние версии</br>SQL Server 2019 | [Включение агента SQL Server](#EnableAgentAfterCU4) |
   | SQL Server 2017 CU3 и более ранние версии | [Установка агента SQL Server](#InstallAgentBelowCU4) |

## <a id="EnableAgentAfterCU4"></a>Включение агента SQL Server

Для SQL Server 2019 и SQL Server 2017 CU4 и более поздних версий необходимо только включить агент SQL Server. Вам не нужно устанавливать отдельный пакет.

Чтобы включить агент SQL Server, выполните указанные ниже действия.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Если вы производите обновление с версии 2017 с накопительным пакетом обновления 3 или более ранней с установленным агентом, агент SQL Server включается автоматически, а предыдущие версии пакета агента удаляются.  

## <a name="InstallAgentBelowCU4"></a>Установка агента SQL Server

Для SQL Server 2017 CU3 и более ранних версий необходимо установить пакет агента SQL Server.

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

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения об использовании агента SQL Server для создания, планирования и выполнения заданий см. в статье [Создание и запуск задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).
