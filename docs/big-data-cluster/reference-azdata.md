---
title: Справочник по azdata
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f4cecd27865b069764944021639ae1a2e553d76
ms.sourcegitcommit: 0c6c1555543daff23da9c395865dafd5bb996948
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70304720"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
|[azdata notebook](reference-azdata-notebook.md) | Команды для просмотра, запуска записных книжек и управления ими из терминала. |
|[azdata sql](reference-azdata-sql.md) | Интерфейс командной строки (CLI) баз данных SQL позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL. |
|[azdata app](reference-azdata-app.md) | Создание, удаление и запуск приложений, а также управление ими. |
|[azdata bdc](reference-azdata-bdc.md) | Создание кластеров больших данных SQL, а также управление ими и обеспечение работы. |
|[элемент управления аздата](reference-azdata-control.md) | Создание, удаление и управление плоскостями управления. |
[azdata login](#azdata-login) | Вход в конечную точку контроллера кластера.
[azdata logout](#azdata-logout) | Выход из кластера.
## <a name="azdata-login"></a>azdata login
Если кластер развернут, выводит список конечных точек контроллера в процессе развертывания, которые следует использовать для входа.  Если вам не известна конечная точка контроллера, вы можете выполнить вход с использованием конфигурации KUBE кластера в системе, которая по умолчанию располагается в каталоге <user home>/.kube/config, или переменной среды KUBECONFIG, то есть экспортировать KUBECONFIG=path/to/.kube/config.
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
Вход не в интерактивном режиме. Выполните вход, указав в качестве аргументов имя кластера, имя пользователя контроллера, конечную точку контроллера, а также информацию о принятии условий лицензионного соглашения. Должна быть задана переменная среды CONTROLLER_PASSWORD.  Если вы не хотите указывать конечную точку контроллера, вы можете использовать конфигурацию KUBE в системе, которая по умолчанию располагается в каталоге <user home>/.kube/config, или переменную среды KUBECONFIG, то есть экспортировать KUBECONFIG=path/to/.kube/config.
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
Конечная точка контроллера кластера "https://host:port". Если вы не хотите использовать этот аргумент, можно использовать конфигурацию KUBE на компьютере. Убедитесь, что конфигурация располагается в заданном по умолчанию месте (<user home>/.kube/config) или используйте переменную среды KUBECONFIG.
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
