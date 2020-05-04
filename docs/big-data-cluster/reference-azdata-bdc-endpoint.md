---
title: Справочник по azdata bdc endpoint
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc endpoint.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 71f52b8312518cf669751d50dcc857c3d892bd98
ms.sourcegitcommit: db1b6153f0bc2d221ba1ce15543ecc83e1045453
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2020
ms.locfileid: "82588080"
---
# <a name="azdata-bdc-endpoint"></a>azdata bdc endpoint

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по команде `bdc endpoint` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc endpoint list](#azdata-bdc-endpoint-list) | Список конечных точек для кластера больших данных.
## <a name="azdata-bdc-endpoint-list"></a>azdata bdc endpoint list
Список конечных точек для кластера больших данных.

```bash
azdata bdc endpoint list [--endpoint-name -e] 
```

### <a name="optional-parameters"></a>Необязательные параметры

#### `--endpoint-name -e`

Имя конечной точки кластера больших данных.

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
