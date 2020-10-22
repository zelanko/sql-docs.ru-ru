---
title: Справочник по azdata arc resource-kind
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata arc resource-kind.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 68d6d4c30e43804c8c18a7dc36d0a9d53bcb5677
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358712"
---
# <a name="azdata-arc-resource-kind"></a>azdata arc resource-kind

Применяется к [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

В следующей статье приводятся справочные сведения по командам **sql** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|Команда|Описание|
| --- | --- |
[azdata arc resource-kind list](#azdata-arc-resource-kind-list) | Перечисляет доступные виды настраиваемых ресурсов для Arc, которые можно определять и создавать.
[azdata arc resource-kind get](#azdata-arc-resource-kind-get) | Получает файл шаблона для вида ресурса Arc.
## <a name="azdata-arc-resource-kind-list"></a>azdata arc resource-kind list
Перечисляет доступные виды настраиваемых ресурсов для Arc, которые можно определять и создавать. После перечисления вы можете получить файл шаблона, необходимый для определения или создания настраиваемого ресурса.
```bash
azdata arc resource-kind list 
```
### <a name="examples"></a>Примеры
Пример команды для перечисления доступных видов настраиваемых ресурсов для Arc.
```bash
azdata arc resource-kind list
```
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
## <a name="azdata-arc-resource-kind-get"></a>azdata arc resource-kind get
Получает файл шаблона для вида ресурса Arc.
```bash
azdata arc resource-kind get --kind -k 
                             [--dest -d]
```
### <a name="examples"></a>Примеры
Пример команды, позволяющей получить файл шаблона определения настраиваемого ресурса (CRD) для вида ресурса Arc.
```bash
azdata arc resource-kind get --kind sqldb
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--kind -k`
Вид ресурса Arc, для которого вам нужен файл шаблона.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--dest -d`
Каталог, в котором вы хотите разместить файлы шаблона.
`template`
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

Дополнительные сведения об установке средства **azdata** см. в разделе [Установка azdata](..\install\deploy-install-azdata.md).

