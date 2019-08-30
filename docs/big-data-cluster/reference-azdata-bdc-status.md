---
title: Справочник по azdata bdc status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 712a5ac51f13450fe5cf6b8cc13400d5666eb4a0
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155199"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Эта статья содержит справочную статью по **аздата**. 

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | Показывает состояние BDC.
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
Показывает состояние BDC.
```bash
azdata bdc status show [--resource -r] 
                       [--all -a]
```
### <a name="examples"></a>Примеры
Состояние кластера больших данных, куда пользователь выполнил вход.
```bash
azdata bdc status show
```
Состояние BDC со всеми экземплярами ресурсов, которые входят в состав.
```bash
azdata bdc status show --all
```
Состояние BDC служб, включающих управляющий ресурс.
```bash
azdata bdc status show --resource control
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--resource -r`
Получите службы, связанные с этим ресурсом.
#### `--all -a`
Отображение всех экземпляров каждого ресурса в службах.
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
