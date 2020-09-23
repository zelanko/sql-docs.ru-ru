---
title: Справочник по командам azdata bdc hdfs mount reference
titleSuffix: SQL Server big data clusters
description: Эта справочная статья содержит описание команд SQL в средстве azdata, а также многие команды hdfs mount.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bf0742083b458fb0d8280199a0afaeb44a05958a
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733979"
---
# <a name="azdata-bdc-hdfs-mount"></a>azdata bdc hdfs mount

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
| Команда | Описание |
| --- | --- |
[azdata bdc hdfs mount create](#azdata-bdc-hdfs-mount-create) | Создает подключения удаленных хранилищ в HDFS.
[azdata bdc hdfs mount delete](#azdata-bdc-hdfs-mount-delete) | Удаляет подключения удаленных хранилищ в HDFS.
[azdata bdc hdfs mount status](#azdata-bdc-hdfs-mount-status) | Получает сведения о состоянии подключений.
[azdata bdc hdfs mount refresh](#azdata-bdc-hdfs-mount-refresh) | Обновляет содержимое подключения в HDFS.
## <a name="azdata-bdc-hdfs-mount-create"></a>azdata bdc hdfs mount create
Создает подключения удаленных хранилищ в HDFS. Если требуются учетные данные для доступа к удаленному хранилищу, они указываются в переменной среды MOUNT_CREDENTIALS в виде списка разделенных запятыми пар ключ=значение. Все запятые в ключах или значениях должны быть экранированы.
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>Примеры
Подключение контейнера "data" в учетной записи ADLS Gen 2 "adlsv2example" по пути HDFS /mounts/adlsv2/data с использованием общего ключа
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
Подключение удаленного подключения к бизнес-данным HDFS (hdfs://namenode1:8080/) по локальному пути HDFS /mounts/hdfs/
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--remote-uri -r`
URI удаленного хранилища, которое требуется подключить (источник подключения).
#### `--mount-path -m`
Путь HDFS, по которому требуется создать подключение (назначение подключения).
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata bdc hdfs mount delete
Удаляет подключения удаленных хранилищ в HDFS.
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>Примеры
Удаление подключения, созданного по пути /mounts/adlsv2/data для учетной записи хранения ADLS Gen 2.
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--mount-path -m`
Путь HDFS, соответствующий удаляемому подключению.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-hdfs-mount-status"></a>azdata bdc hdfs mount status
Получает сведения о состоянии подключений.
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>Примеры
Получение сведений о состоянии подключения по пути
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
Получение сведений о состоянии всех подключений.
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--mount-path -m`
Путь подключения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-hdfs-mount-refresh"></a>azdata bdc hdfs mount refresh
Обновляет содержимое подключения в HDFS.
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>Примеры
Обновление подключения, созданного по пути /mounts/adlsv2/data.
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--mount-path -m`
Путь HDFS, соответствующий обновляемому подключению.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](../install/deploy-install-azdata.md).
