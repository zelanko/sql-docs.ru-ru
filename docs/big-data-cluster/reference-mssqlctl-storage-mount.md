---
title: Справочник по подключения хранилища mssqlctl
titleSuffix: SQL Server big data clusters
description: Справочная статья по команды подключения mssqlctl хранилища.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 523253e8d1ff2d621d9f7a5ef90dbc957fba82ec
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774686"
---
# <a name="mssqlctl-storage-mount"></a>Подключение хранилища mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **подключения хранилища** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание подключения хранилища mssqlctl](#mssqlctl-storage-mount-create) | Создайте подключение удаленных хранилищ в HDFS.
[Удаление подключения mssqlctl хранилища](#mssqlctl-storage-mount-delete) | Удалите подключение удаленных хранилищ в HDFS.
[состояние подключения mssqlctl хранилища](#mssqlctl-storage-mount-status) | Состояние mount(s).
## <a name="mssqlctl-storage-mount-create"></a>Создание подключения хранилища mssqlctl
Создайте подключение удаленных хранилищ в HDFS.
```bash
mssqlctl storage mount create --remote-uri 
                              --mount-path  
                              [--credential-file]
```
### <a name="examples"></a>Примеры
Чтобы подключить контейнер «данные» в учетной записи ADLS Gen 2 «adlsv2example» на /mounts/adlsv2/data пути HDFS, с помощью общего ключа
```bash
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data --credentials credential_file
```
Чтобы подключить удаленный кластер HDFS (hdfs://namenode1:8080 /) на локальном HDFS путь /mounts/hdfs /
```bash
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--remote-uri`
URI удаленного хранилища, который должен быть подключенного (источник подключения).
#### `--mount-path`
Путь к HDFS, где подключения должна создаваться (назначение подключения).
### <a name="optional-parameters"></a>Необязательные параметры
#### `--credential-file`
Файл, содержащий учетные данные для доступа к удаленном хранилище. Учетные данные должны быть указаны в качестве ключа = пар "значение" с одним ключом = значение для каждой строки. Все равно ключи или значения должны быть экранированы. Учетные данные не требуются по умолчанию. Необходимые ключи зависят от типа удаленного хранилища монтирования и тип авторизации используется.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-storage-mount-delete"></a>Удаление подключения mssqlctl хранилища
Удалите подключение удаленных хранилищ в HDFS.
```bash
mssqlctl storage mount delete --mount-path 
                              
```
### <a name="examples"></a>Примеры
Удаление подключения, созданных на /mounts/adlsv2/data для учетной записи хранения ADLS Gen 2.
```bash
mssqlctl storage mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--mount-path`
Путь HDFS, соответствующий монтирования, должны быть удалены.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-storage-mount-status"></a>состояние подключения mssqlctl хранилища
Состояние mount(s).
```bash
mssqlctl storage mount status [--mount-path] 
                              
```
### <a name="examples"></a>Примеры
Получение состояния подключения по пути
```bash
mssqlctl storage mount status --mount-path /mounts/hdfs
```
Получение состояния всех подключений.
```bash
mssqlctl storage mount status
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--mount-path`
Путь подключения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).