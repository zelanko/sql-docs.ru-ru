---
title: mssqlctl cluster config reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды кластере.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 74097057702ad32a803c440d92b0ed7c8f855880
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779420"
---
# <a name="mssqlctl-cluster-config"></a>Конфигурация кластера mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **кластера config** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[show config mssqlctl кластера](#mssqlctl-cluster-config-show) | Получает текущую конфигурацию SQL Server больших данных кластера.
[init config mssqlctl кластера](#mssqlctl-cluster-config-init) | Инициализирует Создание профиля конфигурации кластера, который может использоваться с кластером.
[Список config mssqlctl кластеров](#mssqlctl-cluster-config-list) | Приведен список вариантов файла конфигурации.
[раздел конфигурации кластера mssqlctl](reference-mssqlctl-cluster-config-section.md) | Команды для работы с отдельных разделов файла конфигурации кластера.
## <a name="mssqlctl-cluster-config-show"></a>mssqlctl cluster config show
Возвращает текущего файла конфигурации SQL Server больших данных кластера и выводит его в целевой файл или довольно выводит на консоль.
```bash
mssqlctl cluster config show [--target -t] 
                             [--force -f]
```
### <a name="examples"></a>Примеры
Показать конфигурации кластера в консоли
```bash
mssqlctl cluster config show
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Сохраните результат в выходной файл. Значение по умолчанию — направляются в stdout.
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
## <a name="mssqlctl-cluster-config-init"></a>init config mssqlctl кластера
Инициализирует Создание профиля конфигурации кластера, который может использоваться с кластером. Конкретный источник конфигурации профиля можно указать аргументы из 3 вариантов.
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]  
                             [--force -f]
```
### <a name="examples"></a>Примеры
Пошаговое руководство init конфигурации кластера - будет получать запросы на необходимые значения.
```bash
mssqlctl cluster config init
```
Кластер init конфигурации с аргументами, создает профиль конфигурации aks разработки и тестирования в. / custom.json.
```bash
mssqlctl cluster config init --src aks-dev-test.json --target custom.json
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Путь к файлу место config профиль установлен, значение по умолчанию — cwd с custom-config.json.
#### `--src -s`
Источник конфигурации профиля: ["aks-dev-test.json", "kubeadm-dev-test.json", "minikube-dev-test.json"]
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
## <a name="mssqlctl-cluster-config-list"></a>mssqlctl cluster config list
Приведен список вариантов файл конфигурации, доступные для использования при инициализации конфигурации кластера
```bash
mssqlctl cluster config list [--config-file -c] 
                             
```
### <a name="examples"></a>Примеры
Показывает все имена профилей конфигурации.
```bash
mssqlctl cluster config list
```
Показано json профиля конфигурации.
```bash
mssqlctl cluster config list --config-file aks-dev-test.json
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-file -c`
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