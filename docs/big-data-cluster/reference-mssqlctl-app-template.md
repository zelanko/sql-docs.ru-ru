---
title: Справочник по шаблонам приложений mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Справочная статья по команд шаблона mssqlctl приложения.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 16583ba970bfc13312864ea2e9d2571b04c20fcb
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018500"
---
# <a name="mssqlctl-app-template"></a>Шаблон приложения mssqlctl

В следующей статье приведены ссылки для **шаблон приложения** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a id="commands"></a> Команды

|||
|---|---|
| [list](#list) | Получите поддерживаемые шаблоны. |
| [По запросу](#pull) | Скачайте поддерживаемые шаблоны. |

## <a id="list"></a> Список шаблонов mssqlctl приложения

Получите поддерживаемые шаблоны.

```
mssqlctl app template list
   --url
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--URL-адрес -u** | Укажите расположение репозитория другой шаблон. Значение по умолчанию — https://github.com/Microsoft/sql-server-samples.git. |

### <a name="examples"></a>Примеры

Получите все шаблоны в расположении по умолчанию шаблон репозитория.

```
mssqlctl app template list
```

Получите все шаблоны в расположении другого репозитория.

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

## <a id="pull"></a> mssqlctl приложения шаблона на включение внесенных изменений

Скачайте поддерживаемые шаблоны.

```
mssqlctl app template pull
   --destination
   --name
   --url
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--назначения -d** | Где разместить шаблон скелет приложения.  Значение по умолчанию:. / шаблоны. |
| **--name - n** | Имя шаблона. Для получения полного списка off имена поддерживаемых шаблонов запустите `mssqlctl app template list`. |
| **--URL-адрес -u** | Укажите расположение репозитория другой шаблон. По умолчанию:
https://github.com/Microsoft/sql-server-samples.git. |

### <a name="examples"></a>Примеры

Загрузите все шаблоны в расположении по умолчанию шаблон репозитория.

```
mssqlctl app template pull
```

Загрузите все шаблоны в расположении другого репозитория.

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

Скачайте отдельного шаблона по имени.

```
mssqlctl app template pull --name ssis
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).