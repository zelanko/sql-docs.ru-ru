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
ms.openlocfilehash: f8336c59ffc11ff1a2b7842c393f3387298b832a
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527187"
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
   --local-path
   --remote-uri
   [--credential-file]
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **— локальный путь** | Путь к HDFS, где это подключение должно быть создание (назначение подключения). Обязательный. |
| **--remote-uri** | URI удаленного хранилища, который должен быть подключенного (источник подключения). Обязательный. |
| **--файл учетных данных** | Файл, содержащий учетные данные для доступа к удаленном хранилище. Учетные данные должны быть указаны в качестве ключа = пар "значение" с одним ключом = значение для каждой строки. Все равно ключи или значения должны быть экранированы. Учетные данные не требуются по умолчанию. Необходимые ключи зависят от типа удаленного хранилища монтирования и тип авторизации используется. |

### <a name="examples"></a>Примеры

Чтобы подключить контейнер «данные» в учетной записи ADLS Gen 2 «adlsv2example» по пути HDFS `/mounts/adlsv2/data` с помощью общего ключа:

```
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/ --local-path /mounts/adlsv2/data --credentials credential_file
```

Чтобы подключить удаленный кластер HDFS (`hdfs://namenode1:8080/`) локального пути HDFS `/mounts/hdfs/`:

```
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --local-path /mounts/hdfs/
```

## <a id="delete"></a> mssqlctl storage mount delete

Удалите подключение удаленных хранилищ в HDFS.

```
mssqlctl storage mount delete
   --local-path
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **— локальный путь** | Путь HDFS, соответствующий монтирования, должны быть удалены. Обязательный. |

### <a name="examples"></a>Примеры

Удаление подключения, созданных на /mounts/adlsv2/data для учетной записи хранения ADLS Gen 2.

```
mssqlctl storage mount delete --local-path /mounts/adlsv2/data
```

## <a id="status"></a> состояние подключения mssqlctl хранилища

Состояние mount(s).

```
mssqlctl storage mount status
   --local-path
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