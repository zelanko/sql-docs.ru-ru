---
title: Справочник по azdata bdc pool status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc pool status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eafc72c6d86d38eabd26b735a9d5dab967e2e6be
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653485"
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

Дополнительные сведения об установке средства **аздата** см. в разделе [Установка [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]аздата для управления ](deploy-install-azdata.md).
