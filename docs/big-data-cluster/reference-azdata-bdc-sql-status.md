---
title: Справка по azdata bdc sql status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc sql status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 81c1a84ea196e7f986f9427605de575f59a3152c
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531713"
---
# <a name="azdata-bdc-sql-status"></a>azdata bdc sql status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc sql status show](#azdata-bdc-sql-status-show) | Состояние службы SQL Server.
## <a name="azdata-bdc-sql-status-show"></a>azdata bdc sql status show
Состояние службы SQL Server.
```bash
azdata bdc sql status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Примеры
Получение состояния службы SQL.
```bash
azdata bdc sql status show
```
Получение состояния службы SQL со всеми экземплярами.
```bash
azdata bdc sql status show --all
```
Получение состояния главного ресурса в службе SQL.
```bash
azdata bdc sql status show --resource master
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
