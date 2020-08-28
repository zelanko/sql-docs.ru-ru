---
title: Установка PolyBase на компьютере под управлением Linux
titlesuffix: SQL Server
description: Сведения о том, как установить SQL Server PolyBase в Linux. PolyBase позволяет выполнять внешние запросы к удаленным источникам данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: dakryze
ms.date: 8/18/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 6bed37e6fe0451e45e9d99fd9c15d03d12a30a4b
ms.sourcegitcommit: 19ae05bc69edce1e3b3d621d7fdd45ea5f74969d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88564654"
---
# <a name="install-polybase-on-linux"></a>Установка PolyBase на компьютере под управлением Linux

[!INCLUDE [sqlserver2019-linux](../../includes/applies-to-version/sqlserver2019-linux.md)]

Используйте следующие шаги, чтобы установить [PolyBase](../../relational-databases/polybase/polybase-guide.md) (`mssql-server-polybase` и `mssql-server-polybase-hadoop`) на Linux. PolyBase позволяет выполнять внешние запросы к удаленным источникам данных.

>[!NOTE]
> Перед установкой PolyBase сначала нужна [Установка SQL Server 2019](../../linux/sql-server-linux-setup.md#platforms). Это позволит настроить ключи и репозитории, которые следует использовать при установке пакета `mssql-server-polybase` и `mssql-server-polybase-hadoop`.

>[!NOTE]
>
> - PolyBase не поддерживается в SQL Server 2017 для Linux.
> - Возможность горизонтального масштабирования для PolyBase в Linux сейчас недоступна.

Установите PolyBase для вашей операционной системы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="install-on-rhel"></a><a name="RHEL"></a>Установка в RHEL

Используйте следующую команду для установки `mssql-server-polybase` в Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

Используйте следующую команду для установки `mssql-server-polybase-hadoop`. 

```bash
sudo yum install -y mssql-server-polybase-hadoop
```

Пакет Hadoop для PolyBase имеет зависимости от следующих пакетов.
- `mssql-server`
- `mssql-server-polybase`
- `mssql-server-extensibility`
- `mssql-zulu-jre-11`. 

Запрос на установку для перезапуска `launchpadd`. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-launchpadd
```

>[!NOTE]
>После установки необходимо [задать уровень подключения Hadoop](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md#c-set-hadoop-connectivity).

Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).

## <a name="install-on-ubuntu"></a><a name="ubuntu"></a>Установка в Ubuntu

Используйте следующую команду для установки `mssql-server-polybase` в Ubuntu. 

```bash
sudo apt-get install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).

Используйте следующую команду для установки `mssql-server-polybase-hadoop`. 

```bash
sudo apt-get install mssql-server-polybase-hadoop
```

Пакет Hadoop для PolyBase имеет зависимости от следующих пакетов.
- `mssql-server`
- `mssql-server-polybase`
- `mssql-server-extensibility`
- `mssql-zulu-jre-11`. 

Запрос на установку для перезапуска `launchpadd`. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-launchpadd
```

>[!NOTE]
>После установки необходимо [задать уровень подключения Hadoop](../../relational-databases/polybase/polybase-configure-hadoop.md#configure-hadoop-connectivity).

## <a name="install-on-sles"></a><a name="SLES"></a>Установка в SLES

Используйте следующую команду для установки `mssql-server-polybase` в SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).


## <a name="enable-polybase"></a><a name="enable"></a> Включение PolyBase

Завершив установку, включите компонент PolyBase для доступа к его функциям. Подключитесь к установленному экземпляру SQL Server и используйте следующую команду Transact-SQL для включения.

```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE WITH OVERRIDE;
```

## <a name="update-polybase"></a>Обновление PolyBase

Если у вас уже есть `mssql-server-polybase`, можно обновить пакет до последней версии, выполнив следующие команды:

### <a name="rhel"></a>RHEL

```bash
sudo yum remove -y mssql-server-polybase-hadoop
sudo yum remove -y mssql-server-polybase
sudo yum check-update
sudo yum install -y mssql-server-polybase
sudo yum install -y mssql-server-polybase-hadoop
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

### <a name="ubuntu"></a>Ubuntu

```bash
sudo apt-get remove mssql-server-polybase-hadoop
sudo apt-get remove mssql-server-polybase
sudo apt-get update 
sudo apt-get install mssql-server-polybase
sudo apt-get remove mssql-server-polybase-hadoop
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

### <a name="sles"></a>SLES

```bash
sudo zypper remove mssql-server-polybase
sudo zypper refresh
sudo zypper install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

## <a name="next-steps"></a>Дальнейшие действия

Для PolyBase в Linux доступны следующие источники данных. Следуйте указанным ссылкам, чтобы получить дополнительные сведения о создании внешних таблиц из этих источников в PolyBase. 

- [SQL Server, SQL Database, Azure Synapse Analytics](../../relational-databases/polybase/polybase-configure-sql-server.md)
- [Hadoop](../../relational-databases/polybase/polybase-configure-hadoop.md)
- [Хранилище BLOB-объектов Azure](../../relational-databases/polybase/polybase-configure-azure-blob-storage.md)
- [Oracle](../../relational-databases/polybase/polybase-configure-oracle.md)
- [Teradata](../../relational-databases/polybase/polybase-configure-teradata.md)
- [MongoDB (а также Cosmos DB)](../../relational-databases/polybase/polybase-configure-mongodb.md)

Дополнительные сведения об использовании сопоставления см. в справочнике по Transact-SQL для [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md).
