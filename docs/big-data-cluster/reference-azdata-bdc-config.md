---
title: Справочник по конфигурации BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed777391af3695da69e04c0e2693cff912c76771
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426294"
---
# <a name="azdata-bdc-config"></a>Конфигурация аздата BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки на команды **конфигурации BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Инициализация конфигурации BDC аздата](#azdata-bdc-config-init) | Инициализирует профиль конфигурации кластера больших данных, который можно использовать с созданием кластера.
[список конфигурации BDC аздата](#azdata-bdc-config-list) | Выводит список доступных вариантов профиля конфигурации.
[Просмотр конфигурации BDC аздата](#azdata-bdc-config-show) | Отображается текущая конфигурация или Конфигурация локального файла BDC, например Custom или Cluster. JSON.
[Добавление конфигурации BDC аздата](#azdata-bdc-config-add) | Добавьте значение для пути JSON в файл конфигурации.
[Удаление конфигурации BDC аздата](#azdata-bdc-config-remove) | Удалите значение для пути JSON в файле конфигурации.
[Замена конфигурации BDC аздата](#azdata-bdc-config-replace) | Замените значение для пути JSON в файле конфигурации.
[исправление конфигурации BDC аздата](#azdata-bdc-config-patch) | Исправление файла конфигурации на основе файла обновления JSON.
## <a name="azdata-bdc-config-init"></a>Инициализация конфигурации BDC аздата
Инициализирует профиль конфигурации кластера больших данных, который можно использовать с созданием кластера. Определенный источник профиля конфигурации можно указать в аргументах из трех вариантов.
```bash
azdata bdc config init [--target -t] 
                       [--source -s]  
                       [--force -f]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Интерактивный процесс инициализации конфигурации BDC. Вы получите запрос на ввод необходимых значений.
```bash
azdata bdc config init
```
Инициализация конфигурации BDC с аргументами создает профиль конфигурации AKS-dev-test в./кустом.
```bash
azdata bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Путь к файлу, в котором вы хотите разместить профиль конфигурации, по умолчанию КВД с custom-config. JSON.
#### `--source -s`
Источник профиля конфигурации: ["AKS-dev-test", "кубеадм-dev-test", "minikube-dev-test"]
#### `--force -f`
Принудительная перезапись целевого файла.
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно задать для переменной среды ACCEPT_EULA значение Yes. Условия лицензии для этого продукта можно просмотреть по адресу https://aka.ms/azdata-eula.
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
## <a name="azdata-bdc-config-list"></a>список конфигурации BDC аздата
Список доступных вариантов профиля конфигурации для использования в`bdc config init`
```bash
azdata bdc config list [--config-profile -c] 
                       [--type -t]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Отображает все доступные имена профилей конфигурации.
```bash
azdata bdc config list
```
Отображает JSON определенного профиля конфигурации.
```bash
azdata bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-profile -c`
Профиль конфигурации по умолчанию: ["AKS-dev-test", "кубеадм-dev-test", "minikube-dev-test"]
#### `--type -t`
Тип конфигурации, который вы хотите увидеть.
`cluster`
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно задать для переменной среды ACCEPT_EULA значение Yes. Условия лицензии для этого продукта можно просмотреть по адресу https://aka.ms/azdata-eula.
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
## <a name="azdata-bdc-config-show"></a>Просмотр конфигурации BDC аздата
Отображается текущая конфигурация или Конфигурация локального файла BDC, например Custom или Cluster. JSON. Команда также может иметь путь JSON, если вы хотите получить только раздел.  Можно также указать целевой файл для вывода в.  Если целевой файл не указан, он будет просто выведен в терминал.
```bash
azdata bdc config show [--config-file -c] 
                       [--target -t]  
                       [--json-path -j]  
                       [--force -f]
```
### <a name="examples"></a>Примеры
Отображение конфигурации BDC в консоли
```bash
azdata bdc config show
```
В локальном файле конфигурации получите значение в конце простого пути к ключу JSON.
```bash
azdata bdc config show --config-file custom-config/cluster.json --json-path 'metadata.name' --target section.json
```
В локальном файле конфигурации получает значение в конце пути к ключу JSON с условным значением
```bash
azdata bdc config show --config-file custom-config/cluster.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-file -c`
Путь к файлу конфигурации кластера больших данных, если вы не хотите использовать конфигурацию кластера, в которую вы куррентлилогжеде, например Custom или Cluster. JSON
#### `--target -t`
Выходной файл, в котором сохраняется результат. По умолчанию: направляется в stdout.
#### `--json-path -j`
Путь к ключу JSON, который ведет к нужному разделу или значению из конфигурации, например key1. Key2. key3. Использует язык запросов jsonpath, https://jsonpath.com/ например:-j ' $. spec. Pools [? ( @.spec.type = = "Master")].. конеч
#### `--force -f`
Принудительная перезапись целевого файла.
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
## <a name="azdata-bdc-config-add"></a>Добавление конфигурации BDC аздата
Добавляет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры приведены в bash.  При использовании другой командной строки имейте в виду, что может потребоваться ескапекуотатионс соответствующим образом.  Кроме того, вы можете использовать функцию файла исправления.
```bash
azdata bdc config add --config-file -c 
                      --json-values -j
```
### <a name="examples"></a>Примеры
Пример 1. Добавление хранилища плоскости управления.
```bash
azdata bdc config add --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу конфигурации кластера больших данных, который вы хотите задать, например Custom или Cluster. JSON.
#### `--json-values -j`
Список пар "ключ-значение" путей JSON к значениям: key1. subkey1 = value1, Key2. subkey2 = value2. Можно указать встроенные значения JSON, такие как key = "{" род ":" Cluster "," имя ":" Test-Cluster "}" или указать путь к файлу, например Key =./валуес.жсон. Add не поддерживает условия.  Ознакомьтесь http://jsonpatch.com/ с примерами того, как должен выглядеть путь.  Если вы хотите получить доступ к массиву, это необходимо сделать, указав индекс, например Key. 0 = значение.
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
## <a name="azdata-bdc-config-remove"></a>Удаление конфигурации BDC аздата
Удаляет значение по пути JSON в файле конфигурации.  Все приведенные ниже примеры приведены в bash.  При использовании другой командной строки имейте в виду, что может потребоваться ескапекуотатионс соответствующим образом.  Кроме того, вы можете использовать функцию файла исправления.
```bash
azdata bdc config remove --config-file -c 
                         --json-path -j
```
### <a name="examples"></a>Примеры
Пример 1. Удаление хранилища плоскости управления.
```bash
azdata bdc config remove --config-file custom/control.json --json-path '.spec.storage'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу конфигурации кластера больших данных, который вы хотите задать, например Custom или Cluster. JSON.
#### `--json-path -j`
Список путей JSON на основе библиотеки жсонпатч, которая указывает, какие значения следует удалить, например: key1. subkey1, Key2. subkey2. Remove не поддерживает условия. Ознакомьтесь http://jsonpatch.com/ с примерами того, как должен выглядеть путь.  Если вы хотите получить доступ к массиву, это необходимо сделать, указав индекс, например Key. 0 = значение.
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
## <a name="azdata-bdc-config-replace"></a>Замена конфигурации BDC аздата
Заменяет значение в пути JSON в файле конфигурации.  Все ексамплесбелов выданы в bash.  При использовании другой командной строки имейте в виду, что может потребоваться ескапекуотатионс соответствующим образом.  Кроме того, вы можете использовать функцию файла исправления.
```bash
azdata bdc config replace --config-file -c 
                          --json-values -j
```
### <a name="examples"></a>Примеры
Ex 1. Замените порт одной конечной точки (конечной точки контроллера).
```bash
azdata bdc config replace --config-file custom/control.json --json-values '$.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Пример 2. Замена хранилища плоскости управления.
```bash
azdata bdc config replace --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Пример 3. Замена хранилища пула, включая реплики (пул носителей).
```bash
azdata bdc config replace --config-file custom/cluster.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу конфигурации кластера больших данных, который вы хотите задать, например Custom или Cluster. JSON.
#### `--json-values -j`
Список пар "ключ-значение" путей JSON к значениям: key1. subkey1 = value1, Key2. subkey2 = value2. Можно указать встроенные значения JSON, такие как key = "{" род ":" Cluster "," имя ":" Test-Cluster "}" или указать путь к файлу, например Key =./валуес.жсон. Replace поддерживает условия в библиотеке jsonpath.  Чтобы использовать этот параметр, Начните путь с $. Это позволит выполнить условное действие, например-j $. key1. key2 [? ( @.key3= = ' someValue ']. Key4 = значение. Вы можете увидеть примеры ниже. Дополнительную помощь можно найти в следующих статьях: https://jsonpath.com/
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
## <a name="azdata-bdc-config-patch"></a>исправление конфигурации BDC аздата
Исправление файла конфигурации в соответствии с заданным файлом исправлений. http://jsonpatch.com/ Дополнительные сведения о том, как следует составить эти пути, см. в этом разделе. Операция Replace может использовать условные выражения в пути из-за библиотеки https://jsonpath.com/ jsonpath. Все файлы с исправлениями JSON должны начинаться с ключа Patch, который содержит массив исправлений с соответствующими операциями (Add, Replace, Remove), Path и value. Операция "Remove" не требует значения, просто пути. Ознакомьтесь с приведенными ниже примерами.
```bash
azdata bdc config patch --config-file -c 
                        --patch-file -p
```
### <a name="examples"></a>Примеры
Ex 1. Замените порт одной конечной точки (конечной точки контроллера) на файл исправления.
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Пример 2. Замена хранилища плоскости управления файлом исправления.
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Пример 3. Замена хранилища пула, включая реплики (пул носителей) с файлом исправлений.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -c`
Путь к файлу конфигурации кластера больших данных, который вы хотите задать, например Custom или Cluster. JSON.
#### `--patch-file -p`
Путь к JSON-файлу исправления, который основан на библиотеке жсонпатч: http://jsonpatch.com/. Необходимо запустить JSON-файл исправления с ключом «Patch», значение которого представляет собой массив операций исправления, которые вы собираетесь сделать. В качестве пути к операции исправления можно использовать точечную нотацию, например key1. key2, для большинства операций. Если вы хотите выполнить операцию Replace и заменить значение в массиве, для которого требуется условное выражение, используйте нотацию jsonpath, начинающуюся с символа $. Это позволит выполнить условное действие, например $. key1. key2 [? ( @.key3= = ' someValue ']. Key4. Ознакомьтесь с приведенными ниже примерами. Дополнительные сведения о условных выражениях см. в https://jsonpath.com/ разделе.
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