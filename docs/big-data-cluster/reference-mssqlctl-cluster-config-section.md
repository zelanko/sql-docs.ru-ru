---
title: mssqlctl cluster config section reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по команды раздела конфигурации mssqlctl кластера.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d5a793e7d0fcaf782a09a4981491ef0a8d90ab5a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759141"
---
# <a name="mssqlctl-cluster-config-section"></a>Раздел конфигурации кластера mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **кластера в разделе конфигурации** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[получить mssqlctl в разделе конфигурации кластера](#mssqlctl-cluster-config-section-get) | Получает раздел из файла конфигурации.
[mssqlctl cluster config section set](#mssqlctl-cluster-config-section-set) | Задает раздел файла конфигурации.
## <a name="mssqlctl-cluster-config-section-get"></a>mssqlctl cluster config section get
Получает указанный раздел из файла конфигурации, выбранного в соответствии с json для заданного пути.
```bash
mssqlctl cluster config section get --json-path -j 
                                    --config-file -f  
                                    [--target -t]
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--json-path -j`
Путь ключа json, который приводит к раздел или значение из файла конфигурации, т. е. key1.key2.key3. Использует язык запросов jsonpath, https://github.com/h2non/jsonpath-ng, например: -j "$. spec.pools [? () @.spec.type == "Master")]... конечные точки
#### `--config-file -f`
Путь к файлу конфигурации кластера.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Поместить путь к файлу место файла раздела.
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
## <a name="mssqlctl-cluster-config-section-set"></a>mssqlctl cluster config section set
Задает указанный раздел в файле конфигурации, выбранного в соответствии с json для заданного пути.
```bash
mssqlctl cluster config section set --config-file -f 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--config-file -f`
Путь к файлу конфигурации кластера файла конфигурации вы бы хотели задать
### <a name="optional-parameters"></a>Необязательные параметры
#### `--json-values -j`
Список пара значение ключа пути json для значений: key1.subkey1=value1,key2.subkey2=value2. Можно предоставить встроенные значения json такие как: key = "{«kind»: «кластера», «name»: «test-cluster»}" или укажите путь к файлу, например key=./values.json
#### `--patch-file -p`
Путь к файлу json patch, основанного на библиотеке jsonpatch и jsonpath: https://github.com/stefankoegl/python-json-patch , https://github.com/h2non/jsonpath-ng -простой пример: {«patch»: [{«op»: «добавить», «path»: «metadata.name», «value»: «test»}, {«op»: «добавить», «path»: «metadata.array», «value»: [1, 2, 3]}]} Включить ключ «patch» и имеют значение свойства быть массивом исправлений, которую требуется сделать.  Таким образом он будет выполняться. Более сложный пример: {«patch»: [{«op»: «replace», «path»: «$. spec.pools [? () @.spec.type == "Master")]... конечные точки», «value»: {«name»: «Новую конечную точку»}}]}
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