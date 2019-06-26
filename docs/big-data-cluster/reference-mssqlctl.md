---
title: Справочник по mssqlctl
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2601d526710e6cf51de089f7879f0f5517bf86aa
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388666"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **mssqlctl** средство для [кластеров SQL Server 2019 больших данных (Предварительная версия)](big-data-cluster-overview.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
|[приложение mssqlctl](reference-mssqlctl-app.md) | Создание, удаление, запуска и управления приложениями. |
|[mssqlctl bdc](reference-mssqlctl-bdc.md) | Выберите, управление и работу больших кластерах данных SQL Server. |
|[mssqlctl hdfs](reference-mssqlctl-hdfs.md) | Модуль HDFS предоставляет команды для доступа к HDFS файловая система. |
[Имя входа mssqlctl](#mssqlctl-login) | Войдите в конечную точку кластера контроллера.
[mssqlctl выхода](#mssqlctl-logout) | Выйдите из кластера.
|[mssqlctl sql](reference-mssqlctl-sql.md) | Интерфейс командной строки SQL DB позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL. |
## <a name="mssqlctl-login"></a>Имя входа mssqlctl
При развертывании кластера будут перечислены во время развертывания, который следует использовать конечную точку контроллер с именем входа.  Если вы не знаете конечную точку контроллера, вы имеете права входа в систему за счет конфигурации kube кластера на компьютере в расположении по умолчанию <user home>/.kube/config или использовать KUBECONFIG env var, т. е. Экспорт KUBECONFIG=path/to/.kube/config.
```bash
mssqlctl login [--cluster-name -n] 
               [--controller-username -u]  
               [--controller-endpoint -e]  
               [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Войдите в интерактивном режиме. Имя кластера будет всегда быть запрошены Если не указано в качестве аргумента. Если у вас есть переменные env CONTROLLER_USERNAME CONTROLLER_PASSWORD и ACCEPT_EULA, заданные в вашей системе, они не запрашиваются. Если на компьютере установлен файл конфигурации kube или укажите путь к конфигурации с помощью KUBECONFIG env var, интерактивная сначала попытается использовать файл конфигурации и предложит вам при сбое в файле конфигурации.
```bash
mssqlctl login
```
Вход (не в интерактивном режиме). Войдите с помощью имени кластера, имя пользователя контроллера, контроллер конечной точки и принятия лицензионного соглашения в качестве аргументов. Переменная среды CONTROLLER_PASSWORD необходимо задать.  Если вы не хотите указывать конечную точку контроллера, подготовьте файл конфигурации kube в расположение по умолчанию на компьютере <user home>/.kube/config или использовать KUBECONFIG env var, т. е. Экспорт KUBECONFIG=path/to/.kube/config.
```bash
mssqlctl login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Войдите с помощью конфигурации kube на компьютере и env var для CONTROLLER_USERNAME CONTROLLER_PASSWORD и ACCEPT_EULA.
```bash
mssqlctl login -n ClusterName
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--cluster-name -n`
Имя кластера.
#### `--controller-username -u`
Учетная запись пользователя. Если вы не хотите использовать этот аргумент, можно задать переменную среды CONTROLLER_USERNAME.
#### `--controller-endpoint -e`
Конечная точка контроллера кластера "https://host:port «. Если вы не хотите использовать этот аргумент, можно использовать файл конфигурации kube на вашем компьютере. Убедитесь, файл конфигурации расположен в папке по умолчанию <user home>/.kube/config или используйте переменную среды KUBECONFIG
#### `--accept-eula -a`
Вы принимаете условия лицензионного соглашения? [Да/Нет]. Если вы не хотите использовать этот аргумент, можно задать переменную среды ACCEPT_EULA «Yes»
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