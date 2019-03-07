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
ms.openlocfilehash: 130d3019d49deb7851696f6a1db2f77040734b31
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527217"
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
   --accept-eula
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