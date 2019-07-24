---
title: Справочник по состоянию пула BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам состояния пула BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0a5925af4f16f2147988b2318880d9acec664c3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426134"
---
# <a name="azdata-bdc-pool-status"></a>Состояние пула BDC аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки на команды **состояния пула BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Отображение состояния пула BDC аздата](#azdata-bdc-pool-status-show) | Состояние пула.
## <a name="azdata-bdc-pool-status-show"></a>Отображение состояния пула BDC аздата
Состояние пула.
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>Примеры
Получение состояния пула носителей.
```bash
azdata bdc pool status show --kind storage --name default
```
Получение состояния пула данных.
```bash
azdata bdc pool status show --kind data --name default
```
Возвращает состояние пула вычислений.
```bash
azdata bdc pool status show --kind compute --name default
```
Возвращает состояние главного пула.
```bash
azdata bdc pool status show --kind master --name default
```
Получение состояния пула Spark.
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--kind -k`
Тип пула кластера больших данных.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя пула кластеров больших данных.
`default`
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

Дополнительные сведения об установке средства **аздата** см. в [статье Установка аздата для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
