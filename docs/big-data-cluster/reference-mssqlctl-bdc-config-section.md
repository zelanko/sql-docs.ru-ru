---
title: раздел конфигурации ссылку для mssqlctl bdc
titleSuffix: SQL Server big data clusters
description: Справочная статья по команды раздела конфигурации mssqlctl bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3f3ba7854b4df63495926e4cc207de7cbe6a9378
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958191"
---
# <a name="mssqlctl-bdc-config-section"></a>раздел config mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **раздел конфигурации bdc** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Показать раздел конфигурации bdc mssqlctl](#mssqlctl-bdc-config-section-show) | Получает раздел из профиля конфигурации.
[раздел config set для mssqlctl bdc](#mssqlctl-bdc-config-section-set) | Задает раздел для профиля конфигурации.
## <a name="mssqlctl-bdc-config-section-show"></a>Показать раздел конфигурации bdc mssqlctl
Получает указанный раздел из выбранной конфигурации профиля в соответствии с json для заданного пути.
```bash
mssqlctl bdc config section show --json-path -j 
                                 --config-profile -c  
                                 [--target -t]  
                                 [--force -f]
```
### <a name="examples"></a>Примеры
Получает значение в конце пути к простой json.
```bash
mssqlctl bdc config section show --config-profile custom-config --json-path 'metadata.name' --target section.json
```
Получает значение в конце путь ключа json с помощью условного выражения
```bash
mssqlctl bdc config section show --config-profile custom-config  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--json-path -j`
Путь ключа json, который приводит к раздел или значение из файла профиля конфигурации cluster.json, т. е. key1.key2.key3. Использует язык запросов jsonpath, https://github.com/h2non/jsonpath-ng, например: -j "$. spec.pools [? () @.spec.type == "Master")]... конечные точки
#### `--config-profile -c`
Путь к профилю конфигурации BDC.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Поместить путь к файлу место файла раздела. Значение по умолчанию — направляются в stdout.
#### `--force -f`
Принудительная перезапись целевого файла.
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
## <a name="mssqlctl-bdc-config-section-set"></a>раздел config set для mssqlctl bdc
Задает указанный раздел в профиле выбранной конфигурации в соответствии с json для заданного пути.  Все examplesbelow приведены в Bash.  Если используется другой командной строки, имейте в виду, что может потребоваться escapequotations соответствующим образом.  Кроме того можно использовать функции исправления файлов.
```bash
mssqlctl bdc config section set --config-profile -c 
                                [--json-values -j]  
                                [--patch-file -p]
```
### <a name="examples"></a>Примеры
Пример 1 (встроенные) — задайте номер порта одной конечной точки (конечная точка контроллера).
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values '$.spec.controlPlane.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Пример 1 (исправление) - задайте порт одной конечной точки (конечная точка контроллера) с файлом исправлений.
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Пример 2 (встроенные) — хранилище плоскости управления набора.
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values 'spec.controlPlane.spec.storage=spec.controlPlane.spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Пример 2 (patch) — набор хранилища плоскости управления с помощью файл исправления.
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"spec.controlPlane.spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Ex 3(inline) - задайте хранилище пула, включая реплики (пул носителей).
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
Пример 3 (patch) - задайте хранилище пула, включая реплики (пул носителей) с файлом исправлений.
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-profile -c`
Путь к профилю конфигурации BDC файла конфигурации вы бы хотели задать
### <a name="optional-parameters"></a>Необязательные параметры
#### `--json-values -j`
Список пара значение ключа пути json для значений: key1.subkey1=value1,key2.subkey2=value2. Можно предоставить встроенные значения json такие как: key = "{«kind»: «кластера», «name»: «test-cluster»}" или укажите путь к файлу, например key=./values.json. Если вы хотите задать значение, которое требует условного выражения, используйте нотацию jsonpath начальным пути $. Это позволит вам для этого условного выражения, такие как + j $. key1.key2 [? () @.key3== «someValue»] .key4 = значение. Вы можете увидеть примеры ниже. Дополнительные сведения см. в разделе: https://jsonpath.com/
#### `--patch-file -p`
Путь к файлу json patch, основанного на библиотеке jsonpatch: http://jsonpatch.com/. Исправление json-файл должен начинаться с ключ с именем «исправления», значение которого представляет собой массив операций исправления, которые планируется сделать. Путь к операции исправления вы можете использовать точечную нотацию, например key1.key2 для большинства операций. Если вы хотите сделать операции замены, и требуется заменить значения в массив, который требует условную, используйте нотацию jsonpath начальным пути $. Это позволит вам сделать условного выражения, такие как $. key1.key2 [? () @.key3== «someValue»] .key4. См. в приведенных ниже примерах. Дополнительные сведения см. в разделе: https://jsonpath.com/.
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