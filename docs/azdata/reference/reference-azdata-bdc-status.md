---
title: Справочник по azdata bdc status
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: daf3115a7ccdd73f86dbaa9766049cd5be1e1eb9
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733943"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
| Команда | Описание |
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
Состояние BDC со всеми включенными экземплярами ресурсов.
```bash
azdata bdc status show --all
```
Состояние BDC служб, включая ресурс управления.
```bash
azdata bdc status show --resource control
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--resource -r`
Получение служб, связанных с этим ресурсом.
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](../install/deploy-install-azdata.md).
