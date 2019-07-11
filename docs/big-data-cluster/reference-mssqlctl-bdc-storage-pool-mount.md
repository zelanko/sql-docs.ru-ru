---
title: пул носителей подключения mssqlctl bdc ссылки
titleSuffix: SQL Server big data clusters
description: Справочная статья по команды подключения mssqlctl bdc пула носителей.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4204e87e96fd0d91a9bfbf64813583ef92d3202b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727478"
---
# <a name="mssqlctl-bdc-storage-pool-mount"></a>подключения пула носителей mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **подключения пула носителей bdc** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание подключения пула носителей mssqlctl bdc](#mssqlctl-bdc-storage-pool-mount-create) | Создайте подключение удаленных хранилищ в HDFS.
[пул носителей подключения mssqlctl bdc delete](#mssqlctl-bdc-storage-pool-mount-delete) | Удалите подключение удаленных хранилищ в HDFS.
[состояние подключения mssqlctl bdc пула носителей](#mssqlctl-bdc-storage-pool-mount-status) | Состояние mount(s).
## <a name="mssqlctl-bdc-storage-pool-mount-create"></a>Создание подключения пула носителей mssqlctl bdc
Создайте подключение удаленных хранилищ в HDFS. Учетные данные для доступа к удаленном хранилище, если таковое имеется, должен быть задан в переменной среды MOUNT_CREDENTIALS как разделенный запятыми список ключ = значение. Запятые, ключи или значения должны быть экранированы.
```bash
mssqlctl bdc storage-pool mount create --remote-uri 
                                       --mount-path
```
### <a name="examples"></a>Примеры
Чтобы подключить контейнер «данные» в учетной записи ADLS Gen 2 «adlsv2example» на /mounts/adlsv2/data пути HDFS, с помощью общего ключа
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
mssqlctl bdc storage-pool mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
Для подключения удаленного BDC HDFS (hdfs://namenode1:8080 /) на локальном HDFS путь /mounts/hdfs /
```bash
mssqlctl bdc storage-pool mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--remote-uri`
URI удаленного хранилища, который должен быть подключенного (источник подключения).
#### `--mount-path`
Путь к HDFS, где подключения должна создаваться (назначение подключения).
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
## <a name="mssqlctl-bdc-storage-pool-mount-delete"></a>пул носителей подключения mssqlctl bdc delete
Удалите подключение удаленных хранилищ в HDFS.
```bash
mssqlctl bdc storage-pool mount delete --mount-path 
                                       
```
### <a name="examples"></a>Примеры
Удаление подключения, созданных на /mounts/adlsv2/data для учетной записи хранения ADLS Gen 2.
```bash
mssqlctl bdc storage-pool mount delete --mount-path /mounts/adlsv2/data
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
## <a name="mssqlctl-bdc-storage-pool-mount-status"></a>состояние подключения mssqlctl bdc пула носителей
Состояние mount(s).
```bash
mssqlctl bdc storage-pool mount status [--mount-path] 
                                       
```
### <a name="examples"></a>Примеры
Получение состояния подключения по пути
```bash
mssqlctl bdc storage-pool mount status --mount-path /mounts/hdfs
```
Получение состояния всех подключений.
```bash
mssqlctl bdc storage-pool mount status
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