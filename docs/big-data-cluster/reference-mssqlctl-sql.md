---
title: Справочник по sql mssqlctl
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды sql.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 536d4712a6ccb288ca60c038a37e99c2be8a5eba
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394206"
---
# <a name="mssqlctl-sql"></a>mssqlctl sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **sql** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[оболочка mssqlctl sql](#mssqlctl-sql-shell) | Интерфейс командной строки SQL DB позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL.
[mssqlctl sql-запрос](#mssqlctl-sql-query) | Команды запроса допускает выполнение запроса T-SQL.
## <a name="mssqlctl-sql-shell"></a>оболочка mssqlctl sql
Интерфейс командной строки SQL DB позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL.
```bash
mssqlctl sql shell 
```
### <a name="examples"></a>Примеры
Пример командной строки, чтобы запустить интерактивный интерфейс.
```bash
mssqlctl sql shell
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-sql-query"></a>mssqlctl sql-запрос
Команды запроса допускает выполнение запроса T-SQL.
```bash
mssqlctl sql query --database -d 
                   -q
```
### <a name="examples"></a>Примеры
Выберите список имен таблиц.  По умолчанию используется база данных master.
```bash
mssqlctl sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--database -d`
База данных для выполнения запроса в.  По умолчанию является master.
#### `-q`
Выполняемый запрос T-SQL.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).