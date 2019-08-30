---
title: Справочник по состоянию приложения BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам состояния приложения BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7ebf442b3bf87960d081bfe4b0867cdd082ec22a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158099"
---
# <a name="azdata-bdc-app-status"></a>состояние приложения BDC аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Эта статья содержит справочную статью по **аздата**. 

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Отображение состояния приложения BDC аздата](#azdata-bdc-app-status-show) | Состояние службы приложений.
## <a name="azdata-bdc-app-status-show"></a>Отображение состояния приложения BDC аздата
Состояние службы приложений.
```bash
azdata bdc app status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Примеры
Получение состояния службы приложений.
```bash
azdata bdc app status show
```
Получение состояния службы приложений со всеми экземплярами.
```bash
azdata bdc app status show --all
```
Получение состояния ресурса апппрокси в службе приложений.
```bash
azdata bdc app status show --resource appproxy
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
