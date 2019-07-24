---
title: Справочник по шаблону приложения аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам шаблона приложения аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3b257a2bacc56a7907ab0d25f492ed0ebd605543
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426334"
---
# <a name="azdata-app-template"></a>шаблон приложения аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Следующая статья содержит справочник по командам **шаблона приложения** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[список шаблонов приложений аздата](#azdata-app-template-list) | Получение поддерживаемых шаблонов.
[Извлечение шаблона приложения аздата](#azdata-app-template-pull) | Скачайте Поддерживаемые шаблоны.
## <a name="azdata-app-template-list"></a>список шаблонов приложений аздата
Получение поддерживаемых шаблонов по указанному репозиторию GitHub [URL].
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>Примеры
Получение всех шаблонов в расположении репозитория шаблонов по умолчанию.
```bash
azdata app template list
```
Получение всех шаблонов в другом расположении репозитория.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--url -u`
Укажите другое расположение репозитория шаблонов. Параметры https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-template-pull"></a>Извлечение шаблона приложения аздата
Скачайте Поддерживаемые шаблоны по указанному репозиторию GitHub [URL].
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>Примеры
Скачайте все шаблоны в расположение репозитория шаблонов по умолчанию.
```bash
azdata app template pull
```
Скачайте все шаблоны в другом расположении репозитория.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Скачайте отдельный шаблон по имени.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя шаблона. Полный список поддерживаемых шаблонов намесрун`azdata app template list`
#### `--url -u`
Укажите другое расположение репозитория шаблонов. Параметры https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Место размещения шаблона каркаса приложения.
`./templates`
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
