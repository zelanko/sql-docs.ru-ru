---
title: Установка PolyBase на компьютере под управлением Linux
titlesuffix: SQL Server
description: Сведения о том, как установить SQL Server PolyBase в Linux. PolyBase позволяет выполнять внешние запросы к удаленным источникам данных.
author: MikeRayMSFT
ms.author: mikeray
ms.date: 7/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f886c1d1ae3b5054c6ca0f0159ca8202054ec375
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88087382"
---
# <a name="install-polybase-on-linux"></a>Установка PolyBase на компьютере под управлением Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Используйте следующие шаги, чтобы установить [PolyBase](../../relational-databases/search/full-text-search.md) (**mssql-server-polybase**) на платформе Linux. PolyBase позволяет выполнять внешние запросы к удаленным источникам данных. 

>[!NOTE]
> Перед установкой Polybase сначала нужно [установить предварительную версию SQL Server 2019](../../linux/sql-server-linux-setup.md#platforms). Это позволит настроить ключи и репозитории, которые следует использовать при установке пакета **mssql-server-polybase**.
>
> PolyBase не поддерживается в SQL Server 2017 для Linux.
> Возможность горизонтального масштабирования для PolyBase в Linux сейчас недоступна.

Установите PolyBase для вашей операционной системы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)



## <a name=""></a><a name="RHEL">Установка в RHEL</a>

Используйте следующую команду для установки **mssql-server-polybase** в Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).

## <a name=""></a><a name="ubuntu">Установка в Ubuntu</a>

Используйте следующую команду для установки **mssql-server-polybase** в Ubuntu. 

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

## <a name=""></a><a name="SLES">Установка в SLES</a>

Используйте следующую команду для установки **mssql-server-polybase** в SUSE Linux Enterprise Server. 

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


## <a name=""></a><a name="enable">Включение PolyBase</a> 

Завершив установку, включите компонент PolyBase для доступа к его функциям. Подключитесь к установленному экземпляру SQL Server и используйте следующую команду Transact-SQL для включения.

```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE WITH OVERRIDE;
```

## <a name="update-polybase"></a>Обновление PolyBase

Если у вас уже есть **mssql-server-polybase**, можно обновить пакет до последней версии, выполнив следующие команды:

### <a name="rhel"></a>RHEL

```bash
sudo yum remove -y mssql-server-polybase
sudo yum check-update
sudo yum install -y mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

### <a name="ubuntu"></a>Ubuntu

```bash
sudo apt-get remove mssql-server-polybase
sudo apt-get update 
sudo apt-get install mssql-server-polybase
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

- [SQL Server (база данных SQL, хранилище данных SQL Azure)](../../relational-databases/polybase/polybase-configure-sql-server.md)
- [Oracle](../../relational-databases/polybase/polybase-configure-oracle.md)
- [Teradata](../../relational-databases/polybase/polybase-configure-teradata.md)
- [MongoDB (а также Cosmos DB)](../../relational-databases/polybase/polybase-configure-mongodb.md)

Дополнительные сведения об использовании сопоставления см. в справочнике по Transact-SQL для [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md).
