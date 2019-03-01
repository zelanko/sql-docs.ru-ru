---
title: Справочник по подключения хранилища mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Справочная статья по mssqlctl команды хранилища.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8580c3c52cda484581f1c88ccfc039d8bd0bf78
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018460"
---
# <a name="mssqlctl-storage-mount"></a>mssqlctl подключения хранилища

В следующей статье приведены ссылки для **подключения хранилища** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a id="commands"></a> Команды

|||
|---|---|
| [Создание](#create) | Создайте подключение удаленных хранилищ в HDFS. |
| [delete](#delete) | Удалите подключение удаленных хранилищ в HDFS. |
| [status](#status) | Состояние mount(s). |

## <a id="create"></a> Создание подключения хранилища mssqlctl

Создайте подключение удаленных хранилищ в HDFS.

```
mssqlctl storage mount create
   --mount-path
   --remote-uri
   [--credential-file]
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--путь подключения** | Путь к HDFS, где это подключение должно быть создание (назначение подключения). Обязательный. |
| **--remote-uri** | URI удаленного хранилища, который должен быть подключенного (источник подключения). Обязательный. |
| **--файл учетных данных** | Файл, содержащий учетные данные для доступа к удаленном хранилище. Учетные данные должны быть указаны в качестве ключа = пар "значение" с одним ключом = значение для каждой строки. Все равно ключи или значения должны быть экранированы. Учетные данные не требуются по умолчанию. Необходимые ключи зависят от типа удаленного хранилища монтирования и тип авторизации используется. |

### <a name="examples"></a>Примеры

Чтобы подключить контейнер «данные» в учетной записи ADLS Gen 2 «adlsv2example» по пути HDFS `/mounts/adlsv2/data` с помощью общего ключа:

```
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/ --mount-path /mounts/adlsv2/data --credentials credential_file
```

Чтобы подключить удаленный кластер HDFS (`hdfs://namenode1:8080/`) локального пути HDFS `/mounts/hdfs/`:

```
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```

## <a id="delete"></a> mssqlctl storage mount delete

Удалите подключение удаленных хранилищ в HDFS.

```
mssqlctl storage mount delete
   --mount-path
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--путь подключения** | Путь HDFS, соответствующий монтирования, должны быть удалены. Обязательный. |

### <a name="examples"></a>Примеры

Удаление подключения, созданных на /mounts/adlsv2/data для учетной записи хранения ADLS Gen 2.

```
mssqlctl storage mount delete --mount-path /mounts/adlsv2/data
```

## <a id="status"></a> состояние подключения mssqlctl хранилища

Состояние mount(s).

```
mssqlctl storage mount status
   --mount-path
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--путь подключения** | Путь подключения. Обязательный. |

### <a name="examples"></a>Примеры

Получение состояния подключения по пути

```
mssqlctl storage mount status --mount-path /mounts/hdfs
```

Получение состояния всех подключений.

```
mssqlctl storage mount status
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).