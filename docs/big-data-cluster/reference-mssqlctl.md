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
ms.openlocfilehash: be1ece46bd171370a91273c832bf89a0bf426cd3
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018370"
---
# <a name="mssqlctl"></a>mssqlctl

В следующей статье приведены ссылки для **mssqlctl** средство для кластеров SQL Server 2019 больших данных (Предварительная версия).

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