---
title: Справочник по azdata arc dc config
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata arc dc config.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 302235f43791f1be918f1e78114a40bcb23ea818
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90942833"
---
# <a name="azdata-arc-dc-config"></a>azdata arc dc config

Применяется к `azdata`

В следующей статье приводятся справочные сведения по командам **sql** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|Команда|Описание|
| --- | --- |
[azdata arc dc config init](#azdata-arc-dc-config-init) | Инициализирует профиль конфигурации контроллера данных, который можно использовать с командой control create.
[azdata arc dc config list](#azdata-arc-dc-config-list) | Выводит список доступных профилей конфигурации.
[azdata arc dc config add](#azdata-arc-dc-config-add) | Добавляет значение для пути JSON в файле конфигурации.
[azdata arc dc config remove](#azdata-arc-dc-config-remove) | Удаляет значение пути JSON в файле конфигурации.
[azdata arc dc config replace](#azdata-arc-dc-config-replace) | Заменяет значение пути JSON в файле конфигурации.
[azdata arc dc config patch](#azdata-arc-dc-config-patch) | Вносит исправление в файл конфигурации на основе файла исправления JSON.
## <a name="azdata-arc-dc-config-init"></a>azdata arc dc config init
Инициализирует профиль конфигурации контроллера данных, который можно использовать с командой control create. В аргументах можно указать определенный источник профиля конфигурации.
```bash
azdata arc dc config init [--path -p] 
                          [--source -s]  
                          
[--force -f]
```
### <a name="examples"></a>Примеры
Интерактивный процесс инициализации конфигурации контроллера данных — выводятся подсказки для ввода необходимых значений.
```bash
azdata arc dc config init
```
Команда arc dc config init с аргументами создает профиль конфигурации aks-dev-test в ./custom.
```bash
azdata arc dc config init --source aks-dev-test --path custom
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--path -p`
Путь к файлу, в который следует поместить профиль конфигурации; по умолчанию <cwd>/custom.
#### `--source -s`
Источник профиля конфигурации: ['azure-arc-aks-premium-storage', 'azure-arc-ake', 'azure-arc-openshift', 'azure-arc-gke', 'azure-arc-aks-default-storage', 'azure-arc-aks-dev-test', 'azure-arc-kubeadm', 'azure-arc-kubeadm-dev-test', 'azure-arc-eks', 'azure-arc-azure-openshift', 'azure-arc-aks-hci']
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-arc-dc-config-list"></a>azdata arc dc config list
Выводит список доступных профилей конфигурации для использования в `arc dc config init`.
```bash
azdata arc dc config list [--config-profile -c] 
                          
```
### <a name="examples"></a>Примеры
Выводит имена всех доступных профилей конфигурации.
```bash
azdata arc dc config list
```
Выводит код JSON определенного профиля конфигурации.
```bash
azdata arc dc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-profile -c`
Профиль конфигурации по умолчанию: ['azure-arc-aks-premium-storage', 'azure-arc-ake', 'azure-arc-openshift', 'azure-arc-gke', 'azure-arc-aks-default-storage', 'azure-arc-aks-dev-test', 'azure-arc-kubeadm', 'azure-arc-kubeadm-dev-test', 'azure-arc-eks', 'azure-arc-azure-openshift', 'azure-arc-aks-hci']
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
## <a name="azdata-arc-dc-config-add"></a>azdata arc dc config add
Добавляет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры выполняются в Bash.  Если используется другая оболочка командной строки, может потребоваться экранировать кавычки соответствующим образом.  В качестве альтернативы можно воспользоваться возможностями файла исправления.
```bash
azdata arc dc config add --path -p 
                         --json-values -j
```
### <a name="examples"></a>Примеры
Пример 1. Добавление хранилища контроллера данных.
```bash
azdata arc dc config add --path custom/control.json --json-values "spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь к файлу конфигурации контроллера данных, которую нужно установить, например, custom/cluster.json
#### `--json-values -j`
Список пар "ключ–значение" с путями JSON и значениями: ключ1.подключ1=значение1,ключ2.подключ2=значение2. Вы можете указать значения JSON в коде, например key='{"тип":"кластер","имя":"тестовый-кластер"}', или предоставить путь к файлу, например key=./values.json. При добавлении не поддерживаются условные выражения.  Если указываемое вами встроенное значение представляет собой пару "ключ — значение" с символами "=" и ",", необходимо экранировать эти символы.  Например, key1="key2\=val2\,key3\=val3". Примеры путей см. на сайте http://jsonpatch.com/.  Для доступа к массиву необходимо указать индекс, например ключ.0=значение
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
## <a name="azdata-arc-dc-config-remove"></a>azdata arc dc config remove
Удаляет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры выполняются в Bash.  Если используется другая оболочка командной строки, может потребоваться экранировать кавычки соответствующим образом.  В качестве альтернативы можно воспользоваться возможностями файла исправления.
```bash
azdata arc dc config remove --path -p 
                            --json-path -j
```
### <a name="examples"></a>Примеры
Пример 1. Удаление хранилища контроллера данных.
```bash
azdata arc dc config remove --path custom/control.json --json-path ".spec.storage"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь к файлу конфигурации контроллера данных, которую нужно установить, например custom/cluster.json
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-arc-dc-config-replace"></a>azdata arc dc config replace
Заменяет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры выполняются в Bash.  Если используется другая оболочка командной строки, может потребоваться экранировать кавычки соответствующим образом.  В качестве альтернативы можно воспользоваться возможностями файла исправления.
```bash
azdata arc dc config replace --path -p 
                             --json-values -j
```
### <a name="examples"></a>Примеры
Пример 1. Замена порта одной конечной точки (конечной точки контроллера данных).
```bash
azdata arc dc config replace --path custom/control.json --json-values "$.spec.endpoints[?(@.name=="Controller")].port=30080"
```
Пример 2. Замена хранилища контроллера данных.
```bash
azdata arc dc config replace --path custom/control.json --json-values "spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь к файлу конфигурации контроллера данных, которую нужно установить, например custom/cluster.json
#### `--json-values -j`
Список пар "ключ–значение" с путями JSON и значениями: ключ1.подключ1=значение1,ключ2.подключ2=значение2. Вы можете указать значения JSON в коде, например key='{"тип":"кластер","имя":"тестовый-кластер"}', или предоставить путь к файлу, например key=./values.json. При замене условные выражения поддерживаются посредством библиотеки jsonpath.  Для этого путь должен начинаться с символа $. Это позволяет использовать такие условные конструкции, как -j $.ключ1.ключ2[?(@.key3=='некотороеЗначение'].ключ4=значение. Если указываемое вами встроенное значение представляет собой пару "ключ — значение" с символами "=" и ",", необходимо экранировать эти символы.  Например, key1="key2\=val2\,key3\=val3". Примеры приведены ниже. Дополнительные справочные сведения см. на сайте https://jsonpath.com/.
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
## <a name="azdata-arc-dc-config-patch"></a>azdata arc dc config patch
Вносит исправление в файл конфигурации в соответствии с указанным файлом исправления. Дополнительные сведения о том, как следует составлять пути, см. на сайте http://jsonpatch.com/. При выполнении операции замены в пути могут использоваться условные выражения посредством библиотеки jsonpath https://jsonpath.com/. Все файлы исправлений JSON должны начинаться с ключа "patch", который указывает на массив исправлений с соответствующими операциями (добавление, замена, удаление), путями и значениями. Для операции удаления не требуется значение, только путь. См. примеры ниже.
```bash
azdata arc dc config patch --path 
                           --patch-file -p
```
### <a name="examples"></a>Примеры
Пример 1. Замена порта одной конечной точки (конечной точки контроллера данных) с помощью файла исправления.
```bash
azdata arc dc config patch --path custom/control.json --patch ./patch.json

    Patch File Example (patch.json):
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=="Controller")].port","value":30080}]}
```
Пример 2. Замена хранилища контроллера данных на файл исправления.
```bash
azdata arc dc config patch --path custom/control.json --patch ./patch.json

    Patch File Example (patch.json):
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path`
Путь к файлу конфигурации контроллера данных, которую нужно установить, например custom/cluster.json
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

Дополнительные сведения об установке инструмента **azdata** см. в разделе [Установка azdata](..\install\deploy-install-azdata.md).

