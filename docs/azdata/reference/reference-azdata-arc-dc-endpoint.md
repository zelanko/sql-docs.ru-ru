---
title: Справочник по azdata arc dc endpoint
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata arc dc endpoint.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ea53bb8faef2534034a41422a83af1f16b81a5bf
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358812"
---
# <a name="azdata-arc-dc-endpoint"></a>azdata arc dc endpoint

Применяется к [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

В следующей статье приводятся справочные сведения по командам **sql** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|Команда|Описание|
| --- | --- |
[azdata arc dc endpoint list](#azdata-arc-dc-endpoint-list) | Выводит список конечных точек контроллера данных.
## <a name="azdata-arc-dc-endpoint-list"></a>azdata arc dc endpoint list
Выводит список конечных точек контроллера данных.
```bash
azdata arc dc endpoint list [--endpoint-name -e] 
                            
```
### <a name="examples"></a>Примеры
Выводит список конечных точек контроллера данных в определенном пространстве имен.
```bash
azdata arc dc endpoint list --namespace <ns>
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--endpoint-name -e`
Выводит список конечных точек контроллера данных Arc.
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

