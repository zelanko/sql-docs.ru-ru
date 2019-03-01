---
title: mssqlctl cluster config reference
titleSuffix: SQL Server 2019 big data clusters
description: Справочная статья по mssqlctl команды кластере.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 26e93151a1150bbbbd1798b38486ca5b01aaab1d
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018440"
---
# <a name="mssqlctl-cluster-config"></a>mssqlctl конфигурации кластера

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