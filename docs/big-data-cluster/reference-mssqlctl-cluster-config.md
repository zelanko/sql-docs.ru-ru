---
title: mssqlctl cluster config reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды кластере.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3a4693c5ffb68ad555d97d02f983fadf4e6bbd9a
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774668"
---
# <a name="mssqlctl-cluster-config"></a>Конфигурация кластера mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **кластера config** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Получение конфигурации кластера mssqlctl](#mssqlctl-cluster-config-get) | Получить конфигурацию кластера - kube конфигурации необходим в вашей системе.
[init config mssqlctl кластера](#mssqlctl-cluster-config-init) | Инициализирует конфигурацию кластера.
[Список config mssqlctl кластеров](#mssqlctl-cluster-config-list) | Приведен список вариантов файла конфигурации.
[раздел конфигурации кластера mssqlctl](reference-mssqlctl-cluster-config-section.md) | Команды для работы с использованием отдельных разделов файла конфигурации.
## <a name="mssqlctl-cluster-config-get"></a>mssqlctl cluster config get
Получает текущий файл конфигурации SQL Server больших данных кластера.
```bash
mssqlctl cluster config get --name -n 
                            [--output-file -f]
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя кластера, используемые для пространств имен kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--output-file -f`
Сохраните результат в выходной файл. Значение по умолчанию — направляются в stdout.
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
## <a name="mssqlctl-cluster-config-init"></a>init config mssqlctl кластера
Инициализирует файла конфигурации кластера для пользователя, в зависимости от типа указанное значение по умолчанию.
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Путь к файлу местоположение файла конфигурации размещены, значение по умолчанию — cwd с custom-config.json.
#### `--src -s`
Источник конфигурации: ["aks-dev-test.json", "kubeadm-dev-test.json", "minikube-dev-test.json"]
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
## <a name="mssqlctl-cluster-config-list"></a>mssqlctl cluster config list
Приведен список вариантов файл конфигурации, доступные для использования при инициализации конфигурации кластера
```bash
mssqlctl cluster config list [--config-file -f] 
                             
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-file -f`
Файла конфигурации по умолчанию: ["aks-dev-test.json", "kubeadm-dev-test.json", "minikube-dev-test.json"]
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