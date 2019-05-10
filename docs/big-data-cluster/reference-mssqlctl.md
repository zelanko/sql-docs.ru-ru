---
title: Справочник по mssqlctl
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ebd3b63d641c77dae1afbff21264ec4fe34df4d0
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775500"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **mssqlctl** средство для [кластеров SQL Server 2019 больших данных (Предварительная версия)](big-data-cluster-overview.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
|[приложение mssqlctl](reference-mssqlctl-app.md) | Создание, удаление, запуска и управления приложениями. |
|[mssqlctl кластера](reference-mssqlctl-cluster.md) | Выберите, управление и работу кластеров. |
[Имя входа mssqlctl](#mssqlctl-login) | Войдите кластер.
[mssqlctl выхода](#mssqlctl-logout) | Выйдите из кластера.
|[mssqlctl хранилища](reference-mssqlctl-storage.md) | Управление хранилищем кластера. |
## <a name="mssqlctl-login"></a>Имя входа mssqlctl
Войдите кластер.
```bash
mssqlctl login [--username -u] 
               [--password -p]  
               [--endpoint -e]
```
### <a name="examples"></a>Примеры
Войдите в интерактивном режиме.
```bash
mssqlctl login
```
Войдите с помощью имени пользователя и пароля.
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret
```
Войдите с помощью имени пользователя, пароль и конечная точка кластера.
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--username -u`
Учетная запись пользователя.
#### `--password -p`
Пароль учетных данных.
#### `--endpoint -e`
Кластер узла и порта (например,)) "http://host:port«.
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
## <a name="mssqlctl-logout"></a>mssqlctl выхода
Выйдите из кластера.
```bash
mssqlctl logout 
```
### <a name="examples"></a>Примеры
Выход этого пользователя.
```bash
mssqlctl logout
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

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).