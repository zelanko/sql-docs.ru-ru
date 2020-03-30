---
title: Справочник по azdata sql
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata sql.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f8fa1ca8df7f4d72c6df9b252d639f8771dee30c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74908740"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata sql shell](#azdata-sql-shell) | Интерфейс командной строки (CLI) баз данных SQL позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL.
[azdata sql query](#azdata-sql-query) | Команда query разрешает выполнение запроса T-SQL.
## <a name="azdata-sql-shell"></a>azdata sql shell
Интерфейс командной строки (CLI) баз данных SQL позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL.
```bash
azdata sql shell 
```
### <a name="examples"></a>Примеры
Пример командной строки для запуска интерактивного взаимодействия.
```bash
azdata sql shell
```
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
## <a name="azdata-sql-query"></a>azdata sql query
Команда query разрешает выполнение запроса T-SQL.
```bash
azdata sql query -q --database -d
```
### <a name="examples"></a>Примеры
Выбор списка имен таблиц.  По умолчанию используется база данных master.
```bash
azdata sql query -q 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--database -d`
База данных, в которой нужно выполнить запрос.  По умолчанию используется база данных master.
#### `-q`
Запрос T-SQL для выполнения.
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

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
