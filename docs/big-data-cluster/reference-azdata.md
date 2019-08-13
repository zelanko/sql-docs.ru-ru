---
title: Справочник по azdata
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 24a72683c423661a2981e5a16941bcbc180ac6d1
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68894006"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приводятся справочные сведения по средству **azdata** для [кластеров больших данных SQL Server 2019 (предварительная версия)](big-data-cluster-overview.md). Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
|[azdata app](reference-azdata-app.md) | Создание, удаление и запуск приложений, а также управление ими. |
|[azdata bdc](reference-azdata-bdc.md) | Создание кластеров больших данных SQL, а также управление ими и обеспечение работы. |
|[azdata login](#azdata-login) | Вход в конечную точку контроллера кластера.
|[azdata logout](#azdata-logout) | Выход из кластера.

## <a name="azdata-login"></a>azdata login
При развертывании кластера в ходе развертывания будет отображаться конечная точка контроллера, которую следует использовать для входа в систему.  Если вы не знакомы с конечной точкой контроллера, вы можете войти в систему, указав конфигурацию KUBE кластера в вашей системе в расположении <user home>по умолчанию/.KUBE/config. или использовать KUBECONFIG env var, то есть Export KUBECONFIG = path/to/. KUBE/config.
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Вход в интерактивном режиме. Имя кластера будет запрашиваться всегда, кроме случаев, когда оно задано в качестве аргумента. Если в вашей системе заданы переменные среды CONTROLLER_USERNAME, CONTROLLER_PASSWORD и ACCEPT_EULA, соответствующий запрос не появляется. Если в вашей системе задана конфигурация KUBE или используется переменная среды KUBECONFIG для указания пути к конфигурации, интерактивный интерфейс сначала пробует использовать конфигурацию и только в случае сбоя отображает запрос.
```bash
azdata login
```
Вход не в интерактивном режиме. Выполните вход, указав в качестве аргументов имя кластера, имя пользователя контроллера, конечную точку контроллера, а также информацию о принятии условий лицензионного соглашения. Должна быть задана переменная среды CONTROLLER_PASSWORD.  Если вы не хотите указывать конечную точку контроллера, попросите файл конфигурации KUBE на компьютере в расположении <user home>по умолчанию/.KUBE/config. или используйте KUBECONFIG env var, то есть Export KUBECONFIG = path/to/. KUBE/config.
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Выполните вход с использованием конфигурации KUBE на компьютере с заданными переменными среды CONTROLLER_USERNAME, CONTROLLER_PASSWORD и ACCEPT_EULA.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--cluster-name -n`
Имя кластера.
#### `--controller-username -u`
Имя пользователя учетной записи. Если вы не хотите использовать этот аргумент, можно задать переменную среды CONTROLLER_USERNAME.
#### `--controller-endpoint -e`
Конечная точка контроллера кластера "https://host:port". Если вы не хотите использовать этот аргумент, можно использовать конфигурацию KUBE на компьютере. Убедитесь, что файл конфигурации расположен в расположении <user home>по умолчанию/.KUBE/config. или используйте KUBECONFIG env.
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". 
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см [http://jmespath.org/](http://jmespath.org/]) . в разделе.
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-logout"></a>azdata logout
Выход из кластера.
```bash
azdata logout 
```
### <a name="examples"></a>Примеры
Выход указанного пользователя из системы.
```bash
azdata logout
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см [http://jmespath.org/](http://jmespath.org/]) . в разделе.
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
