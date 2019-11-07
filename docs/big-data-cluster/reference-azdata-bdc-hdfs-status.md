---
title: Справка по azdata bdc hdfs status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc hdfs status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f3548feb06b05699750ce5c088c05c4e3cc67d57
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531785"
---
# <a name="azdata-bdc-hdfs-status"></a>azdata bdc hdfs status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc hdfs status show](#azdata-bdc-hdfs-status-show) | Состояние службы HDFS.
## <a name="azdata-bdc-hdfs-status-show"></a>azdata bdc hdfs status show
Состояние службы HDFS.
```bash
azdata bdc hdfs status show [--resource -r] 
                            [--all -a]
```
### <a name="examples"></a>Примеры
Получение состояния службы HDFS.
```bash
azdata bdc hdfs status show
```
Получение состояния службы HDFS со всеми экземплярами.
```bash
azdata bdc hdfs status show --all
```
Получение состояния ресурса хранилища в службе HDFS.
```bash
azdata bdc hdfs status show --resource storage-0
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
