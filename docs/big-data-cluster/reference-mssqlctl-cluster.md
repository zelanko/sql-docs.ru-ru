---
title: mssqlctl cluster reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды кластере.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c3a15fb9658f25977542754d6479b09b97323f53
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993330"
---
# <a name="mssqlctl-cluster"></a>Кластер mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **кластера** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание кластера mssqlctl](#mssqlctl-cluster-create) | Создание кластера.
[mssqlctl cluster delete](#mssqlctl-cluster-delete) | Удаление кластера.
[mssqlctl конфигурации кластера](reference-mssqlctl-cluster-config.md) | Команды для настройки кластера.
[mssqlctl cluster endpoint](reference-mssqlctl-cluster-endpoint.md) | Команды конечных точек.
[состояние кластера mssqlctl](reference-mssqlctl-cluster-status.md) | Состояние команды.
[Отладка кластера mssqlctl](reference-mssqlctl-cluster-debug.md) | Команды отладки.
[mssqlctl cluster storage-pool](reference-mssqlctl-cluster-storage-pool.md) | Управление пулы носителей кластера.
## <a name="mssqlctl-cluster-create"></a>Создание кластера mssqlctl
Создайте кластер SQL Server больших данных — конфигурации kube необходим в вашей системе, а также следующие переменные среды [«CONTROLLER_USERNAME», «CONTROLLER_PASSWORD», «DOCKER_USERNAME», «DOCKER_PASSWORD», «MSSQL_SA_PASSWORD», «KNOX_PASSWORD»].
```bash
mssqlctl cluster create [--config-file -c] 
                        [--accept-eula -a]  
                        [--node-label -l]  
                        [--force -f]
```
### <a name="examples"></a>Примеры
Пошаговое руководство для развертывания кластера - будет получать запросы на необходимые значения.
```bash
mssqlctl cluster create
```
Развертывание кластера с аргументами.
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json
```
Развертывание кластера с аргументами - без вывода сообщений, предоставляется как force, который используется флаг.
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json --force
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-file -c`
Кластер профиля конфигурации, используемый для развертывания кластера: ["aks-dev-test.json", "kubeadm-dev-test.json", "minikube-dev-test.json"]
#### `--accept-eula -a`
Вы принимаете условия лицензионного соглашения? [Да/Нет]. Если вы не хотите использовать этот аргумент, можно задать переменную среды ACCEPT_EULA «Yes»
#### `--node-label -l`
Метка узла кластера с позволяют указать, какие узлы для развертывания.
#### `--force -f`
Принудительное создание, пользователь не будут запрошены все значения, и все проблемы, которые будут печататься как часть stderr.
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
## <a name="mssqlctl-cluster-delete"></a>mssqlctl cluster delete
Удалить кластер SQL Server больших данных — конфигурации kube необходим в вашей системе, а также следующие переменные среды [«CONTROLLER_USERNAME», «CONTROLLER_PASSWORD»].
```bash
mssqlctl cluster delete --name -n 
                        [--force -f]
```
### <a name="examples"></a>Примеры
Удаление кластера, где контроллер имя пользователя и пароль уже установлены в среде system.
```bash
mssqlctl cluster delete --name <cluster_name>
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя кластера, используемые для пространств имен kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Принудительное удаление кластера.
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
