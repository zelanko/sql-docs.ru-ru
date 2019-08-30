---
title: Справочник по состоянию SQL BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам состояния SQL BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c5c2cdd924f266400125080d21d0461d5f599190
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158259"
---
# <a name="azdata-bdc-sql-status"></a>состояние SQL BDC аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Эта статья содержит справочную статью по **аздата**. 

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Отображение состояния SQL BDC аздата](#azdata-bdc-sql-status-show) | Состояние службы SQL-Server.
## <a name="azdata-bdc-sql-status-show"></a>Отображение состояния SQL BDC аздата
Состояние службы SQL-Server.
```bash
azdata bdc sql status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Примеры
Возвращает состояние службы SQL.
```bash
azdata bdc sql status show
```
Возвращает состояние службы SQL со всеми экземплярами.
```bash
azdata bdc sql status show --all
```
Возвращает состояние главного ресурса в службе SQL.
```bash
azdata bdc sql status show --resource master
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--resource -r`
Получить этот ресурс в этой службе.
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

- Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
