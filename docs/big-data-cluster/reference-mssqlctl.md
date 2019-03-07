---
title: Справочник по mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Справочная статья по mssqlctl команды.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d15b4149fe336b173452030ec67fb7f229e6ae3d
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527287"
---
# <a name="mssqlctl"></a>mssqlctl

В следующей статье приведены ссылки для **mssqlctl** средство для [кластеров SQL Server 2019 больших данных (Предварительная версия)](big-data-cluster-overview.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).

## <a id="commands"></a> Команды

|||
|---|---|
| [Приложение](reference-mssqlctl-app.md) | Создание, удаление, запуска и управления приложениями. |
| [Кластера](reference-mssqlctl-cluster.md) | Выберите, управление и работу кластеров. |
| [Имя входа](#login) | Войдите кластер. |
| [Выход из системы](#logout) | Выйдите из кластера. |
| [Хранилища](reference-mssqlctl-storage.md) | Управление хранилищем кластера. |

## <a id="login"></a> Имя входа mssqlctl

Войдите кластер.

```
mssqlctl login
   --endpoint
   --password
   --username
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|---|---|
|**--конечной точки -e**| Кластер узла и порта (ex) `http://host:port"`. |
|**--пароль -p**| Пароль учетных данных. |
|**--username -u**| Учетная запись пользователя. |

### <a name="examples"></a>Примеры

Войдите в интерактивном режиме.

```
mssqlctl login
```

Войдите с помощью имени пользователя и пароля.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret
```

Войдите с помощью имени пользователя, пароль и конечная точка кластера.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```

## <a id="logout"></a> mssqlctl выхода

Выйдите из кластера.

```
mssqlctl logout
   --username
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--username -u** | Пользователь учетной записи, если она отсутствует, выхода текущей активной учетной записи. |

### <a name="examples"></a>Примеры

Выход этого пользователя.

```
mssqlctl logout --username admin
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).