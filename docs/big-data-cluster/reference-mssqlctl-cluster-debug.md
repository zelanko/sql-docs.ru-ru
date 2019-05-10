---
title: mssqlctl cluster debug reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по команды отладки mssqlctl кластера.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5099a9ac611602e0c4c8d7f0103421e34b7fa8a2
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774857"
---
# <a name="mssqlctl-cluster-debug"></a>Отладка кластера mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **отладки кластера** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Копировать журналы mssqlctl отладки кластера](#mssqlctl-cluster-debug-copy-logs) | Копировать журналы.
[файлы дампа отладки mssqlctl кластера](#mssqlctl-cluster-debug-dump) | Триггер дампа ведения журнала.
## <a name="mssqlctl-cluster-debug-copy-logs"></a>mssqlctl cluster debug copy-logs
Копировать журналы отладки из кластера.
```bash
mssqlctl cluster debug copy-logs --namespace -n 
                                 [--container -c]  
                                 [--target-folder -d]  
                                 [--pod -p]  
                                 [--timeout -t]
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--namespace -n`
Имя кластера, используемые для пространств имен kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--container -c`
Скопировать журналы для контейнеров с похожим именем, необязательно, по умолчанию копирует журналы для всех контейнеров. Нельзя указывать несколько раз. Если указано несколько раз, последний может быть использован один
#### `--target-folder -d`
Целевой путь к папке для копирования журналов. Необязательно, по умолчанию создает результат в локальной папке.  Нельзя указывать несколько раз. Если указано несколько раз, последний может быть использован один
#### `--pod -p`
Скопируйте журналы для модулей POD с похожим именем. Необязательно, по умолчанию копий журналы для всех модулей. Нельзя указывать несколько раз. Если указано несколько раз, последний может быть использован один
#### `--timeout -t`
Число секунд ожидания завершения выполнения команды. Значение по умолчанию — 0, который не ограничен
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
## <a name="mssqlctl-cluster-debug-dump"></a>файлы дампа отладки mssqlctl кластера
Активировать ведение журнала дампа и скопируйте его из контейнера.
```bash
mssqlctl cluster debug dump --namespace -n 
                            --container -c  
                            [--target-folder -d]
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--namespace -n`
Имя кластера, используемые для пространств имен kubernetes.
#### `--container -c`
Скопировать журналы для контейнеров с похожим именем, необязательно, по умолчанию копирует журналы для всех контейнеров. Нельзя указывать несколько раз. Если указано несколько раз, последний может быть использован один
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target-folder -d`
Целевой путь к папке для копирования журналов. Необязательно, по умолчанию создает результат в локальной папке.  Нельзя указывать несколько раз. Если указано несколько раз, последний может быть использован один `./output/dump`
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