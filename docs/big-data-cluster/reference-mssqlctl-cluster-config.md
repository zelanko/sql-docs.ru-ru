---
title: mssqlctl cluster config reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды кластере.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 57b77e83994f8471e677ba2ba367acc48a66cddd
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860025"
---
# <a name="mssqlctl-cluster-config"></a>Конфигурация кластера mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **кластера config** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a id="commands"></a> Команды

|||
|---|---|
| [Получить](#get) | Получите кластера. |

## <a id="get"></a> mssqlctl cluster config get

Получите кластера.

```
mssqlctl cluster config get
   --name
   --output-file
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя кластера, используемые для пространств имен kubernetes. Обязательный. |
| **--выходного файла - f** | Сохраните результат в выходной файл. Обязательный. |

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).