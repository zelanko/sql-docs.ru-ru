---
title: mssqlctl cluster reference
titleSuffix: SQL Server 2019 big data clusters
description: Справочная статья по mssqlctl команды кластере.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 088168e3400feea78fb9b92fa120f1140714ab34
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018430"
---
# <a name="mssqlctl-cluster"></a>mssqlctl кластера

В следующей статье приведены ссылки для **кластера** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a id="commands"></a> Команды

|||
|---|---|
| [Создание](#create) | Создание кластера. |
| [delete](#delete) | Удаление кластера. |
| [конфигурации](reference-mssqlctl-cluster-config.md) | Команды для настройки кластера. |
| [debug](reference-mssqlctl-cluster-debug.md) | Команды отладки. |

## <a id="create"></a> Создание кластера mssqlctl

Создание кластера.

```
mssqlctl cluster create
   --name
   [--accept-eula]
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя кластера, используемые для пространств имен kubernetes. |
| **--принимать лицензионное соглашение - e** | Вы принимаете условия лицензионного соглашения? \[Да/Нет\].  Допустимые значения: нет, Да. Обязательный. |

## <a id="delete"></a> mssqlctl cluster delete

Удаление кластера.

```
mssqlctl cluster delete
   --name
   [--force]
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя кластера, используемые для пространств имен kubernetes. Обязательный. |
| **--force -f** | Принудительное удаление кластера. |

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).