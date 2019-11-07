---
title: Справочник по контекстам azdata
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам контекста azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 36b670ee8485c2e8db58847e9439dfb5fa9920ce
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531680"
---
# <a name="azdata-context"></a>Контекст azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata context list](#azdata-context-list) | Список доступных контекстов в профиле пользователя.
[azdata context delete](#azdata-context-delete) | Удаление контекста с заданным пространством имен из профиля пользователя.
[azdata context set](#azdata-context-set) | Установка контекста с заданным пространством имен в качестве активного контекста в профиле пользователя.
## <a name="azdata-context-list"></a>azdata context list
Можно установить или удалить любой из этих контекстов с помощью команды `azdata context set` или `azdata context delete`. Для входа в новый контекст используется команда `azdata login`.
```bash
azdata context list [--active -a] 
  ```
### <a name="examples"></a>Примеры
Список всех доступных контекстов в профиле пользователя.
```bash
azdata context list
```
Список активных контекстов в профиле пользователя.
```bash
azdata context list --active
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--active -a`
Выводить только текущий активный контекст.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-context-delete"></a>azdata context delete
Если удаленный контекст был активен, пользователю нужно будет задать новый активный контекст. Для просмотра контекстов, доступных для установки или удаления, используется команда `azdata context list`
```bash
azdata context delete --namespace -n 
    ```
### Examples
Deletes contextNamespace from the user profile.
```bash
azdata context delete -n contextNamespace
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--namespace -n`
Пространство имен контекста, который нужно удалить.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-context-set"></a>azdata context set
Для просмотра контекстов, доступных для установки, используется команда `azdata context list`. Если никакие контексты не отображаются, необходимо создать контекст в профиле пользователя, выполнив вход с помощью команды `azdata login`. То, куда выполнен вход, станет активным контекстом. При входе в несколько сущностей можно переключаться между активными контекстами с помощью этой команды. Чтобы увидеть текущий активный контекст, используется команда `azdata context list --active`
```bash
azdata context set --namespace -n 
 ```
### <a name="examples"></a>Примеры
Установка contextNamespace в качестве активного контекста в профиле пользователя.
```bash
azdata context set -n contextNamespace
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--namespace -n`
Пространство имен контекста, который нужно установить.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
