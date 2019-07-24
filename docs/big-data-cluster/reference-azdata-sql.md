---
title: Справочник по SQL аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам SQL аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 90512592901fcf83e4697b5eefc80a6df7aeb032
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426024"
---
# <a name="azdata-sql"></a>аздата SQL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье содержится справочник по командам **SQL** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[оболочка SQL аздата](#azdata-sql-shell) | Интерфейс командной строки SQL DB позволяет пользователю взаимодействовать с SQL Server через T-SQL.
[SQL аздата, запрос](#azdata-sql-query) | Команда запроса разрешает выполнение запроса T-SQL.
## <a name="azdata-sql-shell"></a>оболочка SQL аздата
Интерфейс командной строки SQL DB позволяет пользователю взаимодействовать с SQL Server через T-SQL.
```bash
azdata sql shell 
```
### <a name="examples"></a>Примеры
Пример командной строки для запуска интерактивного интерфейса.
```bash
azdata sql shell
```
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
## <a name="azdata-sql-query"></a>SQL аздата, запрос
Команда запроса разрешает выполнение запроса T-SQL.
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>Примеры
Выберите список имен таблиц.  База данных по умолчанию имеет значение master.
```bash
azdata sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--database -d`
База данных для выполнения запроса в.  Значение по умолчанию — Master.
#### `-q`
Запрос T-SQL для выполнения.
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
