---
title: mssqlctl bdc config reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl bdc команды.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f57ba87ea7cbd770380497bd340b5eaa4d80f29c
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394166"
---
# <a name="mssqlctl-bdc-config"></a>mssqlctl bdc config

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **bdc config** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[mssqlctl bdc config show](#mssqlctl-bdc-config-show) | Получает текущую конфигурацию кластера больших данных.
[mssqlctl bdc config init](#mssqlctl-bdc-config-init) | Инициализирует больших данных кластера, создайте профиль конфигурации, который может использоваться с кластером.
[mssqlctl bdc config list](#mssqlctl-bdc-config-list) | Приведен список вариантов профиля конфигурации.
[раздел config mssqlctl bdc](reference-mssqlctl-bdc-config-section.md) | Команды для работы с отдельными разделами профиля конфигурации кластера больших данных.
## <a name="mssqlctl-bdc-config-show"></a>mssqlctl bdc config show
Получает текущий профиль конфигурации кластера больших данных и выводит его в целевой каталог или довольно выводит на консоль.
```bash
mssqlctl bdc config show [--target -t] 
                         [--force -f]
```
### <a name="examples"></a>Примеры
Показать BDC конфигурации в консоли
```bash
mssqlctl bdc config show
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
## <a name="mssqlctl-bdc-config-init"></a>mssqlctl bdc config init
Инициализирует больших данных кластера, создайте профиль конфигурации, который может использоваться с кластером. Конкретный источник конфигурации профиля можно указать аргументы из 3 вариантов.
```bash
mssqlctl bdc config init [--target -t] 
                         [--source -s]  
                         [--force -f]
```
### <a name="examples"></a>Примеры
Интерактивные возможности init BDC приложения config - будут получать запросы необходимые значения.
```bash
mssqlctl bdc config init
```
Init config BDC с аргументами, создает профиль конфигурации aks разработки и тестирования в. / пользовательский.
```bash
mssqlctl bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--target -t`
Путь к файлу место config профиль установлен, значение по умолчанию — cwd с custom-config.json.
#### `--source -s`
Источник конфигурации профиля: [«aks-dev-test», «kubeadm-dev-test», «minikube — разработка и тестирование»]
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
## <a name="mssqlctl-bdc-config-list"></a>mssqlctl bdc config list
Приведен список вариантов конфигурации профиля для использования в `bdc config init`
```bash
mssqlctl bdc config list [--config-profile -c] 
                         
```
### <a name="examples"></a>Примеры
Показывает все имена профилей конфигурации.
```bash
mssqlctl bdc config list
```
Показано json профиля конфигурации.
```bash
mssqlctl bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-profile -c`
Профиль конфигурации по умолчанию: [«aks-dev-test», «kubeadm-dev-test», «minikube — разработка и тестирование»]
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