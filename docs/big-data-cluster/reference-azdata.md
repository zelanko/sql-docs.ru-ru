---
title: Справочник по azdata
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 94adabb2ace2f5619abd700b2652aa7d88f3e1aa
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74822342"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Справочная статья, в которой описаны команды `azdata`.

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
|[azdata bdc](reference-azdata-bdc.md) | Создание кластеров больших данных SQL, а также управление ими и обеспечение работы. |
|[azdata app](reference-azdata-app.md) | Создание, удаление и запуск приложений, а также управление ими. |
[azdata login](#azdata-login) | Войдите на конечную точку контроллера кластера и задайте его пространство имен в качестве активного контекста. Чтобы использовать пароль при входе, необходимо задать переменную среды AZDATA_PASSWORD.
[azdata logout](#azdata-logout) | Выход из кластера.
|[azdata context](reference-azdata-context.md) | Команды управления контекстом. |
|[azdata control](reference-azdata-control.md) | Создание, удаление уровней управления и управление ими. |
|[azdata sql](reference-azdata-sql.md) | Интерфейс командной строки (CLI) баз данных SQL позволяет пользователю взаимодействовать с SQL Server с помощью T-SQL. |
|[azdata notebook](reference-azdata-notebook.md) | Команды для просмотра, запуска записных книжек и управления ими из терминала. |
## <a name="azdata-login"></a>azdata login
Если кластер развернут, выводит список конечных точек контроллера в процессе развертывания, которые следует использовать для входа.  Если вам не известна конечная точка контроллера, вы можете выполнить вход с использованием конфигурации KUBE кластера в системе, которая по умолчанию располагается в каталоге <user home>/.kube/config, или переменной среды KUBECONFIG, то есть экспортировать KUBECONFIG=path/to/.kube/config.  При входе в систему пространство имен этого кластера будет установлено в ваш активный контекст.
```bash
azdata login [--auth] 
             [--endpoint -e]  
             [--accept-eula -a]  
             [--namespace -n]  
             [--username -u]  
             [--principal -p]
```
### <a name="examples"></a>Примеры
Вход с использованием обычной проверки подлинности.
```bash
azdata login --auth basic --username johndoe --endpoint https://<ip or domain name>:30080            
```
Вход с использованием Active Directory.
```bash
azdata login --auth ad --endpoint https://<ip or domain name>:30080                
```
Вход с использованием Active Directory с явным субъектом.
```bash
azdata login --auth ad --principal johndoe@COSTOSO.COM --endpoint https://<ip or domain name>:30080
```
Вход в интерактивном режиме. Имя кластера будет запрашиваться всегда, кроме случаев, когда оно задано в качестве аргумента. Если в вашей системе заданы переменные среды AZDATA_USERNAME, AZDATA_PASSWORD и ACCEPT_EULA, соответствующий запрос не появляется. Если в вашей системе задана конфигурация KUBE или используется переменная среды KUBECONFIG для указания пути к конфигурации, интерактивный интерфейс сначала пробует использовать конфигурацию и только в случае сбоя отображает запрос.
```bash
azdata login
```
Вход не в интерактивном режиме. Выполните вход, указав в качестве аргументов имя кластера, имя пользователя контроллера, конечную точку контроллера, а также информацию о принятии условий лицензионного соглашения. Должна быть задана переменная среды AZDATA_PASSWORD.  Если вы не хотите указывать конечную точку контроллера, вы можете использовать конфигурацию KUBE в системе, которая по умолчанию располагается в каталоге <user home>/.kube/config, или переменную среды KUBECONFIG, то есть экспортировать KUBECONFIG=path/to/.kube/config.
```bash
azdata login --namespace ClusterName --username johndoe@contoso.com  --endpoint https://<ip or domain name>:30080 --accept-eula yes
```
Выполните вход с использованием конфигурации KUBE на компьютере и с заданными переменными среды AZDATA_USERNAME, AZDATA_PASSWORD и ACCEPT_EULA.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--auth`
Стратегия проверки подлинности. Обычная проверка подлинности или проверка подлинности Active Directory. По умолчанию используется обычная проверка подлинности.
#### `--endpoint -e`
Конечная точка контроллера кластера "https://host:port". Если вы не хотите использовать этот аргумент, можно использовать конфигурацию KUBE на компьютере. Убедитесь, что конфигурация располагается в заданном по умолчанию месте (<user home>/.kube/config) или используйте переменную среды KUBECONFIG.
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". Условия лицензии для этого продукта можно просмотреть по адресу https://aka.ms/eula-azdata-en.
#### `--namespace -n`
Пространство имен уровня управления кластером.
#### `--username -u`
Имя пользователя учетной записи. Если вы не хотите использовать этот аргумент, можно задать переменную среды AZDATA_USERNAME.
#### `--principal -p`
Ваша область Kerberos. В большинстве случаев область Kerberos — это ваше доменное имя прописными буквами.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
