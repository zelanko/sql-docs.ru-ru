---
title: Справочник по подключению HDFS BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам подключения HDFS BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f0b259a3ac4ac0850fa05de3867e928b035307b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426274"
---
# <a name="azdata-bdc-hdfs-mount"></a>Подключение HDFS BDC аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки на команды **подключения HDFS BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание подключения HDFS BDC аздата](#azdata-bdc-hdfs-mount-create) | Создание подключений удаленных хранилищ в HDFS.
[Удаление подключения HDFS BDC аздата](#azdata-bdc-hdfs-mount-delete) | Удаление подключений удаленных хранилищ в HDFS.
[состояние подключения HDFS BDC аздата](#azdata-bdc-hdfs-mount-status) | Состояние подключений.
[Обновление подключения HDFS BDC аздата](#azdata-bdc-hdfs-mount-refresh) | Обновите содержимое подключения в HDFS.
## <a name="azdata-bdc-hdfs-mount-create"></a>Создание подключения HDFS BDC аздата
Создание подключений удаленных хранилищ в HDFS. Учетные данные для доступа к удаленному хранилищу, если таковые имеются, должны быть указаны с помощью переменной среды MOUNT_CREDENTIALS в виде разделенного запятыми списка пар "ключ — значение". Все запятые в ключах или значениях должны быть экранированы.
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>Примеры
Подключение контейнера "Data" к ADLS Gen 2 Account "adlsv2example" по пути HDFS/Mounts/adlsv2/Data using Shared Key
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
Подключение удаленного BDC (hdfs://namenode1:8080/) к локальному каталогу HDFS/Маунтс/хдфс/
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--remote-uri -r`
URI удаленного хранилища, которое должно быть подключено (источник подключения).
#### `--mount-path -m`
Путь HDFS, где необходимо создать подключение (назначение Mount).
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-mount-delete"></a>Удаление подключения HDFS BDC аздата
Удаление подключений удаленных хранилищ в HDFS.
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>Примеры
Удалите подключение, созданное на сайте/Mounts/adlsv2/Data для учетной записи хранения ADLS Gen 2.
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--mount-path -m`
путь HDFS, соответствующий подключению, который необходимо удалить.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-mount-status"></a>состояние подключения HDFS BDC аздата
Состояние подключений.
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>Примеры
Получение состояния подключения по пути
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
Возвращает состояние всех подключений.
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--mount-path -m`
Путь подключения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-mount-refresh"></a>Обновление подключения HDFS BDC аздата
Обновите содержимое подключения в HDFS.
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>Примеры
Обновить подключение, созданное на/Mounts/adlsv2/Data.
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--mount-path -m`
Путь HDFS, соответствующий подключению, который должен быть обновлен.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в [статье Установка аздата для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
