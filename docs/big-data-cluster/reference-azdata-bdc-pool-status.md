---
title: Справочник по azdata bdc pool status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc pool status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0a5925af4f16f2147988b2318880d9acec664c3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426134"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приводятся справочные сведения по командам **bdc pool status** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc pool status show](#azdata-bdc-pool-status-show) | Состояние пула.
## <a name="azdata-bdc-pool-status-show"></a>azdata bdc pool status show
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
Получение состояния вычислительного пула.
```bash
azdata bdc pool status show --kind compute --name default
```
Получение состояния главного пула.
```bash
azdata bdc pool status show --kind master --name default
```
Получение состояния пула spark.
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--kind -k`
Тип кластерного пула больших данных.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя кластерного пула больших данных.
`default`
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

Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
