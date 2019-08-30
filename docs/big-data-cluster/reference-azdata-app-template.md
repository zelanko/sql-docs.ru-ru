---
title: Справочник по azdata app template
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata app template.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 07911616659a29df7f7fa6ce4d356a9c82789ae2
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153231"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Эта статья содержит справочную статью по **аздата**. 

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata app template list](#azdata-app-template-list) | Получение поддерживаемых шаблонов.
[azdata app template pull](#azdata-app-template-pull) | Скачивание поддерживаемых шаблонов.
## <a name="azdata-app-template-list"></a>azdata app template list
Получение поддерживаемых шаблонов из указанного репозитория GitHub [URL].
```bash
azdata app template list 
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
## <a name="azdata-app-template-pull"></a>azdata app template pull
Скачивание поддерживаемых шаблонов из указанного репозитория GitHub [URL].
```bash
azdata app template pull 
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

- Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

- Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
