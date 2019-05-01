---
title: Справочник по шаблонам приложений mssqlctl
titleSuffix: SQL Server big data clusters
description: Справочная статья по команд шаблона mssqlctl приложения.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0b4cbae0ba35c0cef777b3535b2012ab78f8e6da
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473452"
---
# <a name="mssqlctl-app-template"></a>Шаблон приложения mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **шаблон приложения** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Список шаблонов mssqlctl приложения](#mssqlctl-app-template-list) | Получите поддерживаемые шаблоны.
[mssqlctl приложения шаблона на включение внесенных изменений](#mssqlctl-app-template-pull) | Скачайте поддерживаемые шаблоны.
## <a name="mssqlctl-app-template-list"></a>Список шаблонов mssqlctl приложения
Получите поддерживаемые шаблоны в разделе указанный репозиторий github [URL].
```bash
mssqlctl app template list [--url -u] 
                           
```
### <a name="examples"></a>Примеры
Получите все шаблоны в расположении по умолчанию шаблон репозитория.
```bash
mssqlctl app template list
```
Получите все шаблоны в расположении другого репозитория.
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--url -u`
Укажите расположение репозитория другой шаблон. Значение по умолчанию: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="mssqlctl-app-template-pull"></a>mssqlctl приложения шаблона на включение внесенных изменений
Скачайте поддерживаемые шаблоны в разделе указанный репозиторий github [URL].
```bash
mssqlctl app template pull [--name -n] 
                           [--url -u]  
                           [--destination -d]
```
### <a name="examples"></a>Примеры
Загрузите все шаблоны в расположении по умолчанию шаблон репозитория.
```bash
mssqlctl app template pull
```
Загрузите все шаблоны в расположении другого репозитория.
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
Скачайте отдельного шаблона по имени.
```bash
mssqlctl app template pull --name ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя шаблона. Полный список off namesrun поддерживаемых шаблона `mssqlctl app template list`
#### `--url -u`
Укажите расположение репозитория другой шаблон. Значение по умолчанию: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Где разместить шаблон скелет приложения.
`./templates`
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

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).