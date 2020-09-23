---
title: Справочник по azdata bdc debug
titleSuffix: SQL Server big data clusters
description: Эта справочная статья содержит описание команд SQL в средстве azdata, а также многие команды bdc debug.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e9d1f561666bf6aefdef6abf4b1daf568a5a89d8
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89734033"
---
# <a name="azdata-bdc-debug"></a>azdata bdc debug

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
| Команда | Описание |
| --- | --- |
[azdata bdc debug copy-logs](#azdata-bdc-debug-copy-logs) | Копирование журналов.
[azdata bdc debug dump](#azdata-bdc-debug-dump) | Создание дампа памяти.
## <a name="azdata-bdc-debug-copy-logs"></a>azdata bdc debug copy-logs
Копирование журналов отладки из кластера больших данных. В системе должна быть конфигурация Kubernetes.
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           
[--target-folder -d]  
                           
[--pod -p]  
                           
[--timeout -t]  
                           
[--skip-compress -sc]  
                           
[--exclude-dumps -ed]
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--namespace -n`
Имя кластера больших данных, используемого для пространства имен Kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--container -c`
Копирование журналов для контейнеров с одинаковыми именами. Необязательный параметр. По умолчанию копируются журналы для всех контейнеров. Нельзя указывать несколько раз. Если этот параметр указан несколько раз, используется последний параметр.
#### `--target-folder -d`
Путь к конечной папке, в которую должны копироваться журналы. Необязательный параметр. По умолчанию результаты помещаются в локальную папку.  Нельзя указывать несколько раз. Если этот параметр указан несколько раз, используется последний параметр.
#### `--pod -p`
Копирование журналов для объектов pod с одинаковыми именами. Необязательный параметр. По умолчанию копируются журналы для всех объектов pod. Нельзя указывать несколько раз. Если этот параметр указан несколько раз, используется последний параметр.
#### `--timeout -t`
Время ожидания завершения команды в секундах. Значение по умолчанию — 0, что означает неограниченный срок.
#### `--skip-compress -sc`
Следует ли пропустить сжатие папки результатов. Значение по умолчанию — false, которое сжимает папку результатов.
#### `--exclude-dumps -ed`
Следует ли исключать дампы из папки результатов. Значение по умолчанию — false, включающее дампы.
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
## <a name="azdata-bdc-debug-dump"></a>azdata bdc debug dump
Создание дампа памяти и его копирование из контейнера. В системе должна быть конфигурация Kubernetes.
```bash
azdata bdc debug dump --namespace -n 
                      [--container -c]  
                      
[--target-folder -d]
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--namespace -n`
Имя кластера больших данных, используемого для пространства имен Kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--container -c`
Целевой контейнер, запускаемый для создания дампа запущенных процессов `controller`
#### `--target-folder -d`
Целевая папка для копирования дампа. `./output/dump`
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
