---
title: Справочник по azdata bdc spark status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc spark status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 971854997519e4ef9b1e11d0063da1bbc2c583e4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243502"
---
# <a name="azdata-bdc-spark-status"></a>azdata bdc spark status

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
| Команда | Описание |
| --- | --- |
[azdata bdc spark status show](#azdata-bdc-spark-status-show) | Состояние службы Spark.
## <a name="azdata-bdc-spark-status-show"></a>azdata bdc spark status show
Состояние службы Spark.
```bash
azdata bdc spark status show [--resource -r] 
                             [--all -a]
```
### <a name="examples"></a>Примеры
Получение состояния службы Spark.
```bash
azdata bdc spark status show
```
Получение состояния службы Spark со всеми экземплярами.
```bash
azdata bdc spark status show --all
```
Получение состояния ресурса хранилища в составе службы Spark.
```bash
azdata bdc spark status show --resource storage-0
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--resource -r`
Получение ресурса в этой службе.
#### `--all -a`
Отображение всех экземпляров каждого ресурса в службе.
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

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
