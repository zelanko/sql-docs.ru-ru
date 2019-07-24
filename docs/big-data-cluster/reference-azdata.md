---
title: Справочник по аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8136c85f8c32e08423f3d199a021d4f60353b39
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425994"
---
# <a name="azdata"></a>аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье содержится справочник по средству **аздата** для [кластеров больших данных SQL Server 2019 (Предварительная версия)](big-data-cluster-overview.md). Дополнительные сведения об установке средства **аздата** см. в [статье Установка аздата для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
|[приложение аздата](reference-azdata-app.md) | Создание, удаление и запуск приложений, а затем управление ими. |
|[аздата BDC](reference-azdata-bdc.md) | Выбор, управление и работа с SQL Server кластерами больших данных. |
|[Записная книжка аздата](reference-azdata-notebook.md) | Команды для просмотра, запуска и управления записными книжками из терминала. |
[имя входа аздата](#azdata-login) | Войдите в конечную точку контроллера кластера.
[аздата Logout](#azdata-logout) | Выход из кластера.
|[аздата SQL](reference-azdata-sql.md) | Интерфейс командной строки SQL DB позволяет пользователю взаимодействовать с SQL Server через T-SQL. |
## <a name="azdata-login"></a>имя входа аздата
При развертывании кластера в процессе развертывания будет указана конечная точка контроллера, которую следует использовать для входа в систему.  Если вы не знакомы с конечной точкой контроллера, вы можете войти, указав конфигурацию KUBE кластера в вашей системе в расположении <user home>по умолчанию/.KUBE/config. или использовать KUBECONFIG env var, т. е. Export KUBECONFIG = path/to/. KUBE/config.
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>Примеры
Войдите в интерактивном режиме. Имя кластера всегда будет запрашиваться, если не указано в качестве аргумента. Если в системе заданы переменные CONTROLLER_USERNAME, CONTROLLER_PASSWORD и ACCEPT_EULA env, они не будут запрашиваться. Если у вас есть конфигурация KUBE в вашей системе или если вы используете KUBECONFIG env, чтобы указать путь к файлу конфигурации, в интерактивной среде сначала будет предпринята попытка использовать файл конфигурации, а затем появится сообщение о сбое настройки.
```bash
azdata login
```
Войдите в систему (не в интерактивном режиме). Войдите в систему, используя имя кластера, имя пользователя контроллера, конечную точку контроллера и набор принятия условий лицензионного соглашения в качестве аргументов. Необходимо задать переменную среды CONTROLLER_PASSWORD.  Если вы не хотите указывать конечную точку контроллера, создайте файл конфигурации KUBE на компьютере в расположении <user home>по умолчанию/.KUBE/config. или используйте KUBECONFIG env var, т. е. Export KUBECONFIG = path/to/. KUBE/config.
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Войдите в систему с помощью KUBE config на компьютере, а пер установите для CONTROLLER_USERNAME, CONTROLLER_PASSWORD и ACCEPT_EULA.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--cluster-name -n`
Имя кластера.
#### `--controller-username -u`
Пользователь учетной записи. Если вы не хотите использовать этот аргумент, вы можете задать переменную среды CONTROLLER_USERNAME.
#### `--controller-endpoint -e`
Конечная точка контроллера https://host:port кластера "". Если вы не хотите использовать этот аргумент, вы можете использовать конфигурацию KUBE на своем компьютере. Убедитесь, что файл конфигурации расположен в расположении <user home>по умолчанию/.KUBE/config. или используйте KUBECONFIG env.
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно задать для переменной среды ACCEPT_EULA значение Yes. Условия лицензии для этого продукта можно просмотреть по адресу https://aka.ms/azdata-eula.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-logout"></a>аздата Logout
Выход из кластера.
```bash
azdata logout 
```
### <a name="examples"></a>Примеры
Выйдите из этого пользователя.
```bash
azdata logout
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке средства **аздата** см. в [статье Установка аздата для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
