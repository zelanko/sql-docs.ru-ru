---
title: Справочник по azdata app template
description: Справочная статья по командам azdata app template.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: da1b98649eeb48d5ae2d6ca05e61da53f519e944
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75251053"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по командам `app template` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[`azdata app template list`](#azdata-app-template-list) | Получение поддерживаемых шаблонов.
[`azdata app template pull`](#azdata-app-template-pull) | Скачивание поддерживаемых шаблонов.
## <a name="azdata-app-template-list"></a>azdata app template list
Получение поддерживаемых шаблонов из указанного репозитория GitHub [URL].
```bash
azdata app template list [--url -u]
```
### <a name="examples"></a>Примеры
Получение всех шаблонов из расположения репозитория шаблонов по умолчанию.
```bash
azdata app template list
```
Получение всех шаблонов из другого расположения репозитория.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--url -u`
Указание другого расположения репозитория шаблонов. По умолчанию: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-template-pull"></a>azdata app template pull
Скачивание поддерживаемых шаблонов из указанного репозитория GitHub [URL].
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>Примеры
Скачивание всех шаблонов из расположения репозитория шаблонов по умолчанию.
```bash
azdata app template pull
```
Скачивание всех шаблонов из другого расположения репозитория.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Скачивание отдельного шаблона по имени.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя шаблона. Чтобы получить полный список имен поддерживаемых шаблонов, выполните команду `azdata app template list`.
#### `--url -u`
Указание другого расположения репозитория шаблонов. По умолчанию: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Место для размещения шаблона основы приложения.
`./templates`
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

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
