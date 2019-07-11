---
title: Справочник по mssqlctl bdc
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl bdc команды.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 96ecf1c987baffec0ff71b8b6ef5eccb204b3108
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727487"
---
# <a name="mssqlctl-bdc"></a>mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **bdc** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание mssqlctl bdc](#mssqlctl-bdc-create) | Создание кластера больших данных.
[mssqlctl bdc delete](#mssqlctl-bdc-delete) | Удаление кластера больших данных.
[mssqlctl bdc config](reference-mssqlctl-bdc-config.md) | Команды для настройки.
[mssqlctl bdc endpoint](reference-mssqlctl-bdc-endpoint.md) | Команды конечных точек.
[состояние mssqlctl bdc](reference-mssqlctl-bdc-status.md) | Состояние команды.
[mssqlctl bdc отладки](reference-mssqlctl-bdc-debug.md) | Команды отладки.
[mssqlctl bdc-пула носителей](reference-mssqlctl-bdc-storage-pool.md) | Команды пулов хранения.
[элемент управления mssqlctl bdc](reference-mssqlctl-bdc-control.md) | Команды управления.
[пул mssqlctl bdc](reference-mssqlctl-bdc-pool.md) | Команды пулов.
## <a name="mssqlctl-bdc-create"></a>Создание mssqlctl bdc
Создайте кластер SQL Server больших данных — конфигурации kube необходим в вашей системе, а также следующие переменные среды [«CONTROLLER_USERNAME», «CONTROLLER_PASSWORD», «DOCKER_USERNAME», «DOCKER_PASSWORD», «MSSQL_SA_PASSWORD», «KNOX_PASSWORD»].
```bash
mssqlctl bdc create [--config-profile -c] 
                    [--accept-eula -a]  
                    [--node-label -l]  
                    [--force -f]
```
### <a name="examples"></a>Примеры
BDC развертывания интерактивное — будут получать запросы необходимые значения.
```bash
mssqlctl bdc create
```
Развертывание BDC с аргументами.
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test
```
Развертывание BDC с аргументами - без вывода сообщений, предоставляется как force, который используется флаг.
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test --force
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--config-profile -c`
Профиль конфигурации BDC, используемый для развертывания кластера: [«aks-dev-test», «kubeadm-dev-test», «minikube — разработка и тестирование»]
#### `--accept-eula -a`
Вы принимаете условия лицензионного соглашения? [Да/Нет]. Если вы не хотите использовать этот аргумент, можно задать переменную среды ACCEPT_EULA «Yes»
#### `--node-label -l`
BDC метка узла, позволяют указать, какие узлы для развертывания.
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
## <a name="mssqlctl-bdc-delete"></a>mssqlctl bdc delete
Удалить кластер SQL Server больших данных — конфигурации kube необходим в вашей системе, а также следующие переменные среды [«CONTROLLER_USERNAME», «CONTROLLER_PASSWORD»].
```bash
mssqlctl bdc delete --name -n 
                    [--force -f]
```
### <a name="examples"></a>Примеры
Удаление BDC, где контроллера имя пользователя и пароль уже настраиваются в системной среде.
```bash
mssqlctl bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя каталога бизнес-данных, используемое для пространства имен kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Выполните принудительное удаление BDC.
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
