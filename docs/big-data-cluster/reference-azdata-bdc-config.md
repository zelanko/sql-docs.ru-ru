---
title: Справочник по azdata bdc config
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 73db63c485b7a6cd2e9355be935ff574ef827a5d
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653518"
---
# <a name="azdata-bdc-config"></a>azdata bdc config

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приводятся справочные сведения по командам **bdc config** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc config init](#azdata-bdc-config-init) | Инициализирует профиль конфигурации кластера больших данных, который можно использовать с командой cluster create.
[azdata bdc config list](#azdata-bdc-config-list) | Выводит список доступных профилей конфигурации.
[azdata bdc config show](#azdata-bdc-config-show) | Выводит текущую конфигурацию кластера больших данных или конфигурацию из указанного локального файла, например custom/cluster.json.
[azdata bdc config add](#azdata-bdc-config-add) | Добавляет значение для пути JSON в файле конфигурации.
[azdata bdc config remove](#azdata-bdc-config-remove) | Удаляет значение пути JSON в файле конфигурации.
[azdata bdc config replace](#azdata-bdc-config-replace) | Заменяет значение пути JSON в файле конфигурации.
[azdata bdc config patch](#azdata-bdc-config-patch) | Вносит исправление в файл конфигурации на основе файла исправления JSON.
## <a name="azdata-bdc-config-init"></a>azdata bdc config init
Инициализирует профиль конфигурации кластера больших данных, который можно использовать с командой cluster create. В аргументах можно указать один из трех источников профиля конфигурации.
```bash
azdata bdc config init [--target -t] 
                       [--source -s]  
                       [--force -f]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Интерактивный процесс инициализации конфигурации для кластера больших данных — выводятся запросы требуемых значений.
```bash
azdata bdc config init
```
Инициализация конфигурации кластера больших данных с аргументами; создает профиль конфигурации aks-dev-test в ./custom.
```bash
azdata bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Путь к файлу, в который следует поместить профиль конфигурации; по умолчанию cwd с custom-config.json.
#### `--source -s`
Источник профиля конфигурации: ["aks-dev-test", "kubeadm-dev-test", "minikube-dev-test"]
#### `--force -f`
Принудительная перезапись целевого файла.
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". 
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-config-list"></a>azdata bdc config list
Выводит список доступных профилей конфигурации для использования в `bdc config init`.
```bash
azdata bdc config list [--config-profile -c] 
                       [--type -t]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Выводит имена всех доступных профилей конфигурации.
```bash
azdata bdc config list
```
Выводит код JSON определенного профиля конфигурации.
```bash
azdata bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-profile -c`
Профиль конфигурации по умолчанию: ["aks-dev-test", "kubeadm-dev-test", "minikube-dev-test"]
#### `--type -t`
Тип конфигурации, который следует просмотреть.
`cluster`
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". 
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-config-show"></a>azdata bdc config show
Выводит текущую конфигурацию кластера больших данных или конфигурацию из указанного локального файла, например custom/cluster.json. Команда также может принимать только путь JSON, если нужно получить только раздел.  Вы также можете указать целевой файл для вывода данных.  Если целевой файл не указан, выходные данные выводятся в терминал.
```bash
azdata bdc config show [--config-file -c] 
                       [--target -t]  
                       [--json-path -j]  
                       [--force -f]
```
### <a name="examples"></a>Примеры
Вывод конфигурации кластера больших данных в консоли
```bash
azdata bdc config show
```
В локальном файле конфигурации возвращается значение в конце простого пути к ключу JSON.
```bash
azdata bdc config show --config-file custom-config/cluster.json --json-path 'metadata.name' --target section.json
```
В локальном файле конфигурации возвращается значение в конце условного пути к ключу JSON.
```bash
azdata bdc config show --config-file custom-config/cluster.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-file -c`
Путь к файлу конфигурации кластера больших данных, если не требуется конфигурация кластера, в который выполнен вход в настоящее время, то есть custom/cluster.json.
#### `--target -t`
Выходной файл, в котором следует сохранить результат. По умолчанию: направляется в stdout.
#### `--json-path -j`
Путь к ключу JSON, который указывает на требуемый раздел или значение из конфигурации, например key1.key2.key3. Используется язык запросов jsonpath (https://jsonpath.com/ ), например: -j '$.spec.pools[?(@.spec.type == "Master")]..endpoints'
#### `--force -f`
Принудительная перезапись целевого файла.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-config-add"></a>azdata bdc config add
Добавляет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры выполняются в Bash.  Если используется другая оболочка командной строки, может потребоваться экранировать кавычки соответствующим образом.  В качестве альтернативы можно воспользоваться возможностями файла исправления.
```bash
azdata bdc config add --config-file -c 
                      --json-values -j
```
### <a name="examples"></a>Примеры
Пример 1. Добавление хранилища уровня управления
```bash
azdata bdc config add --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу с конфигурацией кластера больших данных, которую нужно задать, например custom/cluster.json
#### `--json-values -j`
Список пар "ключ–значение" с путями JSON и значениями: ключ1.подключ1=значение1,ключ2.подключ2=значение2. Вы можете указать значения JSON в коде, например key='{"тип":"кластер","имя":"тестовый-кластер"}', или предоставить путь к файлу, например key=./values.json. При добавлении не поддерживаются условные выражения.  Примеры путей см. на сайте http://jsonpatch.com/.  Для доступа к массиву необходимо указать индекс, например ключ.0=значение
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-config-remove"></a>azdata bdc config remove
Удаляет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры выполняются в Bash.  Если используется другая оболочка командной строки, может потребоваться экранировать кавычки соответствующим образом.  В качестве альтернативы можно воспользоваться возможностями файла исправления.
```bash
azdata bdc config remove --config-file -c 
                         --json-path -j
```
### <a name="examples"></a>Примеры
Пример 1. Удаление хранилища уровня управления
```bash
azdata bdc config remove --config-file custom/control.json --json-path '.spec.storage'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу с конфигурацией кластера больших данных, которую нужно задать, например custom/cluster.json
#### `--json-path -j`
Список путей JSON на основе библиотеки jsonpatch, в котором перечислены значения, которые необходимо удалить, например: ключ.подключ1,ключ2.подключ2. При удалении не поддерживаются условные выражения. Примеры путей см. на сайте http://jsonpatch.com/.  Для доступа к массиву необходимо указать индекс, например ключ.0=значение
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-config-replace"></a>azdata bdc config replace
Заменяет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры выполняются в Bash.  Если используется другая оболочка командной строки, может потребоваться экранировать кавычки соответствующим образом.  В качестве альтернативы можно воспользоваться возможностями файла исправления.
```bash
azdata bdc config replace --config-file -c 
                          --json-values -j
```
### <a name="examples"></a>Примеры
Пример 1. Замена порта одной конечной точки (конечной точки контроллера)
```bash
azdata bdc config replace --config-file custom/control.json --json-values '$.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Пример 2. Замена хранилища уровня управления
```bash
azdata bdc config replace --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Пример 3. Замена пула носителей, включая реплики (пул носителей)
```bash
azdata bdc config replace --config-file custom/cluster.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу с конфигурацией кластера больших данных, которую нужно задать, например custom/cluster.json
#### `--json-values -j`
Список пар "ключ–значение" с путями JSON и значениями: ключ1.подключ1=значение1,ключ2.подключ2=значение2. Вы можете указать значения JSON в коде, например key='{"тип":"кластер","имя":"тестовый-кластер"}', или предоставить путь к файлу, например key=./values.json. При замене условные выражения поддерживаются посредством библиотеки jsonpath.  Для этого путь должен начинаться с символа $. Это позволяет использовать такие условные конструкции, как -j $.ключ1.ключ2[?(@.key3=='некотороеЗначение'].ключ4=значение. Примеры приведены ниже. Дополнительные справочные сведения см. на сайте https://jsonpath.com/.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-config-patch"></a>azdata bdc config patch
Вносит исправление в файл конфигурации в соответствии с указанным файлом исправления. Дополнительные сведения о том, как следует составлять пути, см. на сайте http://jsonpatch.com/. При выполнении операции замены в пути могут использоваться условные выражения посредством библиотеки jsonpath https://jsonpath.com/. Все файлы исправлений JSON должны начинаться с ключа "patch", который указывает на массив исправлений с соответствующими операциями (добавление, замена, удаление), путями и значениями. Для операции удаления не требуется значение, только путь. См. примеры ниже.
```bash
azdata bdc config patch --config-file -c 
                        --patch-file -p
```
### <a name="examples"></a>Примеры
Пример 1. Замена порта одной конечной точки (конечной точки контроллера) с помощью файла исправления
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Пример 2. Замена хранилища уровня управления с помощью файла исправления
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Пример 3. Замена пула носителей, включая реплики (пул носителей), с помощью файла исправления
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу с конфигурацией кластера больших данных, которую нужно задать, например custom/cluster.json
#### `--patch-file -p`
Путь к файлу исправления JSON на основе библиотеки jsonpatch: http://jsonpatch.com/. Файл исправления JSON должен начинаться с ключа "patch", значением которого является массив операций исправления, подлежащих выполнению. Для пути операции исправления можно использовать точечную нотацию, например ключ1.ключ2 для большинства операций. Если необходимо выполнить операцию замены и для замены значения в массиве требуется условное выражение, используйте нотацию jsonpath, указав в начале пути символ $. Это позволяет использовать такие условные конструкции, как -j $.ключ1.ключ2[?(@.key3=='некотороеЗначение'].ключ4. См. примеры ниже. Дополнительные справочные сведения об условных выражениях см. на сайте https://jsonpath.com/.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в разделе [Установка [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]аздата для управления ](deploy-install-azdata.md).